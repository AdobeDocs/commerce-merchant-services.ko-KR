---
title: "Facet 기술 노트"
description: "사용에 대한 기술 참고 사항 [!DNL Live Search] 패싯."
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Facet 기술 노트

팩시팅은 검색 가능한 정적 및 동적 속성 값의 여러 차원을 검색 기준으로 사용하는 고성능 필터링 방법입니다.

[!DNL Live Search] 를 사용합니다. `productSearch` 다음 항목에 고유한 얼굴 및 기타 데이터를 반환하는 쿼리 [!DNL Live Search]. 을(를) 참조하십시오 [`productSearch` 쿼리](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 코드 예입니다.

## Facet 집계

Facet 집계는 다음과 같이 수행됩니다. 상점 앞에 세 개의 Facet (범주, 색상 및 가격)이 있고 쇼핑객 필터가 세 가지 모두에 있는 경우 (색상 = 파랑, 가격은 $10.00-50.00, 범주 = `promotions`).

* `categories` 집계 - 집계 `categories`를 클릭한 다음 를 적용합니다. `color` 및 `price` 필터(단, `categories` 필터.
* `color` 집계 - 집계 `color`를 클릭한 다음 를 적용합니다.`price` 및 `categories` 필터(단, `color` 필터.
* `price` 집계 - 집계 `price`를 클릭한 다음 를 적용합니다. `color` 및 `categories` 필터(단, `price` 필터.
