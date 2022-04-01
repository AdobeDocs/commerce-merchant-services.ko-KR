---
title: 빠른 둘러보기
description: 상점 앞에서 Live Search를 잠깐 둘러보십시오.
exl-id: bcb19506-6617-4c8a-83df-9d961f81e9e8
source-git-commit: 61d50ec07e7c8ced1696f4169a90302cca4d4f96
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# 빠른 둘러보기

속도, 관련성, 사용 편의성에 중점을 두고 [!DNL Live Search] 는 쇼핑객과 상인을 비슷하게 하기 위한 게임 교환기입니다. 다음에 따라 빨리 [!DNL Live Search] 상점 앞에서

## 입력하는 대로 검색

[!DNL Live Search] 에서 제안된 제품 및 상위 검색 결과의 축소판 이미지에 응답합니다. [poover](storefront-popover.md) 쇼핑객이 [검색](https://docs.magento.com/user-guide/catalog/search-quick.html) 상자. 다음 [제품 세부 사항](https://docs.magento.com/user-guide/quick-tour/product-page.html) 쇼핑객이 추천 또는 추천 제품을 클릭하면 페이지가 표시됩니다. A _모두 보기_ 팝업 바닥글에 있는 링크에 검색 결과 페이지가 표시됩니다.

[!DNL Live Search] 두 자 이상의 쿼리에 대한 &quot;입력할 때 검색&quot; 결과를 반환합니다. 부분 일치의 경우 단어당 최대 문자 수는 20자입니다. 쿼리의 문자 수는 구성할 수 없습니다. 팝오버에는 다음 필드가 포함됩니다. `name`, `sku`, 및 `category_ids`.

![입력 시 storfront - 검색 예](assets/storefront-search-as-you-type.png)

## 모든 검색 결과 보기

&quot;입력한 대로 검색&quot; 쿼리에서 반환된 모든 제품을 나열하려면 _모두 보기_ 맨 아래에 있습니다.

![예제 storfront - 가격 패싯](assets/storefront-view-all-search-results.png)

## 패싯으로 필터링된 검색

필터링된 검색은 여러 속성 값을 사용합니다. 또는 [패싯](facets.md)를 검색 기준으로 사용할 수도 있습니다. 필터 선택은 머천트에서 정의하며 반환되는 제품에 따라 변경되며 가장 일반적으로 사용되는 패싯이 목록 맨 위에 고정됩니다.

## 동의어

[동의어](synonyms.md) 카탈로그의 단어 구매자와 다른 단어를 사용하여 도달 범위를 확장하고 쿼리의 포커스를 선명하게 합니다. 구매자의 참여와 구매 경로를 유지하기 위해 동의어 사전을 세밀하게 조정할 수 있습니다.

## 머천다이징 규칙

머천다이징 [규칙](rules.md) 검색할 논리 및 이벤트를 추가하는 if-then 문으로 쇼핑 경험을 형성합니다. 판촉, 시즌 또는 다른 기간 동안 제품을 쉽게 증폭 또는 파묻을 수 있습니다.
