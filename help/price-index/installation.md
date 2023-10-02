---
title: SaaS 가격 인덱싱 수동 설치
description: 이전 버전에 대한 SaaS 가격 색인화 설치
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: be0b8f4c26f11c31da3e5422bb4f4c4af10f2a00
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# SaaS 가격 인덱싱 수동 설치

SaaS 가격 색인화는 즉시 사용할 수 있습니다. [최신 버전](index.md#Requirements) 상거래 서비스.
최신 버전이 없고 Adobe Commerce 인스턴스에 대해 SaaS 가격 색인화를 활성화하려는 경우 이 미니 안내서를 사용하십시오.

## 전제 조건

* Adobe Commerce 2.4.4+
* 다음 SaaS 서비스 중 하나 이상이 설치되었습니다.

   * [카탈로그 서비스](../catalog-service/overview.md)
   * [라이브 검색](../live-search/guide-overview.md)
   * [제품 Recommendations](../product-recommendations/guide-overview.md)

## 필수 모듈 설치

설정에 따라 설치 프로세스가 약간 다를 수 있습니다.
새 피드와 지원 코드를 추가하는 확장이 있으며, 기본 가격 피드를 제거하는 확장이 있습니다.

1. 에 다음 모듈을 추가합니다. `composer.json` 파일:

   ```json
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
   ```

1. upgrade 명령을 실행합니다.

   ```bash
   bin/magento setup:upgrade
   ```

업그레이드 후 세 가지 새로운 피드를 사용할 수 있습니다.

* `prices` - 가격 데이터를 서비스에 게재할 책임
* `scopesCustomerGroup` - 고객 그룹을 서비스에 게재할 책임
* `scopesWebsite` - 서비스에 웹 사이트, 스토어 그룹 및 스토어 조회수 제공


1. &quot;일정에 따라 업데이트&quot; 모드로 설정하도록 새 피드를 구성합니다.

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. 새 피드를 다시 색인화합니다.

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

필요에 따라 위의 인덱서를 수동으로 실행합니다. 그렇지 않으면 표준 동기화 프로세스에서 데이터가 새로 고쳐집니다. 자세한 내용 [카탈로그 동기화](../landing/catalog-sync.md) 서비스.


Luma 및 Adobe Commerce 핵심 GraphQL 사용자는 [`Catalog Adapter`](catalog-adapter.md) Luma 및 Core GraphQl 호환성을 제공하고 Adobe Commerce 제품 가격 인덱서를 비활성화하는 확장입니다.

## 주의 사항

다음 이전 `103.0.0` 버전, SaaS 가격 색인화는 단순, 그룹, 가상, 구성 및 번들 동적 제품 유형을 지원합니다.
다운로드 가능, 기프트 카드 및 번들 고정 제품 유형에 대한 지원은 다음부터 제공됩니다. `magento/module-saas-price:103.0.0` 버전 및 지원되는 Commerce Services에서 즉시 사용할 수 있습니다.

새 피드를 와 수동으로 동기화해야 함 `resync` [CLI 명령](../landing/catalog-sync.md#resynccmdline). 그렇지 않으면 표준 동기화 프로세스에서 데이터가 새로 고쳐집니다. 에 대한 자세한 정보 보기 [카탈로그 동기화](../landing/catalog-sync.md) 프로세스.