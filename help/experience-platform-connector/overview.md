---
title: 안내서 개요
description: Experience Platform 커넥터를 사용하여 Adobe Commerce 데이터를 Adobe Experience Platform과 통합하는 방법을 알아봅니다.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 092f2f4ab9d34466d66fe5b726bfff67a1309c6f
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# Experience Platform 커넥터 개요

Experience Platform 커넥터 확장을 사용하면 Adobe Commerce 가맹점이 Adobe Experience Platform 에지로 데이터를 전송할 수 있으므로 Adobe Analytics 및 Adobe Target과 같은 다른 Adobe Experience Cloud 제품에서 해당 상거래 데이터를 사용할 수 있습니다. 상거래 데이터를 Adobe Experience Cloud의 다른 제품에 연결하여 사이트에서 사용자 행동을 분석하고 AB 테스트를 수행하고 개인화된 캠페인을 만드는 등의 작업을 수행할 수 있습니다.

[Storefront 이벤트](events.md) 와 같은 고객 상호 작용 캡처 `View Page`, `View Product`, `Add to Cart`등 캡처된 데이터에는 PII(개인 식별 정보)가 포함되지 않습니다. 쿠키 ID 및 IP 주소와 같은 모든 사용자 식별자는 엄격히 익명 처리됩니다. [추가 정보](https://www.adobe.com/privacy/experience-cloud.html).

Experience Platform 커넥터가 상거래 관리자에 나타납니다 **시스템** > 서비스 > **Experience Platform 커넥터**.

![Experience Platform 커넥터 확장 관리 보기](assets/epc-adminui.png)

## 전제 조건 {#prereqs}

Experience Platform 커넥터를 사용하려면 다음을 수행해야 합니다.

- Adobe Commerce 2.4.3 이상
- Adobe ID 및 조직 ID
- 다른 Adobe DX 제품에 대한 권한 부여

## 온보딩 단계

1. [설치](install.md) Experience Platform 커넥터 확장.
1. [로그인](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe 계정 및 [보기](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 조직 ID입니다. 조직 ID 는 공급된 Experience Cloud 회사와 연결된 ID입니다. 이 ID는 24자의 영숫자 문자열과 그 뒤에 오는 (및 는 포함해야 함)입니다 `@AdobeOrg`.
1. [Connect](connect-data.md) Adobe Experience Platform에 Adobe Commerce 인스턴스를 추가합니다.
1. [만들기 또는 업데이트](update-xdm.md) 상거래 관련 필드 그룹을 사용하는 XDM 스키마.
1. [데이터 집합 만들기](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 만들거나 업데이트한 스키마를 기반으로 합니다.
1. [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 및 상거래 관련 필드 그룹을 포함하는 XDM 스키마를 선택합니다.

## Audience

이 안내서는 Adobe Commerce 데이터를 다른 Adobe DX 제품에 연결하려는 Adobe Commerce 머천트용으로 설계되었습니다.

### PWA Studio 지원

자세한 내용은 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) PWA Studio 저장소 내 Experience Platform 커넥터를 사용하는 방법에 대한 설명서입니다.

### AEM 지원 {#aem-support}

자세한 내용은 [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) CIF - Experience Platform 커넥터를 사용하여 AEM으로 렌더링된 제품 페이지에서 Experience Platform으로 storefront 이벤트 데이터를 전송하는 방법을 알아봅니다.

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 리소스를 사용하십시오.

- [도움말 센터](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}- 추가 도움말을 보려면 티켓을 제출하십시오.
