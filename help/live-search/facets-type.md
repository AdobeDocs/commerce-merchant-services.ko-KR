---
title: "패싯 유형"
description: "[!DNL Live Search] 패싯은 동적이며 관련성이 있을 경우 필터 목록에 나타납니다."
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# 패싯 유형

[!DNL Live Search] 에서는 다양한 패싯 유형을 사용하며 *필터* 관련성이 있는 경우에만 나열합니다. 사용 가능한 패싯 목록은 반환된 제품에 따라 변경됩니다. 다음은 프레젠테이션과 동작에 영향을 주는 특성입니다.

* 고정 패싯 - 가장 일반적으로 사용되는 패싯을 목록의 맨 위에 고정할 수 있습니다. 나머지 패싯은에 나열됩니다. *정렬 유형* 고정된 패싯 뒤에 정렬합니다.
* 동적 패싯 - 제품 속성 [Adobe Sensei](https://www.adobe.com/sensei.html) 는 제품 세트 및 쿼리와 가장 관련이 있는 항목을 찾습니다. 이 계산은 전체 카탈로그의 속성 메타데이터를 고려하고 쿼리 시간에 쿼리에 가장 적합한 패싯을 결정합니다.
* 인기 패싯 - 검색 결과에 가장 자주 표시되는 제품 속성.
* 가격 패싯 - 가격 범위별로 제품을 반환합니다. 선택 횟수와 가격 범위 간격을 지정할 수 있습니다. [*설정*](settings.md) 탭.

쿼리 시간에 [!DNL Live Search] 는 동적 패싯과 인기 패싯 그룹으로 검색 결과를 생성합니다.

![패싯 - 가격](assets/storefront-search-results-run-price.png)

## Storefront 및 Headless 옵션

다음에 대해 렌더링되는 Facet [!DNL Commerce] storefront는 검색 어댑터에 의해 처리되며, 검색 어댑터는 요청을 라우팅하고 storefront에서 결과를 렌더링합니다. 모두 [!DNL Commerce] storefront 패싯은 해당 속성에 할당된 입력 유형에 관계없이 단일 선택 옵션을 사용하여 알파벳순으로 정렬됩니다. 상점 첫 화면에서 사용할 수 있는 패싯은 현재 테마에 따라 렌더링되며 계층화된 탐색 표시에 대한 모든 사용자 지정 사항을 반영합니다.

대조적으로, [headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) 구현은 API에 의해 처리되며 추가 옵션을 지원합니다. Headless 패싯은 알파벳순 또는 개수별로 정렬할 수 있으며 단일 또는 다중 선택 옵션을 가질 수 있습니다.

### Facet 레이블

대상 [!DNL Commerce] storefrontes에서 facet 레이블은 [*속성 속성*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). 여러 보기가 있는 저장소의 경우 아래에 추가 레이블을 정의할 수 있습니다. *레이블 관리*. Headless 구현의 경우 레이블은 [작업 영역 구성](faceting-workspace.md).

### 정렬 유형

상점 앞에 대해 렌더링된 모든 패싯은 알파벳순으로 정렬됩니다. Headless 구현의 경우 패싯은 알파벳순 또는 개수별로 정렬할 수 있습니다.

| 정렬 유형 | 설명 |
|--- |--- |
| 알파벳 | 상점 앞에서 *필터* 목록, 패싯은 알파벳순으로 정렬됩니다. |
| 카운트 | (Headless만 해당) Headless 구현의 경우 패싯은 현재 반환된 제품 세트에서 패싯당 찾은 값의 수로 정렬할 수도 있습니다. |
