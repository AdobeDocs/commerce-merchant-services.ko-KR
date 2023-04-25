---
title: "[!DNL Live Search] 색인 지정"
description: "방법 알아보기 [!DNL Live Search] 제품 속성 속성을 인덱싱합니다."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: f310f840e286859070002ab0e23eda3787c89f36
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# 색인 지정

제품 속성 속성(메타데이터)이 결정합니다.

* 카탈로그에서 속성을 사용할 수 있는 방법
* 스토어의 모양과 동작
* 데이터 전송 작업에 포함된 데이터

속성 메타데이터의 범위는 다음과 같습니다 `website/store/store view`.

다음 [!DNL Live Search] API를 사용하면 클라이언트가 [storefront 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` 설정 `Yes` ( Adobe Commerce 관리자) 아래에 그룹화됩니다. 활성화되면, `Search Weight` 및 `Visible in Advanced Search` 속성에 대해 을 설정할 수 있습니다.

[!DNL Live Search] 삭제된 제품이나 `Not Visible Individually`.

>[!NOTE]
>
> 을 사용하는 상거래 고객 [!DNL Live Search] 보다 빠른 가격 변경 업데이트 및 웹 사이트의 동기화 시간을 활용하여 [SaaS 가격 인덱서](../price-index/index.md).

## 인덱싱 파이프라인

클라이언트는 storefront에서 검색 서비스를 호출하여 인덱스 메타데이터(필터링 가능, 정렬 가능)를 검색합니다. 를 사용하여 검색할 수 있는 제품 속성만 *레이어 탐색에서 사용* 속성 설정 `Filterable (with results)` 및 *제품 목록의 정렬에 사용* 설정 `Yes` 검색 서비스에서 호출할 수 있습니다.
동적 쿼리를 만들려면 검색 가능한 속성과 해당 가중치를 검색 서비스가 알아야 합니다. [!DNL Live Search] Adobe Commerce 검색 가중치를 적용합니다(1-10에서 10이 가장 높은 우선 순위). 카탈로그 서비스와 동기화 및 공유되는 데이터 목록은 다음 스키마에 정의되어 있습니다.

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] 클라이언트 검색 다이어그램 인덱싱](assets/indexing-pipeline.svg)

1. 머천트를 확인합니다. [!DNL Live Search] 자격 부여.
1. 특성 메타데이터에 대한 변경 사항을 사용하여 저장소 보기를 가져옵니다.
1. 색인 속성을 저장합니다.
1. 검색 색인을 다시 색인화합니다.

### 전체 인덱스

When [!DNL Live Search] 가 구성 및 온보딩 중에 동기화되므로 초기 인덱스를 만드는 데 최대 8시간이 걸릴 수 있습니다. 프로세스는 다음 시기 이후에 시작됩니다 `cron` 피드를 제출하고 실행을 완료합니다.

다음 이벤트는 전체 동기화 및 인덱스 빌드를 트리거합니다.

* 온보딩 [카탈로그 데이터 동기화](install.md#synchronize-catalog-data)
* 속성 메타데이터 변경

예를 들어 `Use in Search` 속성 `color` 특성 `No` to `Yes` 속성 메타데이터를 로 변경합니다. `searchable=true`, 및 은 전체 동기화 및 재색인을 트리거합니다. 다음 속성 메타데이터는 변경된 경우 전체 동기화 및 재색인을 트리거합니다.

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### 스트리밍 제품 업데이트

다음 기간 동안 초기 색인이 작성되면 [온보딩](install.md#synchronize-catalog-data), 다음 증분 제품 업데이트는 지속적으로 동기화되고 다시 인덱싱됩니다.

* 카탈로그에 추가된 새 제품
* 제품 속성 값 변경

예를 들어 새 견본 값을 `color` 속성은 스트리밍 제품 업데이트로 처리됩니다.
스트리밍 업데이트 워크플로우:

1. 업데이트된 제품은 Adobe Commerce 인스턴스에서 카탈로그 서비스로 동기화됩니다.
1. 인덱싱 서비스는 카탈로그 서비스에서 제품 업데이트를 계속 찾습니다. 업데이트된 제품은 카탈로그 서비스에 도달하면 색인화됩니다.
1. 에서 제품 업데이트를 사용할 수 있는 데에는 최대 15분이 걸릴 수 있습니다. [!DNL Live Search].

## 클라이언트 검색

다음 [!DNL Live Search] API를 사용하면 클라이언트가 [storefront 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *제품 목록의 정렬에 사용됩니다.* to `Yes`. 이 설정은 테마에 따라 속성을 [정렬 기준](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) 카탈로그 페이지의 페이지 매김 제어. 최대 300개의 제품 속성을 [!DNL Live Search], 사용 [storefront 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) 검색 가능하고 필터링 가능한 제품입니다.
인덱스 메타데이터는 색인 파이프라인에 저장되며 검색 서비스에서 액세스할 수 있습니다.

![[!DNL Live Search] 인덱스 메타데이터 API 다이어그램](assets/index-metadata-api.svg)

### 정렬 가능한 속성 워크플로우

1. 클라이언트가 검색 서비스를 호출합니다.
1. 검색 서비스에서 Search Admin Service를 호출합니다.
1. 검색 서비스에서 인덱싱 파이프라인을 호출합니다.

## 모든 제품에 대해 인덱싱됨

이 목록의 필드 순서는 내보낸 제품 데이터의 일반적인 열 순서를 반영합니다.

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

구성 가능한 모든 제품에 대해 다음 필드가 인덱싱됩니다.

* `childrenSkus`
