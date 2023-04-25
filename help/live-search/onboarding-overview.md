---
title: "온보딩 개요"
description: "[!DNL Live Search] 온보딩 흐름, 시스템 요구 사항, 경계 및 제한 사항"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# 온보딩 개요

를 사용하려면 [!DNL Live Search] Adobe Commerce의 경우 온보딩 프로세스를 완료하여 확장을 설치하고 API 키를 구성하고 카탈로그를 동기화합니다.

## 온보딩 흐름

![[!DNL Live Search] 온보딩 다이어그램](assets/onboarding-flow.svg)

## 요구 사항 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 지원되는 플랫폼

* Adobe Commerce On-prem(EE) : 2.4.4+
* Adobe Commerce on Cloud (ECE) : 2.4.4+

## 경계 및 임계값

현재, [!DNL Live Search] 검색/카테고리 API에는 다음과 같은 지원되는 제한 및 정적 경계가 있습니다.

### 색인 지정

* 저장소 보기당 최대 300개의 제품 특성을 인덱싱합니다.
* Adobe Commerce 데이터베이스의 제품만 인덱싱합니다.
* 제품은 기본 공유 카탈로그에 있어야 합니다.
* CMS 페이지는 인덱싱되지 않습니다.

### 쿼리

* [!DNL Live Search] 은 카테고리 트리의 전체 분류에 액세스할 수 없으며, 따라서 몇 가지 계층화된 탐색 검색 시나리오를 만들 수 있습니다.
* [!DNL Live Search] 은(는) 다이내믹 페이팅 및 as-you-type과 같은 기능을 지원하기 위해 쿼리에 고유한 GraphQL 종단점을 사용합니다. 와 비슷하지만 [GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/)에는 몇 가지 차이점이 있으며 일부 필드는 완전히 호환되지 않을 수 있습니다.

카탈로그 권한을 사용하여 고객 그룹을 제한하려면 다음을 수행하십시오.

* 제품을 루트 카테고리에 지정해야 합니다.
* 로그인하지 않음 고객 그룹에는 &quot;허용&quot; 검색 권한이 있어야 합니다.
* 제품을 로그인되지 않은 고객 그룹으로 제한하려면 각 카테고리로 이동하여 각 고객 그룹에 대한 권한을 설정합니다.

### 규칙

* 저장소 보기당 최대 규칙 수는 50개입니다.
* 규칙당 최대 조건 수는 10개입니다.
* 규칙당 최대 이벤트 수는 25개입니다.

### 동의어

* [!DNL Live Search] 저장소 보기당 최대 200개의 동의어를 관리할 수 있습니다.

## Price indexer

라이브 검색 고객은 새로운 기능을 사용할 수 있습니다 [SaaS 가격 인덱서](../price-index/index.md)- 더 빠른 가격 변경 업데이트 및 동기화 시간을 제공합니다.

### PWA 지원

모든 PWA이 테스트되지 않았으므로 라이브 검색 지원은 베타로 간주됩니다 [!DNL Live Search]. 검색 및 제품 목록 페이지와 같은 기본 기능은 Venia에서 작동하지만 Graphql의 일부 순열 기능이 제대로 작동하지 않을 수 있습니다.

* 의 현재 베타 PWA 구현 [!DNL Live Search] 검색 결과를 반환하는 데 보다 많은 처리 시간이 필요합니다. [!DNL Live Search] 네이티브 상거래 상점.
* [!DNL Live Search] 에서 PWA은 지원되지 않습니다 [이벤트 처리](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* 직접 필터링 `description`, `name`, `short_description` 에서 사용하는 경우 GraphQL에서 지원하지 않습니다. [PWA](https://developer.adobe.com/commerce/pwa-studio/)하지만 더 일반적인 필터와 함께 반환됩니다.

### 현재 지원되지 않음

* 다음 [고급 검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 모듈은 [!DNL Live Search] 가 설치되어 있고, 상점 바닥글의 고급 검색 링크가 제거됩니다.
* 에 사용된 복수 재고 위치 [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) 또는 기타 OMS 확장
* 제품 가격은 포함되지 않습니다 [부가세](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (VAT).
* [계층 가격](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 라이브 검색 팝업 및 제품 목록 페이지 위젯에서는 지원되지 않습니다.

## 쿠키

[!DNL Live Search] 기본 기능의 일부로서 사용자 상호 작용 데이터를 수집하고 쿠키는 이 데이터를 저장하는 데 사용됩니다. 사용자 정보를 수집할 때 사용자는 쿠키 저장에 동의해야 합니다. [!DNL Live Search] 및 [!DNL Product Recommendations] 데이터 스트림을 공유하여 동일한 쿠키 메커니즘을 공유합니다. 자세한 내용은 [쿠키 제한 처리](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
