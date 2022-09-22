---
title: 제품 쿼리
description: '''Adobe Commerce 카탈로그 서비스에 대한 ''products'' GraphQL 쿼리에 대한 참조 안내서입니다.'''
source-git-commit: d9b8c89f6d04aa9d569b450af2893b92938119ad
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---


# 제품 쿼리

Adobe Commerce용 카탈로그 서비스 `products` 쿼리는 입력으로 지정된 SKU에 대한 세부 정보를 반환합니다. 이 쿼리의 이름은 [`products` 쿼리](https://devdocs.magento.com/guides/v2.4/graphql/queries/products.html) 여기에는 핵심 Adobe Commerce 및 Magento Open Source이 제공되지만, 몇 가지 차이점이 있습니다.

카탈로그 서비스 쿼리에는 입력으로 하나 이상의 SKU 값이 필요합니다. 쿼리는 주로 다음 유형의 컨텐츠를 렌더링하기 위해 정보를 검색하도록 설계되었습니다.

* 제품 세부 사항 페이지 - 지정된 SKU에서 식별한 제품에 대한 전체 세부 사항을 제공할 수 있습니다.

* 제품 비교 페이지 - 이름, 가격 및 이미지와 같은 여러 제품에 대해 선택한 정보를 검색할 수 있습니다.

다음 `ProductView` 출력 개체는 코어와 크게 다릅니다 `products` 쿼리 `Products` 출력 개체. 주요 차이점은 다음과 같습니다.

* 제품은 간단하거나 복잡합니다. 간단한 가상, 다운로드 가능한 및 기프트 카드 제품은 `SimpleProductView`. 다른 모든 제품 유형은에 매핑됩니다. `ComplexProductView`. 단순한 제품들이 가격을 정의했다. 복합 제품에는 가격 범위가 있습니다. 복합제품은 단순 제품만 여러 개로 이루어져 있기 때문에 단순한 제품 가격에 접근할 수 있다.

* 머천트 정의 속성은 최상위 컨테이너에서 노출되며 해당 저장소 역할을 나타냅니다. 역할에는 PDP에 표시, PLP에 표시 및 검색 결과에 표시 등이 포함됩니다.

* 이미지는 최상위 컨테이너로도 액세스할 수 있으며 해당 역할에 따라 필터링할 수 있습니다. 이미지에는 기본, 작은 또는 축소판 역할이 있을 수 있습니다.

## 구문

```graphql
products (skus [String]) [ProductView]
```

## 필수 헤더

이 쿼리를 실행하려면 다음 HTTP 헤더를 지정해야 합니다.

| Header | 설명 |
| --- | --- |
| `Magento-Customer-Group` | 상점 클라이언트의 경우 이 값은 `dataservices_customer_group` 쿠키 . |
| `Magento-Environment-Id` | 이 값은 다음에 표시됩니다. **시스템** > **Commerce Services 커넥터** > **SaaS 식별자** > **데이터 공간 ID** 또는 를 실행하여 `bin/magento config:show services_connector/services_id/environment_id` 명령. |
| `Magento-Store-Code` | 활성 저장소 보기에 연결된 저장소에 할당된 코드입니다. For example, `main_website_store`. |
| `Magento-Store-View-Code` | 활성 저장소 보기에 지정된 코드입니다. 예, `default`. |
| `Magento-Website-Code` | 활성 저장소 보기와 연결된 웹 사이트에 지정된 코드입니다. 예, `base`. |
| `X-Api-Key` | 온보딩 프로세스 중에 생성된 고유 키입니다. |

## 사용 예

### 단순 제품에 대한 자세한 내용 반환

다음 쿼리는 단순 제품에 대한 세부 사항을 반환합니다.

**요청:**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
        regular {
          amount {
            value
            currency
          }
        }
      }
    }
  }
}
```

**응답:**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### 복잡한 제품에 대한 세부 정보 반환 {#complex-product-example}

다음 쿼리는 구성 가능한 제품에 대한 세부 정보를 반환합니다.

**요청:**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
        }
      }
    }
  }
}
```

**응답:**

