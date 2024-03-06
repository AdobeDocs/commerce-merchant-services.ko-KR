---
title: "기술 개요"
description: "[!DNL Live Search] 온보딩 플로우, 시스템 요구 사항, 경계 및 제한 사항"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 0%

---

# 기술 개요

이 항목에서는 설치 및 최적화를 위한 기술 요구 사항 및 팁을 검토합니다 [!DNL Live Search] Adobe Commerce용

## 요구 사항 {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### 지원되는 플랫폼

* Adobe Commerce 온-프레미스 (EE) : 2.4.4+
* ECE(Adobe Commerce on Cloud) : 2.4.4+

## 엔드포인트

[!DNL Live Search] 은 의 끝점을 통해 통신합니다. `https://catalog-service.adobe.io/graphql`.

다음으로: [!DNL Live Search] 이(가) 전체 제품 데이터베이스에 액세스할 수 없습니다. [!DNL Live Search] GraphQL 및 Commerce 코어 GraphQL에는 전체 패리티가 없습니다.

SaaS API의 직접 호출(특히 카탈로그 서비스 끝점)을 호출하는 것이 좋습니다.

* Commerce 데이터베이스/Graphql 프로세스를 건너뛰어 성능을 향상시키고 프로세서 로드를 줄입니다.
* 다음을 활용하십시오. [!DNL Catalog Service] 호출할 페더레이션 [!DNL Live Search], [!DNL Catalog Service], 및 [!DNL Product Recommendations] 단일 엔드포인트에서

일부 사용 사례의 경우 [!DNL Catalog Service] 제품 세부 사항 및 유사 사례에 대한 정보. 다음을 참조하십시오 [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) 추가 정보.

사용자 지정 Headless 구현이 있는 경우 [!DNL Live Search] 참조 구현:

