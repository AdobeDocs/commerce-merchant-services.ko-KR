---
title: SaaS 가격 인덱싱 설치
description: SaaS 가격 색인화 설치
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# SaaS 가격 인덱싱 설치

SaaS 가격 색인을 설정하려면 새로운 모듈을 설치하고 CLI 명령을 실행해야 합니다. 이 설치를 완료하려면 관리자가 명령줄 액세스 권한이 필요합니다.

## 전제 조건

* Adobe Commerce 2.4.4+
* 다음 SaaS 서비스 중 하나 이상이 설치되었습니다.

   * [카탈로그 서비스](../catalog-service/overview.md)
   * [라이브 검색](../live-search/guide-overview.md)
   * [제품 Recommendations](../product-recommendations/guide-overview.md)

## 필수 모듈 설치

설정에 따라 설치 프로세스가 약간 다를 수 있습니다.
새 피드와 지원 코드를 추가하는 확장이 있으며, 기본 가격 피드를 제거하는 확장이 있습니다.

1. 에 다음 모듈을 추가합니다. `composer.json` 파일:

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
   ```

1. upgrade 명령을 실행합니다.

   ```bash
   bin/magento setup:upgrade
   ```

업그레이드 후 세 가지 새로운 피드를 사용할 수 있습니다.

* `prices` - 가격 데이터를 서비스에 게재할 책임
* `scopesCustomerGroup` - 고객 그룹을 서비스에 게재할 책임
* `scopesWebsite` - 서비스에 웹 사이트, 스토어 그룹 및 스토어 조회수 제공


1. &quot;일정에 따라 업데이트&quot; 모드로 설정하도록 새 피드를 구성합니다.

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 새 피드를 다시 색인화합니다.

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

필요에 따라 위의 인덱서를 수동으로 실행합니다. 그렇지 않으면 표준 동기화 프로세스에서 데이터가 새로 고쳐집니다. 자세한 내용 [카탈로그 동기화](../landing/catalog-sync.md) 서비스.

Luma 및 Adobe Commerce 핵심 GraphQL 사용자는 `catalog-adapter` luma 및 Core GraphQl 호환성을 제공하고 PHP 핵심 가격 인덱서를 비활성화하는 모듈입니다.
을(를) 사용하려면 `catalog-adapter` 모듈, [!DNL Live Search] 및 [!DNL Catalog Service] 먼저 을(를) 설치하고 구성해야 합니다. 다음 [설치 [!DNL Live Search]](../live-search/install.md) 및 [카탈로그 서비스 설치](../catalog-service/installation.md) 계속하기 전 지침

라이브 검색 및 카탈로그 어댑터를 구성하려면 다음을 수행합니다 [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) 지침.

```bash
composer require adobe-commerce/catalog-adapter
```

필요한 경우 다음 명령을 사용하여 PHP 코어 가격 인덱서를 다시 활성화할 수 있습니다.

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
