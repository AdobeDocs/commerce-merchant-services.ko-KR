---
title: Adobe Experience Platform에 상거래 데이터 연결
description: 상거래 데이터를 Adobe Experience Platform에 연결하는 방법을 알아봅니다.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 76bc0650f32e99f568c061e67290de6c380f46a4
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Adobe Experience Platform에 상거래 데이터 연결 {#connectaep}

Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결하려면 조직 ID 및 데이터 스트림 ID를 제공해야 합니다.

![Experience Platform 커넥터 구성](assets/epc-config-sf.png)

## 일반

1. 에서 Adobe 계정에 로그인합니다. [Commerce Services 커넥터](../landing/saas.md#organizationid) 조직 ID를 선택합니다.

1. 관리에서 **시스템** > 서비스 > **Experience Platform 커넥터**.

1. 에서 **범위** 드롭다운에서 컨텍스트를 로 설정합니다. **웹 사이트**.

1. 에서 **조직 ID** 필드에서는 구성한 대로 Adobe Experience Platform 계정과 연결된 ID가 표시됩니다. [Commerce Services 커넥터](../landing/saas.md#organizationid). 조직 ID는 글로벌입니다. Adobe Commerce 인스턴스당 하나의 조직 ID만 연결할 수 있습니다.

1. (선택 사항) 이미 [AEP 웹 SDK(합금)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 사이트에 배포되어 있는 경우 확인란을 활성화하고 AEP 웹 SDK의 이름을 추가합니다. 그렇지 않으면 이러한 필드를 비워 두고 Experience Platform 커넥터가 자동으로 배포합니다.

   >[!NOTE]
   >
   >고유한 AEP Web SDK를 지정하는 경우 Experience Platform 커넥터는 이 페이지에 지정된 데이터 스트림 ID(있는 경우)가 아니라 해당 SDK와 연결된 데이터 스트림 ID를 사용합니다.

## 데이터 수집

에서 **데이터 수집** 섹션에서 수집하여 Experience Platform 에지로 전송할 데이터 유형을 지정합니다. 기본적으로 storefront 이벤트는 AEP 웹 SDK 및 조직 ID가 유효한 한 자동으로 전송됩니다. 자세한 내용은 이벤트 항목을 참조하십시오 [상점](events.md#storefront-events) 및 [사무실](events.md#back-office-events) events.

![Experience Platform 커넥터 구성](assets/epc-config-dc.png)

>[!NOTE]
>
>의 모든 필드 **데이터 수집** 섹션에 적용 **웹 사이트** 범위 이상

1. 선택 **백오피스 이벤트** 주문이 주문되었거나 취소, 환불 또는 출하된 경우와 같은 주문 상태 정보를 발송하려는 경우

   >[!NOTE]
   >
   >기본적으로 모든 백오피스 데이터는 Experience Platform 에지로 전송됩니다. 쇼핑객이 데이터 수집을 옵트아웃하도록 선택하는 경우 Experience Platform에서 쇼핑객의 개인 정보 보호 기본 설정을 명시적으로 설정해야 합니다. 수집기가 이미 구매자의 환경 설정에 따라 동의를 처리하는 상점 이벤트와는 다릅니다. [추가 정보](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) Experience Platform에서 쇼핑객의 개인 정보 보호 기본 설정 설정에 대한 정보.

1. (고유한 AEP 웹 SDK를 사용하는 경우 이 단계를 건너뜁니다.) [만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform의 데이터 스트림을 선택하거나 컬렉션에 사용할 기존 데이터 스트림을 선택합니다.

1. (고유한 AEP 웹 SDK를 사용하는 경우 이 단계를 건너뜁니다.) 에서 **데이터 스트림 ID** 필드에 새 데이터 스트림이나 기존 데이터 스트림의 ID를 붙여넣습니다.

## 필드 설명

| 필드 | 설명 |
|--- |--- |
| 범위 | 구성 설정을 적용할 특정 웹 사이트입니다. |
| 조직 ID(글로벌) | Adobe DX 제품을 구입한 조직에 속한 ID입니다. 이 ID는 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. |
| AEP 웹 SDK가 이미 사이트에 배포되어 있습니까? | 사이트에 고유한 AEP 웹 SDK를 배포한 경우 이 확인란을 선택합니다 |
| AEP 웹 SDK 이름(글로벌) | 사이트에 Experience Platform Web SDK를 이미 배포한 경우 이 필드에 해당 SDK의 이름을 지정합니다. 이를 통해 Storefront Event Collector 및 Storefront Event SDK는 Experience Platform 커넥터에 의해 배포된 버전이 아니라 Experience Platform Web SDK를 사용할 수 있습니다. 사이트에 Experience Platform Web SDK를 배포하지 않은 경우 이 필드를 비워 두면 Experience Platform 커넥터가 자동으로 배포합니다. |
| Storefront 이벤트 | 조직 ID 및 데이터 스트림 ID가 유효한 한 기본적으로 선택됩니다. 상점 이벤트는 사이트를 검색할 때 구매자로부터 익명으로 처리된 행동 데이터를 수집합니다. |
| 백 오피스 이벤트 | 이 확인란을 선택하면 이벤트 페이로드에 주문 주문 처리, 취소, 환급 또는 배송과 같은 익명 처리된 주문 상태 정보가 포함됩니다. |
| 데이터 스트림 ID(웹 사이트) | Adobe Experience Platform에서 다른 Adobe DX 제품으로 데이터를 전송할 수 있는 ID입니다. 이 ID는 특정 Adobe Commerce 인스턴스 내의 특정 웹 사이트에 연결되어 있어야 합니다. 고유한 Experience Platform Web SDK를 지정하는 경우 이 필드에 데이터 스트림 ID를 지정하지 마십시오. Experience Platform 커넥터는 해당 SDK와 연결된 데이터 스트림 ID를 사용하고 이 필드에 지정된 모든 데이터 스트림 ID를 무시합니다(있는 경우). |

Experience Platform 커넥터 확장, 생성된 Adobe Commerce과 Adobe Experience Platform 간 링크 및 지정된 데이터 스트림 ID가 있으면 상거래 데이터가 Adobe Experience Platform 에지 및 기타 Adobe DX 제품으로 이동합니다.

>[!NOTE]
>
> 에지에서 다른 Adobe DX 제품으로 데이터를 이동하는 데 걸리는 시간은 달라질 수 있습니다.

## 데이터가 Experience Platform으로 전송되고 있는지 확인

Adobe Experience Platform Edge로 전자 상거래 데이터가 전송되면 다음과 같은 보고서를 작성할 수 있습니다.

![Adobe Experience Manager의 상거래 데이터](assets/aem-data-1.png)
_Adobe Experience Manager의 상거래 데이터_
