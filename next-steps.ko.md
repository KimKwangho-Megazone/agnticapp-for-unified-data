# `azd init` 이후 다음 단계

## 목차

1. [다음 단계](#다음-단계)
2. [추가된 항목](#추가된-항목)
3. [요금 청구](#요금-청구)
4. [문제 해결](#문제-해결)

## 다음 단계

### 인프라 프로비저닝 및 애플리케이션 코드 배포

`azd up`을 실행하여 인프라를 프로비저닝하고 Azure에 배포하세요(또는 `azd provision` 다음 `azd deploy`를 실행하여 작업을 별도로 수행할 수 있습니다). 나열된 서비스 엔드포인트를 방문하여 실행 중인 애플리케이션을 확인하세요!

문제가 발생하면 [문제 해결](#문제-해결)을 참고하세요.

### 서비스 실행을 위한 환경 변수 구성

[main.parameters.json](./infra/main.parameters.json)의 `settings`를 업데이트하여 서비스 실행을 위한 환경 변수를 구성하세요.

### CI/CD 파이프라인 구성

1. 로컬에서 워크플로 파이프라인 파일을 생성하세요. 다음과 같은 시작 템플릿을 사용할 수 있습니다:
   - [GitHub Actions로 배포하기](https://github.com/Azure-Samples/azd-starter-bicep/blob/main/.github/workflows/azure-dev.yml)
   - [Azure Pipelines로 배포하기](https://github.com/Azure-Samples/azd-starter-bicep/blob/main/.azdo/pipelines/azure-dev.yml)
2. `azd pipeline config`를 실행하여 Azure에 안전하게 연결되도록 배포 파이프라인을 구성하세요.

## 추가된 항목

### 인프라 구성

인프라와 애플리케이션을 설명하기 위해 `azure.yaml`과 함께 다음과 같은 디렉터리 구조의 Bicep 기반 Infrastructure as Code 파일이 추가되었습니다:

```yaml
- azure.yaml        # azd 프로젝트 구성
- infra/            # Infrastructure-as-code Bicep 파일
  - main.bicep      # 구독 수준 리소스
  - resources.bicep # 기본 리소스 그룹 리소스
  - modules/        # 라이브러리 모듈
```

[resources.bicep](./infra/resources.bicep)에 선언된 리소스는 `azd up` 또는 `azd provision` 실행 시 프로비저닝됩니다.
여기에는 다음이 포함됩니다:


- 'app' 서비스를 호스팅하는 Azure Container App
- 'km-charts-function' 서비스를 호스팅하는 Azure Container App
- 'km-rag-function' 서비스를 호스팅하는 Azure Container App
- 'add-user-scripts' 서비스를 호스팅하는 Azure Container App
- 'fabric-scripts' 서비스를 호스팅하는 Azure Container App
- 'index-scripts' 서비스를 호스팅하는 Azure Container App

[Bicep](https://aka.ms/bicep)에 대한 자세한 정보.

### 소스로부터 빌드하기 (Dockerfile 없이)

#### Oryx를 사용한 Buildpacks로 빌드하기

프로젝트에 Dockerfile이 없는 경우, [Oryx](https://github.com/microsoft/Oryx/blob/main/doc/README.md)를 사용하는 [Buildpacks](https://buildpacks.io/)를 통해 `azure.yaml`에 명시된 서비스의 이미지를 생성하여 컨테이너화된 앱을 Azure에 배포합니다.

로컬에서 Docker 이미지를 생성하고 실행하려면:

1. `azd package`를 실행하여 이미지를 빌드하세요.
2. 표시된 *Image Tag*를 복사하세요.
3. `docker run -it <Image Tag>`를 실행하여 로컬에서 이미지를 실행하세요.

#### 노출된 포트

Oryx는 자동으로 `PORT`를 기본값 `80`(Java의 경우 포트 `8080`)으로 설정합니다. 또한 `gunicorn`, `ASP .NET Core`와 같이 지원되는 웹 서버가 대상 `PORT`를 수신하도록 자동 구성합니다. 애플리케이션이 이미 `PORT` 변수로 지정된 포트를 수신하고 있다면 별도 설정 없이 바로 작동합니다. 그렇지 않다면 아래 단계 중 하나를 수행해야 할 수 있습니다:

1. 애플리케이션 코드 또는 구성을 업데이트하여 `PORT` 변수로 지정된 포트를 수신하도록 하세요.
1. (또는) `infra/app` 폴더 아래 .bicep 파일에서 `targetPort`를 찾아 애플리케이션에서 사용하는 포트와 일치하도록 변수를 업데이트하세요.

## 요금 청구

Azure Portal의 *Cost Management + Billing* 페이지를 방문하여 현재 지출 내역을 확인하세요. 청구 방식과 Azure 구독에서 발생한 비용을 모니터링하는 방법에 대한 자세한 내용은 [요금 청구 개요](https://learn.microsoft.com/azure/developer/intro/azure-developer-billing)를 참고하세요.

## 문제 해결

질문: 나열된 서비스 엔드포인트를 방문했는데 빈 페이지, 일반 환영 페이지 또는 오류 페이지가 표시됩니다.

답변: 서비스가 시작되지 못했거나 일부 구성 설정이 누락되었을 수 있습니다. 추가로 조사하려면:

1. `azd show`를 실행하세요. "View in Azure Portal" 아래 링크를 클릭하여 Azure Portal에서 리소스 그룹을 여세요.
2. 배포에 실패한 특정 Container App 서비스로 이동하세요.
3. "Revisions with Issues" 아래의 실패한 리비전을 클릭하세요.
4. 실패 유형에 대한 자세한 정보를 확인하려면 "Status details"를 검토하세요.
5. 오류를 파악하기 위해 Console log stream 및 System log stream에서 로그 출력을 확인하세요.
6. 로그가 디스크에 기록되는 경우, 실행 중인 컨테이너 내부의 셸에 연결하려면 내비게이션에서 *Console*을 사용하세요.

더 많은 문제 해결 정보는 [Container Apps 문제 해결](https://learn.microsoft.com/azure/container-apps/troubleshooting)을 방문하세요.

### 추가 정보

`azd` 프로젝트 설정에 대한 추가 정보는 공식 [문서](https://learn.microsoft.com/azure/developer/azure-developer-cli/make-azd-compatible?pivots=azd-convert)를 방문하세요.
