# 통합 데이터 기반 에이전틱 애플리케이션 (Agentic Applications for Unified Data Foundation)

<br/>
이 솔루션 액셀러레이터는 Microsoft Fabric의 통합 데이터 기반 위에 구축된 에이전틱 AI 솔루션을 활용하여 조직이 더 빠르고 스마트하게 의사결정을 내릴 수 있도록 지원합니다. Microsoft Foundry 에이전트와 Agent Framework 오케스트레이션을 원활하게 통합함으로써, 팀은 반복적인 프로세스를 자동화하고 운영을 간소화하며 기업 데이터 전반에 걸친 자연어 질의를 가능하게 하는 지능형 워크플로를 설계할 수 있습니다. 이를 통해 거버넌스가 적용된 고품질 데이터를 기술 전문가뿐만 아니라 비즈니스 사용자도 활용할 수 있게 되어, 인사이트를 더 쉽게 얻고 신뢰할 수 있는 정보를 기반으로 의사결정을 내릴 수 있는 공유 환경이 만들어집니다. 데이터 접근을 통합하고 업무 흐름 속에서 AI를 적용함으로써, 조직은 변화하는 비즈니스 요구에 신속하게 대응하고, 팀 간 협업을 촉진하며, 더 큰 자신감을 가지고 혁신을 추진할 수 있는 민첩성을 확보하게 됩니다.

<br/>

<br/>
<div align="center">

