---
title: 소개 [!DNL Live Search]
description: "[!DNL Live Search] Adobe Commerce에서 빠르고 관련성이 높고 직관적인 검색 경험을 제공합니다."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 12c9fa011662e2e9fd7bb088db97359dcde87915
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# 소개 [!DNL Live Search]

[!DNL Live Search] 는 표준 검색 기능을 대체하는 Adobe Commerce용 서비스입니다. 다음 [!DNL Live Search] 모듈이 Composer와 함께 설치되고 [!DNL Commerce] 에 설치 [!DNL Live Search] [서비스](../landing/saas.md). 구성되면 기본 검색 텍스트 필드가 로 바뀝니다. [!DNL Live Search] 텍스트 필드. [!DNL Live Search] 또한 검색 결과를 검색할 때 강력한 필터링 기능을 제공하는 PLP(제품 목록 페이지) 위젯을 설치합니다.

[!DNL Live Search] 다음 화면에 나타남: *마케팅* 아래 메뉴 *SEO 및 검색* 다음에서 [!DNL Commerce] *관리자*.

아키텍처의 Adobe Commerce 측에는 검색 호스팅이 포함됩니다 *관리자*, 카탈로그 데이터 동기화 및 쿼리 서비스 실행. 다음 이후 [!DNL Live Search] 가 설치되고 구성되면 Adobe Commerce은 SaaS 서비스와 검색 및 카탈로그 데이터 공유를 시작합니다. 이 시점에서 관리자는 검색을 설정, 사용자 지정 및 관리할 수 있습니다 [패싯](facets.md), [동의어](synonyms.md), 및 [머천다이징 규칙](category-merch.md).

## 라이브 검색 구성 요소

* [!DNL Live Search] [팝오버 위젯](storefront-popover.md) 은 검색 결과가 포함된 검색 필드 아래에 열리는 상자입니다.
* [제품 목록 페이지 위젯](plp-styling.md) 패싯 및 동의어 지원이 포함된 검색 가능한 제품 목록 페이지를 제공합니다.
* AEM CIF 구성 요소: [팝오버 위젯](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) 및 [PLP 위젯](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) AEM 사이트에서 다음을 활용하도록 허용 [!DNL Live Search].
* [[!DNL Live Search] 관리자](workspace.md) 는 규칙, 패싯 및 동의어가 구성되는 위치입니다.

## 워크플로우 개요

[!DNL Live Search] 는 카탈로그 데이터를 Adobe Commerce SaaS 인프라로 이동하고 사용자 유형에 따라 검색 결과를 신속하게 전달하는 데 사용되는 인덱스를 구축하는 방식으로 작동합니다.

### 1. 설치

