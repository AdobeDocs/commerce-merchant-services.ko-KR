---
title: '[!DNL Catalog Service and API Mesh]'
description: '`[!DNL API Mesh] Adobe Commerce용 는 일반적인 GraphQL 종단점을 통해 여러 데이터 소스를 통합하는 방법을 제공합니다.'''
source-git-commit: 7b95be48c21e17cb6ba88d326fd061f7de2f8fb5
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

다음 [Adobe Developer App Builder용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 개발자는 Adobe IO를 사용하여 개인 또는 타사 API 및 기타 인터페이스를 Adobe 제품과 통합할 수 있습니다.

API Mesh를 카탈로그 서비스와 함께 사용하는 첫 번째 단계는 API Mesh를 인스턴스에 연결하는 것입니다. 자세한 지침은 [메쉬 만들기](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

설정을 완료하려면 [Adobe IO CLI 패키지](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) 설치되었습니다.

Adobe IO에 Mesh가 구성되면 다음 명령을 실행하여 `CommerceCatalogServiceGraph` 메쉬에 대한 소스.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

여기서 `variables.json` 는 Adobe IO에 일반적으로 사용되는 값을 저장하는 별도의 파일입니다.
예를 들어 API 키를 파일 내에 저장할 수 있습니다.

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

이 명령을 실행한 후 카탈로그 서비스가 API Mesh를 통해 실행되어야 합니다. 를 실행할 수 있습니다 `aio api-mesh:get` 업데이트된 메쉬의 구성을 확인하는 명령

## API Mesh 사용

API Mesh를 사용하면 사용자가 외부 데이터 소스를 소비하여 Adobe Commerce 인스턴스를 향상시킬 수 있습니다. 새 기능을 활성화하기 위해 기존 상거래 데이터를 구성하는 데에도 사용할 수 있습니다.

이 예에서 API Mesh는 Adobe Commerce에서 계층 가격을 활성화하는 데 사용됩니다.
바꾸기 `name `, `endpoint` 및 `x-api-key` 값.

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
              "x-api-key": "storefront-catalog-apollo",
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

구성이 완료되면 Mesh에서 계층화된 가격을 확인하십시오.

```json
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
