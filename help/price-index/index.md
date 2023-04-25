---
title: SaaS 가격 인덱싱
description: SaaS 가격 인덱싱 기능을 사용하여 성능 향상
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
source-git-commit: c13e836541c8f04c9621802e482754a483ef0a21
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# SaaS 가격 인덱싱

SaaS 가격 인덱싱 기능은 고객이 제출한 후에 가격 변경이 고객의 웹 사이트에 반영되는 데 걸리는 시간을 단축합니다. 이 선택적 모듈을 사용하면 크고 복잡한 카탈로그 또는 여러 웹 사이트 또는 고객 그룹이 있는 판매자가 가격 변경 사항을 보다 빠르고 지속적으로 처리할 수 있습니다.

파이프라인의 가장 큰 병목 현상: 색인 및 가격 계산과 같은 계산 중량이 많은 프로세스가 PHP 코어에서 Adobe의 클라우드 인프라로 이동되었습니다. 이를 통해 가맹점은 신속하게 리소스를 확장하여 가격 색인화 시간을 향상시키고 이러한 변경 사항을 훨씬 빠른 속도로 웹 사이트에 반영할 수 있습니다.

이러한 요구 사항을 충족하는 모든 가맹점은 이러한 개선 사항의 혜택을 누릴 수 있지만, 다음과 같은 혜택을 누릴 수 있는 고객도 있습니다.

* 고정 가격 변경: 빈번한 판촉, 계절별 할인 또는 재고 가격 등과 같은 전략적 목표를 충족하기 위해 가격을 반복적으로 변경해야 하는 상인들.
* 여러 웹 사이트 및/또는 고객 그룹: 여러 웹 사이트(도메인/브랜드) 및/또는 고객 그룹에서 공유 제품 카탈로그를 사용하는 상인.
* 웹 사이트 또는 고객 그룹 간에 고유한 가격이 많은 경우: 서로 다른 가격 전략을 사용하는 B2B 판매자와 같이 웹 사이트나 고객 그룹에서 고유한 가격을 포함하는 광범위한 공유 제품 카탈로그를 가진 판매자.

PHP 코어 가격 인덱서를 사용하는 타사 응용 프로그램이 있는 경우 설명서를 읽고 변경 전에 확장 공급자에게 문의하십시오.

Adobe Commerce 서비스를 사용하는 고객은 SaaS 가격 색인화를 무료로 사용할 수 있습니다.

이 미니 안내서에서는 SaaS 가격 색인화가 작동하는 방식과 활성화하는 방법을 설명합니다.

## 시스템 요구 사항

SaaS 가격 색인을 사용하려면 다음 사항이 필요합니다.

* Adobe Commerce 2.4.4+
* 다음 SaaS 서비스 중 하나 이상 설치됨:

   * [카탈로그 서비스](../catalog-service/overview.md)
   * [라이브 검색](../live-search/guide-overview.md)
   * [제품 Recommendations](../product-recommendations/guide-overview.md)

## 모듈

SaaS 가격 인덱싱은 모듈 집합을 사용하여 기능을 제공합니다. 필요한 모듈 목록은 저장소 설정에 따라 약간 다를 수 있습니다.

이 두 모듈은 새 피드를 관리자에게 추가합니다. 이러한 피드는 가격 계산에 필요한 데이터를 SaaS 인덱서로 전송하고 PHP 코어 가격 인덱서를 무시합니다.

```
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Luma 및 Adobe Commerce Core GraphQL을 사용하는 고객은 Luma 호환성을 제공하고 PHP 코어 가격 색인을 비활성화하는 모듈을 설치할 수 있습니다.

```
adobe-commerce/catalog-adapter
```

다음 `catalog-adapter` 는 2.4.5와만 호환됩니다. 2.4.4 및 2.4.6에 대한 지원은 가까운 시일 내에 출시될 예정입니다.
타사 확장 또는 다른 이유로 필요한 경우 PHP 코어 가격 인덱서를 다시 사용할 수 있습니다.

## 경고

제품 유형, 가격 복잡성 및 카탈로그 크기 등의 요인에 따라 SaaS 가격 인덱싱이 스토어에 적합한 솔루션일 수 있습니다. 다음 제한 사항을 읽고 이 솔루션이 사이트에 적합한 솔루션인지 판별하십시오.

현재 SaaS 가격 인덱싱은 Simple, Grouped, Virtual, Configurable 및 Bundle Dynamic 제품 유형을 지원합니다.
다운로드 가능, 기프트 카드 및 번들 고정 제품 유형에 대한 지원이 곧 제공될 예정입니다.

SaaS 가격 인덱싱은 기본 가격을 지원합니다.

* 최소/최대 정규 가격
* 최소/최대 최종 가격
* 특별 가격
* 고객 그룹 가격
* 카탈로그 규칙 가격

새 가격 책정 피드를 사용하기 위해 옵트인하면 [지원](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) 실행 취소를 돕기 위해.

새 피드는 를 사용하여 수동으로 동기화해야 합니다. `resync` [CLI 명령](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). 그렇지 않으면 표준 동기화 프로세스에서 데이터가 새로 고쳐집니다. 에 대한 자세한 정보 받기 [카탈로그 동기화](../landing/catalog-sync.md) 프로세스.

## 사용 시나리오

### 확장 종속성이 없는 Luma

* 필요한 서비스(Live Search, Product Recommendations, Catalog Service)가 설치된 Luma 또는 Adobor Commerce Core GraphQL 머천트
* PHP 코어 가격 색인에 의존하는 타사 확장이 없음
* 간단하고 구성 가능하고 그룹화된 동적 제품, 가상 제품 및 번들 제품 판매

1. 새 피드를 활성화합니다.
1. 카탈로그 어댑터를 설치합니다.

### PHP 코어 가격 색인 종속성이 있는 Luma 및 Adobor Commerce Core GraphQl

* 지원되는 서비스(Live Search, Product Recommendations, Catalog Service)가 설치된 Luma 또는 Adobor Commerce Core GraphQL 머천트
* PHP 코어 가격 색인에 의존하는 타사 확장 사용
* 간단하고 구성 가능하고 그룹화된 동적 제품, 가상 제품 및 번들 제품 판매

1. 새 피드 활성화
1. 카탈로그 어댑터를 설치합니다.
1. PHP 코어 가격 색인을 다시 사용하도록 설정합니다.
1. 에서 새 피드 및 Luma 호환성 코드를 사용합니다. `catalog-adapter` 모듈.

### 헤드리스 머천트

* 지원되는 서비스(라이브 검색, 제품 Recommendations, 카탈로그 서비스)가 설치되어 있는 헤드리스 머천트입니다
* PHP 코어 가격 색인에 의존하지 않음
* 간단하고 구성 가능하고 그룹화된 동적 제품, 가상 제품 및 번들 제품 판매

1. 새 피드 활성화
1. PHP 코어 가격 인덱서를 사용하지 않는 카탈로그 어댑터를 설치합니다.

### 지원되지 않는 제품 유형이 있는 Luma/Core GraphQL/Headless

* Luma/Headless 머천트
* 기프트 카드, 다운로드 가능 또는 번들 고정 제품 판매

현재 지원되지 않는 제품 유형을 사용하는 경우 전체 제품 유형 지원을 기다립니다.