[!DNL Live Search] 은(는) [설치됨](install.md) 을 통해 Adobe Commerce 인스턴스로 [작성기](https://getcomposer.org/). 서비스에 연결하는 필수 모듈을 설치하고 기본 검색 필드를 재정의하도록 Commerce 인스턴스를 구성합니다. 또한 서비스를 구성하기 위한 Commerce 관리 옵션을 설치합니다.

### 2. 데이터 동기화

[!DNL Live Search] 카탈로그 데이터를 Adobe의 SaaS 인프라로 이동합니다. 데이터가 색인화되고 검색 결과가 이 색인에서 상점 앞으로 직접 전달됩니다. 크기와 복잡성에 따라 색인화는 30분에서 2시간 정도 소요될 수 있습니다.

### 3. 데이터 구성

제품 데이터를 올바르게 구성하면 고객에게 좋은 검색 결과를 얻을 수 있습니다. 범주 할당 및 속성 구성, 두 가지 설정 단계가 필요합니다.

#### 범주 할당

제품이 반품됨 [!DNL Live Search] 은(는) 을(를) 할당해야 합니다. [범주](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). 예를 들어 Luma에서 제품은 &quot;남성&quot;, &quot;여성&quot; 및 &quot;톱니바퀴&quot;와 같은 범주에 배치됩니다. 또한 하위 카테고리는 &quot;Tops&quot;, &quot;Bottom&quot; 및 &quot;Watches&quot;에 대해 설정됩니다. 이를 통해 필터링 시 세부기간을 향상시킬 수 있습니다.

#### 검색 및 필터링 가능한 필드

제품이 할당됨 [속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 검색 및 필터링에 사용할 수 있습니다. 속성은 &quot;Color&quot;, &quot;Size&quot;, &quot;Material Type&quot;과 같은 것입니다. 이러한 속성을 사용하면 &quot;녹색 꼭대기&quot;를 찾을 수 있습니다. 각 제품에는 Commerce 관리자에 정의된 많은 속성이 있을 수 있습니다.

이러한 각 속성은 다음과 같이 정의할 수 있습니다. [&quot;검색 가능&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) 관리자. &quot;검색 가능&quot;으로 설정된 경우 다음 방법으로 해당 속성을 검색할 수 있습니다. [!DNL Live Search].

[패싯](facets.md) 는에 정의된 제품 속성입니다. [!DNL Live Search] 필터링할 수 있습니다. 필터링 가능한 속성은 모두 패싯으로 설정할 수 있습니다. [!DNL Live Search] 그러나 한 번에 검색할 수 있는 패싯 수에 제한이 있습니다.

[동의어](synonyms.md) 는 사용자에게 올바른 제품을 안내하기 위해 정의할 수 있는 용어입니다. 바지를 찾는 사용자들은 &quot;바지&quot; 또는 &quot;바지&quot;를 타이핑할 수 있습니다. 이러한 검색어가 사용자에게 &quot;바지&quot; 결과를 가져오도록 동의어를 설정할 수 있습니다.

## [!DNL Live Search] 작업 영역

다음 [!DNL Live Search] [작업 영역](workspace.md) 는 관리자에서 를 구성하는 영역입니다 [!DNL Live Search] 동의어, 패싯 및 카테고리 머천다이징과 같은 기능.

## 이벤트

[!DNL Live Search] 사용 [events](events.md) 계산하려면 [지능형 머천다이징](category-merch.md) 및 [성능](performance.md) 대시보드. 이벤트에는 기본 구현이 제공됩니다. 헤드리스 상점 첫 화면의 이벤트는 수동으로 활성화해야 합니다.

## 위젯 사용자 정의

대부분의 상점 소유자는 [!DNL Live Search] 위젯은 저장소 모양과 느낌을 준수합니다.

팝오버 및 PLP 위젯은 필요에 따라 사용자 정의 CSS 규칙을 정의하여 스타일을 지정할 수 있습니다. 다음을 참조하십시오 [팝오버 요소 스타일링](storefront-popover-styling.md) 및 [제품 목록 페이지 위젯](plp-styling.md).

위젯의 기능을 확장하려는 경우 각각의 소스 코드를 공용 리포지토리에서 사용할 수 있습니다.
이 시나리오에서는 사용자 자신의 요구 사항에 맞게 JavaScript를 사용자 지정한 다음 CDN에서 사용자 지정 코드를 호스팅할 수 있습니다. 이 사용자 지정 스크립트는 [!DNL Live Search] 서비스를 실행하고 일반적인 결과를 반환하여 위젯의 기능을 제어할 수 있습니다.

* [PLP 위젯 저장소](https://github.com/adobe/storefront-product-listing-page)
* [검색창 저장소](https://github.com/adobe/storefront-search-as-you-type)

자세한 내용 보기 [!DNL Live Search] 다음에서 [기술 개요](technical-overview.md).

## [!DNL Live Search] 데모

자세한 내용은 이 비디오 를 참조하십시오 [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

라이브 검색 사용 및 구성 방법에 대한 자세한 비디오는 [의 전체 데모 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) 주제.
