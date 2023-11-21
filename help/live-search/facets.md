---
title: "패싯"
description: "[!DNL Live Search] 패싯은 속성 값의 여러 차원을 검색 기준으로 사용합니다."
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: a8643ca9567feb7dde67358eeae321825b0253f2
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# 패싯

페이스팅은 속성 값의 여러 차원을 검색 기준으로 사용하는 고성능 필터링 방법입니다. 패싯형 검색은 유사하지만 표준보다 상당히 &quot;똑똑하다&quot; [계층화된 탐색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). 사용 가능한 필터 목록은 다음을 통해 결정됩니다. [필터링 가능한 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) 검색 결과에서 반환된 제품

[!DNL Live Search] 를 사용합니다. `productSearch` 다음에 고유한 얼굴 및 기타 데이터를 반환하는 쿼리 [!DNL Live Search]. 을(를) 참조하십시오 [`productSearch` 쿼리](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) 코드 예제에 대해서는 개발자 설명서에서 참조하십시오.

![필터링된 검색 결과](assets/storefront-search-results-run.png)

정의된 모든 패싯은 URL 매개 변수로 사용할 수 있으며 결과는 매개 변수 값을 기반으로 필터링됩니다. `http://yourstore.com?brand=acme&color=red`.

## 요구 사항 충족

얼굴에 대한 카테고리 및 제품 속성 요구 사항은 계층 탐색에 사용된 필터링 가능한 속성과 유사합니다. 각 특성의 storefront 속성을 다음으로 설정해야 합니다. `filterable (with results)`.

[!DNL Live Search] 는 최대 다음 지원:

* 패싯으로 구성된 100개 속성
* 정렬 가능한 속성 50개
* 필터링 가능한 특성 200개
* 검색 가능한 속성 200개

>[!NOTE]
>
> 필터링 가능한 속성이 200개 이상 정의된 경우 실제로 인덱싱할 200개는 결정적이지 않습니다.

경합할 속성이 많은 경우 속성을 하나의 &quot;meta-attribute&quot;로 결합하는 것이 좋습니다. 예를 들어, 신발은 일반적으로 숫자 크기를 가지지만 셔츠는 일반적으로 &quot;S/M/L/XL&quot; 크기를 갖습니다. 이 두 가지 유형의 크기를 하나의 검색 가능한 속성으로 결합할 수 있습니다.

| 설정 | 설명 |
|--- |--- |
| [범주 표시 설정](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | 앵커 - `Yes` |
| [속성 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [카탈로그 입력 유형](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (위젯만), `Text swatch` (위젯만) |
| 속성 storefront 속성 | 검색 결과 계층 탐색 -에서 사용 `Yes` |

## Facet 집계

Facet 집계는 다음과 같이 수행됩니다. 상점 첫 번째 패싯이 세 개 있고(카테고리, 색상 및 가격) 쇼핑객 필터가 세 개 모두 있는 경우(색상 = 파란색이며 가격은 $10.00-50.00, 카테고리 = `promotions`).

* `categories` 집계 - 집계 `categories`를 클릭한 다음 를 적용합니다. `color` 및 `price` 필터(단, `categories` 필터.
* `color` 집계 - 집계 `color`를 클릭한 다음 를 적용합니다.`price` 및 `categories` 필터(단, `color` 필터.
* `price` 집계 - 집계 `price`를 클릭한 다음 를 적용합니다. `color` 및 `categories` 필터(단, `price` 필터.

## 기본 속성 값

다음 제품 속성에는 [storefront 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 다음에 의해 사용됨: [!DNL Live Search] 기본적으로 활성화되어 있습니다.

| 속성 | Storefront 속성 | 속성 |
|---|---|---|
| 정렬 가능 | 제품 목록에서 정렬에 사용됨 | `price` |
| 검색 가능 | 검색에 사용 | `price` <br />`sku`<br />`name` |
| 필터링 가능한 검색 | 레이어 탐색에서 사용 - 필터링 가능(결과 포함) | `price`<br />`visibility`<br />`category_name` |

## 기본 비시스템 속성 속성

다음 표는 Luma 샘플 데이터와 관련된 속성을 포함하여 비시스템 속성의 기본 검색 및 필터링 가능한 속성을 보여 줍니다. 설정 *검색에 사용* 속성 속성 대상 `Yes` 속성을 두 가지 모두에서 검색할 수 있게 만듭니다. [!DNL Live Search] 및 기본 Adobe Commerce

| 속성 코드 | 검색 가능 | 레이어 탐색에서 사용 |
|--- |--- |--- |
| 활동 | 예 | 필터링 가능(결과 포함) |
| attributes_brand | 예 | 아니요 |
| 브랜드 | 예 | 아니요 |
| 기후 | 예 | 필터링 가능(결과 포함) |
| 고리 | 예 | 필터링 가능(결과 포함) |
| 색상 | 예 | 필터링 가능(결과 포함) |
| 비용 | 예 | 아니요 |
| eco_collection | 예 | 필터링 가능(결과 포함) |
| 성별 | 예 | 필터링 가능(결과 포함) |
| 제조업체 | 예 | 필터링 가능(결과 포함) |
| 재질 | 예 | 필터링 가능(결과 포함) |
| 목적 | 예 | 필터링 가능(결과 포함) |
| strap_bags | 예 | 필터링 가능(결과 포함) |
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
| 두께 | 예 | 아니요 |
