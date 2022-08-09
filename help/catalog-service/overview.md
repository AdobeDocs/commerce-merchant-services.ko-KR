---
title: '"[!DNL Catalog Service]"'
description: '"[!DNL Catalog Service] Adobe Commerce용 는 기본 Adobe Commerce GraphQL 쿼리보다 제품 표시 페이지 및 제품 목록 페이지의 컨텐츠를 훨씬 빠르게 검색하는 방법을 제공합니다."'
source-git-commit: eb2242ac99cfaef4ed75936a1b5cc800cc451c83
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# [!DNL Catalog Service] Adobe Commerce

{{catalog-service-beta}}

다음 [!DNL Catalog Service] Adobe Commerce 확장의 경우 다음을 포함하여 제품 관련 상점 경험을 빠르고 완전히 렌더링할 수 있도록 풍부한 보기 모델(읽기 전용) 카탈로그 데이터를 제공합니다.

* 제품 세부 사항 페이지
* 제품 목록 및 카테고리 페이지
* 검색 결과 페이지
* 제품 회전 메뉴
* 제품 비교 페이지
* 장바구니, 주문 및 위시 목록 페이지와 같이 제품 데이터를 렌더링하는 다른 모든 페이지

다음 [!DNL Catalog Service] 사용 [GraphQL](https://graphql.org/) 제품 데이터를 요청 및 수신하기 위해. GraphQL은 프런트 엔드 클라이언트가 Adobe Commerce과 같은 백엔드에 정의된 API(애플리케이션 프로그래밍 인터페이스)와 통신하는 데 사용하는 쿼리 언어입니다. GraphQL은 가볍고 시스템 통합자가 각 응답의 내용과 순서를 지정할 수 있으므로 널리 사용되는 통신 방법입니다.

Adobe Commerce에는 두 개의 GraphQL 시스템이 있습니다. 핵심 GraphQL 시스템은 쇼핑객이 제품, 고객 계정, 장바구니, 체크아웃 등을 비롯하여 다양한 유형의 페이지와 상호 작용할 수 있도록 다양한 쿼리(읽기 작업) 및 돌연(쓰기 작업)을 제공합니다. 그러나 제품 정보를 반환하는 쿼리는 속도에 최적화되지 않습니다. 서비스 GraphQL 시스템은 제품 및 관련 정보에 대해서만 쿼리를 수행할 수 있습니다. 이러한 쿼리는 유사한 핵심 쿼리보다 성능이 더 좋습니다.

## 아키텍처

다음 다이어그램은 두 GraphQL 시스템을 보여줍니다.

![카탈로그 아키텍처 다이어그램](assets/catalog-service-architecture.png)

코어 GraphQL 시스템에서 PWA은 상거래 애플리케이션에 요청을 전송하여 각 요청을 수신하고 처리하며 여러 하위 시스템을 통해 요청을 전송한 다음 스토어에 대한 응답을 반환합니다. 이 라운드 트립은 페이지 로드 시간이 느려져 전환율이 낮아질 수 있습니다.

[!DNL Catalog Service] 별도의 GraphQL 게이트웨이에 쿼리를 보냅니다. 이 서비스는 제품 속성, 변형, 가격 및 카테고리와 같은 제품 세부 사항 및 관련 정보가 포함된 별도의 데이터베이스에 액세스합니다. 서비스는 색인을 통해 데이터베이스를 Adobe Commerce과 계속 동기화합니다.
서비스는 애플리케이션과 직접 통신을 생략하므로 요청 및 응답 주기의 지연 시간을 줄일 수 있습니다.

>[!NOTE]
>
>게이트웨이는 향후 Adobe와의 통합을 위한 것입니다 [!DNL Live Search] 및 [!DNL Product Recommendations]. 이 릴리스에서는 [!DNL Catalog Service] 두 제품에 대해 유효한 라이센스 키가 있는 경우 동일한 끝점의 라이브 검색 쿼리를 사용합니다. 그러나 두 제품의 쿼리는 현재 응답 데이터를 공유하지 않습니다.

코어 및 서비스 GraphQL 시스템은 서로 직접 통신하지 않습니다. 다른 URL에서 각 시스템에 액세스하면 호출에 다른 헤더 정보가 필요합니다. 두 GraphQL 시스템은 함께 사용하도록 설계되었습니다. 다음 [!DNL Catalog Service] GraphQL 시스템은 핵심 시스템을 확장하여 제품 상점 경험을 더 빠르게 만듭니다.

원할 경우 구현할 수 있습니다 [Adobe Developer App Builder용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/) Adobe Developer을 사용하여 두 Adobe Commerce GraphQL 시스템을 개인 및 타사 API 및 기타 소프트웨어 인터페이스와 통합합니다. 각 종단점으로 라우팅된 호출에 헤더에 올바른 인증 정보가 포함되도록 메쉬를 구성할 수 있습니다.

## 구현

설치 프로세스에는 [Commerce Services 커넥터](../landing/saas.md). 이 작업이 완료되면 시스템 통합자가 상점 코드를 업데이트하여 [!DNL Catalog Service] 쿼리 모두 [!DNL Catalog Service] 쿼리는 GraphQL 게이트웨이로 라우팅됩니다. URL은 온보딩 프로세스 중에 제공됩니다.

[Adobe Commerce Devdocs](https://devdocs.magento.com/catalog-service/index.html) 코어와 의 차이점에 대해 설명합니다. [!DNL Catalog Service] 쿼리 각 쿼리에 대한 참조 정보도 포함됩니다.