```json
{
  "data": {
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## 출력 필드

다음 `ProductView` 반환 개체는 다음 필드를 포함할 수 있는 인터페이스입니다. 이 변수는 [`SimpleProductView`](#SimpleProductView-type) 및 [`ComplexProductView`](#ComplexProductView-type) 유형.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 상기 스토어프런트에 대해 지정된 상인의 정의 속성 목록. |
| `description` | 문자열 | 제품에 대한 자세한 설명입니다. |
| `id` | ID! | 복합 키로 생성된 로케일별 고유한 제품 ID입니다. |
| `images(roles: [String])` | [ProductViewImage] | 제품에 대해 정의된 이미지 목록입니다. |
| `metaDescription` | 문자열 | 검색 결과 목록에 대한 제품에 대한 간략한 개요. |
| `metaKeyword` | 문자열 | 검색 엔진에만 표시되는 쉼표로 구분된 키워드 목록입니다. |
| `metaTitle` | 문자열 | 브라우저의 제목 표시줄과 탭 및 검색 결과 목록에 표시되는 문자열입니다. |
| `name` | 문자열 | 제품 이름. |
| `shortDescription` | 문자열 | 제품의 요약. |
| `sku` | 문자열 | 제품 SKU. |
| `url` | 문자열 | 제품의 정식 URL입니다. |

### ComplexProductView 유형 {#ComplexProductView-type}

다음 `ComplexProductView` type 은 번들, 구성 가능 및 그룹 제품을 나타냅니다. 가격 값은 선택한 옵션에 따라 다를 수 있으므로 복잡한 제품 가격이 가격 범위로 반환됩니다. 형식이 구현됩니다 `ProductView`.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 상기 스토어프런트에 대해 지정된 상인의 정의 속성 목록. |
| `description` | 문자열 | 제품에 대한 자세한 설명입니다. |
| `id` | ID! | 복합 키로 생성된 로케일별 고유한 제품 ID입니다. |
| `images(roles: [String])` | [ProductViewImage] | 제품에 대해 정의된 이미지 목록입니다. |
| `metaDescription` | 문자열 | 검색 결과 목록에 대한 제품에 대한 간략한 개요. |
| `metaKeyword` | 문자열 | 검색 엔진에만 표시되는 쉼표로 구분된 키워드 목록입니다. |
| `metaTitle` | 문자열 | 브라우저의 제목 표시줄과 탭 및 검색 결과 목록에 표시되는 문자열입니다. |
| `name` | 문자열 | 제품 이름. |
| `options` | [ProductViewOption] | 선택 가능한 옵션 목록입니다. |
| `priceRange` | ProductViewPriceRange | 복합 제품에 대한 가능한 가격 범위입니다. |
| `shortDescription` | 문자열 | 제품의 요약. |

### 가격 유형

다음 `Price type` 단순 제품 또는 복합 제품에 대한 가격 범위의 일부를 정의합니다. 여기에는 가격 조정 목록이 포함될 수 있습니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `amount` | ProductViewMoney | 제품의 통화 값과 통화 코드를 포함합니다. |

### 가격 조정 유형

다음 `PriceAdjustment` 유형 가격 조정의 금액과 유형을 지정합니다. 코드 값의 예는 입니다. `weee`.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `amount` | 부동 | 가격 조정 금액입니다. |
| `code` | 문자열 | 가격 조정 유형을 식별합니다. |

### ProductViewAttribute 형식

다음 `ProductViewAttribute` 유형 은 storefront에 표시되는 고객 정의 속성의 컨테이너입니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `label` | 문자열 | 특성의 레이블입니다. |
| `name` | 문자열! | 속성 코드의 이름입니다. |
| `roles` | [문자열] | &quot;PLP에 표시&quot;, &quot;PDP에 표시&quot; 또는 &quot;검색에 표시&quot;와 같이 상점 전면의 속성에 대해 지정된 역할. |
| `value` | JSON | 임의 유형의 속성 값. |

### ProductViewImage 유형

다음 `ProductViewImage` 유형 에는 제품 이미지에 대한 세부 사항이 포함되어 있습니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `label` | 문자열 | 제품 이미지의 표시 레이블입니다. |
| `roles` | [문자열] | 이미지 사용 방법을 설명하는 목록입니다. 다음을 수행할 수 있습니다. `image`, `small_image`, 또는 `thumbnail`. |
| `url` | 문자열! | 제품 이미지의 URL. |

### ProductViewMoney 유형

다음 `ProductViewMoney` 유형은 숫자 값과 통화 코드를 포함하여 통화 값을 정의합니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `currency` | ProductViewCurrency | USD 또는 EUR과 같은 세 문자로 된 통화 코드입니다. |
| `value` | 부동 | 통화 가치를 나타내는 숫자. |

### ProductViewOption 유형

제품 옵션은 특정 옵션 값을 선택하여 제품을 구성하는 방법을 제공합니다. 하나 이상의 옵션을 선택하면 특정 간단한 제품이 선택됩니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `id` | ID | 옵션 ID입니다. |
| `multi` | 부울 | 옵션을 통해 여러 선택 사항을 허용할지 여부를 나타냅니다. |
| `required` | 부울 | 옵션을 선택해야 하는지 여부를 나타냅니다. |
| `title` | 문자열 | 옵션의 표시 이름입니다. |
| `values` | [ProductViewOptionValue!] | 사용 가능한 옵션 값 목록입니다. |

### ProductViewOptionValue 인터페이스

다음 `ProductViewOptionValue` 인터페이스는 `ProductViewOptionValueProduct` 및 `ProductViewOptionValueConfiguration` 유형.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `id` | ID | 옵션 값의 ID입니다. |
| `title` | 문자열 | 옵션 값의 표시 이름입니다. |

### ProductViewOptionValueConfiguration 유형

다음 `ProductViewOptionValueConfiguration` type은 의 구현입니다. `ProductViewOptionValue` 참조하십시오.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `id` | ID | 옵션 값의 ID입니다. |
| `title` | 문자열 | 옵션 값의 표시 이름입니다. |

### ProductViewOptionValueProduct 유형

다음 `ProductViewOptionValueProduct` type은 의 구현입니다. `ProductViewOptionValue` 단순한 제품에 대한 세부 정보가 추가됩니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `id` | ID | 옵션 값의 ID입니다. |
| `title` | 문자열 | 옵션 값의 표시 이름입니다. |
| `product` | SimpleProductView | 간단한 제품에 대한 세부 사항입니다. |

### ProductViewPrice 유형

다음 `ProductViewPrice` 유형은 간단한 제품에 고유한 기본 제품 가격 보기를 제공합니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `final` | 가격 | 할인 후 가격(개인화된 프로모션 제외) |
| `regular` | 가격 | 머천트에서 지정한 기본 제품 가격. |
| `roles` | [문자열] | 가격을 표시할지 여부를 결정합니다. |

### ProductViewPriceRange 유형

다음 `ProductViewPriceRange` type은 복잡한 제품의 최소 및 최대 가격을 나열합니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `maximum` | ProductViewPrice | 최대 가격. |
| `minimum` | ProductViewPrice | 최소 가격입니다. |

### SimpleProductView 유형 {#SimpleProductView-type}

다음 `SimpleProductView` type 은 번들, 구성 가능 및 그룹을 제외한 모든 제품 유형을 나타냅니다. 단순 제품 가격에는 가격 범위가 포함되지 않습니다. `SimpleProductView` 구현 `ProductView`.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | 상기 스토어프런트에 대해 지정된 상인의 정의 속성 목록. |
| `description` | 문자열 | 제품에 대한 자세한 설명입니다. |
| `id` | ID! | 복합 키로 생성된 로케일별 고유한 제품 ID입니다. |
| `images(roles: [String])` | [ProductViewImage] | 제품에 대해 정의된 이미지 목록입니다. |
| `metaDescription` | 문자열 | 검색 결과 목록에 대한 제품에 대한 간략한 개요. |
| `metaKeyword` | 문자열 | 검색 엔진에만 표시되는 쉼표로 구분된 키워드 목록입니다. |
| `metaTitle` | 문자열 | 브라우저의 제목 표시줄과 탭 및 검색 결과 목록에 표시되는 문자열입니다. |
| `name` | 문자열 | 제품 이름. |
| `price` | ProductViewPrice | 기본 제품 가격 보기. |
| `shortDescription` | 문자열 | 제품의 요약. |
| `sku` | 문자열 | 제품 SKU. |
| `url` | 문자열 | 제품의 정식 URL입니다. |
