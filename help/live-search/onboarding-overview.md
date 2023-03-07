---
title: "온보딩 개요"
description: "[!DNL Live Search] 온보딩 플로우, 시스템 요구 사항, 경계 및 제한 사항"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# 온보딩 개요

을(를) 시작하려면 [!DNL Live Search] Adobe Commerce의 경우 온보딩 프로세스를 완료하여 확장을 설치하고, API 키를 구성하고, 카탈로그를 동기화합니다.

## 온보딩 플로우

![[!DNL Live Search] 온보딩 다이어그램](assets/onboarding-flow.svg)

## 요구 사항 {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.4+
* PHP 8.1, 8.2
* [!DNL Composer]

### 지원되는 플랫폼

* Adobe Commerce on prem (EE) : 2.4.4+
* ECE(Adobe Commerce on Cloud) : 2.4.4+

## 경계 및 임계값

현재, [!DNL Live Search] search/category API에는 다음과 같은 지원되는 제한 사항과 정적 경계가 있습니다.

### 색인화

* 스토어 보기당 최대 300개의 제품 속성을 인덱싱합니다.
* Adobe Commerce 데이터베이스의 제품만 인덱싱합니다.
* CMS 페이지가 인덱싱되지 않았습니다.

### 쿼리

* [!DNL Live Search] 은 카테고리 트리의 전체 분류법에 액세스할 수 없으므로 해당 범위 밖에 일부 계층화된 탐색 검색 시나리오가 만들어집니다.
* [!DNL Live Search] 에서는 쿼리에 고유한 GraphQL 끝점을 사용하여 지능형 페이스팅 및 유형별 검색과 같은 기능을 지원합니다. 와 유사하긴 하지만 [GRAPHQL API MAGENTO](https://developer.adobe.com/commerce/webapi/graphql/), 몇 가지 차이점이 있으며 일부 필드는 현재 완전히 호환되지 않을 수 있습니다.

### 규칙

* 스토어 조회당 최대 규칙 수는 50개입니다.
* 규칙당 최대 조건 수는 10개입니다.
* 규칙당 최대 이벤트 수는 25개입니다.

### 동의어

* [!DNL Live Search] 스토어 조회당 최대 200개의 동의어를 관리할 수 있습니다.

### PWA 베타 릴리스

* 라이브 검색의 현재 베타 PWA 구현에는 기본 Commerce 상점 있는 라이브 검색보다 검색 결과를 반환하는 데 더 많은 처리 시간이 필요합니다.
* 다음에 대한 PWA 베타 릴리스 [!DNL Live Search] 은(는) 을 지원하지 않습니다. [이벤트 처리](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 다음 제품 속성은 의 베타 릴리스와 관련하여 사용될 때 GraphQL에서 지원되지 않습니다. [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### 현재 지원되지 않음

* 다음 [고급 검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 다음 경우에 모듈이 비활성화됩니다. [!DNL Live Search] 가 설치되고 상점 첫 번째 바닥글의 고급 검색 링크가 제거됩니다.
* [사용자 정의 가격 그룹](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* 에서 사용하는 여러 재고 위치 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 또는 기타 OMS 확장
* 제품 가격에는 다음이 포함되지 않습니다. [부가 가치세](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT)
