---
title: '라이브 검색 설정'
description: 다음 [!DNL Live Search] 작업 영역은 검색 성능을 구성, 관리 및 모니터링하는 데 사용됩니다.
exl-id: fb85974a-a5f9-4e6c-bd03-451e6457f2d2
source-git-commit: 5e79bb43449b95b4c6aa0e234a0dbc999c312e59
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# 라이브 검색 설정

작업 영역에서는 의 성능을 구성, 관리 및 모니터링합니다. [!DNL Live Search]. 맨 위에 있는 메뉴를 통해 각 기능 영역의 도구에 액세스할 수 있습니다. 사용 가능한 기능은 현재 메뉴 선택을 반영합니다.

![Workspace](assets/workspace.png)

## 데이터 수집

작업 영역의 각 기능 영역에 올바른 데이터가 포함되어 있는지 확인하려면 선택한 Storefront 구현을 기반으로 데이터 수집을 구성해야 합니다.

1. Luma - 데이터 수집은 즉시 사용할 수 있습니다.
1. Headless - 데이터 수집은 상점 구현에 따라 수동으로 구성해야 합니다.

Headless Storefront를 사용하는 경우 다음 설명서를 참조하여 추가해야 하는 필수 이벤트에 대한 자세한 내용을 확인하십시오.

