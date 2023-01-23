---
title: 온보딩 및 설치
description: 설치 방법 알아보기 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 3cf7959ece051c82a0f9ed1125571f223427923e
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# 온보딩 및 설치

## 전제 조건

에 대한 온보딩 프로세스 [!DNL Catalog Service] 서버의 명령줄에 액세스해야 합니다. 명령줄에서 작업하는 방법을 잘 모를 경우 개발자나 시스템 통합자에게 도움을 요청하십시오.

### 소프트웨어 요구 사항

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- 작성기: 2.x, 1.x

### 지원되는 플랫폼

- Adobe Commerce on cloud 인프라: 2.4.x
- Adobe Commerce 온-프레미스: 2.4.x

## 환경

카탈로그 서비스에는 온보딩에 사용할 수 있는 두 가지 환경이 있습니다.

- 샌드박스 (https://catalog-service-sandbox.adobe.io/graphql) - 라이브로 전환되기 전에 테스트 및 유효성 검사에 사용됨
- 프로덕션 (https://catalog-service.adobe.io/graphql)-) 상거래 상인 및 웹 사이트의 라이브 트래픽에 사용됨

## 설치 및 구성

Adobe Commerce용 카탈로그 서비스를 시작하려면 다음 단계를 수행해야 합니다.

- 데이터 내보내기 확장 설치
- 서비스 및 데이터 내보내기 구성
- 서비스 액세스

### 데이터 내보내기 확장 설치

카탈로그 서비스에 대한 온보딩 프로세스에서는 서버의 명령줄에 액세스해야 합니다.

카탈로그 서비스 확장은 Adobe Commerce 클라우드 인프라 및 온-프레미스 인스턴스 모두에 설치할 수 있습니다.

카탈로그 서비스가 전자 상거래 계정에 연결된 작성기 키와 함께 설치됩니다 [자이드](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 등록 프로세스 중에 제공됩니다. 작성기는 Adobe Commerce의 초기 설치 중에 또는 작성기 키가 이전에 외부 키에 저장되지 않았던 상황에서 이러한 키를 사용합니다 `auth.json` 파일.

자세한 내용은 [인증 키 가져오기](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) 작성기 키 가져오기에 대한 자세한 정보.

#### Adobe Commerce on cloud 인프라

Commerce Cloud 인스턴스에 대해 카탈로그 서비스 확장을 설치하는 데 이 방법을 사용합니다.

1. 를 엽니다. `<Commerce_root>/composer.json` 텍스트 편집기에서 파일을 작성하고 다음과 같이 필요한 섹션을 업데이트합니다.

   ```json
   "require": {
     "magento/module-saas-catalog": "^101.4.0",
     "magento/module-saas-product-override": "^101.4.0",
     "magento/module-saas-product-variant": "^101.4.0",
     "magento/module-bundle-product-data-exporter": "^101.3.1",
     "magento/module-catalog-data-exporter": "^101.3.1",
     "magento/module-catalog-inventory-data-exporter": "^101.3.1",
     "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
     "magento/module-configurable-product-data-exporter": "^101.3.1",
     "magento/module-data-exporter": "^101.3.1",
     "magento/module-parent-product-data-exporter": "^101.3.1",
     "magento/module-product-override-data-exporter": "^101.3.1",
     "magento/data-services": "^7.0.11",
     "magento/services-id": "^3.0.1",
     "magento/services-connector": "1.2.1",
     "magento/module-catalog-service-installer": "1.0.1"
   }
   ```

1. 로컬에서 새 구성을 테스트하고 종속성을 업데이트합니다.

```bash
composer update
```

명령은 모든 종속성을 업데이트합니다.

1. 변경 내용 커밋 및 푸시 `composer.json` 및 `composer.lock`.

#### 온-프레미스

온-프레미스 인스턴스에 대한 카탈로그 서비스 확장을 설치하는 데 이 방법을 사용합니다.

1. 를 엽니다. `<Commerce_root>/composer.json` 텍스트 편집기에서 파일을 작성하고 다음과 같이 필요한 섹션을 업데이트합니다.

```json
"require": {
 "magento/module-saas-catalog": "^101.4.0",
 "magento/module-saas-product-override": "^101.4.0",
 "magento/module-saas-product-variant": "^101.4.0",
 "magento/module-bundle-product-data-exporter": "^101.3.1",
 "magento/module-catalog-data-exporter": "^101.3.1",
 "magento/module-catalog-inventory-data-exporter": "^101.3.1",
 "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
 "magento/module-configurable-product-data-exporter": "^101.3.1",
 "magento/module-data-exporter": "^101.3.1",
 "magento/module-parent-product-data-exporter": "^101.3.1",
 "magento/module-product-override-data-exporter": "^101.3.1",
 "magento/data-services": "^7.0.11",
 "magento/services-id": "^3.0.1",
 "magento/services-connector": "1.2.1",
 "magento/module-catalog-service-installer": "1.0.1"
}
```

1. 종속성을 업데이트하고 확장을 설치합니다.

```bash
composer update
```

명령은 모든 종속성을 업데이트합니다.

1. Adobe Commerce 업그레이드:

```bash
bin/magento setup:upgrade
```

1. 캐시 지우기:

```bash
bin/magento cache:clean
```

### 서비스 및 데이터 내보내기 구성

카탈로그 서비스를 설치한 후 다음을 구성해야 합니다 [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) API 키를 지정하고 SaaS 데이터 공간을 선택하여 데이터를 삭제합니다.

SaaS 구성이 완료되면 다음을 수행하여 초기 데이터 동기화를 수행합니다 [카탈로그 동기화](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 안내서.

카탈로그 내보내기가 올바르게 실행되는지 확인하려면:

- 크론 작업이 실행 중인지 확인합니다.
- 인덱서가 실행 중인지 확인합니다.
- 다음을 확인합니다. `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, 및 `Product Variant Feed` 인덱서는 &quot;Update by Schedule&quot;로 설정됩니다.

카탈로그 크기에 따라 초기 동기화가 몇 분에서 몇 시간 정도 걸릴 수 있습니다. 초기 동기화 후 카탈로그는 서비스를 최신 상태로 유지하기 위해 지속적으로 상거래 서버에서 상거래 서비스로 제품 데이터를 내보냅니다.

### 서비스 액세스

카탈로그 서비스 API는 HTTPS를 통해 POST 명령을 사용하여 액세스할 수 있습니다.

api 키를 얻으려면 관리자의 Commerce Service Connector 영역으로 이동하여 공개 API 키를 복사합니다.

다음 문서를 참조하십시오. [GraphQL 설명서](https://developer.adobe.com/commerce/webapi/graphql/) api 요청을 생성하는 데 필요한 헤더를 쿼리하고 전송하는 방법을 이해합니다.

## 카탈로그 서비스 및 API Mesh

다음 [Adobe Developer App Builder용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 개발자는 Adobe IO를 사용하여 개인 또는 타사 API 및 기타 인터페이스를 Adobe 제품과 통합할 수 있습니다.

자세한 내용은  [카탈로그 서비스 및 API Mesh](mesh.md) 설치 및 구성 세부 정보에 대한 항목입니다.
