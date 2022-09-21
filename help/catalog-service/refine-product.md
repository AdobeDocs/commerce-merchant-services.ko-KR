---
title: refineProduct 쿼리
description: '''Adobe Commerce 카탈로그 서비스에 대한 ''refineProduct'' GraphQL 쿼리에 대한 참조 안내서입니다.'''
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 0%

---


# refineProduct 쿼리

다음 `refineProduct` 쿼리는 `products` 복합 제품에 대해 실행된 쿼리 를 실행하기 전에 `refineProduct` query를 실행하려면 `products` 쿼리 및 구성을 통해 `options` 내 `ComplexProductView` 인라인 조각. 쇼핑객이 상점에서 제품 옵션(크기 또는 색상 등)을 선택하면 `refineProduct` SKU 및 선택한 옵션 값 ID를 입력으로 지정하여 쿼리를 클릭합니다. 복잡한 제품에 있는 제품 옵션의 수에 따라 `refineProduct` 쇼핑객이 특정 변형을 선택할 때까지 여러 번 쿼리합니다.

쿼리에 대한 응답을 작성하여 `ComplexProductView` 및 `SimpleProductView` 인라인 조각. 구매자가 필수 옵션을 모두 선택하지 않은 경우 선택한 옵션과 가능한 나머지 옵션을 기준으로 선택되지 않은 옵션의 ID와 제품의 최소 및 최대 가격을 반환합니다. 구매자가 모든 필수 옵션을 선택한 경우, 설정된 가격을 포함하는 단순 제품에 대한 세부 정보를 반환합니다.

## 구문

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
```

## 필수 헤더

이 쿼리를 실행하려면 다음 HTTP 헤더를 지정해야 합니다.

| Header | 설명 |
|--- | ---|
| `Magento-Customer-Group` | 상점 클라이언트의 경우 이 값은 `dataservices_customer_group` 쿠키 . |
| `Magento-Environment-Id` | 이 값은 다음에 표시됩니다. **시스템** > **Commerce Services 커넥터** > **SaaS 식별자** > **데이터 공간 ID** 또는 를 실행하여 `bin/magento config:show services_connector/services_id/environment_id` 명령. |
| `Magento-Store-Code` | 활성 저장소 보기에 연결된 저장소에 할당된 코드입니다. For example, `main_website_store`. |
| `Magento-Store-View-Code` | 활성 저장소 보기에 지정된 코드입니다. 예, `default`. |
| `Magento-Website-Code` | 활성 저장소 보기와 연결된 웹 사이트에 지정된 코드입니다. 예, `base`. |
| `X-Api-Key` | 온보딩 프로세스 중에 생성된 고유 키입니다. |

## 사용 예

### 부분적으로 선택된 복합 제품에 대한 세부 정보 반환

다음 쿼리는 중간 크기의 제품 변형에 사용할 수 있는 색상 옵션에 대한 세부 사항을 반환합니다 `MH12`. 의 값 `optionIDs` 입력 매개 변수는 `products` 쿼리 [복잡한 제품에 대한 세부 정보 반환](products.md#complex-product-example) 예.

**요청:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
                    }
                }
            }
        }
        ... on ComplexProductView {
            options {
                id
                title
                required
                values {
                    id
                    title

                }
            }
            priceRange {
                maximum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### 완전히 선택된 복합 제품에 대한 세부 정보 반환

다음 쿼리에서 쇼퍼는 크기와 색상 모두에 대한 옵션을 선택했습니다. 응답에는 해당 단순 제품에 대한 세부 사항이 포함되어 있습니다.

**요청:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
                    }
                }
            }
        }
        ... on ComplexProductView {
            options {
                id
                title
                required
                values {
                    id
                    title

                }
            }
            priceRange {
                maximum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
                        }
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## 입력 필드

SKU 값과 하나 이상의 옵션 ID를 입력으로 지정해야 합니다.

| 필드 | 데이터 유형 | 설명 |
|--- | --- | ---|
| `optionIds` | [문자열!]! | 구매자가 선택한 제품 옵션에 지정된 특정 색상 및 크기 등의 ID 목록입니다. |
| `sku` | 문자열! | 복잡한 제품의 SKU입니다. |

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
