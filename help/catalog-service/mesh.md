---
title: '[!DNL Catalog Service and API Mesh]'
description: '''[!DNL API Mesh] for Adobe Commerce은 공통 GraphQL 엔드포인트를 통해 여러 데이터 소스를 통합하는 방법을 제공합니다."'
exl-id: cdda4a83-3c5f-4a69-8279-b90464e16c0e
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

다음 [Adobe Developer 앱 빌더용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 을 사용하면 개발자가 Adobe I/O Runtime을 사용하여 개인 또는 서드파티 API 및 기타 인터페이스를 Adobe 제품과 통합할 수 있습니다.

![카탈로그 아키텍처 다이어그램](assets/catalog-service-architecture-mesh.png)

API Mesh를 카탈로그 서비스와 함께 사용하는 첫 번째 단계는 API Mesh를 인스턴스에 연결하는 것입니다. 자세한 내용은 의 지침을 참조하십시오 [메쉬 만들기](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

설치를 완료하려면 [Adobe Developer CLI 패키지](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

Adobe I/O Runtime에 메쉬가 구성되면 다음 명령을 실행하여 `CommerceCatalogServiceGraph` 메쉬에 소스를 추가합니다.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

위치 `variables.json` 는 Adobe I/O Runtime에 대해 일반적으로 사용되는 값을 저장하는 별도의 파일입니다.
예를 들어 API 키는 다음 파일 내에 저장할 수 있습니다.

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

이 명령을 실행한 후에는 API Mesh를 통해 카탈로그 서비스를 실행해야 합니다. 다음을 실행할 수 있습니다. `aio api-mesh:get` 업데이트된 메쉬의 구성을 보는 명령입니다.

## API Mesh 예

API Mesh를 사용하면 외부 데이터 소스를 사용하여 Adobe Commerce 인스턴스를 향상시킬 수 있습니다. 또한 기존 상거래 데이터를 구성하여 새로운 기능을 활성화하는 데 사용할 수 있습니다.

### 계층 가격 활성화

이 예에서는 API Mesh를 사용하여 Adobe Commerce에서 계층 가격을 활성화합니다.
바꾸기 `name `, `endpoint`, 및 `x-api-key` 값.

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

구성이 완료되면 Mesh에 계층화된 가격을 쿼리합니다.

```graphql
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```

### 엔티티 ID 가져오기

이 메쉬는 다음을 추가합니다. `entityId` 를 추가합니다. 바꾸기 `name `, `endpoint`, 및 `x-api-key` 값.

```json
{
    "meshConfig": {
      "sources": [
        {
          "name": "<Commerce Instance Name>",
          "handler": {
            "graphql": {
              "endpoint": "<Adobe Commerce GraphQL endpoint>"
            }
          },
          "transforms": [
              {
                  "prefix": {
                      "includeRootOperations": true,
                        "value": "Core_"
                  }
              }
          ]
        },
        {
          "name": "CommerceCatalogServiceGraph",
          "handler": {
            "graphql": {
              "endpoint": "https://catalog-service.adobe.io/graphql",
              "operationHeaders": {
                "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
                "Magento-Website-Code": "{context.headers['magento-website-code']}",
                "Magento-Store-Code": "{context.headers['magento-store-code']}",
                "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>",
                "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
              },
              "schemaHeaders": {
                "x-api-key": "<YOUR_CATALOG_SERVICE_API_KEY>"
              }
            }
          }
        }
      ],
      "additionalTypeDefs": "extend interface ProductView {\n  entityId: String\n}\n extend type SimpleProductView {\n  entityId: String\n}\n extend type ComplexProductView {\n  entityId: String\n}\n",
      "additionalResolvers": [
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n    items {\n  sku\n uid\n  }\n    }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          },
          {
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "entityId",
            "sourceName": "MagentoCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{ sku\n }",
            "sourceSelectionSet": "{\n items {\n  sku\n uid\n }}",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].uid",
            "resultType": "String"
          }
      ]
    }
  }
```

`entityId` 이제 쿼리할 수 있음:

```graphql
query {
  products(skus: ["MH07"]){
    sku
    name
    id
    entityId
  }
}
```
