---
title: Commerce Services 커넥터
description: 프로덕션 및 샌드박스 API 키를 사용하여 Adobe Commerce 또는 Magento Open Source 인스턴스를 서비스에 통합하는 방법을 알아봅니다.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: 506b00e72d65fbafa071476608bb658cb59404b4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

일부 Adobe Commerce 및 Magento Open Source 기능은에서 제공합니다. [!DNL Commerce Services]  SaaS(Software as a Service)로 배포됩니다. 이러한 서비스를 사용하려면 다음을 연결해야 합니다. [!DNL Commerce] 프로덕션 및 샌드박스 API 키를 사용하는 인스턴스와 [구성](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). 한 번만 설정하면 됩니다.

## 사용 가능한 서비스 {#availableservices}

다음은 [!DNL Commerce] 다음을 통해 액세스할 수 있는 기능 [!DNL Commerce Services Connector]:

| 서비스 | 사용 가능 |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) Adobe Sensei 제공 | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) Adobe Sensei 제공 | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce 및 Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce 및 Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [Experience Platform 커넥터](/help/experience-platform-connector/overview.md) | Adobe Commerce |

## 아키텍처

높은 수준에서 [!DNL Commerce Services Connector] 는 다음 핵심 요소로 구성됩니다.

![Commerce Services 커넥터 아키텍처](assets/saas-config-sync-workflow.png)

다음 섹션에서는 이러한 각 요소에 대해 자세히 설명합니다.

## 자격 증명 {#apikey}

프로덕션 및 샌드박스 API 키는 [!DNL Commerce] 고유 (으)로 식별되는 라이선스 소유자의 계정 [!DNL Commerce] ID (MageID). 다음과 같은 서비스에 대한 자격 검증을 통과하려면 [!DNL Product Recommendations] 또는 [!DNL Live Search], 판매자 조직의 라이선스 소유자는 계정이 양호한 상태인 한 API 키 세트를 생성할 수 있습니다. 라이선스 소유자를 대신하여 프로젝트 및 환경을 관리하는 시스템 통합자 또는 개발 팀과 &quot;필요한 정보&quot;에 따라 키를 공유할 수 있습니다. 또한 솔루션 통합자는 [!DNL Commerce Services]. 솔루션 통합자인 경우 [!DNL Commerce] 파트너 계약에서 API 키를 생성해야 합니다.

### 프로덕션 및 샌드박스 API 키 생성 {#genapikey}

