---
title: 패싯 기술 정보
description: 라이브 검색 패싯 사용에 대한 기술 참고 사항.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# 패싯 기술 정보

검색 가능한 정적 및 동적 속성 값의 여러 차원을 검색 기준으로 사용하는 고성능 필터링 방법입니다.

[!DNL Live Search] 사용 `productSearch` 계면 및 기타 데이터 [!DNL Live Search]. 을(를) 참조하십시오. [`productSearch` 쿼리](https://devdocs.magento.com/live-search/product-search.html) 코드 예제 의 경우.

## 패싯 집계

패싯 집계는 스토어에 세 개의 패싯(카테고리, 색상 및 가격)과 세 개의 패싯(색상 = 파란색, 가격은 $10.00-50.00, 카테고리 = 인 경우 다음과 같이 수행됩니다. `promotions`).

* `categories` 합계 - 집계 `categories`, 적용 `color` 및 `price` 필터 `categories` 필터.
* `color` 합계 - 집계 `color`, 적용 `price` 및 `categories` 필터 `color` 필터.
* `price` 합계 - 집계 `price`, 적용 `color` 및 `categories` 필터 `price` 필터.

## 기본 속성 값

다음 제품 속성에는 몇 가지 기능이 있습니다 [storefront 속성](https://docs.magento.com/user-guide/stores/attributes-product.html) 기본적으로 활성화되어 있습니다.

| 속성 | Storefront 속성 | 속성 |
|---|---|---|
| 정렬 가능 | 제품 목록의 정렬에 사용됩니다. | `price` |
| 검색 가능 | 검색에서 사용 | `price` <br />`sku`<br />`name` |
| FilterableInSearch | 레이어 탐색 - 필터링 가능(결과 포함)에서 사용 | `price`<br />`visibility`<br />`category_name` |
