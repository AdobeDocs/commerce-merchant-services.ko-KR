---
title: 카탈로그 어댑터 확장
description: 카탈로그 어댑터를 사용하여 Commerce Services의 가격 렌더링
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
source-git-commit: 6b578e7113c278a05a64f2db5e032bccc4a9580a
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# 카탈로그 어댑터

다음 `Catalog Adapter` 확장은 기본 Adobe Commerce 제품 가격 인덱서를 비활성화하고 대신 [카탈로그 서비스](../catalog-service/overview.md).
Adobe Commerce 제품 가격 인덱서가 비활성화되어 있으므로 이러한 확장 모듈이 설치되어 있으면 이 인덱서를 켤 수 없습니다. 이 확장을 제거하거나 사용하지 않도록 설정해야만 기본 제품 가격 인덱서를 다시 사용할 수 있습니다.

## 요구 사항

* Adobe Commerce 2.4.4+
* 다음 Commerce Services 중 하나가 설치되었습니다.

   * [카탈로그 서비스](../catalog-service/overview.md)
   * [라이브 검색](../live-search/guide-overview.md)

## 설치

을(를) 사용하려면 `catalog-adapter` 모듈, [!DNL Live Search] 및 [!DNL Catalog Service] 먼저 을(를) 설치하고 구성해야 합니다. 다음 [설치 [!DNL Live Search]](../live-search/install.md) 및 [카탈로그 서비스 설치](../catalog-service/installation.md) 계속하기 전 지침

이러한 서비스가 설치되면 다음 명령을 실행합니다.

```bash
composer require adobe-commerce/catalog-adapter
```

## Adobe Commerce 제품 가격 인덱서 다시 실행

기본 Adobe Commerce 제품 가격 인덱서를 사용하는 서드파티 애플리케이션이 있는 경우 다음 명령을 사용하여 다시 활성화할 수 있습니다.

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# reindex Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## Headless Storefront 시나리오에 대한 제품 가격 인덱서 비활성화

Headless Commerce 인스턴스가 있는 경우 Adobe Commerce 제품 가격 인덱서를 비활성화하여 Adobe Commerce 인스턴스의 로드를 줄여야 할 수 있습니다.
이 작업은 다음을 설치하여 수행합니다. `magento/module-price-indexer-disabler` 모듈:

```bash
composer require magento/module-price-indexer-disabler
```

## 사용 시나리오

다음은 몇 가지 일반적인 사항입니다 `Catalog Adapter` 시나리오.

### Adobe Commerce 제품 가격 인덱서에 대한 종속성 없음

* 필요한 서비스(라이브 검색, 제품 Recommendations, 카탈로그 서비스)가 설치된 Luma 또는 Adobe Commerce 핵심 GraphQL 판매자입니다
* Adobe Commerce 제품 가격 인덱서에 의존하는 서드파티 확장이 없음

1. 카탈로그 어댑터를 설치합니다.

### Adobe Commerce 제품 가격 인덱서에 대한 종속성 포함

* 지원 서비스(라이브 검색, 제품 Recommendations, 카탈로그 서비스)가 설치된 Luma 또는 Adobe Commerce 핵심 GraphQL 판매자입니다
* Adobe Commerce 제품 가격 인덱서에 의존하는 타사 확장을 사용합니다

1. 카탈로그 어댑터를 설치합니다.
1. 기본 Adobe Commerce 제품 가격 인덱서를 다시 사용하도록 설정합니다.

### Headless Commerce 인스턴스

* 필수 서비스(Live Search, Product Recommendations, Catalog Service)가 설치된 Headless Commerce 인스턴스가 있는 판매자입니다.
* 기본 Adobe Commerce 제품 가격 인덱서에 의존하지 않음

1. 카탈로그 어댑터 패키지에서 &quot;가격 비활성화&quot;를 설치합니다.
