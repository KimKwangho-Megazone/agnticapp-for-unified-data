# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository

Fork of `microsoft/agentic-applications-for-unified-data-foundation-solution-accelerator`. `origin` points to the fork (`KimKwangho-Megazone`), `upstream` points to the original Microsoft repo. Work in feature branches pushed to `origin`; don't assume push access to `upstream`.

## What this solution is

An Azure Developer CLI (azd) solution accelerator that lets users query structured enterprise data (sales/products/customers) in natural language. Microsoft Fabric (SQL Database in Fabric / Lakehouse) holds the data, an AI Foundry Agent (via Microsoft Agent Framework) does orchestration and NL→SQL, and a React web app provides the chat UI. Two architecture options exist: (1) Fabric + Copilot Studio surfaced in Teams, (2) Fabric + Microsoft Foundry + App Service web app (the one the local dev stack in this repo runs). See `documents/TechnicalArchitecture.md`.

## Repo layout

- `src/App/` — React + TypeScript frontend (Fluent UI, Redux Toolkit, Chart.js/D3 for visualizations, MSAL for auth).
- `src/api/python/` — FastAPI backend (one of two interchangeable backend implementations).
- `src/api/dotnet/` — ASP.NET Core 8 backend (the other implementation, same API surface). **Only one backend runs at a time**; both talk to the same frontend and Fabric SQL / AI Foundry backends.
- `src/test/api/python/` — unit tests for the Python backend (pytest).
- `src/api/dotnet/tests/CsApi.Tests/` — unit tests for the .NET backend.
- `tests/e2e-test/` — Playwright/pytest end-to-end UI tests against a deployed environment.
- `scripts/` — numbered pipeline (`00`–`09`) that builds the whole solution end-to-end: generate sample data → create Fabric Lakehouse/Ontology → load data → generate agent prompt → upload docs to AI Search → upload to Azure SQL (non-Fabric mode) → create the Foundry agent → test the agent → configure deployed-app roles. `00_build_solution.py` is the orchestrator and accepts `--from <step>` to resume.
- `infra/` — Bicep IaC (`main.bicep` is the entry point) plus `infra/scripts/` (post-provision automation: agent creation, Fabric item creation, SQL/search index setup, Copilot Studio agent setup — these are what `azd`'s postprovision hooks in `azure.yaml` invoke).
- `documents/` — setup/deployment/architecture docs; read `LocalDevelopmentSetup.md` and `DeploymentGuide.md` before changing dev/deploy workflows.
- `workshop/` — mkdocs-based workshop site (separate `requirements.txt`).

## Backend architecture (both implementations)

Both backends expose the same REST surface and share these concerns:
- `/api/*` — chat endpoints, backed by an `agent_framework.ChatAgent` (Agent Framework) wired to an Azure AI Foundry agent (`AzureAIClient`). Agent Framework is the Python package name in `chat.py`/`history_sql.py`; the .NET equivalent lives in `Services/AgentFrameworkService.cs`.
- `/history/*` — chat history persisted via Cosmos DB (Python: `history.py`).
- `/historyfab/*` — chat history persisted in the Fabric/Azure SQL database (Python: `history_sql.py`; .NET: `Repositories/SqlConversationRepository.cs` + `Controllers/HistoryFabController.cs`), connected via `pyodbc`/ADO.NET using Azure AD auth (no stored credentials — managed identity / `AzureCliCredential` locally).
- `/health` — liveness check present in both.
- Auth: both backends read identity from headers set upstream (Easy Auth / App Service auth in deployment; local dev uses a sample user — see `src/api/python/auth/`). .NET uses `HeaderUserContextAccessor`/`UserContextMiddleware` for the same purpose.
- Telemetry: OpenTelemetry + Azure Monitor, enabled when `APPLICATIONINSIGHTS_CONNECTION_STRING` is set.
- `AZURE_ENV_ONLY` / `AZURE_ENV_DEPLOY_APP` / `IS_WORKSHOP` env vars toggle between "Fabric SQL mode" and "Azure-SQL-only mode", and workshop-specific deploy behavior — check these before assuming Fabric is present.

## Commands

### Python backend (`src/api/python/`)
```bash
cd src/api/python
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp .env.sample .env   # then fill in Azure config
python app.py          # http://localhost:8000, docs at /docs
```

### .NET backend (`src/api/dotnet/`)
```bash
cd src/api/dotnet
cp appsettings.json.sample appsettings.json   # then fill in Azure config
dotnet restore
dotnet run              # or `dotnet watch run`; http://localhost:8000, swagger at /swagger
```

### Frontend (`src/App/`)
```bash
cd src/App
npm install
npm start                # dev server on http://localhost:3000, proxies to backend
npm run build
npm test                 # react-scripts test (Jest + Testing Library)
```

### Python backend tests (run from repo root — `pytest.ini` sets `pythonpath = ./src/api/python`)
```bash
pytest src/test/api/python                       # all backend unit tests
pytest src/test/api/python/test_chat.py           # single file
pytest src/test/api/python/test_chat.py::test_name -v   # single test
pytest -m unittest                                 # marker-filtered run (markers: unittest, functional, azure — see pytest.ini)
pytest src/test/api/python --cov=src/api/python --cov-report=term-missing   # with coverage (CI enforces 80%)
```
Note: `src/test/api/python/conftest.py` mocks `azure.ai.*` / `agent_framework` modules to work around SDK import/version issues — real Azure calls are never made in unit tests.

### .NET backend tests
```bash
cd src/api/dotnet
dotnet test                                                    # all tests
dotnet test --filter "FullyQualifiedName~ChatControllerTests"  # by class/name
dotnet test --settings tests/CsApi.Tests/coverlet.runsettings --collect:"XPlat Code Coverage"   # with coverage (CI enforces 80%)
```

### Lint
```bash
flake8 --config=.flake8 src/api/python
```

### E2E tests (`tests/e2e-test/`, against a deployed environment)
```bash
cd tests/e2e-test
pip install -r requirements.txt
pytest -m smoke     # or other markers defined in tests/e2e-test/pytest.ini
```

### Build the full data/agent solution (requires `az login` and provisioned Azure/Fabric resources)
```bash
python scripts/00_build_solution.py              # run the whole pipeline
python scripts/00_build_solution.py --from 06     # resume from a given step
```
Each numbered script (`01_generate_data.py` … `09_app_deployment.py`) can also be run standalone; see the module docstring in each file for prerequisites — they expect to run in sequence (e.g. `02`/`03` need `01`'s `DATA_FOLDER`, `07` needs `01` and `06`).

### Infra / deployment
```bash
azd up            # provision + deploy (or `azd provision` then `azd deploy`)
azd down          # tear down — do this when done to avoid ongoing costs
```
`azure.yaml` postprovision hooks print follow-up commands (`infra/scripts/agent_scripts/run_create_agents_scripts.sh`, `infra/scripts/fabric_scripts/run_fabric_items_scripts.sh <workspace_id>`) that must be run manually after `azd up` to create agents and Fabric items.

## Key conventions

- Only touch one backend per change unless a task explicitly requires parity — Python and .NET implementations must stay functionally equivalent (same routes, same response shapes; see `Converters/PythonCompatibleDateTimeConverter.cs` in .NET, added specifically to match the Python JSON date format).
- No hard-coded credentials: Azure resource access uses Managed Identity in deployment and `az login`/`AzureCliCredential` locally — follow this pattern for any new Azure SDK usage (see `auth/azure_credential_utils.py` and `Auth/AzureCredentialFactory.cs`).
- `data/`, `.env` files, and `appsettings.json` (not `.sample`) are local/generated artifacts — never commit real values from them.
