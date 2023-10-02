---
title: SaaS 가격 인덱싱
description: SaaS 가격 색인을 사용하여 성능 향상
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: b7989b416f852d2c7164d21e8f0598373662b760
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# SaaS 가격 인덱싱

SaaS 가격 인덱싱은 가격 변경 사항이 반영되는 데 걸리는 시간을 단축합니다. [상거래 서비스](../landing/saas.md) 제출 후. 따라서 크고 복잡한 카탈로그가 있거나 여러 웹 사이트 또는 고객 그룹이 있는 판매자는 가격 변경을 지속적으로 처리할 수 있습니다.
헤드리스 매장이 있거나 [카탈로그 어댑터](./catalog-adapter.md) 확장 프로그램에서 고객은 Adobe Commerce 핵심 가격 인덱서를 비활성화할 수 있습니다.

색인 및 가격 산정과 같은 계산 중심의 프로세스가 Commerce 코어에서 Adobe의 클라우드 인프라로 이전되었습니다. 이를 통해 판매자는 신속하게 리소스를 확장하여 가격 인덱싱 시간을 늘리고 이러한 변경 사항을 보다 빠르게 반영할 수 있습니다.

SaaS 서비스로의 핵심 인덱싱 데이터 흐름은 다음과 같습니다.

![기본 데이터 흐름](assets/old_way.png)

SaaS 가격 인덱싱을 사용하면 다음과 같은 흐름이 가능합니다.

![SaaS 가격 인덱싱 데이터 흐름](assets/new_way.png)

모든 상인은 이러한 개선 사항의 이점을 누릴 수 있지만, 가장 큰 이익을 볼 수 있는 고객은 다음과 같은 이점을 가진 고객입니다.

* 지속적인 가격 변경: 빈번한 프로모션, 시즌 할인 또는 재고 감소와 같은 전략적 목표를 충족하기 위해 가격을 반복적으로 변경해야 하는 판매자입니다.
* 여러 웹 사이트 및/또는 고객 그룹: 여러 웹 사이트(도메인/브랜드) 및/또는 고객 그룹에 공유된 제품 카탈로그를 보유한 판매자입니다.
* 웹 사이트 또는 고객 그룹에서 고유 가격이 많음: 사전 협상된 가격을 제공하는 B2B 가맹점, 다른 가격 전략을 사용하는 브랜드 등 웹 사이트 또는 고객 그룹에서 고유 가격을 포함하는 광범위한 공유 제품 카탈로그를 사용하는 가맹점.

SaaS 가격 색인화는 Adobe Commerce 서비스를 사용하는 고객에게 무료로 제공되며, 모든 빌트인 Adobe Commerce 제품 유형에 대한 가격 계산을 지원합니다.

이 미니 가이드에서는 SaaS 가격 인덱싱의 작동 방식과 사용 방법에 대해 설명합니다.

## 요구 사항

* Adobe Commerce 2.4.4+
* 최신 버전의 Adobe Commerce 확장을 사용하는 다음 Commerce Services 중 하나 이상:

   * [카탈로그 서비스](../catalog-service/overview.md)
   * [라이브 검색](../live-search/guide-overview.md)
   * [제품 Recommendations](../product-recommendations/guide-overview.md)

Luma 및 Adobe Commerce 핵심 GraphQL 사용자는 [`catalog-adapter`](catalog-adapter.md) Luma 및 Core GraphQl 호환성을 제공하고 Adobe Commerce 제품 가격 인덱서를 비활성화하는 확장입니다.

## 사용

SaaS 가격 색인화 지원을 사용하여 Adobe Commerce 인스턴스를 업그레이드한 후 새 피드를 동기화합니다.

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
magento/module-bundle-product-override-data-exporter
magento/module-gift-card-product-data-exporter
```

## 사용자 정의 제품 유형에 대한 가격

가격 계산은 기준 가격, 특별 가격, 그룹 가격, 카탈로그 규칙 가격 등과 같은 사용자 지정 제품 유형에 대해 지원됩니다.

특정 공식을 사용하여 최종 가격을 계산하는 사용자 정의 제품 유형이 있는 경우 제품 가격 피드의 동작을 확장할 수 있습니다.

## 사용

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
    </type>
</config>
```

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

## 사용자 정의 가격

SaaS 가격 인덱서는 특별 가격, 그룹 가격 및 카탈로그 규칙 가격과 같이 Adobe Commerce에서 사용할 수 있는 사용자 정의 제품 유형 가격 기능을 지원합니다.

예: 사용자 정의 제품 유형이 있습니다  `custom_type` SKU &quot;사용자 정의 유형 제품&quot;을 사용하는 제품입니다.

기본적으로 Commerce 데이터 내보내기 확장은 가격 인덱서로 다음 가격 피드를 보냅니다.

```json
{
    "sku": "Custom Type Product",
    "type": "SIMPLE", // must be "SIMPLE" regardless of the real product type
    "customerGroupCode": "0",
    "websiteCode": "base",
    "regular": 123, // the regular base price found in catalog_product_entity_decimal table
    "discounts":    // list of discounts: special_price, group, catalog_rule
    [
        {
            "code": "catalog_rule",
            "price": 102.09
        }
    ],
    "deleted": false,
    "updatedAt": "2023-07-31T13:07:54+00:00"
}
```

&quot;사용자 정의 제품 유형&quot;이 제품 가격을 계산하기 위해 고유한 공식을 사용하는 경우 시스템 통합자는 Commerce 데이터 내보내기 확장 기능을 확장하여 가격 및 할인 필드를 재정의할 수 있습니다.

1. 에서 플러그인 만들기 `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` 클래스.

`di.xml` 파일:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
        <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" disabled="false" />
    </type>
</config>
```

1. 사용자 지정 수식으로 메서드를 만듭니다.

```php
class UpdatePriceFromFeed
{
    /**
    * @param ProductPrice $subject
    * @param array $result
    * @param array $values
    *
    * @return array
    */
    public function afterGet(ProductPrice $subject, array $result, array $values) : array
    {
        // Get all custom products, prices and discounts per website and customer groups
        // Override the output $result with your data for the corresponding products
        return $result;
    }
}
```
