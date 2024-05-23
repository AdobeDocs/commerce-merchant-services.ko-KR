---
title: 온보딩 및 설치
description: "설치 방법 알아보기 [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: a2841b809cfc52798dc3f1bdcc033a77333bf0e5
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# 온보딩 및 설치

다음을 사용하여 Commerce 인스턴스에서 제품 데이터를 요청하고 수신하려면 카탈로그 서비스를 설치하십시오. [카탈로그 서비스 GraphQL API](https://developer.adobe.com/commerce/services/graphql/catalog-service/). 카탈로그 서비스는 repo.magento.com 저장소에서 작성기 메타패키지로 제공됩니다.

>[!NOTE]
>
>Commerce 인스턴스에서 라이브 검색 또는 Product Recommendations을 사용하는 경우 해당 서비스를 온보딩하거나 업그레이드할 때 카탈로그 서비스가 자동으로 설치 또는 업데이트됩니다. 자세한 내용은 다음 설치 지침을 참조하십시오. [라이브 검색](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) 및 [제품 Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).



## 시스템 요구 사항

**소프트웨어 요구 사항**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3
- 작성기: 2.x

**지원되는 플랫폼**

- 클라우드 인프라의 Adobe Commerce: 2.4.4+
- Adobe Commerce 온프레미스: 2.4.4+

## 엔드포인트

[!DNL Catalog Service] 에는 온보딩에 사용할 수 있는 두 개의 엔드포인트가 있습니다.

- 샌드박스 (`https://catalog-service-sandbox.adobe.io/graphql`) - 시작하기 전에 테스트 및 유효성 검사에 사용됩니다.
- 프로덕션 (`https://catalog-service.adobe.io/graphql`) - Commerce 판매자 및 웹 사이트의 라이브 트래픽에 사용됩니다.

모든 Commerce 테스트 인스턴스는 샌드박스 엔드포인트를 사용합니다.

샌드박스 엔드포인트에서 모든 로드 테스트를 수행합니다. 로드 테스트를 시작하기 전에 [지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 서비스 팀이 추가 서버 트래픽을 예측할 수 있도록 합니다.

## 설치 및 구성

시작하려면 [!DNL Catalog Service] Adobe Commerce의 경우 다음 단계가 필요합니다.

- 카탈로그 서비스 확장 설치(`magento/catalog-service`)
- 서비스 및 데이터 내보내기 구성
- 서비스 액세스

### 카탈로그 서비스 확장 설치

>[!BEGINSHADEBOX]

**전제 조건**

- 액세스 [repo.magento.com](https://repo.magento.com) 확장을 설치합니다. 키 생성 및 필요한 권한 획득에 대한 자세한 내용은 [인증 키 받기](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). 클라우드 설치의 경우 다음을 참조하십시오 [Commerce on Cloud Infrastructure 안내서](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Adobe Commerce 애플리케이션 서버의 명령줄에 액세스합니다.

>[!ENDSHADEBOX]

최신 버전의 카탈로그 서비스 확장 설치(`magento/catalog-service`)을 클릭하여 제품에서 사용할 수 있습니다. Adobe Commerce 버전 2.4.4 이상을 실행 중인 Adobe Commerce 인스턴스. 카탈로그 서비스는 의 작성기 메타패키지로 제공됩니다. [repo.magento.com](https://repo.magento.com) 리포지토리.

>[!BEGINTABS]

>[!TAB 클라우드 인프라]

이 메서드를 사용하여 다음을 설치하십시오. [!DNL Catalog Service] Commerce Cloud 인스턴스에 대한 확장입니다.

1. 로컬 워크스테이션에서 Adobe Commerce on cloud infrastructure 프로젝트의 프로젝트 디렉터리로 변경합니다.

   >[!NOTE]
   >
   >Commerce 프로젝트 환경을 로컬로 관리하는 방법에 대한 자세한 내용은 [CLI를 사용하여 분기 관리](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) 다음에서 _Adobe Commerce on Cloud Infrastructure 사용 안내서_.

1. Adobe Commerce Cloud CLI를 사용하여 업데이트할 환경 분기를 확인하십시오.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. 카탈로그 서비스 모듈을 추가합니다.

   ```bash
   composer require "magento/catalog-service" "^3.0.1" --no-update
   ```

1. 패키지 종속성을 업데이트합니다.

   ```bash
   composer update "magento/catalog-service"
   ```

1. 에 대한 코드 변경 내용 커밋 및 푸시 `composer.json` 및 `composer.lock` 파일.

1. 에 대한 코드 변경 사항을 추가, 커밋 및 푸시합니다. `composer.json` 및 `composer.lock` 파일을 클라우드 환경으로 가져왔습니다.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   업데이트를 푸시하면 [Commerce 클라우드 배포 프로세스](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) 를 눌러 변경 사항을 적용합니다. 에서 배포 상태를 확인합니다. [로그 배포](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB 온-프레미스]

이 메서드를 사용하여 다음을 설치하십시오. [!DNL Catalog Service] 온-프레미스 인스턴스에 대한 확장.

1. 작성기를 사용하여 프로젝트에 카탈로그 서비스 모듈을 추가합니다.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"  --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update  "magento/catalog-service"
   ```

1. Adobe Commerce 업그레이드:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시를 지웁니다.

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >경우에 따라, 특히 프로덕션에 배포 시 시간이 걸릴 수 있으므로 컴파일된 코드를 지우지 않는 것이 좋습니다. 변경하기 전에 시스템을 백업해야 합니다.

>[!ENDTABS]

### 서비스 및 데이터 내보내기 구성

를 설치한 후 [!DNL Catalog Service]카탈로그 서비스를 Adobe Commerce 인스턴스와 통합하려면 다음 작업을 완료하십시오. 이 통합을 통해 Commerce 인스턴스, 카탈로그 서비스 및 기타 지원 서비스 간에 데이터를 동기화하고 통신할 수 있습니다.

1. 다음을 설정합니다. [Commerce Services 커넥터](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) api 키를 지정하고 SaaS 데이터 공간을 선택합니다.

   Commerce 서비스 커넥터 설정은 카탈로그 서비스, 라이브 검색 및 제품 Recommendations과 같은 Adobe Commerce 서비스를 사용하는 데 필요한 일회성 프로세스입니다. 다른 서비스에 대한 커넥터를 이미 구성한 경우 이 단계를 건너뜁니다.

1. 에서 초기 데이터 동기화 수행 [데이터 관리 대시보드](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   초기 동기화는 카탈로그 크기에 따라 몇 분에서 몇 시간 정도 소요될 수 있습니다. 데이터 관리 대시보드에서 동기화 상태를 모니터링할 수 있습니다. 초기 동기화 후 카탈로그는 지속적으로 제품 데이터를 내보내 서비스를 최신 상태로 유지합니다.

카탈로그 내보내기가 올바르게 실행되는지 확인하려면 다음을 수행하십시오.

- [cron 작업이 실행 중인지 확인](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- 인덱서가 다음에서 실행 중인지 확인 [관리자](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 또는 Commerce CLI 명령 사용 `bin/magento indexer:info`.
- 다음을 확인합니다 `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, 및 `Product Variant Feed` 인덱서가 다음으로 설정됨: `Update by Schedule`.

### 서비스 액세스

다음 [!DNL Catalog Service] GraphQL API는 다음에서 액세스할 수 있습니다. ` https://catalog-service.adobe.io/graphql` https에서 POST 명령을 사용하는 엔드포인트.

GraphQL 쿼리에서 관리자의 Adobe Commerce 서비스 커넥터 구성에 추가한 공개 API 키를 포함하여 여러 HTTP 헤더를 지정해야 합니다. 자세한 내용은 [Storefront Services GraphQL](https://developer.adobe.com/commerce/services/graphql/) 설명서를 참조하십시오.

### 방화벽 구성

허용하려면 [!DNL Catalog Service] 방화벽을 통해 추가 `commerce.adobe.io` 허용 목록에 추가하다로

## 카탈로그 서비스 및 API 메쉬

다음 [Adobe Developer 앱 빌더용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 을 사용하면 개발자가 Adobe IO를 사용하여 개인 또는 서드파티 API 및 기타 인터페이스를 Adobe 제품과 통합할 수 있습니다.

다음을 참조하십시오. [[!DNL Catalog Service] 및 API 메쉬](mesh.md) 항목 설치 및 구성 세부 정보.

## 데이터 관리 대시보드

에 대한 자세한 내용 [!DNL Catalog Service] 데이터 동기화를 참조하십시오. [데이터 관리 대시보드](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