[**솔루션 개요**](#솔루션-개요)  \| [**빠른 배포**](#빠른-배포)  \| [**비즈니스 시나리오**](#비즈니스-시나리오)  \| [**지원 문서**](#지원-문서)

</div>
<br/>

 **참고:** 이 템플릿을 사용하여 생성하는 모든 AI 솔루션에 대해, 관련된 모든 위험을 평가하고 적용 가능한 모든 법률 및 안전 기준을 준수하는 것은 사용자의 책임입니다. 자세한 내용은 [Agent Service](https://learn.microsoft.com/en-us/azure/ai-foundry/responsible-ai/agents/transparency-note) 및 [Agent Framework](https://github.com/microsoft/agent-framework/blob/main/TRANSPARENCY_FAQ.md)의 투명성 문서를 참고하세요.
<br/>

<h2><img src="./documents/Images/ReadMe/solution-overview.png" width="48" />
솔루션 개요
</h2>


Fabric의 통합 데이터 기반 액셀러레이터, Fabric SQL 데이터베이스, Agent Framework, AI Foundry를 활용하여 구조화된 데이터를 질의합니다. 구조화된 데이터 세트는 시맨틱 모델과 데이터 자산을 탐색할 수 있는 대화형 웹 프런트엔드를 통해 지능적이고 체계적인 응답으로 분석됩니다. 인사이트는 자연어를 통해 생성됩니다.

### 솔루션 아키텍처

Microsoft Fabric 및 Microsoft Copilot Studio:
|![image](./documents/Images/ReadMe/solution-architecture-cps.png)
|---|

Microsoft Fabric 및 Microsoft Foundry:
|![image](./documents/Images/ReadMe/solution-architecture.png)
|---|

### 추가 리소스

[기술 아키텍처](./documents/TechnicalArchitecture.md)

## 기능
### 주요 기능
<details open>
<summary>이 솔루션이 제공하는 주요 기능 자세히 보기</summary>

**Microsoft Fabric + Microsoft Foundry 기반**
- **Fabric 기반 통합 데이터 기반** <br/>
Microsoft Fabric과 통합 데이터 기반의 기본 역량을 활용하여 오케스트레이션, 검색, 사용자 경험 측면에서 차별화된 지능형 에이전트를 구축합니다.

- **대규모 거버넌스 데이터** <br/>
Fabric의 데이터 기반과 원활하게 통합하여 성능, 확장성, 확장 가능성을 보장합니다.

- **자연어 상호작용** <br/>
Microsoft Foundry 에이전트가 오케스트레이션과 검색을 조율하여 빠르고 맥락에 맞는 답변을 제공하고 더 빠르게 인사이트를 실현합니다. 기업 데이터 자산 전반에 걸친 접근을 통합하는 직관적인 자연어 질의 기능을 제공합니다.

</details>

## 시작하기

### <img src="./documents/Images/ReadMe/quick-deploy.png" width="48" /> 빠른 배포

#### 설치 또는 배포 방법
배포 가이드의 빠른 배포 단계를 따라 이 솔루션을 본인의 Azure 구독에 배포하세요.

Azure 배포: [배포 가이드 바로가기](./documents/DeploymentGuide.md)
<br/><br/>
로컬 개발:
- [로컬 개발 환경 설정 가이드](./documents/LocalDevelopmentSetup.md) - Windows 및 Linux용 상세 설정 안내
- 네이티브 Windows 설정, WSL2 구성, 크로스 플랫폼 개발 도구 포함

워크숍: [워크숍 가이드](https://microsoft.github.io/agentic-applications-for-unified-data-foundation-solution-accelerator/quick-deploy/deployment-guide-optionA/) - 비정형 문서 지식과 정형 기업 데이터를 결합한 AI 에이전트를 구축하는 실습형 단계별 가이드
<br/><br/>


| [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/microsoft/agentic-applications-for-unified-data-foundation-solution-accelerator) | [![Open in Dev Containers](https://img.shields.io/static/v1?style=for-the-badge&label=Dev%20Containers&message=Open&color=blue&logo=visualstudiocode)](https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/microsoft/agentic-applications-for-unified-data-foundation-solution-accelerator) | [![Open in Visual Studio Code Web](https://img.shields.io/static/v1?style=for-the-badge&label=Visual%20Studio%20Code%20(Web)&message=Open&color=blue&logo=visualstudiocode&logoColor=white)](https://vscode.dev/azure/?vscode-azure-exp=foundry&agentPayload=eyJiYXNlVXJsIjogImh0dHBzOi8vcmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbS9taWNyb3NvZnQvYWdlbnRpYy1hcHBsaWNhdGlvbnMtZm9yLXVuaWZpZWQtZGF0YS1mb3VuZGF0aW9uLXNvbHV0aW9uLWFjY2VsZXJhdG9yL3JlZnMvaGVhZHMvbWFpbi9pbmZyYS92c2NvZGVfd2ViIiwgImluZGV4VXJsIjogIi9pbmRleC5qc29uIiwgInZhcmlhYmxlcyI6IHsiYWdlbnRJZCI6ICIiLCAiY29ubmVjdGlvblN0cmluZyI6ICIiLCAidGhyZWFkSWQiOiAiIiwgInVzZXJNZXNzYWdlIjogIiIsICJwbGF5Z3JvdW5kTmFtZSI6ICIiLCAibG9jYXRpb24iOiAiIiwgInN1YnNjcmlwdGlvbklkIjogIiIsICJyZXNvdXJjZUlkIjogIiIsICJwcm9qZWN0UmVzb3VyY2VJZCI6ICIiLCAiZW5kcG9pbnQiOiAiIn0sICJjb2RlUm91dGUiOiBbImFpLXByb2plY3RzLXNkayIsICJweXRob24iLCAiZGVmYXVsdC1henVyZS1hdXRoIiwgImVuZHBvaW50Il19) |
|---|---|---|

<br/>

> ⚠️ **중요: Azure OpenAI 할당량(Quota) 확인**
 <br/>솔루션을 배포하기 전에 구독에 충분한 할당량이 있는지 확인하려면 [할당량 확인 안내 가이드](./documents/QuotaCheck.md)를 따르세요.

## 안내

### 사전 요구 사항 및 비용
이 솔루션 액셀러레이터를 배포하려면 리소스 그룹, 리소스, 앱 등록을 생성하고 리소스 그룹 수준에서 역할을 할당할 수 있는 권한을 가진 [Azure 구독](https://azure.microsoft.com/free/)이 필요합니다. 여기에는 구독 수준의 Contributor 역할과 구독 및/또는 리소스 그룹 수준의 RBAC(역할 기반 액세스 제어) 역할이 포함되어야 합니다. [Azure 계정 설정](./documents/AzureAccountSetUp.md)의 단계를 따르세요. 또한 최소 F2 Fabric 용량이 필요합니다. [Fabric 용량 설정](https://learn.microsoft.com/en-us/fabric/admin/capacity-settings?tabs=fabric-capacity#create-a-new-capacity) 단계를 따르세요.

서비스가 제공되는 지역의 예시: East US, East US2, Australia East, UK South, France Central.

[지역별 Azure 제품](https://azure.microsoft.com/en-us/explore/global-infrastructure/products-by-region/?products=all&regions=all) 페이지를 확인하여 아래 서비스가 제공되는 **지역**을 선택하세요.

가격은 지역 및 사용량에 따라 다르므로 정확한 사용 비용을 예측하는 것은 불가능합니다. 이 인프라에서 사용되는 대부분의 Azure 리소스는 사용량 기반 요금제입니다. 다만 Azure Container Registry(레지스트리당 일일 고정 비용 발생)나 프로비저닝된 Cosmos DB, SQL Database와 같은 일부 서비스는 실제 사용량과 관계없이 기본 비용이 발생할 수 있습니다.

[Azure 가격 계산기](https://azure.microsoft.com/en-us/pricing/calculator)와 [Fabric 용량 추정기](https://www.microsoft.com/en-us/microsoft-fabric/capacity-estimator)를 사용하여 구독에서 이 솔루션의 비용을 계산하세요.

사용량을 커스터마이징하고 확장하려는 경우 [샘플 가격표](https://azure.com/e/708895d4fc4449b1826016fad8a83fe0)를 참고하세요.

_참고: 선택한 SKU, 확장된 사용량, 커스터마이징 및 자체 테넌트로의 통합에 따라 전체 소비량이 달라질 수 있으므로, 이는 모든 비용을 나타내기 위한 것이 아닙니다. 샘플 가격표는 구체적인 요구 사항에 맞게 추정치를 커스터마이징할 수 있는 출발점을 제공하기 위한 것입니다._

## 리소스
| 제품 | 설명 | 티어 / 예상 사용량 참고 | 비용 |
|---|---|---|---|
| [Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry) | Azure AI 서비스를 결합한 AI 워크플로를 오케스트레이션하고 구축하는 데 사용됩니다. | 무료 티어 | [가격](https://azure.microsoft.com/pricing/details/ai-studio/) |
| [Azure AI Services (OpenAI)](https://learn.microsoft.com/en-us/azure/cognitive-services/openai/overview) | GPT 모델을 사용한 언어 이해 및 채팅 기능을 제공합니다. | S0 티어; 토큰 사용량 및 사용 모델(예: GPT-4o-mini)에 따라 가격이 결정됩니다. | [가격](https://azure.microsoft.com/pricing/details/cognitive-services/) |
| [Azure Container Apps](https://learn.microsoft.com/en-us/azure/container-apps/overview) | 프런트엔드 및 백엔드 오케스트레이션을 구동하는 마이크로서비스와 API를 호스팅합니다. | 소비 플랜, 0.5 vCPU, 1GiB 메모리; 무료 사용 티어 포함. | [가격](https://azure.microsoft.com/pricing/details/container-apps/) |
| [Azure Container Registry](https://learn.microsoft.com/en-us/azure/container-registry/container-registry-intro) | Azure Container Apps에서 사용하는 컨테이너 이미지를 저장하고 제공합니다. | Basic 티어; 레지스트리당 고정 일일 비용. | [가격](https://azure.microsoft.com/pricing/details/container-registry/) |
| [Azure Monitor / Log Analytics](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-overview) | 서비스 및 컨테이너의 원격 분석 데이터와 로그를 수집하고 분석합니다. | 종량제; 데이터 수집량에 따라 과금. | [가격](https://azure.microsoft.com/pricing/details/monitor/) |
| [SQL Database in Fabric](https://learn.microsoft.com/en-us/fabric/fundamentals/microsoft-fabric-overview) | 인사이트, 메타데이터, 채팅 기록을 포함한 구조화된 데이터를 저장합니다. | F2 용량; 용량당 고정 월 비용. | [가격](https://azure.microsoft.com/en-us/pricing/details/microsoft-fabric/) |

>⚠️ **중요:** 불필요한 비용을 피하기 위해, 더 이상 사용하지 않는 경우 Azure Portal에서 리소스 그룹을 삭제하거나 `azd down`을 실행하여 앱을 종료하는 것을 잊지 마세요.

<br /><br />
<h2><img src="./documents/Images/ReadMe/business-scenario.png" width="48" />
비즈니스 시나리오
</h2>


|![image](./documents/Images/ReadMe/ui.png)|
|---|

<br/>

샘플 데이터는 이 액셀러레이터가 여러 산업에 걸쳐 영업 분석가 시나리오에 어떻게 활용될 수 있는지를 보여줍니다.
이 시나리오에서 한 조직은 영업 리서치를 위해 최고 성과 제품을 분석하는 과정에 있습니다. 이전에는 영업 분석가가 데이터 사일로 전반에 흩어진 영업 및 고객 데이터를 일일이 찾아봐야 했습니다. 이 솔루션 액셀러레이터를 활용하면 분석가는 Microsoft Fabric에 통합된 데이터에 접근하여 고객 및 영업 성과 데이터를 종합적으로 파악할 수 있습니다. 이 기능을 통해 분석가는 "어떤 고객 세그먼트가 가장 강력한 전년 대비 매출 성장을 보이는가", "인구통계별 최고 성과 제품은 무엇인가"와 같은 질문을 데이터에 던질 수 있습니다.


⚠️ 이 저장소에서 사용되는 샘플 데이터는 합성(synthetic) 데이터이며 생성된 것입니다. 이 데이터는 샘플 용도로만 사용하기 위한 것입니다.


### 비즈니스 가치
<details>
  <summary>이 솔루션이 제공하는 가치 자세히 보기</summary>
<br/>

  - **지능형 데이터 상호작용**
회사 고유의 데이터를 이해하고 자연어 질문을 데이터 기반 답변을 위한 자동화된 쿼리로 변환하는 대화형 에이전트를 활성화합니다. 에이전트에 지침을 학습시켜 가시성을 확보하세요.

- **가속화된 인사이트 및 생산성**
지능형 데이터 준비, 원활한 통합, AI 기반 탐색을 통해 신속한 인사이트를 확보하세요. 데이터를 분석하고 보강하여 트렌드를 발견하고, 워크플로를 자동화하며, 아이디어를 확장 가능한 에이전틱 솔루션으로 전환합니다.

- **거버넌스가 적용된 확장 가능하고 신뢰할 수 있는 데이터**
견고한 거버넌스와 메타데이터를 통해 실행 가능한 인사이트를 제공합니다. 통합 플랫폼에서 안전한 셀프서비스 방식으로 고품질 데이터에 접근하여 의사결정, 운영 효율성을 개선하고 비용을 절감합니다.


</details>

### 사용 사례
<details>
  <summary>이 솔루션이 제공하는 사용 사례 자세히 보기</summary>
<br/>

  | **사용 사례** | **페르소나** | **과제** | **요약/접근 방식** |
  |---|---|---|---|
  | 영업 분석 및 제품 성과 | 영업 분석가 | 분산된 데이터 사일로를 탐색하는 데 상당한 시간이 소요되어, 완전한 영업/제품/고객 정보를 빠르고 정확하게 확보하기 어려움.| 자연어를 통해 상호작용하는 고객, 제품, 영업 데이터의 종합적인 뷰를 제공. 복잡한 보고서와 대시보드를 탐색하지 않고도 더 빠르게 인사이트를 확보.|
  고객 미팅 개선, 고객 미팅 준비 | 계정 관리자 | 수작업 프로세스와 분절된 시스템으로 인해 일상 업무가 지연되고, 인사이트를 찾기 어려우며, 개인화된 고객 상호작용이 제한되어 이탈률 증가와 만족도 저하로 이어짐 | 자연어 질의를 통해 업무 흐름 속에서 고객 데이터를 제공하고 실행 가능한 인사이트를 발굴하며, 상호작용을 개인화하여 이탈을 줄이고 고객 만족도를 높임. |

</details>

<br /><br />

<h2><img src="./documents/Images/ReadMe/supporting-documentation.png" width="48" />
지원 문서
</h2>

### 보안 가이드라인

이 솔루션은 로컬 개발 및 프로덕션 배포 시 Azure 리소스에 안전하게 접근하기 위해 [관리 ID(Managed Identity)](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)를 사용하며, 이를 통해 하드코딩된 자격 증명이 필요 없습니다.

강력한 보안 관행을 유지하기 위해, 이 솔루션을 기반으로 구축된 GitHub 저장소는 [GitHub 보안 스캐닝(secret scanning)](https://docs.github.com/code-security/secret-scanning/about-secret-scanning)을 활성화하여 실수로 노출된 자격 증명을 탐지하는 것이 권장됩니다.

추가 보안 고려 사항은 다음과 같습니다:

- Azure 리소스를 모니터링하고 보호하기 위해 [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud)를 활성화합니다.
- 무단 접근으로부터 Azure Container Apps를 보호하기 위해 [가상 네트워크](https://learn.microsoft.com/en-us/azure/container-apps/networking?tabs=workload-profiles-env%2Cazure-cli) 또는 [방화벽 규칙](https://learn.microsoft.com/en-us/azure/container-apps/waf-app-gateway)을 사용합니다.

<br/>

### 참고 자료 (Cross references)
유사한 솔루션 액셀러레이터를 확인해보세요

| 솔루션 액셀러레이터 | 설명 |
|---|---|
| [Fabric&nbsp;기반&nbsp;통합&nbsp;데이터&nbsp;기반](https://github.com/microsoft/unified-data-foundation-with-fabric-solution-accelerator) | Microsoft Fabric, Microsoft Purview, Azure Databricks를 활용한 통합 데이터 아키텍처로 통합되고 거버넌스가 적용된 분석 플랫폼을 제공하는 통합 데이터 기반을 제공합니다. |


<br/>


💡 Microsoft의 AI 및 데이터 엔지니어링 모범 사례를 더 알아보고 싶으신가요? 저희 플레이북을 확인해보세요

| 플레이북 | 설명 |
|:---|:---|
| [AI&nbsp;플레이북](https://learn.microsoft.com/en-us/ai/playbook/) | AI(인공지능) 플레이북은 엔터프라이즈 소프트웨어 엔지니어에게 실제 AI 문제를 해결하기 위해 개발된 솔루션, 역량, 코드를 제공합니다. |
| [데이터&nbsp;플레이북](https://learn.microsoft.com/en-us/data-engineering/playbook/understanding-data-playbook) | 데이터 플레이북은 엔터프라이즈 소프트웨어 엔지니어에게 실제 문제를 해결하기 위해 개발된 코드를 포함한 솔루션을 제공합니다. 플레이북의 모든 내용은 Microsoft의 가장 크고 영향력 있는 고객 및 파트너 중 일부와 함께 개발되고 검증되었습니다. |

<br/>

## 피드백 제공

질문이 있거나, 버그를 발견했거나, 기능을 요청하고 싶으신가요? 이 저장소에 [새 이슈를 등록](https://github.com/microsoft/agentic-applications-for-unified-data-foundation-solution-accelerator/issues)해 주시면 연락드리겠습니다.

<br/>

## 책임감 있는 AI 투명성 FAQ
이 솔루션 액셀러레이터의 책임감 있는 AI 투명성에 대한 자세한 내용은 [투명성 FAQ](./TRANSPARENCY_FAQ.md)를 참고하세요.

<br/>

## 면책 조항

소프트웨어에 Microsoft 제품 또는 서비스(Microsoft Azure 서비스를 포함하되 이에 국한되지 않음, 이하 "Microsoft 제품 및 서비스")에서 사용되거나 파생된 구성 요소 또는 코드가 포함된 경우, 해당 Microsoft 제품 및 서비스에 적용되는 제품 약관을 준수해야 합니다. 소프트웨어를 규율하는 라이선스는 Microsoft 제품 및 서비스를 사용할 수 있는 라이선스 또는 기타 권리를 부여하지 않음을 인정하고 동의합니다. 라이선스 또는 본 ReadMe 파일의 어떠한 내용도 Microsoft 제품 및 서비스에 대한 제품 약관의 조건을 대체, 수정, 종료 또는 변경하지 않습니다.

귀하는 또한 소프트웨어에 적용되는 목적지, 최종 사용자, 최종 용도에 대한 제한을 포함하는 모든 국내 및 국제 수출 법률 및 규정을 준수해야 합니다. 수출 제한에 대한 자세한 내용은 https://aka.ms/exporting 을 방문하세요.

귀하는 소프트웨어 및 Microsoft 제품 및 서비스가 (1) 의료 기기로 설계, 의도 또는 제공되지 않으며, (2) 전문적인 의학적 조언, 진단, 치료 또는 판단을 대체하도록 설계되거나 의도되지 않았으며 이를 대체하거나 대신하는 용도로 사용되어서는 안 됨을 인정합니다. 고객은 온라인 서비스 구현과 관련하여 최종 사용자에게 적절한 동의, 경고, 면책 조항 및 승인을 표시하고/하거나 확보할 책임을 단독으로 집니다.

귀하는 소프트웨어가 SOC 1 및 SOC 2 준수 감사의 대상이 아님을 인정합니다. 소프트웨어를 포함한 어떠한 Microsoft 기술이나 그 구성 기술도 공인 금융 서비스 전문가의 전문적인 조언, 의견 또는 판단을 대체하기 위해 의도되거나 제공되지 않습니다. 전문적인 재무 자문이나 판단을 대체, 대신하거나 제공하기 위해 소프트웨어를 사용하지 마십시오.

소프트웨어에 접근하거나 사용함으로써, 귀하는 소프트웨어가 서비스 중단, 결함, 오류 또는 기타 장애로 인해 사람의 사망 또는 심각한 신체적 상해 또는 물리적/환경적 피해를 초래할 수 있는 용도("고위험 사용")를 지원하도록 설계되거나 의도되지 않았음을 인정하며, 소프트웨어의 중단, 결함, 오류 또는 기타 장애가 발생할 경우 산업 전반 또는 특정 산업에서 합리적이고 적절하며 합법적인 수준 이하로 사람, 재산, 환경의 안전이 저하되지 않도록 보장할 것임을 인정합니다. 소프트웨어에 접근함으로써, 귀하는 소프트웨어의 고위험 사용이 전적으로 귀하 자신의 책임임을 추가로 인정합니다.
