---
title: '[!DNL Catalog Service] 릴리스 정보'
description: 의 최신 릴리스 정보 [!DNL Catalog Service] Adobe Commerce용
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 822108fb92b2cac7cc62d00db035faed81ae9e25
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# [!DNL Catalog Service] 릴리스 정보

이 릴리스 노트는 최신 버전의 [!DNL Catalog Service].
현재 주요 릴리스 버전에 대한 지원이 제공됩니다. 이전 버전에 대한 릴리스 노트는 참조를 위해 제공됩니다.
업데이트에는 다음이 포함됩니다.

![신규](../assets/new.svg) 새로운 기능
![수정](../assets/fix.svg) 수정 사항 및 향상된 기능
![버그](../assets/bug.svg) 알려진 문제

## 현재 메이저 버전

### V1.11 릴리스

_2023년 7월 18일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 카탈로그 서비스가 이제 다음을 지원합니다. [`recommendations`](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) Recommendations 제품에 대한 GraphQL 쿼리.

#### 알려진 제한 사항

다음 기능은 아직 지원되지 않습니다.

* 고정 가격으로 번들 제품
* 동적 특성 페이로드의 최대 크기는 9MB입니다.
* 그룹 제품 가격. 간단한 제품 가격으로 계산할 수 있습니다.
* 이미지 배열에서는 첫 번째 이미지만 역할을 포함합니다.

API Mesh 및 Core GraphQL API를 사용하면 다음 제한 사항을 해결할 수 있습니다.

* 최소 광고 가격
* [계층 가격](mesh.md)
* 다운로드 가능한 제품 및 기프트 카드

### V1.10 릴리스

_2023년 6월 27일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 이제 카탈로그 서비스가 제품 세부 사항 페이지 위젯에 관련 제품을 표시할 수 있습니다.

### V1.7 릴리스

_2023년 4월 12일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 이제 카탈로그 서비스가 삭제된 제품 변형을 정리합니다.
![수정](../assets/fix.svg) 인프라 확장성 및 성능 향상

### V1.6 릴리스

_2023년 3월 28일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 에 견본이 추가되었습니다. [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) 쿼리.
![신규](../assets/new.svg) 을(를) 가져오는 기능이 추가됨 `entityId` 사용 [API 메쉬](mesh.md).

### V1.5 릴리스

_2023년 3월 6일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 추가됨 [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) GraphQL 기능.
![수정](../assets/fix.svg) 향상된 성능 및 API 확장성.

### V1.4 릴리스

_2023년 2월 7일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 설치 단계를 간소화하기 위한 카탈로그 서비스 메타패키지가 게시되었습니다.
![수정](../assets/fix.svg) API 확장성 및 성능 개선.

### V1.3 릴리스

_2023년 1월 17일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 온보딩 경험을 단순화하고 개선했습니다.
![신규](../assets/new.svg) 새 고객 샌드박스 엔드포인트는 사전 프로덕션 테스트에 사용할 수 있습니다.
![신규](../assets/new.svg) 가상 제품에 대한 지원이 추가되었습니다.
![수정](../assets/fix.svg) API 확장성 및 성능 개선.

### V1.1 릴리스

_2022년 11월 18일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 카탈로그 서비스가 이제 Adobe의 [API 메쉬](https://developer.adobe.com/graphql-mesh-gateway/).
![수정](../assets/fix.svg) API 확장성과 전반적인 성능이 개선되었습니다.

### V1.0 릴리스

_2022년 10월 4일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 이제 번들 및 그룹화된 제품을 지원합니다.
![신규](../assets/new.svg) B2B 가시성 재정의가 추가되었습니다. 이제 제품을 검색할 수 있으며 특정 고객 그룹을 위해 장바구니에 추가할 수 있습니다.
![수정](../assets/fix.svg) 이제 서비스가 보다 안정적이고 성능이 향상되었습니다.

## 이전 버전

+++베타 릴리스

### 0.3 릴리스 - Beta+

_2022년 9월 12일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 변형 이미지 지원: 제품 이미지는 선택한 옵션에 따라 반환됩니다
![신규](../assets/new.svg) 가격 지원에 대한 역할: 특정 고객 그룹의 구성원만 제품 가격을 볼 수 있도록 허용
![수정](../assets/fix.svg) 서비스의 안정성 및 성능 향상
![신규](../assets/new.svg) 카탈로그에서 제품이 삭제되면 업데이트가 수신됨

### 베타 릴리스

_2022년 8월 9일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 다음 `products` 및 `refineProduct` 쿼리는 다음 데이터를 반환합니다.

* 사전 정의된(시스템) 제품 속성.
* 동적 제품 속성을 확인하고 역할별로 필터링합니다(제품 표시 페이지/제품 목록 페이지).
* 제품 옵션.
* 제품 이미지를 만들고 역할(PDP/PLP)별로 필터링합니다.
* 간단한 제품에 대한 특정 가격 및 구성 가능한 제품에 대한 가격 범위입니다.
* 고객 그룹 가격 및 가격 범위. 고객 그룹이 없는 쇼핑객에 대해 대체 기본 가격을 반환합니다.
* B2B 고객별 가격을 사용하는 제품 유형입니다.

+++
