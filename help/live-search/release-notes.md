---
title: "[!DNL Live Search] 릴리스 정보"
description: "에 대한 최신 릴리스 정보 [!DNL Live Search] Adobe Commerce"
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 07d8a80cc8afe34cd0363a7705465b5565f5c196
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 1%

---

# [!DNL Live Search] 릴리스 정보

이러한 릴리스 노트에서는 최신 버전의 [!DNL Live Search] 다음을 포함합니다.

* ![새로 만들기](../assets/new.svg) - 새로운 기능
* ![수정](../assets/fix.svg) - 수정 사항 및 향상된 기능
* ![버그](../assets/bug.svg) - 알려진 문제

## [!DNL Live Search] 2.0.3

* Adobe Commerce(EE)와 호환됩니다. 2.4.x
* Adobe Commerce for Cloud(ECE)와 호환됩니다. 2.4.x
* 안정성: 안정적인

* ![새로 만들기](../assets/new.svg) - 이제 Live Search는 카테고리 권한, 공유 카탈로그 및 고객 그룹별 가격을 적용하여 B2B 기능을 지원합니다.

가맹점은 Live Search 확장 버전 >= 2.0.3을 업그레이드하여 이러한 기능에 액세스해야 합니다.

프로덕션에 투입하기 전에 업그레이드 및 테스트를 수행하는 것이 좋습니다. 테스트 환경 결과를 확인한 후 비스파이크 시간 동안 프로덕션 환경을 업그레이드하는 것이 좋습니다.

>[!NOTE]
>
>B2B 지원은 8월 9일부터 백엔드 서비스에서 단계적인 방식으로 추가되며, 마이그레이션은 8월 말까지 완료될 예정입니다. 라이브 검색 확장이 업그레이드되지 않은 경우 스토어는 정상적으로 계속 작동하지만 B2B 기능은 없습니다.

### 알려진 제한 사항 / 버그:

* ![버그](../assets/bug.svg) - 고객 그룹에 표시할 수 없는 제품에서 제안이 소싱됩니다.
* ![버그](../assets/bug.svg) - &quot;기본 공유 카탈로그&quot;에 추가되지 않은 경우 제품이 표시되지 않습니다.
* PWA Studio이 PWA Studio에 대한 지원을 추가할 때까지 B2B에 대한 라이브 검색을 사용할 수 없습니다.
* 제품 무시 및 제품 특성 피드에 관리자가 실행해야 하는 동기화 문제가 있을 수 있습니다 `bin/magento indexer:reset` 및 `bin/magento indexer:reindex` 올바르게 다시 동기화하려면 다음을 수행하십시오.
* 카탈로그 권한/공유 카탈로그/B2B 기능을 활성화하거나 비활성화하는 경우, `productOverrides` 인덱서가 업데이트되지 않고 &#39;valid&#39;로 잘못 표시됩니다. 사용 `bin/magento saas:resync --feed=productOverrides` 문제를 해결하기 위해

## [!DNL Live Search] 2.0

* Adobe Commerce(EE)와 호환됩니다. 2.4.x
* Adobe Commerce for Cloud(ECE)와 호환됩니다. 2.4.x
* 안정성: 안정적인

기존 [!DNL Live Search] 설치는 로 업그레이드해야 합니다. [!DNL Live Search] 2.0.0에서 다음과 같은 새로운 기능, 수정 사항 및 개선 사항을 활용할 수 있습니다.

