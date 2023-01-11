---
title: "온보딩 개요"
description: "[!DNL Live Search] 온보딩 흐름, 시스템 요구 사항, 경계 및 제한 사항"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# 온보딩 개요

를 사용하려면 [!DNL Live Search] Adobe Commerce의 경우 온보딩 프로세스를 완료하여 확장을 설치하고 API 키를 구성하고 카탈로그를 동기화합니다.

## 온보딩 흐름

![[!DNL Live Search] 온보딩 다이어그램](assets/onboarding-flow.svg)

## 요구 사항 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### 지원되는 플랫폼

* Adobe Commerce on prem (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## 경계 및 임계값

현재, [!DNL Live Search] 검색/카테고리 API에는 다음과 같은 지원되는 제한 및 정적 경계가 있습니다.

### 색인 지정

* 저장소 보기당 최대 300개의 제품 특성을 인덱싱합니다.
* Adobe Commerce 데이터베이스의 제품만 인덱싱합니다.
* CMS 페이지는 인덱싱되지 않습니다.

### 쿼리

* [!DNL Live Search] 은 카테고리 트리의 전체 분류에 액세스할 수 없으며, 따라서 몇 가지 계층화된 탐색 검색 시나리오를 만들 수 있습니다.
* [!DNL Live Search] 은 지능형 세그먼트와 사용자 지정 검색 등의 기능을 지원하기 위해 쿼리에 고유한 GraphQL 종단점을 사용합니다. 와 비슷하지만 [GraphQL API Magento](https://developer.adobe.com/commerce/webapi/graphql/)에는 몇 가지 차이점이 있으며 일부 필드는 현재 완전히 호환되지 않을 수 있습니다.

### 규칙

* 저장소 보기당 최대 규칙 수는 50개입니다.
* 규칙당 최대 조건 수는 10개입니다.
* 규칙당 최대 이벤트 수는 25개입니다.

### 동의어

* [!DNL Live Search] 저장소 보기당 최대 200개의 동의어를 관리할 수 있습니다.

### PWA 베타 릴리스

* 라이브 검색의 현재 베타 PWA 구현에는 기본 상거래 스토어를 사용하는 라이브 검색보다 검색 결과를 반환하기 위한 처리 시간이 더 필요합니다.
* 용 PWA 베타 릴리스 [!DNL Live Search] 을 지원하지 않음 [이벤트 처리](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 다음 제품 속성은 베타 릴리스와 관련하여 GraphQL에서 지원되지 않습니다 [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 현재 지원되지 않음

* 다음 [고급 검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 모듈은 [!DNL Live Search] 가 설치되어 있고, 상점 바닥글의 고급 검색 링크가 제거됩니다.
* [사용자 지정 가격 그룹](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* 에 사용된 복수 재고 위치 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 또는 기타 OMS 확장
* 제품 가격은 포함되지 않습니다 [부가세](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT).
