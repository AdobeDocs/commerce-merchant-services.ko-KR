---
title: 패싯
description: 라이브 검색 패싯에서는 여러 속성 값의 차원을 검색 기준으로 사용합니다.
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 554b07c233da2af2ca2d9aacf56bdfe09dc67cd3
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# 패싯

검색 기준으로 여러 차원 속성 값을 사용하는 고성능 필터링 방법입니다. 면처리 검색은 비슷하지만 표준보다 상당히 &quot;더 스마트함&quot;입니다 [계층 탐색](https://docs.magento.com/user-guide/catalog/navigation-layered.html). 사용 가능한 필터 목록은 [필터링 가능한 속성](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) 검색 결과에 반환되는 제품 수.

![필터링된 검색 결과](assets/storefront-search-results-run.png)

## 계면 요구 사항

페이싱을 위한 카테고리 및 제품 속성 요구 사항은 계층화된 탐색에 사용되는 필터링 가능한 속성과 유사합니다. 각 특성의 storefront 속성은 `filterable (with results)`.

* 최대 100개의 속성을 [!DNL Live Search].
* [!DNL Live Search] 는 최대 300개의 속성을 필터링 가능/검색/정렬 가능하고 검색 결과에 표시됩니다.

| 설정 | 설명 |
|--- |--- |
| [카테고리 표시 설정](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | 앵커 - `Yes` |
| [속성 속성](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [카탈로그 입력 유형](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| 속성 저장소 등록 정보 | 레이어 탐색에서 사용 - `Filterable (with results)` |

## 기본 속성 값

다음 제품 속성은 다음과 같습니다 [storefront 속성](https://docs.magento.com/user-guide/stores/attributes-product.html) 다음에서 사용 [!DNL Live Search] 기본적으로 활성화되어 있습니다.

| 속성 | Storefront 속성 | 속성 |
|---|---|---|
| 정렬 가능 | 제품 목록의 정렬에 사용됩니다. | `price` |
| 검색 가능 | 검색에서 사용 | `price` <br />`sku`<br />`name` |
| FilterableInSearch | 레이어 탐색 - 필터링 가능(결과 포함)에서 사용 | `price`<br />`visibility`<br />`category_name` |

## 기본 비시스템 속성 속성

다음 표는 Luma 샘플 데이터에 고유한 속성을 포함하여 비시스템 속성의 기본 검색 및 필터링 가능한 속성을 보여줍니다. 설정 *검색에서 사용* 속성 속성 `Yes` 은 두 가지 모두에서 속성을 검색할 수 있도록 합니다 [!DNL Live Search] 및 네이티브 Adobe Commerce.

| 속성 코드 | 검색 가능 | 레이어 탐색에서 사용 |
|--- |--- |--- |
| 활동 | 예 | 필터링 가능(결과 포함) |
| attributes_brand | 예 | 아니요 |
| 브랜드 | 예 | 아니요 |
| 기후 | 예 | 필터링 가능(결과 포함) |
| 칼라 | 예 | 필터링 가능(결과 포함) |
| 색상 | 예 | 필터링 가능(결과 포함) |
| 비용 | 예 | 아니요 |
| eco_collection | 예 | 필터링 가능(결과 포함) |
| 성별 | 예 | 필터링 가능(결과 포함) |
| 제조업체 | 예 | 필터링 가능(결과 포함) |
| 재료 | 예 | 필터링 가능(결과 포함) |
| 목적 | 예 | 필터링 가능(결과 포함) |
| string_bag | 예 | 필터링 가능(결과 포함) |
| style_general | 예 | 필터링 가능(결과 포함) |

## 기본 시스템 속성 속성

다음 표에서는 시스템 속성의 기본 검색 및 필터링 가능한 속성을 보여 줍니다.

| 속성 코드 | 검색 가능 | 레이어 탐색에서 사용 |
|--- |--- |--- |
| allow_open_amount | 예 | 필터링 가능(결과 포함) |
| 설명 | 예 | 아니요 |
| 이름 | 예 | 아니요 |
| 가격 | 예 | 필터링 가능(결과 포함) |
| short_description | 예 | 아니요 |
| sku | 예 | 아니요 |
| 상태 | 예 | 아니요 |
| tax_class_id | 예 | 아니요 |
| url_key | 예 | 아니요 |
| 가중치 | 예 | 아니요 |
