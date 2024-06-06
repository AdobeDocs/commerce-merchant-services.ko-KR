---
title: '경계 및 제한'
description: 의 경계 및 제한에 대해 알아보기 [!DNL Live Search] 비즈니스 요구 사항을 충족하도록 보장합니다.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 63c90d4ef0e14c0baaf8c79569a01e5dffa5b450
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# 경계 및 제한

사이트 검색과 관련하여 Adobe Commerce은 옵션을 제공합니다. 다음 경계 및 제한을 검토하여 다음을 확인합니다 [!DNL Live Search] 및 [!DNL Catalog Service] 비즈니스 요구 사항을 충족합니다. 콘텐츠 검색, BYOA(bring-your-own-algorithm) 또는 속성 기반 머천다이징과 같은 고급 검색 기능이 필요한 경우 서드파티 검색 솔루션을 고려하십시오.

## 일반

- 다음 [고급 검색](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 다음 경우에 모듈이 비활성화됩니다. [!DNL Live Search] 가 설치되고 상점 첫 번째 바닥글의 고급 검색 링크가 제거됩니다.
- [계층 가격](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) 및 [특별 가격](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) 은(는) 다음에서 지원되지 않습니다. [!DNL Live Search] 필드 및 제품 목록 페이지 위젯.
- 제품 가격에는 부가가치세(VAT)가 포함되지 않습니다.
- 콘텐츠 검색이 지원되지 않습니다.
- 페이지 매김이 가능한 제품은 10k개로 제한됩니다.
- 검색 어댑터는 사용자 지정 소스 모델로 만들어져 패싯으로 사용되는 제품 속성을 지원하지 않습니다. 이 기능을 지원하려면 다음을 사용해야 합니다 [제품 목록 페이지 위젯](plp-styling.md).

## 색인화

- [!DNL Live Search] [색인](indexing.md) 스토어 조회당 최대 450개의 제품 속성. 이는 다음과 같이 배포됩니다.
   - 정렬 가능한 속성 50개
   - 필터링 가능한 특성 200개
   - 검색 가능한 속성 200개
- [!DNL Live Search] 는 Adobe Commerce 데이터베이스의 제품만 인덱싱합니다.
- CMS 페이지가 인덱싱되지 않았습니다.
- SKU, 이름 및 카테고리 속성은 기본적으로 검색할 수 있으며 검색에서 제외할 수 없습니다. 해당 범주에 포함시키려는 제품이 아닌 경우 해당 범주에서 제품 할당을 취소해야 합니다.

## 패싯

- 인덱싱할 수 있는 200개의 필터링 가능한 속성에서 패싯으로 최대 100개의 속성을 구성할 수 있습니다.
- Facet 내에서 최대 30개의 버킷이 반환될 수 있습니다. 30개 이상의 버킷이 반환되어야 하는 경우 [지원 티켓 만들기](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) 따라서 Adobe은 성능 영향을 분석하고 환경에 대한 이 제한을 늘릴 수 있는지 여부를 결정할 수 있습니다.
- 동적 패싯은 큰 인덱스와 순서가 높은 인덱스에서 성능 문제를 일으킬 수 있습니다. 동적 패싯을 만들어 성능 저하 또는 페이지가 시간 초과 오류와 함께 로드되지 않은 것을 발견한 경우 패싯을 고정으로 변경하여 성능 문제가 해결되는지 확인하십시오.
- 재고 상태 (`quantity_and_stock_status`)은 패싯으로 지원되지 않습니다. 다음을 사용할 수 있습니다. `inStock: 'true'` 재고 제품을 필터링합니다. 이 기능은 의 기본 기능으로 지원됩니다 `LiveSearchAdapter` 모듈에서 &quot;재고 부족 제품 표시&quot;가 &quot;True&quot;로 설정된 경우 [!DNL Commerce] 관리자.
- 날짜 유형 속성은 패싯으로 지원되지 않습니다.

## 쿼리

- [!DNL Live Search] 은 카테고리 트리의 전체 분류법에 액세스할 수 없으므로 해당 범위 밖에 일부 계층화된 탐색 검색 시나리오가 만들어집니다.
- [!DNL Live Search] 고유 사용 [GraphQL 엔드포인트](https://developer.adobe.com/commerce/services/graphql/live-search/) 동적 팩팅 및 검색할 때 사용 가능한 검색 등의 기능을 지원하는 쿼리입니다. 와 유사하긴 하지만 [GRAPHQL API](https://developer.adobe.com/commerce/webapi/graphql/)에 몇 가지 차이점이 있으며 일부 필드가 완전히 호환되지 않을 수 있습니다.
- 검색 쿼리에서 반환할 수 있는 최대 결과 수는 10,000개입니다.
- 날짜 유형 특성을 사용하여 결과를 필터링할 수 없습니다.

## 규칙

- 최대 검색 머천다이징 수 [규칙](rules.md) 스토어 조회수는 50입니다.
- 카테고리 머천다이징에는 카테고리당 하나의 규칙이 있을 수 있습니다.
- 규칙당 최대 조건 수는 10개입니다.
- 규칙당 최대 이벤트 수는 25개입니다.

## 동의어

- [!DNL Live Search] 최대 200개까지 관리 가능 [동의어](synonyms.md) 스토어 보기별
- 다중 단어 동의어는 스토어 보기당 20개로 제한됩니다.

## 카테고리 머천다이징

- 각 스토어 보기에 대해 카테고리당 하나의 규칙을 만들 수 있습니다. 각 규칙에는 다음이 포함될 수 있습니다.
   - 최대 10개의 조건
   - 최대 25개 이벤트

## B2B 및 범주 권한

- 기본 공유 카탈로그에 추가되지 않은 제품은 표시되지 않습니다.
- 카탈로그 권한을 사용하여 고객 그룹을 제한하려면 다음을 수행하십시오.
   - 제품을 루트 범주에 할당해야 합니다.
   - &quot;로그인되지 않은&quot; 고객 그룹에는 &quot;허용&quot; 검색 권한이 부여되어야 합니다.
   - 제품을 &quot;로그인되지 않음&quot; 고객 그룹으로 제한하려면 각 범주로 이동하여 각 고객 그룹에 대한 권한을 설정합니다.
- PWA Studio에 대한 실시간 검색이 있는 B2B에 대한 지원은 현재 지원되지 않습니다.