* [PLP 위젯](https://github.com/adobe/storefront-product-listing-page)
* [라이브 검색 필드](https://github.com/adobe/storefront-search-as-you-type)

Luma의 검색 어댑터 또는 위젯 또는 AEM CIF 위젯과 같은 기본 구성 요소를 사용하지 않는 경우 이벤트(Intelligent Merchandising 및 성능 메트릭을 위해 Adobe Sensei에 데이터를 제공하는 클릭스트림 데이터)가 즉시 작동하지 않으며 Headless 이벤트를 구현하기 위해 사용자 정의 개발이 필요하다는 것을 알고 있어야 합니다.
의 최신 버전 [!DNL Live Search] 이미 사용 중 [!DNL Catalog Service] 및 설치 [!DNL Catalog Service] 모듈.

## 경계 및 임계값

현재, [!DNL Live Search] search/category API에는 다음과 같은 지원되는 제한 사항과 정적 경계가 있습니다.

### 색인화

* [색인](indexing.md) 스토어 조회당 최대 300개의 제품 속성.
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

* 최대 검색 머천다이징 수 [규칙](rules.md) 스토어 조회수는 50입니다.
* 카테고리 머천다이징에는 카테고리당 하나의 규칙이 있을 수 있습니다.
* 규칙당 최대 조건 수는 10개입니다.
* 규칙당 최대 이벤트 수는 25개입니다.

### 동의어

* [!DNL Live Search] 최대 200개까지 관리 가능 [동의어](synonyms.md) 스토어 보기별

## 언어 지원

[!DNL Live Search] 위젯은 다음 언어를 지원합니다.

|  |  |  |  |
|--- |--- |--- |--- |
| 언어 | 지역 | 언어 코드 | Magento 로케일 |
| 불가리아어 | 불가리아 | bg_BG | bg_BG |
| 카탈로니아어 | 스페인 | ca_ES | ca_ES |
| 체코어 | 체코 | cs_CZ | cs_CZ |
| 덴마크어 | 덴마크 | da_DK | da_DK |
| 독일어 | 독일 | de_DE | de_DE |
| 그리스어 | 그리스 | el_GR | el_GR |
| 영어 | 영국 | en_GB | en_GB |
| 영어 | 미국 | en_US | en_US |
| 스페인어 | 스페인 | es_ES | es_ES |
| 에스토니아어 | 에스토니아 | et_EE | et_EE |
| 바스크어 | 스페인 | eu_ES | eu_ES |
| 페르시아어 | 이란 | fa_IR | fa_IR |
| 핀란드어 | 핀란드 | fi_FI | fi_FI |
| 프랑스어 | 프랑스 | fr_FR | fr_FR |
| 갈리시아어 | 스페인 | gl_ES | gl_ES |
| 힌디어 | 인도 | hi_IN | hi_IN |
| 헝가리어 | 헝가리 | hu_HU | hu_HU |
| 인도네시아어 | 인도네시아 | id_ID | id_ID |
| 이탈리아어 | 이탈리아 | it_IT | it_IT |
| 한국어 | 대한민국 | ko_KR | ko_KR |
| 리투아니아어 | 리투아니아 | lt_LT | lt_LT |
| 라트비아어 | 라트비아 | lv_LV | lv_LV |
| 노르웨이어 | 노르웨이 복말 | nb_NO | nb_NO |
| 네덜란드어 | 네덜란드 | nl_NL | nl_NL |
| 포르투갈어 | 브라질 | pt_BR | pt_BR |
| 포르투갈어 | 포르투갈 | pt_PT | pt_PT |
| 루마니아어 | 루마니아 | ro_RO | ro_RO |
| 러시아어 | 러시아 | ru_RU | ru_RU |
| 스웨덴어 | 스웨덴 | sv_SE | sv_SE |
| 태국인 | 태국 | th_TH | th_TH |
| 터키어 | 터키 | tr_TR | tr_TR |
| 중국어 | 중국 | zh_CN | zh_Hans_CN |
| 중국어 | 대만 | zh_TW | zh_Hant_TW |

위젯이 Commerce 관리자 언어 설정(_스토어_ > 설정 > _구성_ > _일반_ > 국가 옵션) 지원되는 언어와 일치하면 기본적으로 해당 언어로 설정됩니다. 그렇지 않은 경우 위젯은 기본적으로 영어로 설정됩니다.

관리자는 의 언어를 설정할 수도 있습니다. [검색 색인](settings.md#language): 더 나은 검색 결과를 보장해 줍니다.

## 카테고리 머천다이징

[카테고리 머천다이징](category-merch.md) 을(를) 구성할 수 있습니다. [!DNL Live Search] 제품 범주 수준에서 작업합니다.

이 비디오는 카테고리 머천다이징에 대해 소개합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## 위젯 코드 저장소

제품 목록 페이지 위젯 및 라이브 검색 필드 위젯은 모두 github 저장소에서 다운로드할 수 있습니다.

이를 통해 개발자는 기능과 스타일을 완전히 맞춤화할 수 있습니다. 이러한 사용자는 코드 자체를 호스팅하면서도 [!DNL Live Search] 서비스.

* [PLP 위젯](https://github.com/adobe/storefront-product-listing-page)
* [검색 창](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] 지원 [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) commerce(이전에는 MSI라고 함)의 기능. 전체 지원을 활성화하려면 다음을 수행해야 합니다 [업데이트](install.md#update) 종속성 모듈 `commerce-data-export` 버전 102.2.0+에

[!DNL Live Search] Inventory management 내에서 제품을 사용할 수 있는지 여부를 나타내는 부울을 반환하지만, 재고가 있는 소스에 대한 정보는 포함하지 않습니다.

## 가격 인덱서

라이브 검색 고객은 새 [SaaS 가격 인덱서](../price-index/price-indexing.md)를 통해 가격 변경 업데이트 및 동기화 시간이 빨라집니다.

## 가격 지원

Live Search 위젯은 Adobe Commerce에서 지원하는 대부분의 가격 유형을 지원하지만 일부 가격 유형은 지원하지 않습니다.

현재 기본 가격이 지원됩니다. 지원되지 않는 고급 가격은 다음과 같습니다.

* 비용
* 최소 광고 가격

다음 항목 보기 [API 메쉬](../catalog-service/mesh.md) 보다 복잡한 가격 계산을 위해.

가격 형식은 Commerce 인스턴스 내의 로케일 구성 설정을 지원합니다. *스토어* > 설정 > *구성* > 일반 > *일반* > 로컬 옵션 > 로케일.

## PWA 지원

[!DNL Live Search] 은 PWA Studio에서 작동하지만 다른 Commerce 구현에 비해 약간의 차이가 있을 수 있습니다. 검색 및 제품 목록 페이지와 같은 기본 기능은 Venia에서 작동하지만 Graphql의 일부 순열이 제대로 작동하지 않을 수 있습니다. 성능 차이도 있을 수 있습니다.

* 의 현재 PWA 구현 [!DNL Live Search] 검색 결과를 반환하는 데 보다 많은 처리 시간이 필요합니다. [!DNL Live Search] 기본 Commerce 상점 포함.
* [!DNL Live Search] PWA에서 을(를) 지원하지 않습니다. [이벤트 처리](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). 따라서 검색 보고나 지능형 머천다이징도 작동합니다.
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
* [계층 가격](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) 및 [특별 가격](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) 은(는) 다음에서 지원되지 않습니다. [!DNL Live Search] 필드 및 제품 목록 페이지 위젯.

## 쿠키

[!DNL Live Search] 는 기본 기능의 일부로 사용자 상호 작용 데이터를 수집하며 쿠키는 이 데이터를 저장하는 데 사용됩니다. 사용자 정보를 수집할 때 사용자는 쿠키를 저장하는 데 동의해야 합니다. [!DNL Live Search] 및 [!DNL Product Recommendations] 데이터 스트림을 공유하여 동일한 쿠키 메커니즘을 공유합니다. 자세한 내용 보기 [쿠키 제한 처리](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
