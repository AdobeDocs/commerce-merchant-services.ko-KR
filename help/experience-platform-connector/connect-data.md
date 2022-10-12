---
title: Adobe Experience Platform에 상거래 데이터 연결
description: 상거래 데이터를 Adobe Experience Platform에 연결하는 방법을 알아봅니다.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Experience Platform에 상거래 데이터 연결 {#connectaep}

Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결하려면 조직 ID 및 데이터 스트림 ID를 제공해야 합니다.

![Experience Platform 커넥터 구성](assets/epc-config.png)

1. 에서 Adobe 계정에 로그인합니다. [Commerce Services 커넥터](../landing/saas.md#organizationid) 조직 ID를 선택합니다.

1. 관리에서 **시스템** > 서비스 > **Experience Platform 커넥터**.

1. 에서 **범위** 드롭다운에서 컨텍스트를 로 설정합니다. **웹 사이트**.

1. 에서 **조직 ID** 필드에서는 구성한 대로 Adobe Experience Platform 계정과 연결된 ID가 표시됩니다. [Commerce Services 커넥터](../landing/saas.md#organizationid). 조직 ID는 글로벌입니다. Adobe Commerce 인스턴스당 하나의 조직 ID만 연결할 수 있습니다.

1. 에서 **데이터 스트림 ID** 필드에서 데이터 스트림의 ID를 붙여넣습니다. [생성됨](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) Adobe Experience Platform에서 확인하십시오.

   >[!NOTE]
   >
   >데이터 스트림 ID의 범위는 웹 사이트 수준 이상으로 설정되어야 합니다. 이 수준에서 계층의 각 웹 사이트에 대해 동일한 데이터 스트림 ID가 사용됩니다. 저장소 보기 수준에서 데이터 스트림 ID 범위를 설정할 수 없습니다.

1. (선택 사항) 사이트에 AEP Web SDK가 배포되지 않은 경우 이 필드를 비워 두고 Experience Platform 커넥터가 자동으로 배포합니다. 그렇지 않으면 AEP 웹 SDK의 이름을 추가합니다.

## 필드 설명

| 필드 | 설명 |
|--- |--- |
| 범위 | 구성 설정을 적용할 특정 웹 사이트입니다. |
| 조직 ID(글로벌) | Adobe DX 제품을 구입한 조직에 속한 ID입니다. 이 ID는 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. |
| 데이터 스트림 ID(웹 사이트) | Adobe Experience Platform에서 다른 Adobe DX 제품으로 데이터를 전송할 수 있는 ID입니다. 이 ID는 특정 Adobe Commerce 인스턴스 내의 특정 웹 사이트에 연결되어 있어야 합니다. |
| AEP 웹 SDK 이름(글로벌) | 사이트에 AEP Web SDK가 배포되지 않은 경우 이 필드를 비워 두고 Experience Platform 커넥터가 자동으로 배포합니다. 사이트에 AEP 웹 SDK를 이미 배포하고 있는 경우 이 필드에 해당 SDK의 이름을 지정합니다. 이를 통해 Storefront Event Collector 및 Storefront Event SDK는 Experience Platform 커넥터에 의해 배포된 버전이 아니라 AEP Web SDK를 사용할 수 있습니다. |

Experience Platform 커넥터 확장, 생성된 Adobe Commerce과 Adobe Experience Platform 간 링크 및 지정된 데이터 스트림 ID가 있으면 상거래 데이터가 Adobe Experience Platform 에지 및 기타 Adobe DX 제품으로 이동합니다.

>[!NOTE]
>
> 에지에서 다른 Adobe DX 제품으로 데이터를 이동하는 데 걸리는 시간은 달라질 수 있습니다.

## 엣지의 상거래 데이터

Adobe Experience Platform Edge로 전자 상거래 데이터가 전송되면 다음과 같은 보고서를 작성할 수 있습니다.

![Adobe Experience Manager의 상거래 데이터](assets/aem-data-1.png)
_Adobe Experience Manager의 상거래 데이터_
