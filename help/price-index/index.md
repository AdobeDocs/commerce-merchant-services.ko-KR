---
title: SaaS 가격 인덱싱
description: SaaS 가격 색인을 사용하여 성능 향상
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 19c4d3263c22914672b38c5dc5ec9908889bb9b6
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# SaaS 가격 인덱싱

SaaS 가격 색인화는 가격 변경 사항이 제출된 후 SaaS 고객의 웹 사이트에 반영되는 데 걸리는 시간을 단축합니다. 이 옵션 모듈을 사용하면 크고 복잡한 카탈로그가 있거나 여러 웹 사이트 또는 고객 그룹이 있는 판매자가 가격 변경을 보다 빠르고 지속적으로 처리할 수 있습니다.

파이프라인의 가장 큰 병목 현상: 인덱싱과 가격 계산과 같은 계산 중심의 프로세스가 PHP 코어에서 Adobe의 클라우드 인프라로 이동되었습니다. 이를 통해 판매자는 리소스를 빠르게 확장하여 가격 책정 시간을 늘리고 훨씬 빠른 속도로 웹 사이트에 이러한 변경 사항을 반영할 수 있습니다.

SaaS 서비스로의 핵심 인덱싱 데이터 흐름은 다음과 같습니다.

![기본 데이터 흐름](assets/old_way.png)

SaaS 가격 인덱싱을 사용하면 다음과 같은 흐름이 가능합니다.

![SaaS 가격 인덱싱 데이터 흐름](assets/new_way.png)

요구 사항을 충족하는 모든 상인은 이러한 개선 사항의 이점을 누릴 수 있지만, 가장 큰 이익을 얻을 수 있는 고객은 다음과 같은 고객을 보유하고 있습니다.

* 지속적인 가격 변경: 빈번한 프로모션, 시즌 할인 또는 재고 감소와 같은 전략적 목표를 충족하기 위해 가격을 반복적으로 변경해야 하는 판매자입니다.
* 여러 웹 사이트 및/또는 고객 그룹: 여러 웹 사이트(도메인/브랜드) 및/또는 고객 그룹에 공유된 제품 카탈로그를 보유한 판매자입니다.
* 웹 사이트 또는 고객 그룹에서 고유 가격이 많음: 사전 협상된 가격을 가진 B2B 가맹점, 다른 가격 전략을 가진 브랜드 등 웹 사이트 또는 고객 그룹에서 고유 가격을 포함하는 광범위한 공유 제품 카탈로그를 가진 가맹점.

PHP 핵심 가격 인덱서를 사용하는 서드파티 애플리케이션이 있는 경우 설명서를 읽고 확장 공급자와 상의한 후 변경하십시오.

Adobe Commerce 서비스를 이용하는 고객은 SaaS 가격 인덱싱을 무료로 이용할 수 있다.

이 미니 가이드에서는 SaaS 가격 인덱싱의 작동 방식과 사용 방법에 대해 설명합니다.

## 시스템 요구 사항

SaaS 가격 색인화를 사용하려면 다음이 필요합니다.

* Adobe Commerce 2.4.4+
* 다음 SaaS 서비스 중 하나 이상이 설치되었습니다.

   * [카탈로그 서비스](../catalog-service/overview.md)
   * [라이브 검색](../live-search/guide-overview.md)
   * [제품 Recommendations](../product-recommendations/guide-overview.md)

## 모듈

SaaS 가격 인덱싱은 모듈 세트를 사용하여 기능을 제공합니다. 저장소 설정에 따라 필요한 모듈 목록이 약간 다를 수 있습니다.

이러한 모듈은 새 피드를 관리자에 추가합니다. 이러한 피드는 가격 계산에 필요한 데이터를 SaaS 인덱서로 전송하고 PHP 핵심 가격 인덱서를 무시합니다.

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Luma 및 Adobe Commerce 핵심 GraphQL을 사용하는 고객은 Luma 및 핵심 GraphQL 호환성을 제공하고 PHP 핵심 가격 인덱서를 비활성화하는 모듈을 설치할 수 있습니다.

```
adobe-commerce/catalog-adapter
```

다음 `catalog-adapter` 는 2.4.5와만 호환됩니다. 2.4.4 및 2.4.6에 대한 지원은 가까운 시일 내에 릴리스될 예정입니다.
PHP 코어 가격 인덱서는 타사 확장 프로그램 또는 기타 다른 이유로 필요한 경우 다시 활성화할 수 있습니다.

## 주의 사항

제품 유형, 가격 복잡성, 카탈로그 크기 등의 요소에 따라 SaaS 가격 색인화가 스토어에 적합한 솔루션이 될 수 있습니다. 다음 제한 사항을 읽고 이것이 사이트에 적합한 솔루션인지 확인하십시오.

현재 SaaS 가격 인덱싱은 단순, 그룹화, 가상, 구성 및 [동적 번들](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-bundle.html) 제품 유형.
다운로드 가능, 기프트 카드 및 번들 고정 제품 유형에 대한 지원이 곧 제공될 예정입니다.

새 피드를 와 수동으로 동기화해야 함 `resync` [CLI 명령](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 그렇지 않으면 표준 동기화 프로세스에서 데이터가 새로 고쳐집니다. 에 대한 자세한 정보 보기 [카탈로그 동기화](../landing/catalog-sync.md) 프로세스.

## 사용 시나리오

### 확장 종속성 없는 Luma

* 필요한 서비스(라이브 검색, 제품 Recommendations, 카탈로그 서비스)를 설치한 Luma 또는 Adobe Commerce 핵심 GraphQL 판매자
* PHP 코어 가격 인덱서에 의존하는 타사 확장 없음
* 간편한 구성, 그룹화, 가상 및 번들 동적 제품 판매

1. 새 피드를 활성화합니다.
1. 카탈로그 어댑터를 설치합니다.

### PHP 핵심 가격 인덱서 종속성이 있는 Luma 및 Adobe Commerce 핵심 GraphQl

* 지원 서비스(라이브 검색, 제품 Recommendations, 카탈로그 서비스)가 설치된 Luma 또는 Adobe Commerce 핵심 GraphQL 판매자
* PHP 코어 가격 인덱서에 의존하는 타사 확장 포함
* 간편한 구성, 그룹화, 가상 및 번들 동적 제품 판매

1. 새 피드 활성화
1. 카탈로그 어댑터를 설치합니다.
1. PHP 코어 가격 인덱서를 다시 사용하도록 설정합니다.
1. 에서 새 피드 및 Luma 호환성 코드 사용 `catalog-adapter` 모듈.

### 헤드리스 판매자

* 지원 서비스(Live Search, Product Recommendations, Catalog Service)가 설치된 Headless 판매업체
* PHP 핵심 가격 인덱서에 의존하지 않음
* 간편한 구성, 그룹화, 가상 및 번들 동적 제품 판매

1. 새 피드 사용
1. PHP 코어 가격 인덱서를 비활성화하는 카탈로그 어댑터를 설치합니다.

### 지원되지 않는 제품 유형을 사용하는 Luma/Core GraphQL/Headless

* Luma/Headless 판매자
* 기프트 카드, 다운로드 가능 또는 번들 고정 제품 판매

현재 지원되지 않는 제품 유형을 사용하는 경우 전체 제품 유형이 지원될 때까지 기다리십시오.
