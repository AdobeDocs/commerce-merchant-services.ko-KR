---
title: "[!DNL Live Search] 색인화"
description: "방법 알아보기 [!DNL Live Search] 는 제품 속성 속성을 인덱싱합니다."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: a062133d94cb4898149b9cc878351ca2fad3c09e
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 0%

---

# 색인화

제품 속성 속성(메타데이터)은 다음을 결정합니다.

* 카탈로그에서 속성을 사용하는 방법
* 스토어에서의 모양 및 동작
* 데이터 전송 작업에 포함된 데이터

특성 메타데이터의 범위는 다음과 같습니다. `website/store/store view`.

다음 [!DNL Live Search] API를 사용하면 클라이언트가 [storefront 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` 을 로 설정 `Yes` Adobe Commerce 관리자. 활성화된 경우 `Search Weight` 및 `Visible in Advanced Search` 속성에 대해 를 설정할 수 있습니다.

[!DNL Live Search] 삭제된 제품 또는 (으)로 설정된 제품을 색인화하지 않음 `Not Visible Individually`.

>[!NOTE]
>
> 다음을 보유한 상거래 고객 [!DNL Live Search] 을(를) 통해 웹 사이트에서 더 빠른 가격 변경 업데이트 및 동기화 시간을 이용할 수 있습니다. [SaaS 가격 인덱서](../price-index/index.md).

## 색인 지정 파이프라인

클라이언트가 검색(필터링 가능, 정렬 가능) 인덱스 메타데이터를 검색하기 위해 상점 첫 화면에서 검색 서비스를 호출합니다. 를 사용하는 검색 가능한 제품 속성만 *레이어 탐색에서 사용* 속성이 로 설정됨 `Filterable (with results)` 및 *제품 목록에서 정렬에 사용* 을 로 설정 `Yes` 검색 서비스에서 를 호출할 수 있습니다.
동적 쿼리를 만들려면 검색 서비스는 검색할 수 있는 특성과 해당 특성을 알아야 합니다 [두께](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search). [!DNL Live Search] 는 Adobe Commerce 검색 가중치를 부여합니다(1-10, 여기서 10이 가장 높은 우선 순위). 동기화되어 카탈로그 서비스와 공유되는 데이터 목록은 다음 위치에 정의된 스키마에서 찾을 수 있습니다.

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 색인화 클라이언트 검색 다이어그램](assets/indexing-pipeline.svg)

1. 다음에 대한 판매자 확인 [!DNL Live Search] 권한 부여.
1. 속성 메타데이터에 대한 변경 사항을 포함하여 스토어 보기를 가져옵니다.
1. 색인 지정 속성을 저장합니다.
1. 검색 색인을 다시 색인화합니다.

### 전체 색인

날짜 [!DNL Live Search] 온보딩 중에 가 구성되고 동기화되므로 초기 색인을 작성하는 데 최대 30분이 걸릴 수 있습니다. 큰 카탈로그는 색인화하는 데 시간이 더 걸릴 수 있습니다. 이 프로세스는 다음 이후에 시작됩니다. `cron` 피드를 제출하고 실행을 완료합니다.

다음 이벤트는 전체 동기화 및 색인 빌드를 트리거합니다.

* 온보딩 [카탈로그 데이터 동기화](install.md#synchronize-catalog-data)
* 속성 메타데이터 변경 사항

예: `Use in Search` 의 속성 `color` 속성 출처: `No` 끝 `Yes` 속성 메타데이터를 다음으로 변경합니다. `searchable=true`및 는 전체 동기화 및 색인 재지정을 트리거합니다. 다음 특성 메타데이터는 변경 시 전체 동기화를 트리거하고 다시 인덱싱합니다.

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 스트리밍 제품 업데이트

다음 기간 동안 초기 색인이 빌드된 후: [온보딩](install.md#synchronize-catalog-data), 다음 증분 제품 업데이트가 계속 동기화되고 다시 인덱싱됩니다.

* 새 제품이 카탈로그에 추가됨
* 제품 속성 값 변경

예를 들어 새 견본 값을 `color` 속성은 스트리밍 제품 업데이트로 처리됩니다.
스트리밍 업데이트 워크플로우:

1. 업데이트된 제품은 Adobe Commerce 인스턴스에서 카탈로그 서비스로 동기화됩니다.
1. 색인 지정 서비스는 카탈로그 서비스에서 제품 업데이트를 계속 검색합니다. 업데이트된 제품은 카탈로그 서비스에 도착하면 색인화됩니다.
1. 에서 제품 업데이트를 사용할 수 있으려면 최대 15분이 걸릴 수 있습니다. [!DNL Live Search].

## 클라이언트 검색

다음 [!DNL Live Search] API를 사용하면 클라이언트는 다음을 설정하여 정렬 가능한 제품 속성별로 정렬할 수 있습니다. [storefront 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *제품 목록에서 정렬하는 데 사용됨* 끝 `Yes`. 이 설정은 테마에 따라 속성이 의 옵션으로 포함됩니다. [정렬 기준:](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) 카탈로그 페이지의 페이지 매김 제어. 최대 200개의 제품 속성을으로 인덱싱할 수 있음 [!DNL Live Search], 포함 [storefront 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 검색과 필터링이 가능합니다.
인덱스 메타데이터는 인덱싱 파이프라인에 저장되고 검색 서비스에서 액세스할 수 있습니다.

![[!DNL Live Search] 인덱스 메타데이터 API 다이어그램](assets/index-metadata-api.svg)

### 정렬 가능한 속성 워크플로

1. 클라이언트가 검색 서비스를 호출합니다.
1. 검색 서비스는 검색 관리자 서비스를 호출합니다.
1. 검색 서비스가 색인화 파이프라인을 호출합니다.

## 모든 제품에 대해 색인화됨

이 목록에 있는 필드의 순서는 내보낸 제품 데이터의 일반적인 열 순서를 반영합니다.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

다음 필드는 구성 가능한 모든 제품에 대해 색인화됩니다.

* `childrenSkus`
