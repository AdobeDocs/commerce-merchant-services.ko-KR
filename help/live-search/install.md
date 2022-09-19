---
title: "설치 [!DNL Live Search]"
description: "설치, 업데이트 및 제거 방법을 알아봅니다. [!DNL Live Search] Adobe Commerce"
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: a17c9ef193394d86f5439f900ebba3dd68d33b45
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 0%

---

# 설치 [!DNL Live Search]

Live Search는 Marketplace에서 확장으로 설치됩니다. 다음 이후 [!DNL Live Search] 모듈(카탈로그 모듈을 종속성으로 사용)이 설치 및 구성되고 [!DNL Commerce] SaaS 서비스와 검색 및 카탈로그 데이터 공유를 시작합니다. 이 시점에서 *관리* 사용자는 검색 패싯, 동의어 및 머천다이징 규칙을 설정, 사용자 지정 및 관리할 수 있습니다.

이 항목에서는 다음을 수행하는 지침을 제공합니다.

* 설치 [!DNL Live Search] (방법 1 및 2)
* [업데이트 [!DNL Live Search]](#update)
* [제거 [!DNL Live Search]](#uninstall)

## 시작하기 전에 {#before-you-begin}

다음을 수행합니다.

1. 확인 [직장](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) 및 [인덱서](https://docs.magento.com/user-guide/system/index-management.html) 실행 중입니다.

1. 요구 사항을 충족하는 온보딩 방법을 선택하고 지침을 따르십시오.

   * [방법 1](#method-1): 설치 안 함 [!DNL Elasticsearch]
   * [방법 2](#method-2): 설치 [!DNL Elasticsearch] (다운타임 없음)

## 방법 1: Elasticsearch 없이 설치 {#method-1}

이 온보딩 방법은 설치할 때 권장됩니다 [!DNL Live Search] 아래와 같이 변경하는 것을 의미합니다.

* 새로 만들기 [!DNL Commerce] 설치
* 스테이징 환경

이 시나리오에서는 [!DNL Live Search] 서비스는 카탈로그의 모든 제품을 인덱싱합니다. 설치하는 동안 [!DNL Live Search] 모듈이 활성화되어 있고 [!DNL Elasticsearch] 모듈이 비활성화되어 있습니다.

>[!TIP]
>
>입력 오류가 발생하지 않도록 하려면 코드 상자의 오른쪽 맨 위를 마우스로 가리킨 다음 [!UICONTROL **복사**] 를 연결하고 명령줄에 붙여 넣습니다.

1. 없이 Adobe Commerce 2.4.x 설치 [!DNL Live Search].

1. 를 다운로드하려면 `live-search` package에서 다음 명령을 실행합니다.

   ```bash
   composer require magento/live-search
   ```

   자세한 내용은 [!DNL Live Search] [종속성](#dependencies) 에 의해 [!DNL Composer].

1. 다음 명령을 실행하여 비활성화하십시오 [!DNL Elasticsearch] 및 관련 모듈 및 설치 [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > 데이터가 색인화되고 동기화되는 동안 검색 및 범주 찾아보기 작업은 상점 전면에서 사용할 수 없습니다. 카탈로그의 크기에 따라 프로세스가 시간에서 최소 1시간이 소요될 수 있습니다 `cron` 를 실행하여 데이터 동기화 [!DNL Live Search] 서비스.

1. 다음을 확인합니다 [인덱서](https://docs.magento.com/user-guide/system/index-management.html) 가 로 설정되어 있습니다. `Update by Schedule`:

   * 제품 피드
   * 제품 변형 피드
   * 카탈로그 속성 피드

1. 구성 [API 키](#configure-api-keys) 카탈로그 데이터가 [동기화](#synchronize-catalog-data) with [!DNL Live Search] 서비스.

1. 패싯을 스토어에 필터로 사용할 수 있도록 하려면 [패싯](facets-add.md) 당신이 필요로 하는 것은 [계면 요구 사항](facets.md).

   다음에 패싯을 추가할 수 있습니다 `cron` 속성 피드를 실행하고 속성 메타데이터를 내보냅니다.

1. 적어도 한 시간 후에 대기 `cron` 를 실행하여 데이터를 동기화합니다. 그럼, [확인](#verify-export) 데이터가 내보내졌음.

1. [테스트](#test-the-connection) 상점 전면의 연결.

## 방법 2: Elasticsearch으로 설치 {#method-2}

이 온보딩 방법은 설치할 때 권장됩니다 [!DNL Live Search] 변환:

* 기존 프로덕션 [!DNL Commerce] 설치

이 시나리오에서는 [!DNL Elasticsearch] 가 [!DNL Live Search] 서비스는 일반 상점 작업에 중단 없이 백그라운드에 있는 모든 제품을 색인화합니다. [!DNL Elasticsearch] 이 비활성화되어 있고 [!DNL Live Search] 모든 카탈로그 데이터가 인덱싱되고 동기화된 후에 활성화됩니다.

>[!TIP]
>
>입력 오류가 발생하지 않도록 하려면 코드 상자의 오른쪽 맨 위를 마우스로 가리킨 다음 [!UICONTROL **복사**] 를 연결하고 명령줄에 붙여 넣습니다.

1. 를 다운로드하려면 `live-search` package에서 다음 명령을 실행합니다.

   ```bash
   composer require magento/live-search
   ```

   자세한 내용은 [!DNL Live Search] [종속성](#live-search-dependencies) 에 의해 [!DNL Composer].

1. 다음 명령을 실행하여 일시적으로 [!DNL Live Search] storefront 검색 결과를 제공하는 모듈입니다.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] 는 [!DNL Live Search] 서비스는 카탈로그 데이터와 인덱스 제품을 백그라운드에서 동기화합니다.

1. 다음을 확인합니다 [인덱서](https://docs.magento.com/user-guide/system/index-management.html) 가 로 설정되어 있습니다. `Update by Schedule`:

   * 제품 피드
   * 제품 변형 피드
   * 카탈로그 속성 피드

1. 구성 [API 키](#configure-api-keys) 카탈로그 데이터가 [동기화](#synchronize-catalog-data) with [!DNL Live Search] 서비스.

1. 패싯을 스토어에 필터로 사용할 수 있도록 하려면 [패싯](facets-add.md) 당신이 필요로 하는 것은 [계면 요구 사항](facets.md).

   다음에 패싯을 추가할 수 있습니다 `cron` 제품 및 속성 피드를 실행하고 속성 메타데이터를 로 내보냅니다. [!DNL Live Search] 서비스.

1. 데이터가 인덱싱되고 동기화될 때까지 최소 1시간 대기합니다. 그런 다음 [GraphQL 놀이터](https://devdocs.magento.com/live-search/graphql-support.html) 기본 쿼리를 사용하여 다음을 확인합니다.

   * 반환된 제품 개수가 저장소 보기에 대해 예상한 개수와 일치합니다.
   * 패싯이 반환됩니다.

1. 다음 명령을 실행하여 [!DNL Live Search] 모듈, 비활성화 [!DNL Elasticsearch], 및 실행 `setup`.

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

1. [테스트](#test-the-connection) 상점 전면의 연결.

## API 키 구성 {#configure-api-keys}

연결하려면 Adobe Commerce API 키 및 관련 개인 키가 필요합니다 [!DNL Live Search] Adobe Commerce을 설치하는 동안 변경되었습니다. API 키는 [!DNL Commerce] 개발자 또는 SI와 공유할 수 있는 라이센스 소지자. 그런 다음 개발자는 라이센스 보유자를 대신하여 SaaS 데이터 공간을 만들고 관리할 수 있습니다.  이미 API 키 세트가 있는 경우 다시 생성할 필요가 없습니다.

### Adobe Commerce 라이선스 소유자

API 키 및 개인 키를 생성하려면 다음을 참조하십시오 [Commerce Services 커넥터](../landing/saas.md).

### Adobe Commerce 개발자 또는 SI

개발자 또는 SI는 *상거래 서비스* 섹션에 나열된 상태로 남아 있습니다. 에서 *관리*, Commerce Services는 *구성* SaaS 모듈이 설치된 경우 사이드바

## 카탈로그 데이터 동기화 {#synchronize-catalog-data}

[!DNL Live Search] 검색 작업을 위해 동기화된 제품 데이터와 패싯을 구성하려면 동기화된 속성 데이터가 필요합니다. 제품 카탈로그와 카탈로그 서비스 간의 초기 동기화는 [!DNL Live Search] 가 처음 연결되었습니다. 카탈로그의 설치 방법 및 크기에 따라 데이터를 내보내고 인덱싱하는 데 최대 8시간이 걸릴 수 있습니다. [!DNL Live Search]. 카탈로그 서비스와 동기화되고 공유되는 데이터 목록은 다음 스키마에 정의되어 있습니다.

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### 내보내기 확인 {#verify-export}

카탈로그 데이터를 Adobe Commerce 인스턴스에서 내보내고 을 동기화했는지 확인하려면 [!DNL Live Search]에서는 다음 표에서 항목을 찾습니다.

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

자세한 도움말은 [[!DNL Live Search] 카탈로그가 동기화되지 않음](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) 지원 기술 자료에서

### 향후 제품 업데이트

초기 동기화 후 증분 제품 업데이트를 상점 검색에 사용할 수 있게 되는 데 최대 15분이 걸릴 수 있습니다. 자세한 내용을 보려면 [색인 지정 - 스트리밍 제품 업데이트](indexing.md).

## 연결 테스트 {#test-connection}

스토어에서 다음을 확인합니다.

* 다음 [!UICONTROL Search] 결과 반환
* 카테고리 찾아보기가 결과를 올바르게 반환합니다
* 패싯은 검색 결과 페이지에서 필터로 사용할 수 있습니다

모든 것이 제대로 작동한다면, 축하합니다! [!DNL Live Search] 설치, 연결 및 사용 준비가 되었습니다.

상점 앞에서 문제가 발생하면 `var/log/system.log` 파일 을 참조하십시오.

## 설치된 버전 확인

라이브 검색을 업데이트하기 전에 명령줄에서 다음을 실행하여 현재 설치된 라이브 검색 버전을 확인합니다.

```bash
composer show magento/module-live-search | grep version
```

## 업데이트 중 [!DNL Live Search] {#update}

업데이트하려면 [!DNL Live Search]명령줄에서 다음을 실행합니다.

```bash
composer update magento/live-search --with-dependencies
```

1.0.0에서 2.0.0과 같은 주요 버전으로 업데이트하려면 프로젝트의 루트를 편집하십시오 [!DNL Composer] `.json` 파일:

1. 현재 설치되어 있는 경우 `magento/live-search` version `1.3.1` 또는 아래에 있는 를 버전으로 업그레이드할 수 있습니다 `2.0.0` 업그레이드 전에 다음 명령을 실행하십시오.

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   현재 설치된 항목에 대한 자세한 정보 `magento/live-search` version, 다음 명령을 실행합니다.

   ```bash
   composer show magento/live-search
   ```

1. 루트 열기 `composer.json` 파일 및 검색 `magento/live-search`.

1. 에서 `require` 섹션에서 버전 번호를 다음과 같이 업데이트합니다.

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **저장** `composer.json`. 그런 다음 명령줄에서 다음을 실행합니다.

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## 제거 [!DNL Live Search] {#uninstall}

제거하려면 [!DNL Live Search]를 참조하려면 [모듈 제거](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).

## [!DNL Live Search] 패키지 {#packages}

| 패키지 | 설명 |
|--- |--- |
| `module-live-search` | 상인들은 계면, 동의어, 쿼리 규칙 등에 대한 검색 설정을 구성할 수 있으며, 읽기 전용 GraphQL 놀이터에 액세스하여 *관리*. |
| `module-live-search-adapter` | 스토어프론트에서 다음으로 검색 요청을 라우팅합니다. [!DNL Live Search] 서비스를 제공하고 결과를 상점 앞에 렌더링합니다. <br />- 범주 찾아보기 - 상점 전면의 요청을 라우팅합니다. [위쪽 탐색](https://docs.magento.com/user-guide/catalog/navigation-top.html) 를 클릭합니다.<br />- 전역 검색 - [빠른 검색](https://docs.magento.com/user-guide/catalog/search-quick.html) 상점 오른쪽 상단의 상자 [!DNL Live Search] 서비스. |
| `module-live-search-storefront-popover` | &quot;입력할 때 검색&quot; 팝오버는 표준 빠른 검색을 대체하고 상위 검색 결과의 동적 제품 제안 및 미리 보기를 반환합니다. |

## [!DNL Live Search] 종속성 {#dependencies}

다음 [!DNL Live Search] 종속성은 [!DNL Composer]:

| 종속성 | 설명 |
|--- |--- |
| 모듈 내보내기 | 다음 모듈은 카탈로그 데이터를 수집하고 동기화합니다.<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Commerce Services에 대한 연결을 구성하는 데 필요합니다. |
| `module-services-id` | Commerce Services에 대한 연결을 구성하는 데 필요합니다. |
