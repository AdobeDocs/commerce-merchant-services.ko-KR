---
title: 소개 [!DNL Live Search]
description: "[!DNL Live Search] Adobe Commerce에서는 매우 빠르고, 관련성이 높고, 직관적인 검색 환경을 제공합니다."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 3352bd1390704646f4c21599ebf204eda2e1488c
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# 소개 [!DNL Live Search]

[!DNL Live Search] 는 표준 검색 기능을 대체하는 Adobe Commerce용 서비스입니다. 다음 [!DNL Live Search] 모듈이 Composer와 함께 설치되고 [!DNL Commerce] 에 설치 [!DNL Live Search] [서비스](../landing/saas.md). 구성되면 기본 검색 텍스트 필드가 로 바뀝니다. [!DNL Live Search] 텍스트 필드.

[!DNL Live Search] 다음 화면에 나타남: *마케팅* 아래 메뉴 *SEO 및 검색* 다음에서 [!DNL Commerce] *관리자*.

아키텍처의 Adobe Commerce 측에는 검색 호스팅이 포함됩니다 *관리자*, 카탈로그 데이터 동기화 및 쿼리 서비스 실행. 다음 이후 [!DNL Live Search] 가 설치되고 구성되면 Adobe Commerce은 SaaS 서비스와 검색 및 카탈로그 데이터 공유를 시작합니다. 이 시점에서 관리자는 검색을 설정, 사용자 지정 및 관리할 수 있습니다 [패싯](facets.md), [동의어](synonyms.md), 및 [머천다이징 규칙](category-merch.md).

![라이브 검색 아키텍처 다이어그램](assets/architecture-diagram.svg)

## 라이브 검색 구성 요소

* [!DNL Live Search] [팝오버](storefront-popover.md) 은 검색 결과가 포함된 검색 필드 아래에 열리는 상자입니다.
* [제품 목록 페이지 위젯](plp-styling.md) 패싯 및 동의어 지원이 포함된 검색 가능한 제품 목록 페이지를 제공합니다.
* AEM CIF 구성 요소: [팝오버 위젯](https://github.com/adobe/aem-cif-guides-venia/pull/319) 및 [PLP 위젯](https://github.com/adobe/aem-cif-guides-venia/pull/320) AEM 사이트에서 다음을 활용하도록 허용 [!DNL Live Search].
* [[!DNL Live Search] 관리자](workspace.md) 는 규칙, 패싯 및 동의어가 구성되는 위치입니다.
* 검색 어댑터는 의 기본 구현입니다 [!DNL Live Search].

## [!DNL Live Search] 데모

자세한 내용은 이 비디오 를 참조하십시오 [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

라이브 검색 사용 및 구성 방법에 대한 자세한 비디오는 [의 전체 데모 [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) 주제.
