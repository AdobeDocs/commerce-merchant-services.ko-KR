---
title: "시작하기 [!DNL Live Search]"
description: "시스템 요구 사항 및 설치 단계 알아보기 [!DNL Live Search] Adobe Commerce에서."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: c66eab4ae0dda9a447a17f357ee0bb7364dc46ba
workflow-type: tm+mt
source-wordcount: '2405'
ht-degree: 0%

---

# 을(를) 통한 성공을 위한 설정 [!DNL Live Search]

Adobe Commerce [!DNL Live Search] 및 [[!DNL Catalog Service]](../catalog-service/guide-overview.md) 협력하여 성능이 뛰어나고 관련성이 있으며 직관적인 검색 솔루션을 제공하여 고객이 필요한 것을 신속하게 찾을 수 있도록 하십시오. 특히, [!DNL Catalog Service] 은 다음과 같은 SaaS 서비스를 위한 카탈로그 데이터를 표시합니다. [!DNL Live Search] 사용할 수 있습니다.

이 문서에서는 구현을 위한 단계별 지침을 제공합니다 [!DNL Live Search] 포함 [!DNL Catalog Service].

>[!IMPORTANT]
>
>사이트 검색과 관련하여 Adobe Commerce은 옵션을 제공합니다. 다음을 읽으십시오. [경계 및 제한](boundaries-limits.md) 구현하기 전에 [!DNL Live Search] 은(는) 귀하의 비즈니스 요구에 적합합니다.

## 대상자

이 문서는 Adobe Commerce 인스턴스 설치 및 구성을 담당하는 개발자나 시스템 통합자를 대상으로 합니다.

## 요구 사항

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## 지원되는 플랫폼

- ECE(Adobe Commerce on Cloud) : 2.4.4+
- Adobe Commerce 온-프레미스 (EE) : 2.4.4+

## 워크플로우 개요

높은 수준에서 온보딩 [!DNL Live Search] 은(는) 다음을 필요로 합니다.

![라이브 검색 워크플로](assets/livesearch-workflow.png)

## 1. 설치 [!DNL Live Search] 확장

