---
title: "설치 [!DNL Live Search]"
description: "설치, 업데이트 및 제거 방법 알아보기 [!DNL Live Search] Adobe Commerce에서."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---

# 설치 [!DNL Live Search]

[!DNL Live Search] 는 Adobe 마켓플레이스에서 확장으로 설치됩니다. 다음 이후 [!DNL Live Search] 모듈(카탈로그 모듈을 종속성으로 사용)이 설치되고 구성된 경우 [!DNL Commerce] 는 SaaS 서비스와 검색 및 카탈로그 데이터 공유를 시작합니다. 이 시점에서 *관리자* 사용자는 검색 패싯, 동의어, 머천다이징 규칙을 설정, 사용자 지정 및 관리할 수 있습니다.

이 항목에서는 다음 작업을 수행하는 방법에 대한 지침을 제공합니다.

* 설치 [!DNL Live Search] (방법 1 및 2)
* [업데이트 [!DNL Live Search]](#update)
* [제거 [!DNL Live Search]](#uninstall)

## 시작하기 전에 {#before-you-begin}

다음을 수행합니다.

1. 다음을 확인합니다 [cron jobs](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 및 [인덱서](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 실행 중입니다.

1. 요구 사항에 맞는 온보딩 방법을 선택하고 지침을 따르십시오.

   * [방법 1](#method-1): 설치 [!DNL Elasticsearch]
   * [방법 2](#method-2): 다음으로 설치 [!DNL Elasticsearch] (다운타임 없음)

## 방법 1: Elasticsearch 없이 설치 {#method-1}

설치할 때 이 온보딩 방법이 권장됩니다 [!DNL Live Search] 대상:

* 신규 [!DNL Commerce] 설치
* 스테이징 환경

이 시나리오에서는 [!DNL Live Search] 서비스는 카탈로그의 모든 제품을 색인화합니다. 설치하는 동안 [!DNL Live Search] 모듈이 활성화되고 [!DNL Elasticsearch] 모듈이 비활성화되었습니다.

>[!NOTE]
>
>2023년 3월 현재 라이브 검색은 버전 2.4.4 이상만 지원합니다.

1. 없이 Adobe Commerce 2.4.4+ 설치 [!DNL Live Search].

1. 다운로드하려면 `live-search` package, 명령줄에서 다음을 실행합니다.

   ```bash
   composer require magento/live-search
   ```

   자세한 내용은 다음 목록을 참조하십시오 [!DNL Live Search] [종속성](#dependencies) 다음에 의해 캡처됩니다. [!DNL Composer].

1. 다음 명령을 실행하여 비활성화합니다. [!DNL Elasticsearch] 및 관련 모듈 및 설치 [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 데이터가 색인화되고 동기화되는 동안 상점에서는 검색 및 카테고리 찾아보기 작업을 사용할 수 없습니다. 카탈로그의 크기에 따라 프로세스는 최소 한 시간 정도 소요될 수 있습니다 `cron` 를 실행하여 데이터를 와 동기화합니다. [!DNL Live Search] 서비스.

1. 다음을 확인하십시오 [인덱서](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 이(가) (으)로 설정됩니다. `Update by Schedule`:

   * 제품 피드
   * 제품 변형 피드
   * 카탈로그 속성 피드

1. 구성 [API 키](#configure-api-keys) 카탈로그 데이터가 [동기화됨](#synchronize-catalog-data) 포함 [!DNL Live Search] 서비스.

1. 패싯을 상점 첫 화면의 필터로 사용하려면 [패싯](facets-add.md) 다음 내용에 따라 필요합니다. [요구 사항 충족](facets.md).

   다음 시간 후에 패싯을 추가할 수 있습니다. `cron` 속성 피드를 실행하고 속성 메타데이터를 내보냅니다.

1. 다음 이후 최소 1시간 대기 `cron` 를 실행하여 데이터를 동기화합니다. 그런 다음, [확인](#verify-export) 데이터를 내보냈습니다.

1. [테스트](#test-the-connection) 상점과의 연결.

## 방법 2: Elasticsearch과 함께 설치 {#method-2}

>[!IMPORTANT]
>
>2023년 8월의 Elasticsearch 7 지원 종료 발표로 인해 모든 Adobe Commerce 고객은 OpenSearch 2.x 검색 엔진으로 마이그레이션하는 것이 좋습니다. 제품 업그레이드 중 검색 엔진 마이그레이션에 대한 자세한 내용은 [OpenSearch로 마이그레이션](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration.html) 다음에서 _업그레이드 안내서_.

설치할 때 이 온보딩 방법이 권장됩니다 [!DNL Live Search] 끝:

* 기존 프로덕션 [!DNL Commerce] 설치

이 시나리오에서는 [!DNL Elasticsearch] 이(가) 다음을 수행하는 동안 상점의 검색 요청을 일시적으로 관리합니다. [!DNL Live Search] 서비스는 정상적인 상점 운영을 중단하지 않고 백그라운드에 있는 모든 제품을 색인화합니다. [!DNL Elasticsearch] 이(가) 비활성화되어 있고 [!DNL Live Search] 모든 카탈로그 데이터가 인덱싱되고 동기화된 후 활성화됩니다.

1. 다운로드하려면 `live-search` package, 명령줄에서 다음을 실행합니다.

   ```bash
   composer require magento/live-search
   ```

   자세한 내용은 다음 목록을 참조하십시오 [!DNL Live Search] [종속성](#live-search-dependencies) 다음에 의해 캡처됩니다. [!DNL Composer].

1. 다음 명령을 실행하여 를 일시적으로 비활성화합니다. [!DNL Live Search] storefront 검색 결과를 제공하는 모듈입니다.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 은(는) 다음 기간 동안 상점 첫 화면의 검색 요청을 계속 관리합니다. [!DNL Live Search] 서비스는 카탈로그 데이터를 동기화하고 백그라운드에서 제품을 인덱싱합니다.

1. 다음을 확인하십시오 [인덱서](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 이(가) (으)로 설정됩니다. `Update by Schedule`:

   * 제품 피드
   * 제품 변형 피드
   * 카탈로그 속성 피드

1. 구성 [API 키](#configure-api-keys) 카탈로그 데이터가 [동기화됨](#synchronize-catalog-data) 포함 [!DNL Live Search] 서비스.

1. 패싯을 상점 첫 화면의 필터로 사용하려면 [패싯](facets-add.md) 다음 내용에 따라 필요합니다. [요구 사항 충족](facets.md).

   다음 시간 후에 패싯을 추가할 수 있습니다. `cron` 는 제품 및 속성 피드를 실행하고 속성 메타데이터를 로 내보냅니다. [!DNL Live Search] 서비스.

1. 데이터가 인덱싱되고 동기화될 때까지 최소 한 시간 동안 기다립니다. 그런 다음 를 사용합니다. [GraphQL 플레이그라운드](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) 기본 쿼리를 사용하여 다음을 확인합니다.

   * 반환된 제품 수는 스토어 보기에 예상되는 값과 비슷합니다.
   * 패싯이 반환됩니다.

1. 활성화하려면 다음 명령을 실행하십시오 [!DNL Live Search] 모듈, 비활성화 [!DNL Elasticsearch], 및 실행 `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [테스트](#test-the-connection) 상점과의 연결.

## API 키 구성 {#configure-api-keys}

연결하려면 Adobe Commerce API 키 및 관련 개인 키가 필요합니다. [!DNL Live Search] Adobe Commerce 설치를 참조하십시오. API 키는 의 계정에서 생성되고 유지됩니다. [!DNL Commerce] 라이선스 소유자, 개발자 또는 SI와 공유할 수 있습니다. 그런 다음 개발자는 라이선스 소유자를 대신하여 SaaS Data Spaces를 만들고 관리할 수 있습니다.  이미 API 키 세트가 있는 경우 재생성할 필요가 없습니다.

### Adobe Commerce 라이선스 소유자

API 키 및 개인 키를 생성하려면 다음을 참조하십시오. [Commerce Services 커넥터](../landing/saas.md).

### Adobe Commerce 개발자 또는 SI

개발자 또는 SI는 다음에 설명된 대로 SaaS 데이터 공간을 구성합니다 *상거래 서비스* 섹션에 자세히 설명되어 있습니다. 다음에서 *관리자*, Commerce Services를에서 사용할 수 있습니다. *구성* SaaS 모듈이 설치된 경우 사이드바

## 카탈로그 데이터 동기화 {#synchronize-catalog-data}

[!DNL Live Search] 검색 작업에는 동기화된 제품 데이터가 필요하고 패싯을 구성하려면 동기화된 특성 데이터가 필요합니다. 제품 카탈로그와 카탈로그 서비스 간의 초기 동기화는 [!DNL Live Search] 는 첫 번째로 연결됩니다. 카탈로그의 설치 방법 및 크기에 따라 데이터를 내보내고 인덱싱하는 데 최대 30분이 소요될 수 있습니다 [!DNL Live Search]. 카탈로그 서비스와 동기화되고 공유되는 데이터 목록은 스키마에서 찾을 수 있으며, 스키마는에 정의되어 있습니다.

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 내보내기 확인 {#verify-export}

카탈로그 데이터가 Adobe Commerce 인스턴스에서 내보내지고 동기화되었는지 확인하려면 [!DNL Live Search]다음 표에서 항목을 찾습니다.

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

추가 도움말은 를 참조하십시오. [[!DNL Live Search] 카탈로그가 동기화되지 않음](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync.html) 지원 기술 자료.

### 향후 제품 업데이트

초기 동기화 후 점포 검색에서 증분 제품 업데이트를 사용할 수 있는 데 최대 15분이 걸릴 수 있습니다. 자세한 내용을 보려면 다음 위치로 이동하십시오. [색인화 - 스트리밍 제품 업데이트](indexing.md).

## 연결 테스트 {#test-connection}

상점 첫 화면에서 다음을 확인합니다.

* 다음 [!UICONTROL Search] 상자가 결과를 올바르게 반환합니다.
* 범주 찾아보기가 결과를 올바르게 반환합니다.
* 패싯은 검색 결과 페이지에서 필터로 사용할 수 있습니다.

모든 것이 올바르게 작동한다면, 축하합니다! [!DNL Live Search] 가 설치되었으며 연결되어 있고 사용할 준비가 되었습니다.

상점 앞에서 문제가 발생하면 `var/log/system.log` 서비스 측에서 API 통신 오류 또는 오류에 대한 파일입니다.

## 설치된 버전 확인

Live Search를 업데이트하기 전에 명령줄에서 다음을 실행하여 현재 설치된 Live Search 버전을 확인합니다.

```bash
composer show magento/module-live-search | grep version
```

## 업데이트 중 [!DNL Live Search] {#update}

업데이트하려면 [!DNL Live Search]를 클릭하고 명령줄에서 다음을 실행합니다.

```bash
composer update magento/live-search --with-dependencies
```

2.0.0에서 3.0.1로 등 주요 버전으로 업데이트하려면 프로젝트의 루트를 편집합니다 [!DNL Composer] `.json` 파일을 다음과 같이 지정합니다.

1. 현재 설치된 경우 `magento/live-search` 버전: `2.0.3` 또는 그 이하이며 버전으로 업그레이드 중입니다. `3.0.0` 또는 업그레이드 전에 다음 명령을 실행하십시오.

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
      "magento/live-search": "^3.0",
      ...
    }
   ```

1. **저장** `composer.json`. 그런 다음 명령줄에서 다음을 실행합니다.

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## 제거 중 [!DNL Live Search] {#uninstall}

제거하려면 [!DNL Live Search], 참조 [모듈 제거](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).

## [!DNL Live Search] 패키지 {#packages}

| 패키지 | 설명 |
|--- |--- |
| `module-live-search` | 판매자는 페이스팅, 동의어, 쿼리 규칙 등에 대한 검색 설정을 구성할 수 있으며, 읽기 전용 GraphQL 플레이그라운드에 액세스하여 *관리자*. |
| `module-live-search-adapter` | 상점 첫 화면에서 검색 요청을 다음으로 보냅니다. [!DNL Live Search] 서비스를 제공하고 상점에서 결과를 렌더링합니다. <br />- 카테고리 찾아보기 - 상점 첫 화면에서 요청을 라우팅합니다. [위쪽 탐색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-top.html) 검색 서비스에 연결합니다.<br />- 글로벌 검색 - (으)로부터 요청을 라우팅합니다. [빠른 검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 상점가의 오른쪽 상단에 있는 상자 [!DNL Live Search] 서비스. |
| `module-live-search-storefront-popover` | &quot;입력할 때 검색&quot; 팝오버는 표준 빠른 검색을 대체하며 상위 검색 결과의 데이터 및 썸네일을 반환합니다. |

## [!DNL Live Search] 종속성 {#dependencies}

다음 [!DNL Live Search] 종속성 캡처 대상: [!DNL Composer]:

| 종속성 | 설명 |
|--- |--- |
| 모듈 내보내기 | 다음 모듈은 카탈로그 데이터를 수집하고 동기화합니다.<br />`module-sass-catalog`<br />`module-sass-product-override`<br />`module-bundle-product-data-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter`<br />`module-product-override-data-exporter` |
| `data-services` | 상거래 서비스에 대한 연결을 구성하는 데 필요합니다. |
| `services-id` | 상거래 서비스에 대한 연결을 구성하는 데 필요합니다. |
