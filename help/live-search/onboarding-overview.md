---
title: "온보딩 개요"
description: "[!DNL Live Search] 온보딩 플로우, 시스템 요구 사항, 경계 및 제한 사항"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: 48f16a0c5ce6c2a3226acf4a61525cfbf4a0f35f
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# 온보딩 개요

을(를) 시작하려면 [!DNL Live Search] Adobe Commerce의 경우 온보딩 프로세스를 완료하여 확장을 설치하고, API 키를 구성하고, 카탈로그를 동기화합니다.

## 요구 사항 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 지원되는 플랫폼

* Adobe Commerce 온-프레미스 (EE) : 2.4.4+
* ECE(Adobe Commerce on Cloud) : 2.4.4+

## 엔드포인트

[!DNL Live Search] 은 의 끝점을 통해 통신합니다. `https://catalog-service.adobe.io/graphql`.

## 경계 및 임계값

현재, [!DNL Live Search] search/category API에는 다음과 같은 지원되는 제한 사항과 정적 경계가 있습니다.

### 색인화

* 스토어 보기당 최대 300개의 제품 속성을 인덱싱합니다.
* Adobe Commerce 데이터베이스의 제품만 인덱싱합니다.
* CMS 페이지가 인덱싱되지 않았습니다.

### 쿼리

* [!DNL Live Search] 은 카테고리 트리의 전체 분류법에 액세스할 수 없으므로 해당 범위 밖에 일부 계층화된 탐색 검색 시나리오가 만들어집니다.
* [!DNL Live Search] 에서는 쿼리에 고유한 GraphQL 끝점을 사용하여 동적 팩팅 및 유형별 검색과 같은 기능을 지원합니다. 와 유사하긴 하지만 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)에 몇 가지 차이점이 있으며 일부 필드가 완전히 호환되지 않을 수 있습니다.

카탈로그 권한을 사용하여 고객 그룹을 제한하려면 다음을 수행하십시오.

* 제품을 루트 범주에 할당해야 합니다.
* &quot;로그인되지 않은&quot; 고객 그룹에는 &quot;허용&quot; 검색 권한이 부여되어야 합니다.
* 제품을 로그인되지 않은 고객 그룹으로 제한하려면 각 범주로 이동하여 각 고객 그룹에 대한 권한을 설정합니다.

### 규칙

* 스토어 조회당 최대 규칙 수는 50개입니다.
* 규칙당 최대 조건 수는 10개입니다.
* 규칙당 최대 이벤트 수는 25개입니다.

### 동의어

* [!DNL Live Search] 스토어 조회당 최대 200개의 동의어를 관리할 수 있습니다.

## 언어 지원

[!DNL Live Search] 위젯은 다음 언어를 지원합니다.

* en_US(기본값)
* de_DE
* es_MX
* fr_FR
* it_IT
* ja_JA
* nl_NL
* no_NO
* pt_PT

위젯이 Commerce 관리자 언어 설정(_스토어_ > 설정 > _구성_ > _일반_ > 국가 옵션) 지원되는 언어와 일치하면 기본적으로 해당 언어로 설정됩니다. 그렇지 않은 경우 위젯은 기본적으로 영어로 설정됩니다.

## 카테고리 머천다이징

카테고리 머천다이징을 사용하여 다음을 구성할 수 있습니다. [!DNL Live Search] 제품 범주 수준에서 작업합니다.

이 비디오는 카테고리 머천다이징에 대해 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Inventory management

[!DNL Live Search] 지원 [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) commerce(이전에는 MSI라고 함)의 기능. 전체 지원을 활성화하려면 다음을 수행해야 합니다 [업데이트](install.md#update) 종속성 모듈 `commerce-data-export` 버전 102.2.0+에

[!DNL Live Search] Inventory management 내에서 제품을 사용할 수 있는지 여부를 나타내는 부울을 반환하지만, 재고가 있는 소스에 대한 정보는 포함하지 않습니다.

## 가격 인덱서

라이브 검색 고객은 새 [SaaS 가격 인덱서](../price-index/index.md)를 통해 가격 변경 업데이트 및 동기화 시간이 빨라집니다.

## PWA 지원

[!DNL Live Search] 은 PWA Studio에서 작동하지만 다른 Commerce 구현에 비해 약간의 차이가 있을 수 있습니다. 검색 및 제품 목록 페이지와 같은 기본 기능은 Venia에서 작동하지만 Graphql의 일부 순열이 제대로 작동하지 않을 수 있습니다. 성능 차이도 있을 수 있습니다.

* 의 현재 PWA 구현 [!DNL Live Search] 검색 결과를 반환하는 데 보다 많은 처리 시간이 필요합니다. [!DNL Live Search] 기본 Commerce 상점 포함.
* [!DNL Live Search] PWA에서 을(를) 지원하지 않습니다. [이벤트 처리](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). 따라서 지능형 머천다이징은 작동하지 않습니다.
* 바로 필터링 `description`, `name`, `short_description` 과 함께 사용할 경우 GraphQL에서 지원되지 않음 [PWA](https://developer.adobe.com/commerce/pwa-studio/), 하지만 더 일반적인 필터와 함께 반환됩니다.

사용 [!DNL Live Search] PWA Studio을 사용하는 통합자는 다음 작업도 수행해야 합니다.

1. 설치 [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. 설정 `environmentId` 다음에서 `storeDetails` 개체.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

## 현재 지원되지 않음

* 다음 [고급 검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 다음 경우에 모듈이 비활성화됩니다. [!DNL Live Search] 가 설치되고 상점 첫 번째 바닥글의 고급 검색 링크가 제거됩니다.
* [계층 가격](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 는 라이브 검색 팝오버 및 제품 목록 페이지 위젯에서 지원되지 않습니다.

## 쿠키

[!DNL Live Search] 는 기본 기능의 일부로 사용자 상호 작용 데이터를 수집하며 쿠키는 이 데이터를 저장하는 데 사용됩니다. 사용자 정보를 수집할 때 사용자는 쿠키를 저장하는 데 동의해야 합니다. [!DNL Live Search] 및 [!DNL Product Recommendations] 데이터 스트림을 공유하여 동일한 쿠키 메커니즘을 공유합니다. 자세한 내용 보기 [쿠키 제한 처리](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