[!DNL Live Search] 에서 확장으로 설치됩니다. [Adobe 마켓플레이스](https://commercemarketplace.adobe.com/magento-live-search.html) 에서 [작성기](https://getcomposer.org/). 설치 및 구성 후 [!DNL Live Search], ADOBE [!DNL Commerce] 는 SaaS 서비스와 검색 및 카탈로그 데이터 공유를 시작합니다. 이 시점에서 *관리자* 사용자는 검색 패싯, 동의어, 머천다이징 규칙을 설정, 사용자 지정 및 관리할 수 있습니다.

>[!NOTE]
>
>기준: [!DNL Live Search] 3.0.2, [!DNL Catalog Service] 확장은 와 번들로 제공됩니다. [!DNL Live Search] 설치.

1. 다음을 확인합니다 [cron jobs](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) 및 [인덱서](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 실행 중입니다.

   >[!IMPORTANT]
   >
   >2023년 8월의 Elasticsearch 7 지원 종료 발표로 인해 모든 Adobe Commerce 고객은 OpenSearch 2.x 검색 엔진으로 마이그레이션하는 것이 좋습니다. 제품 업그레이드 중에 검색 엔진을 마이그레이션하는 방법에 대한 자세한 내용은 [OpenSearch로 마이그레이션](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) 다음에서 _업그레이드 안내서_.

1. 다운로드 `live-search` 패키지 위치: [Adobe 마켓플레이스](https://commercemarketplace.adobe.com/magento-live-search.html).

1. 명령줄에서 다음을 실행합니다.

   ```bash
   composer require magento/live-search
   ```

   을(를) 추가하는 경우 [!DNL Live Search] 확장자: **신규** Adobe Commerce을 설치하려면 다음을 실행하여 비활성화하십시오. [!DNL OpenSearch] 및 관련 모듈 및 설치 [!DNL Live Search]. 그런 다음 4단계로 진행합니다.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   을(를) 추가하는 경우 [!DNL Live Search] 에 대한 확장 **기존** Adobe Commerce 설치를 위해 다음을 실행하여 를 일시적으로 비활성화합니다. [!DNL Live Search] storefront 검색 결과를 제공하는 모듈입니다. 그런 다음 4단계로 진행합니다.

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] 은(는) 다음 기간 동안 상점 첫 화면의 검색 요청을 계속 관리합니다. [!DNL Live Search] 서비스는 카탈로그 데이터를 동기화하고 백그라운드에서 제품을 인덱싱합니다.

1. 다음을 실행합니다.

   ```bash
   bin/magento setup:upgrade
   ```

1. 다음을 확인하십시오 [인덱서](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) &quot;일정별 업데이트&quot;로 설정된 경우:

   - 제품 피드
   - 제품 변형 피드
   - 카탈로그 속성 피드
   - 제품 가격 피드
   - 범위 웹 사이트 데이터 피드
   - Scopes 고객 그룹 데이터 피드
   - 카테고리 피드
   - 범주 권한 피드

1. 를 설치하는 경우 [!DNL Live Search] 새 Commerce 인스턴스에서 완료되었으며 [2. API 키 구성](#2-configure-api-keys) 섹션. 기존 Commerce 인스턴스에 라이브 검색을 설치하는 경우 다음 단계를 진행합니다.

1. 다음 명령을 실행하여 [!DNL Live Search] 확장, 비활성화 [!DNL OpenSearch], 및 실행 `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

## 2. API 키 구성

연결하려면 Adobe Commerce API 키 및 관련 개인 키가 필요합니다. [!DNL Live Search] Adobe Commerce 설치를 참조하십시오. API 키는 의 계정에서 생성되고 유지됩니다. [!DNL Commerce] 개발자 또는 시스템 통합자와 공유할 수 있는 라이선스 소유자입니다. 그런 다음 개발자는 라이선스 소유자를 대신하여 SaaS Data Spaces를 만들고 관리할 수 있습니다. 이미 API 키 세트가 있는 경우 재생성할 필요가 없습니다.

에서 API 키를 구성하는 방법을 알아봅니다. [Commerce Services 커넥터](../landing/saas.md) 기사.

## 3. 카탈로그 데이터 동기화 {#synchronize-catalog-data}

[!DNL Live Search] 카탈로그 데이터를 Adobe의 SaaS 인프라로 이동합니다. 데이터가 색인화되고 검색 결과가 이 색인에서 상점 앞으로 직접 전달됩니다. 크기와 복잡성에 따라 색인화는 30분에서 2시간 정도 소요될 수 있습니다.

카탈로그 데이터를 SaaS 서비스에 초기 동기화하려면 다음 명령을 순서대로 실행합니다.

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

이 명령을 실행하면 카탈로그 데이터가 SaaS 서비스에 처음 동기화됩니다.

>[!WARNING]
>
> 데이터가 색인화되고 동기화되는 동안 상점에서는 검색 및 카테고리 찾아보기 작업을 사용할 수 없습니다. 카탈로그의 크기에 따라 프로세스는 최소 한 시간 정도 소요될 수 있습니다 `cron` 를 실행하여 데이터를 SaaS 서비스에 동기화합니다.

### 동기화 진행 상황 모니터링

을 사용하여 동기화되고 공유되는 데이터를 볼 수 있습니다. [데이터 관리 대시보드](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). 이 대시보드는 상점 제품 데이터의 가용성에 대한 중요한 통찰력을 제공하여 구매자에게 즉시 표시되도록 합니다.

![데이터 관리 대시보드](assets/data-management-dashboard.png)

#### 향후 제품 업데이트

초기 동기화 후 점포 검색에서 증분 제품 업데이트를 사용할 수 있는 데 최대 15분이 걸릴 수 있습니다. 자세한 내용은 다음을 참조하십시오. [색인화 - 스트리밍 제품 업데이트](indexing.md).

## 4. 데이터를 내보냈는지 확인 {#verify-export}

카탈로그 데이터가 Adobe Commerce 인스턴스에서 내보내지고 동기화되었는지 확인하려면 [!DNL Live Search], 다음 두 가지 옵션이 있습니다.

- 다음 표에서 항목을 찾습니다.

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- 사용 [GraphQL 플레이그라운드](https://developer.adobe.com/commerce/services/graphql/live-search/) 기본 쿼리를 사용하여 다음을 확인합니다.

   - 반환된 제품 수는 스토어 보기에 예상되는 값과 비슷합니다.
   - Facet이 반환됩니다.

추가 도움말은 다음을 참조하십시오. [[!DNL Live Search] 카탈로그가 동기화되지 않음](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) 지원 기술 자료.

## 5. 데이터 구성

제품 데이터를 올바르게 구성하면 고객에게 좋은 검색 결과를 얻을 수 있습니다. 이 섹션에서는 제품 목록 위젯을 활성화하고 카테고리와 속성을 할당합니다.

### 제품 목록 위젯 활성화

설치 시 [!DNL Live Search] 4.0.0+, 제품 목록 위젯은 기본적으로 활성화됩니다. 위젯이 활성화되면 검색 결과 페이지 및 카테고리 찾아보기 제품 목록 페이지에 대해 다른 UI 구성 요소가 사용됩니다. 이 UI 구성 요소는 [카탈로그 서비스 API](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/): 응답 시간이 빨라집니다.

다음 항목이 있는 경우: [!DNL Live Search] 4.0.0+ 이전 버전에서는 제품 목록 위젯을 수동으로 활성화해야 합니다.

1. 다음에서 *관리자*&#x200B;로 이동합니다. **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 아래 **[!UICONTROL Live Search]**, 선택 **[!UICONTROL Storefront Features]**.
1. 설정 **[!UICONTROL Enable Product Listing Widgets]** 끝 `Yes`.

   ![제품 목록 위젯 활성화](assets/ls-admin-enable-widget.png)

이 구성을 변경하면 메시지가 표시됩니다 `Page cache is invalidated` 가 표시됩니다. 변경 사항을 저장하려면 Magento 캐시를 플러시해야 합니다.

1. 액세스 [캐시 관리](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) 다음 중 하나를 수행하여 페이지를 만듭니다.

   - 다음을 클릭합니다. **[!UICONTROL Cache Management]** 작업 영역 위의 메시지에 있는 링크.
   - 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. 다음 항목 선택 **구성** [!UICONTROL Cache Type] 및 클릭 **[!UICONTROL Flush Magento Cache]**.

   Storefront에 대한 변경 사항은 캐시를 플러시한 직후 입니다.

### 범주 할당

반환된 제품 [!DNL Live Search] 은(는) 다음에 할당되어야 합니다. [범주](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). 예를 들어 Luma에서 제품은 &quot;남성&quot;, &quot;여성&quot; 및 &quot;톱니바퀴&quot;와 같은 범주에 배치됩니다. 또한 하위 카테고리는 &quot;Tops&quot;, &quot;Bottom&quot; 및 &quot;Watches&quot;에 대해 설정됩니다. 이를 통해 필터링 시 세부기간을 향상시킬 수 있습니다.

### 검색 및 필터링 가능한 필드

제품이 할당됨 [속성](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes) 검색 및 필터링에 사용할 수 있습니다. 속성은 &quot;Color&quot;, &quot;Size&quot;, &quot;Material Type&quot;과 같은 것입니다. 이러한 속성을 사용하면 &quot;녹색 꼭대기&quot;를 찾을 수 있습니다. 각 제품에는에 정의된 많은 속성이 있을 수 있습니다. [!DNL Commerce] 관리자.

이러한 각 속성은 다음과 같이 정의할 수 있습니다. [&quot;검색 가능&quot;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 관리에서. &quot;검색 가능&quot;으로 설정된 경우 다음 방법으로 해당 속성을 검색할 수 있습니다. [!DNL Live Search].

[패싯](facets.md) 는에 정의된 제품 속성입니다. [!DNL Live Search] 필터링할 수 있습니다. 필터링 가능한 속성은 모두 패싯으로 설정할 수 있습니다. [!DNL Live Search] 그러나 한 번에 검색할 수 있는 패싯 수에 제한이 있습니다.

[동의어](synonyms.md) 는 사용자에게 올바른 제품을 안내하기 위해 정의할 수 있는 용어입니다. 바지를 찾는 사용자들은 &quot;바지&quot; 또는 &quot;바지&quot;를 타이핑할 수 있습니다. 이러한 검색어가 사용자에게 &quot;바지&quot; 결과를 가져오도록 동의어를 설정할 수 있습니다.

## 6. 연결 테스트 {#test-connection}

이제 SaaS에서 카탈로그 데이터를 사용하여 다음 시나리오에서 제품 데이터가 반환되는지 테스트하십시오.

- 다음 [!UICONTROL Search] 상자가 결과를 올바르게 반환합니다.
- 범주 찾아보기가 결과를 올바르게 반환합니다.
- 패싯은 검색 결과 페이지에서 필터로 사용할 수 있습니다

모든 것이 제대로 작동하면, [!DNL Live Search] 가 설치되었으며 연결되어 있고 사용할 준비가 되었습니다.

상점 앞에서 문제가 발생하면 `var/log/system.log` 서비스 측에서 API 통신 오류 또는 오류에 대한 파일입니다.

허용하려면 [!DNL Live Search] 방화벽을 통해 추가 `commerce.adobe.io` 허용 목록에 추가하다로

## 7. 상점 전면을 맞춤 설정합니다

을(를) 설치했습니다 [!DNL Live Search] 확장, 동기화, 유효성 검사 및 데이터 구성 이제 다음을 확인해야 합니다. [!DNL Live Search] 위젯은 스토어의 모양과 느낌을 따릅니다.

필요에 따라 사용자 정의 CSS 규칙을 정의하여 팝오버 및 PLP 위젯의 스타일을 지정할 수 있습니다. 다음을 참조하십시오 [팝오버 요소 스타일링](storefront-popover-styling.md) 및 [제품 목록 페이지 위젯](plp-styling.md).

위젯의 기능을 확장하려는 경우 각각의 소스 코드를 공용 리포지토리에서 사용할 수 있습니다.
이 시나리오에서는 사용자 자신의 요구 사항에 맞게 JavaScript를 사용자 지정한 다음 CDN에서 사용자 지정 코드를 호스팅할 수 있습니다. 이 사용자 지정 스크립트는 [!DNL Live Search] 서비스를 실행하고 일반적인 결과를 반환하여 위젯의 기능을 제어할 수 있습니다.

- [PLP 위젯 저장소](https://github.com/adobe/storefront-product-listing-page)
- [검색창 저장소](https://github.com/adobe/storefront-search-as-you-type)

## 업데이트 중 [!DNL Live Search] {#update}

Live Search를 업데이트하기 전에 명령줄에서 다음을 실행하여 설치된 Live Search 버전을 확인합니다.

```bash
composer show magento/module-live-search | grep version
```

업데이트하려면 [!DNL Live Search]를 클릭하고 명령줄에서 다음을 실행합니다.

```bash
composer update magento/live-search --with-dependencies
```

3.1.1에서 4.0.0으로 업데이트와 같은 주요 버전으로 업데이트하려면 프로젝트의 루트를 편집합니다 [!DNL Composer] `.json` 파일을 다음과 같이 지정합니다.

1. 현재 설치된 경우 `magento/live-search` 버전: `3.1.1` 또는 그 이하이며 버전으로 업그레이드 중입니다. `4.0.0` 또는 업그레이드 전에 다음 명령을 실행하십시오.

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   현재 설치된 항목에 대한 정보 `magento/live-search` version에서 다음 명령을 실행합니다.

   ```bash
   composer show magento/live-search
   ```

1. 루트 열기 `composer.json` 파일 및 검색 `magento/live-search`.

1. 다음에서 `require` 섹션에서 버전 번호를 다음과 같이 업데이트합니다.

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. 저장 `composer.json`. 그런 다음 명령줄에서 다음을 실행합니다.

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## 제거 중 [!DNL Live Search] {#uninstall}

제거하려면 [!DNL Live Search], 참조 [모듈 제거](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] 패키지 {#packages}

다음 [!DNL Live Search] 확장은 다음 패키지로 구성됩니다.

| 패키지 | 설명 |
|--- |--- |
| `module-live-search` | 판매자가 페이스팅, 동의어, 쿼리 규칙 등에 대한 검색 설정을 구성할 수 있도록 하고, 읽기 전용 GraphQL 플레이그라운드에 액세스하여 *관리자*. |
| `module-live-search-adapter` | 상점 첫 화면에서 검색 요청을 다음으로 보냅니다. [!DNL Live Search] 서비스를 제공하고 상점에서 결과를 렌더링합니다. <br />- 카테고리 찾아보기 - 상점 첫 화면에서 요청을 라우팅합니다. [위쪽 탐색](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) 검색 서비스에 연결합니다.<br />- 글로벌 검색 - (으)로부터 요청을 라우팅합니다. [빠른 검색](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) 상점가의 오른쪽 상단에 있는 상자 [!DNL Live Search] 서비스. |
| `module-live-search-storefront-popover` | &quot;입력할 때 검색&quot; 팝오버는 표준 빠른 검색을 대체하며 상위 검색 결과의 데이터 및 썸네일을 반환합니다. |

## [!DNL Live Search] 종속성 {#dependencies}

다음 [!DNL Live Search] 종속성 캡처 대상: [!DNL Composer].

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## 고급 개념

다음 섹션에서는 사용 시 더 많은 고급 항목을 제공합니다 [!DNL Live Search] 및 [!DNL Catalog Service].

### 엔드포인트

[!DNL Live Search] 은 의 끝점을 통해 통신합니다. `https://catalog-service.adobe.io/graphql`.

다음으로: [!DNL Live Search] 이(가) 전체 제품 데이터베이스에 액세스할 수 없습니다. [!DNL Live Search] GraphQL 및 Commerce 코어 GraphQL에는 전체 패리티가 없습니다.

SaaS API(특히 카탈로그 서비스 끝점)를 직접 호출하는 것이 좋습니다.

- Commerce 데이터베이스/Graphql 프로세스를 건너뛰어 성능 향상 및 프로세서 로드 감소
- 다음을 활용하십시오. [!DNL Catalog Service] 호출할 페더레이션 [!DNL Live Search], [!DNL Catalog Service], 및 [!DNL Product Recommendations] 단일 엔드포인트에서

일부 사용 사례의 경우 [!DNL Catalog Service] 제품 세부 사항 및 유사 사례에 대한 정보. 다음을 참조하십시오 [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) 추가 정보.

사용자 지정 Headless 구현이 있는 경우 [!DNL Live Search] 참조 구현:

- [PLP 위젯](https://github.com/adobe/storefront-product-listing-page)
- [라이브 검색 필드](https://github.com/adobe/storefront-search-as-you-type)

Luma의 검색 어댑터 또는 위젯 또는 AEM CIF 위젯과 같은 기본 구성 요소를 사용하지 않는 경우 이벤트(Intelligent Merchandising 및 성능 지표를 위해 Adobe Sensei에 제공하는 클릭스트림 데이터)가 즉시 작동하지 않으며 Headless 이벤트를 구현하기 위해 사용자 정의 개발이 필요합니다.

의 최신 버전 [!DNL Live Search] 이미 사용 중 [!DNL Catalog Service].

### 언어 지원

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
| 폴란드어 | 폴란드 | pl_PL | pl_PL |
| 포르투갈어 | 브라질 | pt_BR | pt_BR |
| 포르투갈어 | 포르투갈 | pt_PT | pt_PT |
| 루마니아어 | 루마니아 | ro_RO | ro_RO |
| 러시아어 | 러시아 | ru_RU | ru_RU |
| 스웨덴어 | 스웨덴 | sv_SE | sv_SE |
| 태국인 | 태국 | th_TH | th_TH |
| 터키어 | 터키 | tr_TR | tr_TR |
| 중국어 | 중국 | zh_CN | zh_Hans_CN |
| 중국어 | 대만 | zh_TW | zh_Hant_TW |

위젯이 Commerce 관리 언어 설정을 감지하면(_스토어_ > 설정 > _구성_ > _일반_ > 국가 옵션) 지원되는 언어와 일치하면 기본적으로 해당 언어로 설정됩니다. 그렇지 않은 경우 위젯은 기본적으로 영어로 설정됩니다.

관리자는 의 언어를 설정할 수도 있습니다. [검색 색인](settings.md#language): 더 나은 검색 결과를 보장해 줍니다.

### 위젯 코드 저장소

제품 목록 페이지 위젯 및 라이브 검색 필드 위젯은 모두 github 저장소에서 다운로드할 수 있습니다.

이를 통해 개발자는 기능과 스타일을 완전히 맞춤화할 수 있습니다. 이러한 사용자는 코드 자체를 호스팅하면서도 [!DNL Live Search] 서비스.

- [PLP 위젯](https://github.com/adobe/storefront-product-listing-page)
- [검색 창](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] 지원 [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Commerce(이전에는 MSI라고 함)의 기능. 전체 지원을 활성화하려면 다음을 수행해야 합니다 [업데이트](install.md#update) 종속성 모듈 `commerce-data-export` 버전 102.2.0+에

[!DNL Live Search] Inventory management 내에서 제품을 사용할 수 있는지 여부를 나타내는 부울을 반환하지만, 재고가 있는 소스에 대한 정보는 포함하지 않습니다.

### 가격 인덱서

라이브 검색 고객은 새 [SaaS 가격 인덱서](../price-index/price-indexing.md)를 통해 가격 변경 업데이트 및 동기화 시간이 빨라집니다.

### 가격 지원

라이브 검색 위젯은 Adobe Commerce에서 지원하는 대부분의 가격 유형을 지원하지만 일부 가격 유형은 지원하지 않습니다.

현재 기본 가격이 지원됩니다. 지원되지 않는 고급 가격은 다음과 같습니다.

- 비용
- 최소 광고 가격

다음 항목 보기 [API 메쉬](../catalog-service/mesh.md) 보다 복잡한 가격 계산을 위해.

가격 형식은 Commerce 인스턴스 내의 로케일 구성 설정을 지원합니다. *스토어* > 설정 > *구성* > 일반 > *일반* > 로컬 옵션 > 로케일.

### 헤드리스 상점 첫 화면 지원

선택적으로 다음을 설치해야 할 수 있습니다. `module-data-services-graphql` 상점 행동 데이터 수집에 필요한 필드를 포함하도록 애플리케이션의 기존 GraphQL 범위를 확장하는 모듈입니다.

```bash
composer require magento/module-data-services-graphql
```

이 모듈은 GraphQL 쿼리에 추가 컨텍스트를 추가합니다.

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### PWA 지원

[!DNL Live Search] 은 PWA Studio에서 작동하지만 다른 Commerce 구현과 비교하여 약간의 차이가 있을 수 있습니다. 검색 및 제품 목록 페이지와 같은 기본 기능은 Venia에서 작동하지만 Graphql의 일부 순열이 제대로 작동하지 않을 수 있습니다. 성능 차이도 있을 수 있습니다.

- 의 현재 PWA 구현 [!DNL Live Search] 검색 결과를 반환하는 데 보다 많은 처리 시간이 필요합니다. [!DNL Live Search] 기본 Commerce 상점 포함.
- [!DNL Live Search] PWA에서 을(를) 지원하지 않습니다. [이벤트 처리](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). 따라서 검색 보고나 지능형 머천다이징도 작동합니다.
- 바로 필터링 `description`, `name`, `short_description` 과 함께 사용할 경우 GraphQL에서 지원되지 않음 [PWA](https://developer.adobe.com/commerce/pwa-studio/), 하지만 더 일반적인 필터와 함께 반환됩니다.

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

### 쿠키

[!DNL Live Search] 는 기본 기능의 일부로 사용자 상호 작용 데이터를 수집하며 쿠키는 이 데이터를 저장하는 데 사용됩니다. 사용자 정보를 수집할 때 사용자는 쿠키를 저장하는 데 동의해야 합니다. [!DNL Live Search] 및 [!DNL Product Recommendations] 데이터 스트림을 공유하여 동일한 쿠키 메커니즘을 공유합니다. 자세한 내용 보기 [쿠키 제한 처리](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
