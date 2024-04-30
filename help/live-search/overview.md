---
title: 이란? [!DNL Live Search]?
description: "[!DNL Live Search] Adobe Commerce에서 빠르고 관련성이 높고 직관적인 검색 경험을 제공합니다."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: aba552808ea7af540f64f00a2ae4aeaf2b9cc52e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 이란? [!DNL Live Search]?

[!DNL Live Search] 는 Adobe Commerce의 표준 검색 기능을 대체하는 확장입니다. 다음 [!DNL Live Search] 확장이 Composer와 함께 설치되고 [!DNL Commerce] 에 설치 [!DNL Live Search] [서비스](../landing/saas.md). 구성되면 기본 검색 텍스트 필드가 로 바뀝니다. [!DNL Live Search] 텍스트 필드. [!DNL Live Search] 또한 검색 결과를 검색할 때 강력한 필터링 기능을 제공하는 PLP(제품 목록 페이지) 위젯을 설치합니다.

포함 [!DNL Live Search], 다음 작업을 수행할 수 있습니다.

- 의미 있는 검색 경험을 만들어 쇼핑객과 구매자가 가능한 한 적은 노력으로 원하는 것을 찾을 수 있도록 지원합니다.
- 세션 내 구매자 행동에 대응하여 검색 결과를 AI에서 제공하는 동적 팩팅 및 재순위를 활용하십시오.
- 간단한 업데이트를 제공하고 라이선스에 포함되어 TCO를 절감하는 간단한 SaaS 기반 서비스를 사용합니다.
- GraphQL API, Headless 유연성, API 샌드박스 환경 및 초고속 SaaS를 활성화하여 기술력을 얻으십시오.

>[!IMPORTANT]
>
>사이트 검색과 관련하여 Adobe Commerce은 옵션을 제공합니다. 다음을 읽으십시오. [경계 및 제한](boundaries-limits.md) 구현하기 전에 [!DNL Live Search] 은(는) 귀하의 비즈니스 요구에 적합합니다.

## 아키텍처

아키텍처의 Adobe Commerce 측에는 검색 호스팅이 포함됩니다 *관리자*, 카탈로그 데이터 동기화 및 쿼리 서비스 실행. 다음 이후 [!DNL Live Search] 가 설치되고 구성되면 Adobe Commerce은 SaaS 서비스와 검색 및 카탈로그 데이터 공유를 시작합니다. 이 시점에서 관리자는 검색을 설정, 사용자 지정 및 관리할 수 있습니다 [패싯](facets.md), [동의어](synonyms.md), 및 [머천다이징 규칙](category-merch.md).

![라이브 검색 데이터 흐름](assets/ls-cs-data-flow.png)

## 빠른 둘러보기

속도, 관련성 및 사용 편이성에 중점을 두고 [!DNL Live Search] 은 쇼핑객과 상인들을 위한 게임 체인저입니다. 다음 비디오를 시청한 다음 간단히 살펴보십시오. [!DNL Live Search] 가게 앞에서요

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

라이브 검색 사용 및 구성 방법에 대한 자세한 비디오는 [의 전체 데모 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) 주제.

### 입력할 때 검색

[!DNL Live Search] 추천 제품 및 상위 검색 결과의 썸네일 이미지로 응답함 [팝오버](storefront-popover.md) 구매자가 다음에 쿼리를 입력할 때 [검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 상자. 다음 [제품 세부 사항](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) 쇼핑객이 추천 또는 추천 제품을 클릭하면 페이지가 표시됩니다. A _모두 보기_ 팝오버의 바닥글에 있는 링크에 검색 결과 페이지가 표시됩니다.

[!DNL Live Search] 둘 이상의 문자로 이루어진 쿼리에 대해 &quot;검색할 때&quot; 결과를 반환합니다. 부분 일치의 경우 단어 당 최대 문자 수는 20자입니다. 쿼리의 문자 수를 구성할 수 없습니다. 팝오버에는 다음이 포함됩니다.`name`, `sku`, 및 `category_ids` 필드.

![예 storefront - 입력할 때 검색](assets/storefront-search-as-you-type.png)

### 모든 검색 결과 보기

&quot;입력할 때 검색&quot; 쿼리에서 반환된 모든 제품을 나열하려면 _모두 보기_ 팝오버의 바닥글에 있습니다.

![예 storefront - 가격 패싯](assets/storefront-view-all-search-results.png)

### 패싯으로 필터링된 검색

필터링된 검색은 속성 값의 여러 차원을 사용하거나 [패싯](facets.md)을 검색 기준으로 사용합니다. 필터 선택은 판매자에 의해 정의되며 반환되는 제품에 따라 변경되며, 가장 일반적으로 사용되는 패싯은 목록의 맨 위에 고정됩니다.

패싯을 URL 매개 변수로 사용:`http://yourwebsite.com?color=red`, 및 라이브 검색 필터는 이러한 속성 값을 기반으로 결과를 필터링합니다.

### 동의어

[동의어](synonyms.md) 범위를 확장하고 쇼핑객이 카탈로그에 있는 것과 다른 단어를 사용하여 쿼리의 초점을 선명하게 합니다. 동의어 사전을 미세 조정하여 쇼핑객이 구매 경로에 계속 참여하도록 할 수 있습니다.

### 머천다이징 규칙

머천다이징 [규칙](rules.md) 검색할 논리 및 이벤트를 추가하는 if-then 문을 사용하여 쇼핑 경험을 구체화합니다. 프로모션, 계절 또는 기타 기간 동안 제품을 쉽게 부스트하거나 묻을 수 있습니다.

### 검색어 지원

[!DNL Live Search] Commerce 지원 [검색어 리디렉션](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). 예를 들어 &quot;배송비&quot;와 같은 용어를 검색하여 배송비 페이지로 바로 이동할 수 있습니다.

## 라이브 검색 구성 요소

- [!DNL Live Search] [팝오버 위젯](storefront-popover.md) 은 검색 결과가 포함된 검색 필드 아래에 열리는 상자입니다.
- [제품 목록 페이지 위젯](plp-styling.md) 패싯 및 동의어 지원이 포함된 검색 가능한 제품 목록 페이지를 제공합니다.
- [[!DNL Live Search] 관리자](workspace.md) 는 규칙, 패싯 및 동의어가 구성되는 위치입니다.

## [!DNL Live Search] 작업 영역

다음 [!DNL Live Search] [작업 영역](workspace.md) 는 관리자가 구성하는 영역입니다. [!DNL Live Search] 동의어, 패싯 및 카테고리 머천다이징과 같은 기능.

## 이벤트

[!DNL Live Search] 사용 [events](events.md) 계산하려면 [지능형 머천다이징](category-merch.md) 및 [성능](performance.md) 대시보드. 이벤트에는 기본 구현이 제공됩니다. 헤드리스 상점 첫 화면의 이벤트는 수동으로 활성화해야 합니다.