* ![새로 만들기](../assets/new.svg) - [!DNL Live Search] 는 이제 Adobe Commerce 2.4.4를 실행하는 설치에 대해 PHP 8.1을 지원합니다.
* ![새로 만들기](../assets/new.svg) - `Magento_ElasticsearchCatalogPermissionsGraphQl` 모듈이 설치 중에 비활성화된 모듈 목록에 추가됩니다.
* ![새로 만들기](../assets/new.svg) - 사용 가능한 줄 수 [[!DNL storefront popover]](quick-tour.md) 는 *관리*.
* ![새로 만들기](../assets/new.svg) - 베타 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 호환성 [!DNL Live Search].
* ![새로 만들기](../assets/new.svg) - [!DNL Live Search] 설치 프로세스는 고급 프로세스 변경 사항으로 업데이트됩니다.
* ![수정](../assets/fix.svg) - [고급 검색](https://docs.magento.com/user-guide/catalog/search-advanced.html) 링크가 상점 바닥글에서 제거되었습니다.
* ![버그](../assets/bug.svg) - 다음 제품 속성은 [Magento GraphQL API](https://devdocs.magento.com/guides/v2.4/graphql) PWA 베타 릴리스와 관련하여 사용하는 경우: `description`, `name`, `short_description`
* ![버그](../assets/bug.svg) - PWA 베타 릴리스 [!DNL Live Search] 을 지원하지 않음 [이벤트 처리](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1

* Adobe Commerce(EE)와 호환됩니다. 2.4.x
* Adobe Commerce for Cloud(ECE)와 호환됩니다. 2.4.x
* 안정성: 안정적인

* ![수정](../assets/fix.svg) - [사용자 지정 가격 속성](https://docs.magento.com/user-guide/stores/attributes-input-types.html) 로 구성할 때 더 이상 오류를 반환하지 않습니다. [패싯]({% 링크 live-search/facets-add.md %}).
* ![수정](../assets/fix.svg) - 없을 때 오류가 발생하는 문제를 수정했습니다. [통화 기호](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`사용 가능합니다.
* ![수정](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) 이제 를 표시합니다. [특별 가격](https://docs.magento.com/user-guide/catalog/product-price-special.html) (최소 최종 가격) 사용 가능한 경우

## [!DNL Live Search] 1.3.0

* Adobe Commerce(EE)와 호환됩니다. 2.4.x
* Adobe Commerce for Cloud(ECE)와 호환됩니다. 2.4.x
* 안정성: 안정적인

* ![새로 만들기](../assets/new.svg) - [성능](performance.md) 보고 대시보드는 구매자들이 사용하는 검색어에 대한 통찰력을 제공합니다.
* ![새로 만들기](../assets/new.svg) - [!DNL Live Search] [Storefront 이벤트 SDK](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) 이벤트 게시 및 구독 서비스, 지표 등을 통해 일반 데이터 계층에 대한 액세스 권한을 제공합니다.
* ![수정](../assets/fix.svg) - [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) 새 항목 있음 `active` 의 클래스 `.search-autocomplete` 가시성을 제어하는 컨테이너입니다.
* ![수정](../assets/fix.svg) - 상점 앞에서 [검색어](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) 바닥글 링크가 제거되고 캐시가 비활성화되어 있습니다. [!DNL Live Search] 설치.
* ![버그](../assets/bug.svg) - 검색 어댑터용 패치는 중복 제품을 처리합니다.
* ![버그](../assets/bug.svg) - [!DNL Live Search] 지원 [단일 소스](https://docs.magento.com/user-guide/catalog/inventory-sources.html) (물리적) 복수(가상)가 있는 재고 위치 [주식](https://docs.magento.com/user-guide/catalog/inventory-stock.html). 현재 여러 인벤토리 소스가 지원되지 않습니다.

## [!DNL Live Search] 1.2.0

* Adobe Commerce(EE)와 호환됩니다. 2.4.x
* Adobe Commerce for Cloud(ECE)와 호환됩니다. 2.4.x
* 안정성: 안정적인

* ![새로 만들기](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) 쇼핑객이 검색 상자에 쿼리를 입력할 때 상위 검색 결과의 추천 제품 및 축소판 이미지를 표시합니다.
* ![새로 만들기](../assets/new.svg) - 상거래 *관리* 장기간 키보드 비활성화 시 세션 열기 유지
* ![새로 만들기](../assets/new.svg) - [!DNL Live Search] 은 온보딩 후 자동으로 활성화됩니다
* ![수정](../assets/fix.svg) - 초기 인덱싱 시간이 1시간 미만
* ![수정](../assets/fix.svg) - 제품 업데이트 시간이 거의 실시간으로 변경됨(설치 및 설정 후)
* ![수정](../assets/fix.svg) - 동의어 편집기의 정렬 가능한 열
* ![수정](../assets/fix.svg) - [!DNL Live Search] 검색 기준에 빈 정렬 순서 값이 포함되어 있으면 더 이상 오류가 발생하지 않습니다
* ![수정](../assets/fix.svg) - 속성 코드에 문자열 &quot;to&quot; 또는 &quot;from&quot;이 포함된 경우 범위 필터링이 더 이상 중단되지 않습니다.

## [!DNL Live Search] 1.1.0

* Adobe Commerce(EE)와 호환됩니다. 2.4.x
* Adobe Commerce for Cloud(ECE)와 호환됩니다. 2.4.x
* 안정성: 안정적인

* ![버그](../assets/bug.svg) - [!DNL Live Search] 서비스는 만 지원합니다 [기본 통화](https://docs.magento.com/user-guide/stores/currency-configuration.html) Adobe Commerce 설치 섹션에 자세히 설명되어 있습니다.
* ![버그](../assets/bug.svg) - 패싯을 추가할 때 을 설정할 때 제품 속성 피드가 올바르게 업데이트되지 않음 `Update on Save`. 이 문제를 방지하려면 다음 위치로 이동하십시오. [인덱스 관리](https://docs.magento.com/user-guide/system/index-management.html) 제품 속성 피드를 로 설정하고 `Update by Schedule`.
* ![버그](../assets/bug.svg) - [!DNL Live Search] 동의어는 스토어 보기별로 정의되지만, 현재 웹 사이트별로 저장되며, `environmentId` + `storeViewCode`. 따라서 Adobe Commerce 설치 내의 모든 웹 사이트 및 저장소 뷰는 동일한 동의어 집합을 공유합니다. 저장소 보기에 대해 가장 최근에 만든 동의어 세트가 우선합니다.
* ![버그](../assets/bug.svg) - 동의어 용어에 여러 단어가 포함된 경우 각 단어는 별도의 동의어로 처리됩니다. 예를 들어 &quot;time piece&quot;를 &quot;watch&quot;의 동의어로 정의하는 경우 &quot;time&quot;과 &quot;piece&quot;가 모두 시계의 동의어로 처리됩니다.

## 설명서

자세한 내용:

* [Adobe Commerce 개발자 설명서](https://devdocs.magento.com/)
* [Adobe Commerce 사용 안내서](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] Marketplace에서](https://marketplace.magento.com/magento-live-search.html)
