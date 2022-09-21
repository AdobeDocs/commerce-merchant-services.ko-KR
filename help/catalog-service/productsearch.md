---
title: productSearch 쿼리
description: '''Adobe Commerce 카탈로그 서비스에 대한 ''productSearch'' GraphQL 쿼리에 대한 참조 안내서입니다.'''
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 2%

---


# productSearch 쿼리

Adobe Commerce용 카탈로그 서비스 `productSearch` query에서는 LiveSearch를 사용하여 입력으로 지정된 SKU에 대한 세부 사항을 반환할 수 있습니다. 이 쿼리는 [`productSearch` 쿼리](https://devdocs.magento.com//live-search/product-search.html), LiveSearch는 `productView` 개체. 자세한 내용은 [`productSearch` 쿼리](https://devdocs.magento.com//live-search/product-search.html) 참조 정보 항목입니다.

## 구문

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
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

다음 예에서 쿼리는 이전 예와 동일한 제품에 대한 정보를 반환합니다. 하지만 카탈로그 서비스 내에 항목 정보를 반환하도록 구성되었습니다 `productView` 코어 대신 개체를 작성합니다. `product` 개체. 가격 정보는 제품 유형에 따라 달라집니다. 간결성을 위해 패싯 정보는 표시되지 않습니다.

**요청:**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
            final {
              amount {
                value
                currency
              }
            }
            regular {
              amount {
                value
                currency
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
                  currency
                }
              }
              regular {
                amount {
                  value
                  currency
                }
              }
            }
            minimum {
              final {
                amount {
                  value
                  currency
                }
              }
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
    }
  }
}
```

**응답:**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
