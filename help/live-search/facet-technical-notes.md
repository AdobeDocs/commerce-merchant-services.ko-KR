---
title: 패싯 기술 정보
description: 라이브 검색 패싯 사용에 대한 기술 참고 사항.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: e53fb13b98684757b8081b2e19dd33d925e8ce5d
workflow-type: tm+mt
source-wordcount: '114'
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
