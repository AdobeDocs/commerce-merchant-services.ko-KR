---
title: "빠른 둘러보기"
description: '"간단히 살펴보기 [!DNL Live Search] 가게 앞에서요.'
exl-id: bcb19506-6617-4c8a-83df-9d961f81e9e8
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# 빠른 둘러보기

속도, 관련성 및 사용 편이성에 중점을 두고 [!DNL Live Search] 은 쇼핑객과 상인들을 위한 게임 체인저입니다. 다음 단계를 따라 간단히 살펴보기 [!DNL Live Search] 가게 앞에서요

## 입력할 때 검색

[!DNL Live Search] 추천 제품 및 상위 검색 결과의 썸네일 이미지로 응답함 [팝오버](storefront-popover.md) 구매자가 다음에 쿼리를 입력할 때 [검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 상자. 다음 [제품 세부 사항](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) 쇼핑객이 추천 또는 추천 제품을 클릭하면 페이지가 표시됩니다. A _모두 보기_ 팝오버의 바닥글에 있는 링크에 검색 결과 페이지가 표시됩니다.

[!DNL Live Search] 둘 이상의 문자로 이루어진 쿼리에 대해 &quot;검색할 때&quot; 결과를 반환합니다. 부분 일치의 경우 단어 당 최대 문자 수는 20자입니다. 쿼리의 문자 수를 구성할 수 없습니다. 다음 필드가 팝오버에 포함됩니다. `name`, `sku`, 및 `category_ids`.

![예 storefront - 입력할 때 검색](assets/storefront-search-as-you-type.png)

## 모든 검색 결과 보기

&quot;입력할 때 검색&quot; 쿼리에서 반환된 모든 제품을 나열하려면 _모두 보기_ 팝오버의 바닥글에 있습니다.

![예 storefront - 가격 패싯](assets/storefront-view-all-search-results.png)

## 패싯으로 필터링된 검색

필터링된 검색은 속성 값의 여러 차원을 사용하거나 [패싯](facets.md)을 검색 기준으로 사용합니다. 필터 선택은 판매자에 의해 정의되며 반환되는 제품에 따라 변경되며, 가장 일반적으로 사용되는 패싯은 목록의 맨 위에 고정됩니다.

## 동의어

[동의어](synonyms.md) 범위를 확장하고 쇼핑객이 카탈로그에 있는 것과 다른 단어를 사용하여 쿼리의 초점을 선명하게 합니다. 동의어 사전을 미세 조정하여 쇼핑객이 구매 경로에 계속 참여하도록 할 수 있습니다.

## 머천다이징 규칙

머천다이징 [규칙](rules.md) 검색할 논리 및 이벤트를 추가하는 if-then 문을 사용하여 쇼핑 경험을 구체화합니다. 프로모션, 계절 또는 기타 기간 동안 제품을 쉽게 부스트하거나 묻을 수 있습니다.
