---
title: 온보딩 및 설치
description: "설치 방법 알아보기 [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 8a98e069cd9ec3d2c4fec33485e5c8186d94518f
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---

# 온보딩 및 설치

다음 비디오는 다음 사항을 안내합니다. [!DNL Catalog Service] 프로세스.

**파트 1**: 온보딩 및 설치

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**파트 2**: 사용 [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## 전제 조건

에 대한 온보딩 프로세스 [!DNL Catalog Service] 서버의 명령줄에 대한 액세스 권한이 필요합니다. 명령줄 작업에 익숙하지 않은 경우 개발자 또는 시스템 통합자에게 도움을 요청하십시오.

**소프트웨어 요구 사항**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- 작성기: 2.x

**지원되는 플랫폼**

- 클라우드 인프라의 Adobe Commerce: 2.4.4+
- Adobe Commerce 온프레미스: 2.4.4+

>[!ENDSHADEBOX]

## 엔드포인트

[!DNL Catalog Service] 에는 온보딩에 사용할 수 있는 두 개의 엔드포인트가 있습니다.

- 샌드박스 (`https://catalog-service-sandbox.adobe.io/graphql`) - 시작하기 전에 테스트 및 유효성 검사에 사용됩니다.
- 프로덕션 (`https://catalog-service.adobe.io/graphql`) - Commerce 판매자 및 웹 사이트의 라이브 트래픽에 사용됩니다.

Commerce의 모든 테스트 인스턴스는 샌드박스 엔드포인트를 사용해야 합니다.

로드 테스트는 샌드박스 엔드포인트에서만 수행해야 합니다. 권장 사항: [지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 서비스 팀이 추가 서버 트래픽을 예측할 수 있도록 로드 테스트 시 를 엽니다.

## 설치 및 구성

시작하려면 [!DNL Catalog Service] Adobe Commerce의 경우 다음 단계가 필요합니다.

- 데이터 내보내기 확장 설치
- 서비스 및 데이터 내보내기 구성
- 서비스 액세스

### 데이터 내보내기 확장 설치

에 대한 온보딩 프로세스 [!DNL Catalog Service] 서버의 명령줄에 대한 액세스 권한이 필요합니다.

다음 [!DNL Catalog Service] 확장은 Adobe Commerce cloud 인프라와 온프레미스 인스턴스 모두에 설치할 수 있습니다.

다음 [!DNL Catalog Service] 은 Commerce 계정에 연결된 작성기 키와 함께 설치됩니다 [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) 등록 프로세스 중에 제공됩니다. Composer는 Adobe Commerce을 처음 설치하는 동안 또는 이전에 Composer 키가 외부에 저장되지 않은 상황에서 이 키를 사용합니다 `auth.json` 파일.

다음을 참조하십시오 [인증 키 받기](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) composer 키를 가져오는 방법에 대한 자세한 내용은 를 참조하십시오.

#### 클라우드 인프라의 Adobe Commerce

다음 설치 시 이 방법 사용 [!DNL Catalog Service] Commerce Cloud 인스턴스에 대한 확장입니다.

1. 로컬 워크스테이션에서 프로젝트 디렉터리로 변경합니다.
1. 카탈로그 서비스 모듈을 추가합니다.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. 패키지 종속성을 업데이트합니다.

   ```bash
   composer update
   ```

1. 에 대한 코드 변경 내용 커밋 및 푸시 `composer.json` 및 `composer.lock` 파일.

#### 온-프레미스

다음 설치 시 이 방법 사용 [!DNL Catalog Service] 온-프레미스 인스턴스에 대한 확장.

1. 작성기를 사용하여 프로젝트에 카탈로그 서비스 모듈을 추가합니다.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

1. Adobe Commerce 업그레이드:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시를 지웁니다.

   ```bash
   bin/magento cache:clean
   ```

### 서비스 및 데이터 내보내기 구성

설치 후 [!DNL Catalog Service], 다음을 구성해야 합니다. [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) api 키를 지정하고 SaaS 데이터 공간을 선택합니다.

SaaS 구성이 완료되면 다음을 사용하여 초기 데이터 동기화를 수행합니다. [데이터 관리 대시보드](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). 이 대시보드를 사용하여 Commerce 데이터베이스에서 Commerce SaaS 서비스로 전송되는 제품 데이터의 동기화 상태를 모니터링할 수 있습니다.

카탈로그 내보내기가 올바르게 실행되는지 확인하려면 다음을 수행하십시오.

- cron 작업이 실행 중인지 확인합니다.
- 인덱서가 실행 중인지 확인합니다.
- 다음을 확인합니다. `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, 및 `Product Variant Feed` 인덱서가 &quot;일정별로 업데이트&quot;로 설정되어 있습니다.

초기 동기화는 카탈로그 크기에 따라 몇 분에서 몇 시간 정도 소요될 수 있습니다. 초기 동기화 후 카탈로그는 서비스를 최신 상태로 유지하기 위해 지속적으로 Commerce 서버의 제품 데이터를 Commerce 서비스로 내보냅니다. 동기화 상태를 모니터링하려면 다음을 참조하십시오 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html).

### 서비스 액세스

다음 [!DNL Catalog Service] API는 HTTPS를 통해 POST 명령을 사용하여 액세스할 수 있습니다.

API 키를 가져오려면 관리자의 Commerce 서비스 커넥터 영역으로 이동하여 공개 API 키를 복사합니다.

읽기 [GraphQL 설명서](https://developer.adobe.com/commerce/services/graphql/) api 요청 생성에 필요한 헤더를 쿼리하고 전송하는 방법을 이해합니다.

허용하려면 [!DNL Catalog Service] 방화벽을 통해 추가 `commerce.adobe.io` 허용 목록에 추가하다로

## 카탈로그 서비스 및 API 메쉬

다음 [Adobe Developer 앱 빌더용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 을 사용하면 개발자가 Adobe IO를 사용하여 개인 또는 서드파티 API 및 기타 인터페이스를 Adobe 제품과 통합할 수 있습니다.

다음을 참조하십시오.  [[!DNL Catalog Service] 및 API 메쉬](mesh.md) 항목 설치 및 구성 세부 정보.

## 데이터 관리 대시보드

사용자는 다음을 참조할 수 있습니다. [데이터 관리 대시보드](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 다음에 대한 추가 데이터: [!DNL Catalog Service] 데이터 동기화 중.
