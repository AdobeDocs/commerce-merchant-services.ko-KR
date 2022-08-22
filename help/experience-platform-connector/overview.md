---
title: 안내서 개요
description: Adobe Commerce용 Adobe Experience Platform 커넥터는 상거래 인스턴스를 다른 Adobe Experience Cloud 제품에 연결합니다.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 2fb44e73a76ad4e1433b2abd88be1304e7e10596
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---

# Experience Platform 커넥터 개요

Experience Platform 커넥터 확장을 사용하면 Adobe Commerce 가맹점이 Adobe Experience Platform 에지로 데이터를 전송할 수 있으므로 Adobe Analytics 및 Adobe Target과 같은 다른 Adobe Experience Cloud 제품에서 해당 상거래 데이터를 사용할 수 있습니다. 상거래 데이터를 Adobe Experience Cloud의 다른 제품에 연결하여 사이트에서 사용자 행동을 분석하고 AB 테스트를 수행하고 개인화된 캠페인을 만드는 등의 작업을 수행할 수 있습니다.

Storfront 이벤트는 다음과 같은 쇼퍼 상호 작용을 캡처합니다. `View Page`, `View Product`, `Add to Cart`등 캡처된 데이터에는 PII(개인 식별 정보)가 포함되지 않습니다. 쿠키 ID 및 IP 주소와 같은 모든 사용자 식별자는 엄격히 익명 처리됩니다. [추가 정보](https://www.adobe.com/privacy/experience-cloud.html). 전체 목록 보기 [storefront 이벤트](events.md).

Experience Platform 커넥터가 상거래 관리자에 나타납니다 **시스템** > 서비스 > **Experience Platform 커넥터**.

![Experience Platform 커넥터 확장 관리 보기](assets/epc-adminui.png)

## Experience Platform 커넥터 사용을 위한 사전 요구 사항 {#prereqs}

Experience Platform 커넥터를 사용하려면 먼저 다음을 수행해야 합니다.

- 다음을 입력합니다 [양식](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) 및 Adobe은 데이터 스트림 및 Adobe Experience Platform(필요한 경우)에 대한 액세스 권한을 제공합니다.

액세스 권한이 부여되면:

1. [로그인](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe 계정에 연결할 수도 있습니다.
1. 네 [조직](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 조직 ID 는 공급된 Experience Cloud 회사와 연결된 ID입니다. 이 ID는 24자의 영숫자 문자열과 그 뒤에 오는 (및 는 포함해야 함)입니다 `@AdobeOrg`.
1. 만들기 또는 업데이트 [XDM 스키마](update-xdm.md) 를 사용합니다.
1. [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 상거래 특정 스키마를 포함하는 XDM 스키마를 선택하고 선택합니다 **필드 그룹**.

>[!NOTE]
>
> 조직 ID 및 데이터 스트림은 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결하는 데 사용됩니다.

## 다음 단계

- 설치 [Experience Platform 커넥터 확장](install.md).

   Experience Platform 커넥터 확장은 서버의 명령줄에서 설치되며 Adobe Commerce 설치에 다음으로 연결됩니다. [서비스](../landing/saas.md). 프로세스가 완료되면 Experience Platform 커넥터가 **시스템** 메뉴 아래의 **서비스** 상거래 _관리_.
- [쇼퍼 프로필 업로드](profile.md) Adobe Experience Platform에 연결하여 상점 데이터를 제공하는 것은 특정 쇼핑객이 쇼핑 경험을 향상시키는 데 도움이 될 수 있습니다.

## Audience

이 안내서는 Adobe Commerce 상점 데이터를 다른 Adobe DX 제품에 연결해야 하는 Adobe Commerce 머천트용으로 설계되었습니다.

### PWA Studio 지원

자세한 내용은 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) PWA Studio 저장소 내 Experience Platform 커넥터를 사용하는 방법에 대한 설명서입니다.

## 알려진 문제

현재 Experience Platform 커넥터에는 다음과 같은 알려진 문제가 있습니다.

- 검색 이벤트는 B2B 모듈이 설치된 Adobe Commerce Enterprise Edition에서 지원되지 않습니다.
- Adobe Experience Platform 에지에 연결한 후 Adobe Commerce에서 다양한 대상으로 연결하는 데 약 1시간이 소요됩니다.

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 리소스를 사용하십시오.

- [도움말 센터](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [지원 티켓](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} - 추가 도움말을 받으려면 티켓을 제출하십시오.