- [필수 이벤트](events.md) 라이브 검색 대시보드용
- [Storefront 이벤트 수집기](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) 필수 구성 요소로 추가해야 합니다.
- [예](https://github.com/adobe/commerce-events/tree/main/examples) 이벤트 구조

## 범위 설정

처음에는 [범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 전체 중 [!DNL Live Search] 설정이 (으)로 설정됨 `Default Store View`. 다음의 경우 [!DNL Commerce] 설치에는 여러 스토어 보기, 세트가 포함됩니다. **범위** (으)로 [스토어 뷰](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 패싯 설정이 적용되는 위치입니다.

## 메뉴 옵션

| 옵션 | 설명 |
|--- |--- |
| [성능](performance.md) | 대시보드는 제품 검색 성능에 대한 통찰력을 제공합니다. |
| [안면 효과](facets.md) | 여러 차원의 속성 값을 사용하여 검색 기준을 구체화하는 고성능 필터링입니다. |
| [동의어](synonyms.md) | 쇼핑객이 카탈로그에 있는 것과 다른 제품을 찾는 데 사용할 수 있는 단어를 포함하도록 검색 범위를 확장하십시오. |
| [머천다이징 검색](rules.md) | 예약된 작업을 트리거하는 논리 규칙으로 검색 환경을 구성합니다. 비즈니스 목표를 지원하기 위해 검색 결과를 보정하기 위해 제품을 증폭, 매몰, 고정 또는 숨깁니다. |
| [카테고리 머천다이징](category-merch.md) | 카테고리 수준에서 규칙 및 지능형 머천다이징을 적용합니다. |
| [GraphQL](graphql.md) | 저장소 관리자에 로그인한 개발자는 실제 카탈로그 데이터로 쿼리를 작성하고 테스트할 수 있습니다. 자세한 내용을 보려면 다음 위치로 이동하십시오. [GraphQL 개요](https://developer.adobe.com/commerce/webapi/graphql/) 다음에서 [!DNL Live Search] 개발자 설명서. |
| [설정](settings.md) | 가격 패싯 값을 상점 가격 범위별로 그룹화하는 방법을 결정하고 색인화 언어를 설정합니다. |

## 속성을 검색 가능한 것으로 설정

고도로 타겟팅된 결과를 생성하려면 다음을 검토하십시오. [검색 가능](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) 제품 속성. 관련성을 보장하려면 명확하고 간결한 의미가 있는 콘텐츠가 포함된 경우에만 속성을 검색할 수 있도록 하십시오. 다음과 같이 정확하지 않고 긴 텍스트가 포함된 속성은 사용하지 마십시오. `description`는 기본적으로 검색을 활성화하지만 검색 결과의 정밀도를 줄일 수 있습니다. 예를 들어, &quot;반바지&quot;를 검색하는 사람이 &quot;반팔&quot;이라는 용어가 포함된 설명이 있는 셔츠가 있으면 해당 셔츠가 검색 결과에 포함됩니다.

속성을 검색할 수 있도록 허용하려면 다음 단계를 완료하십시오.

1. 관리에서 **스토어** > *속성* > **제품**.
1. 검색할 속성을 선택합니다. 예: `color`.
1. 선택 **Storefront 속성** 및 설정 **검색에 사용** 끝 `yes`.

   ![Workspace](assets/attribute-searchable.png)

[!DNL Live Search] 또한 다음을 준수합니다. [두께](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) Adobe Commerce 내에 설정된 제품 속성. 가중치가 높은 속성은 검색 결과 내에서 더 높게 표시됩니다.

다음 속성은 항상 검색할 수 있습니다.

- `sku`
- `name`
- `categories`

[패싯](facets.md) 는에 정의된 제품 속성입니다. [!DNL Live Search] 필터링할 수 있습니다. 필터링 가능한 모든 속성을에서 패싯으로 설정할 수 있습니다 [!DNL Live Search], 하지만 [제한](boundaries-limits.md) 한 번에 검색할 수 있는 패싯 수를 표시합니다.

[동의어](synonyms.md) 는 사용자에게 올바른 제품을 안내하기 위해 정의할 수 있는 용어입니다. 바지를 찾는 사용자들은 &quot;바지&quot; 또는 &quot;바지&quot;를 타이핑할 수 있습니다. 이러한 검색어가 사용자에게 &quot;바지&quot; 결과를 가져오도록 동의어를 설정할 수 있습니다.

## Commerce 구성 설정

다음 섹션에서는 지원되는 와 지원되지 않는 Commerce 구성 설정에 대해 설명합니다 [!DNL Live Search].

### 지원되는 구성 값

| Commerce 구성 설정 | 설명 | 팝오버에서 지원됨 | 어댑터에서 지원 |
|---|---|---|---|
| 스토어 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 페이지당 모든 제품 허용 | 로 설정된 경우 `Yes`, 다음을 포함 `ALL` 옵션은 &quot;페이지당 표시&quot; 컨트롤에 표시됩니다. | 예. 최대 500개 제품 | 예. 최대 500개 제품 |
| 저장소 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 최소 쿼리 길이 | 카탈로그 검색에 허용되는 최소 문자 수입니다. | 예 | 예 |
| 스토어 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 그리드 허용 값의 페이지당 제품 | 눈금 보기에 표시되는 제품 수를 결정합니다. | 예 | 예 |
| 스토어 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 그리드의 페이지당 제품 기본값 | 그리드 보기에서 기본적으로 페이지당 표시되는 제품 수를 결정합니다. | 예. 최대 500개 제품 | 예. 최대 500개 제품 |
| 스토어 > 구성 > 카탈로그 > 재고 > 재고 부족 제품 표시 | 품절된 제품을 표시합니다. | 예, v2.0.4+ | 예, v2.0.4+ |
| Stores > Configuration > Currency > Default Display Currency | 가격을 표시하는 데 사용되는 기본 통화. | 예, 3.1.0+ | 예, 3.1.0+ |
| 스토어 > 구성 > 일반 > 통화 설정 > 통화 옵션 > 기본 통화 | 모든 온라인 결제 거래에 사용되는 기본 통화. | 예 | 예 |

위젯 제품 목록 페이지 및 팝오버의 가격은 구성된 환율을 사용하여 기본 표시 통화로 전환됩니다.

### 지원되지 않는 구성 값

| Commerce 구성 설정 | 설명 | 메모 |
|---|---|---|
| 스토어 > 구성 > 카탈로그 > 상점 > 목록 모드 | 검색 결과 목록의 형식을 결정합니다. | 올바르게 렌더링되지만 일부 페이지 상호 작용에 대해 이벤트가 전송되지 않음 |
| 저장소 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 최대 쿼리 길이 | 카탈로그 검색에 허용되는 최대 문자 수. | 구현되지 않음. 검색 서비스는 최대 255자를 허용합니다. |
| 구성 > 판매 > 세금 > 가격 표시 설정 > 카탈로그에 제품 가격 표시 | 카탈로그에 게시된 제품 가격에 세금이 포함되는지 또는 제외되는지 여부를 결정하거나 두 가지 버전의 가격을 표시합니다(하나는 세금이 포함됨). |  |
| 스토어 > 구성 > 카탈로그 > 상점 > 제품 목록 정렬 기준 | 검색 결과 목록의 정렬 순서를 결정합니다. | 에는 적용되지 않습니다. [!DNL Live Search] [제품 목록 페이지 위젯](plp-styling.md) |

### 검색어

[!DNL Live Search] 지원 [검색어 리디렉션](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) Luma 및 기타 php 기반 테마에서와 같이 Adobe Commerce이 라우팅을 처리하는 구현에서.