1. 에 로그인 [!DNL Commerce] 계정 위치: [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. 아래 **Magento** 탭, 선택 **API 포털** 사이드바에서

1. 다음에서 _환경_ 메뉴, 선택 **프로덕션** 또는 **샌드박스**.

1. 에 이름 입력 _API 키_ 섹션 및 클릭 **새로 추가**.

   그러면 새 키를 다운로드하는 대화 상자가 열립니다.

   ![개인 키 다운로드](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > 이는 키를 복사하거나 다운로드해야 하는 유일한 기회입니다.

1. 클릭 **다운로드** 그런 다음 을 클릭합니다. **취소**.

1. 각 환경(프로덕션 및 샌드박스)에 대해 위의 단계를 반복합니다.

   다음 **API 키** 이제 섹션에 API 키가 표시됩니다. 다음과 같은 경우 프로덕션 키와 샌드박스 키가 모두 필요합니다. [SaaS 프로젝트 선택 또는 만들기](#createsaasenv).

## SaaS 구성 {#saasenv}

[!DNL Commerce] 인스턴스는 SaaS 프로젝트 및 SaaS 데이터 공간으로 구성해야 합니다. [!DNL Commerce Services] 는 데이터를 올바른 위치에 보낼 수 있습니다. SaaS 프로젝트는 모든 SaaS 데이터 공간을 그룹화합니다. SaaS 데이터 공간은 다음을 가능하게 하는 데이터를 수집하고 저장하는 데 사용됩니다. [!DNL Commerce Services] 일 때문에. 이 데이터 중 일부는 [!DNL Commerce] 인스턴스 및 일부는 상점 위의 쇼핑객 행동에서 수집될 수 있습니다. 그런 다음 해당 데이터는 보안 클라우드 스토리지로 유지됩니다.

대상 [!DNL Product Recommendations], SaaS 데이터 공간에는 카탈로그 및 동작 데이터가 포함됩니다. 다음을 지정할 수 있습니다. [!DNL Commerce] 다음을 통해 SaaS 데이터 공간으로 인스턴스: [선택](https://docs.magento.com/user-guide/configuration/services/saas.html) 다음에서 [!DNL Commerce] 구성.

>[!WARNING]
>
> 프로덕션 SaaS 데이터 공간은 프로덕션 환경에서만 사용합니다. [!DNL Commerce] 데이터 충돌을 방지하기 위한 설치 그렇지 않으면 테스트 데이터로 프로덕션 사이트 데이터를 오염시켜 배포가 지연될 위험이 있습니다. 예를 들어 스테이징 URL과 같은 스테이징 데이터에서 프로덕션 제품 데이터를 실수로 덮어쓸 수 있습니다.

### SaaS 프로젝트 선택 또는 만들기 {#createsaasenv}

>[!NOTE]
>
> 표시되지 않는 경우 **[!UICONTROL Commerce Services Connector]** 의 섹션 [!DNL Commerce] 구성, 다음을 설치해야 합니다. [!DNL Commerce] 원하는 모듈 [[!DNL Commerce] 서비스](#availableservices).

SaaS 프로젝트를 선택하거나 만들려면 다음을 요청하십시오. [!DNL Commerce] 의 API 키 [!DNL Commerce] 귀하의 스토어에 대한 라이선스 보유자입니다.

1. 다음에서 _관리자_ 사이드바, 이동 **시스템** > 서비스 > **Commerce Services 커넥터**.

1. 다음에서 _샌드박스 API 키_ 및 _프로덕션 API 키_ 섹션, 키 값을 붙여넣습니다.

   비공개 키에는 다음이 포함되어야 합니다. `----BEGIN PRIVATE KEY---` 의 시작 부분에서 `----END PRIVATE KEY----` 개인 키 종료 시.

1. 클릭 **저장**.

키와 연결된 모든 SaaS 프로젝트가 **프로젝트** 의 필드 **SaaS 식별자** 섹션.

1. SaaS 프로젝트가 없는 경우 **프로젝트 만들기**. 그런 다음 **프로젝트** 필드에 SaaS 프로젝트의 이름을 입력합니다.

   SaaS 프로젝트를 만들 때 [!DNL Commerce] 에 따라 하나 이상의 SaaS 데이터 공간을 생성합니다. [!DNL Commerce] 라이선스:
   - Adobe Commerce - 프로덕션 데이터 공간 1개, 테스트 데이터 공간 2개
   - Magento Open Source - 프로덕션 데이터 공간 1개, 테스트 데이터 공간 없음

1. 다음 항목 선택 **데이터 공간** 의 현재 구성에 을 사용하려면 [!DNL Commerce] 저장.

>[!WARNING]
>
> 내 계정의 API 포털 섹션에서 새 키를 생성하는 경우 관리 구성에서 API 키를 즉시 업데이트합니다. 새 키를 생성하고 관리에서 업데이트하지 않으면 SaaS 확장이 더 이상 작동하지 않고 중요한 데이터를 잃게 됩니다.

SaaS 프로젝트 또는 데이터 공간 이름을 변경하려면 **이름 바꾸기**.

## IMS 조직(선택 사항) {#organizationid}

Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결하려면 Adobe ID을 사용하여 Adobe 계정에 로그인합니다. 로그인하면 Adobe 계정과 연결된 IMS 조직이 이 섹션에 표시됩니다.

## 카탈로그 동기화

다음의 경우 [!DNL Commerce] 인스턴스가 성공적으로 연결 [!DNL Commerce Services], 카탈로그 동기화 프로세스가 [!DNL Commerce] 서버 대상 [!DNL Commerce Services]. 현재 Recommendations 제품만 카탈로그 동기화 서비스를 사용합니다. [자세히 알아보기](catalog-sync.md) 카탈로그 동기화 프로세스 정보.
