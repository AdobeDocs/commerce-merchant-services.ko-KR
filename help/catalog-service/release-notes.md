---
title: '"[!DNL Catalog Service] 릴리스 정보"'
description: '"에 대한 최신 릴리스 정보 [!DNL Catalog Service] Adobe Commerce에 대해 설명합니다."'
source-git-commit: 3959cc5d07f9a0da0ba772a4f3bc56adeb3c6bf3
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 2%

---


# [!DNL Catalog Service] 릴리스 정보

{{catalog-service-beta}}

이러한 릴리스 노트에서는 최신 버전의 [!DNL Catalog Service] 다음을 포함합니다.

* ![새로 만들기](../assets/new.svg) - 새로운 기능
* ![수정](../assets/fix.svg) - 수정 사항 및 향상된 기능
* ![버그](../assets/bug.svg) - 알려진 문제

## 베타 릴리스

* ![새로 만들기](../assets/new.svg) - `products` 및 `refineProduct` 쿼리는 다음 데이터를 반환합니다.
   * 사전 정의된(시스템) 제품 속성입니다.
   * 동적 제품 속성을 역할(제품 표시 페이지/제품 목록 페이지)로 필터링합니다.
   * 제품 옵션.
   * 제품 이미지를 만든 후 역할별로 필터링합니다(PDP/PLP).
   * 구성 가능한 제품에 대한 특정 가격 및 가격 범위입니다.
   * 고객 그룹 가격 및 가격 범위입니다. 고객 그룹 없이 구매자에게 기본 폴백 가격을 반환합니다.
   * B2B 고객별 가격을 사용하는 제품 유형.

## 알려진 제한 사항

* 계층 가격이 지원되지 않습니다.
* 이미지 배열에서는 첫 번째 이미지만 역할을 포함합니다.
* 변형에 대한 이미지를 검색할 수 없습니다.
* 카탈로그에서 제품이나 변형을 삭제하면 업데이트가 수신되지 않습니다.
