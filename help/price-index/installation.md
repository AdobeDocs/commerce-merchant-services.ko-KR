---
title: SaaS 가격 인덱싱 설치
description: SaaS 가격 인덱싱 설치
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
source-git-commit: 077be6d893b800b9571a869237501e58accc01e8
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# SaaS 가격 인덱싱 설치

SaaS 가격 색인을 설정하려면 새 모듈을 설치하고 CLI 명령을 실행해야 합니다. 관리자는 이 설치를 완료하려면 명령줄 액세스 권한이 필요합니다.

## 전제 조건

* Adobe Commerce 2.4.4+
* 다음 SaaS 서비스 중 하나 이상 설치됨:

   * [카탈로그 서비스](../catalog-service/overview.md)
   * [라이브 검색](../live-search/guide-overview.md)
   * [제품 Recommendations](../product-recommendations/guide-overview.md)

## 필요한 모듈 설치

설정에 따라 설치 프로세스가 약간 다를 수 있습니다.
새 피드 및 지원 코드를 추가하는 확장이 있으며 기본 가격 피드를 제거하는 확장이 있습니다.

1. 다음 모듈을 `composer.json` 파일:

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

업그레이드 후에는 다음 세 개의 새 피드를 사용할 수 있습니다.

* `prices` - 가격 데이터를 서비스에 전달하는 책임
* `scopesCustomerGroup` - 고객 그룹을 서비스에 전달할 책임
* `scopesWebsite` - 서비스에 웹 사이트, 스토어 그룹 및 스토어 보기 제공 담당자


1. &quot;일정에 따라 업데이트&quot; 모드로 설정할 새 피드를 구성합니다.

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 새 피드를 다시 색인화합니다.

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

필요에 따라 위의 인덱스를 수동으로 실행합니다. 그렇지 않으면 표준 동기화 프로세스에서 데이터가 새로 고쳐집니다. 자세한 내용 [카탈로그 동기화](../landing/catalog-sync.md) 서비스.

Luma 및 Adobe Commerce Core GraphQL 사용자는 `catalog-adapter` Luma 및 Core GraphQl 호환성을 제공하고 PHP 코어 가격 색인을 비활성화하는 모듈입니다.
를 사용하려면 `catalog-adapter` 모듈, [!DNL Live Search] 먼저 설치해야 합니다. 다음을 수행합니다 [설치 [!DNL Live Search]](../live-search/install.md) 지침을 따르십시오.

```bash
composer require adobe-commerce/catalog-adapter
```

필요한 경우 다음 명령을 사용하여 PHP 코어 가격 인덱서를 다시 사용할 수 있습니다.

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
