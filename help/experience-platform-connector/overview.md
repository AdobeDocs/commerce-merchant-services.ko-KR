---
title: 안내서 개요
description: Adobe Commerce용 Adobe Experience Platform 커넥터 이 연결됩니다 [!DNL Commerce] 다른 Adobe Experience Cloud 제품에 대한 인스턴스입니다.
source-git-commit: dc4bb1ea7d2ffc953cca31637bf5aefba6266241
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Experience Platform 커넥터 개요

Experience Platform 커넥터 확장을 사용하면 Adobe Commerce 가맹점이 Adobe Experience Platform 에지로 데이터를 전송할 수 있으므로 Adobe Analytics 및 Adobe Target과 같은 다른 Adobe Experience Cloud 제품에서 사용할 수 있습니다 [!DNL Commerce] 데이터. 연결 [!DNL Commerce] 데이터를 Adobe Experience Cloud의 다른 제품에 사용하면 사이트에서 사용자 행동을 분석하고 AB 테스트를 수행하며 개인화된 캠페인을 만드는 등의 작업을 수행할 수 있습니다.

Storfront 이벤트는 다음과 같은 쇼퍼 상호 작용을 캡처합니다. `View Page`, `View Product`, `Add to Cart`등 캡처된 데이터에는 PII(개인 식별 정보)가 포함되지 않습니다. 쿠키 ID 및 IP 주소와 같은 모든 사용자 식별자는 엄격히 익명 처리됩니다. [추가 정보](https://www.adobe.com/privacy/experience-cloud.html). 전체 목록 보기 [storefront 이벤트](events.md).

## Experience Platform 커넥터 사용을 위한 사전 요구 사항 {#prereqs}

Experience Platform 커넥터를 사용하려면 먼저 다음을 수행해야 합니다.

- 다음을 입력합니다 [양식](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) 및 Adobe은 데이터 스트림 및 Adobe Experience Platform(필요한 경우)에 대한 액세스 권한을 제공합니다.

액세스 권한이 부여되면:

1. [로그인](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe 계정에 연결할 수도 있습니다.
1. 네 [조직](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 조직 ID 는 공급된 Experience Cloud 회사와 연결된 ID입니다. 이 ID는 24자의 영숫자 문자열과 @AdobeOrg(포함 필수)로 구성됩니다.
1. 데이터 스트림 작업 공간에 액세스하고 [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en).

조직 ID 및 데이터 스트림은 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결할 때 사용됩니다.

## 다음 단계

- 설치 [Experience Platform 커넥터 확장](install.md).

   Experience Platform 커넥터 확장은 서버의 명령줄에서 설치되며 Adobe Commerce 설치에 다음으로 연결됩니다. [서비스](../landing/saas.md). 프로세스가 완료되면 Experience Platform 커넥터가 **시스템** 메뉴 아래의 **서비스** 에서 [!DNL Commerce] _관리_.

## Audience

이 안내서는 Adobe Commerce 상점 데이터를 다른 Adobe DX 제품에 연결해야 하는 Adobe Commerce 머천트용으로 설계되었습니다.

## 알려진 문제

현재 Experience Platform 커넥터에는 다음과 같은 알려진 문제가 있습니다.

- 검색 이벤트는 B2B 모듈이 설치된 Adobe Commerce Enterprise Edition에서 지원되지 않습니다.
- Adobe Experience Platform 에지에 연결한 후 Adobe Commerce에서 다양한 대상으로 연결하는 데 약 1시간이 소요됩니다.

## 지원

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 Slack 채널에 게시하십시오.

- `#beacon-ama`
