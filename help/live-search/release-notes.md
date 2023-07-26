---
title: '''[!DNL Live Search] 릴리스 정보'
description: "의 최신 릴리스 정보 [!DNL Live Search] Adobe Commerce에서."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: 0c8d9498ea7a30a99f834694ef8a865ad24466ab
workflow-type: tm+mt
source-wordcount: '1277'
ht-degree: 0%

---

# [!DNL Live Search] 릴리스 정보

이 릴리스 노트는 최신 버전의 [!DNL Live Search].
현재 주요 릴리스 버전에 대한 지원이 제공됩니다. 이전 버전에 대한 릴리스 노트는 참조를 위해 제공됩니다.
업데이트에는 다음이 포함됩니다.

![신규](../assets/new.svg) 새로운 기능
![수정](../assets/fix.svg) 수정 사항 및 향상된 기능
![버그](../assets/bug.svg) 알려진 문제


_2023년 6월 13일_

![신규](../assets/new.svg) 이제 라이브 검색에서 5개 더 지원 [구성 값](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/configuration.html).
![수정](../assets/fix.svg) 따옴표나 아포스트로피와 같은 일부 문자로 인해 순위 문제가 발생하는 문제가 해결되었습니다. 리인덱싱하면 이러한 문제가 해결됩니다.

_2023년 4월 25일_

![신규](../assets/new.svg) 이제 라이브 검색 고객이 새로운 기능을 이용할 수 있습니다 [SaaS 가격 인덱서](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_2023년 3월 14일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

### 새로운 기능

* 규칙 미리보기의 제품 항목 카드
* [제품 목록 페이지 위젯](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [범주 필터링 옵션](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* 끌어서 놓아 고정 이벤트를 만드는 기능이 추가되었습니다.
* 새 고정 작업:
   * 위치에 고정 - 한 번의 클릭으로 고정 이벤트를 만들기 위한 고정 단추
   * 맨 위에 고정 - 제품을 첫 번째 위치에 배치합니다.
   * 맨 아래에 고정 - 제품을 결과의 맨 아래에 배치합니다.
   * 한 번의 클릭으로 이벤트 고정 해제
* [규칙에 대한 지능형 순위](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### 업데이트

* 이제 규칙 구성에서 위치를 고유하게 자동으로 정렬합니다.
* 기존 이벤트를 삭제하면 이제 미리보기가 업데이트됩니다.
* 이벤트가 없는 규칙은 저장할 수 있습니다.
* 얼굴 &quot;유형 선택&quot; 선택기 제거
* 저장되지 않은 규칙에 대해 새 &quot;편집 중&quot; 상태 추가됨

### 수정 사항

* 저장하는 동안 완료되지 않은 이벤트가 있을 때 서버 오류를 수정했습니다.
* 여러 이벤트가 있는 경우 특정 이벤트를 올바르게 삭제하는 문제가 해결되었습니다.
* 새 이벤트가 추가되었을 때 기존 규칙 이벤트가 업데이트되지 않는 문제를 해결했습니다
* 세부 정보에서 두 번째 &quot;편집&quot; 클릭을 수정했습니다. [!DNL Live Search] 다시 로드해야 하는 페이지
* 동의어: 사용자가 입력을 클릭했을 때 필드에 포커스를 반환할 수 없는 문제가 해결되었습니다.
* 기타 사소한 버그 수정 및 성능 업데이트


* ![버그](../assets/bug.svg) - &quot;추천&quot;별 순위는 라이브 검색 위젯 내에서만 지원됩니다. 기본 Luma 및 PWA 검색 기능에서는 지원되지 않습니다.
* ![버그](../assets/bug.svg) - 사용자 지정 가격 속성 패싯이 Luma에서 올바르게 렌더링되지 않지만 API가 해당 패싯을 제대로 필터링합니다.

판매자는 다음을 업그레이드해야 합니다. [!DNL Live Search] 확장 버전 >= 3.0.1 을 사용하여 이러한 기능에 액세스할 수 있습니다.

프로덕션으로 푸시하기 전에 업그레이드 및 테스트하는 것이 좋습니다. 테스트 환경 결과를 확인한 후 사용량이 적은 시간 동안 프로덕션 환경을 업그레이드하는 것이 좋습니다.

## 이전 버전

+++2.0.5 및 이전

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

* ![수정](../assets/fix.svg) - 네트워크 문제로 인해 SDK 리소스를 사용할 수 없으면 라이브 검색에서 오류가 발생합니다. 이 버그는 수정되었습니다.

이러한 기능에 액세스하려면 Live Search 확장 버전 >= 2.0.5를 업그레이드해야 합니다.

프로덕션으로 푸시하기 전에 업그레이드 및 테스트하는 것이 좋습니다. 테스트 환경 결과를 확인한 후 사용량이 적은 시간 동안 프로덕션 환경을 업그레이드하는 것이 좋습니다.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![신규](../assets/new.svg) 이제 라이브 검색은 관리자의 &#39;재고 부족 제품 표시&#39; 설정에 의한 필터링을 지원합니다. &#39;재고 부족 제품 표시&#39;가 false로 설정된 경우 `inStock = true` 가 필터에 추가됩니다.
![수정](../assets/fix.svg) 성능을 개선하기 위해 &#39;제안&#39; 블록이 라이브 검색 팝업에서 제거되었습니다. 기능을 교체하려는 경우 데이터는 여전히 GraphQL을 통해 전달됩니다.
![수정](../assets/fix.svg) `categories` 및 `categoryPath` 을(를) 대체했습니다. `categoryIds` 카테고리 필터링에 사용됩니다. 자세한 내용 [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) 주제.
![수정](../assets/fix.svg) 이전에는 B2B 회사에 연결된 사용자가 검색을 수행할 때 잘못된 고객 그룹 코드를 받았습니다. 이제 Live Search에서 올바른 값을 반환합니다.
![수정](../assets/fix.svg) 이전에는 존재하지 않는 용어를 검색할 때 라이브 검색에서 오류가 반환되었습니다. 해당 버그는 이제 수정되었습니다.

판매자는 다음을 업그레이드해야 합니다. [!DNL Live Search] 확장 버전 >= 2.0.4 를 사용하여 이러한 기능에 액세스할 수 있습니다.

사용자는 프로덕션으로 푸시하기 전에 업그레이드 및 테스트하는 것이 좋습니다. 테스트 환경 결과를 확인한 후 사용량이 적은 시간 동안 프로덕션 환경을 업그레이드하는 것이 좋습니다.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![신규](../assets/new.svg) 이제 Live Search는 범주 권한, 공유 카탈로그 및 고객 그룹별 가격을 준수하여 B2B 기능을 지원합니다.

판매자는 다음을 업그레이드해야 합니다. [!DNL Live Search] 확장 버전 >= 2.0.3 을 사용하여 이러한 기능에 액세스할 수 있습니다.

사용자는 프로덕션으로 푸시하기 전에 업그레이드 및 테스트하는 것이 좋습니다. 테스트 환경 결과를 확인한 후 사용량이 적은 시간 동안 프로덕션 환경을 업그레이드하는 것이 좋습니다.

### [!DNL Live Search] 2.0 {#20}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

기존 항목 [!DNL Live Search] 설치를으로 업그레이드해야 합니다. [!DNL Live Search] 2.0.0을 통해 다음과 같은 새로운 기능, 수정 사항 및 개선 사항을 활용할 수 있습니다.

![신규](../assets/new.svg) [!DNL Live Search] 는 이제 Adobe Commerce 2.4.4를 실행하는 설치용 PHP 8.1을 지원합니다.
![신규](../assets/new.svg) 다음 `Magento_ElasticsearchCatalogPermissionsGraphQl` 설치 중에 비활성화된 모듈 목록에 모듈이 추가됩니다.
![신규](../assets/new.svg) 에서 사용 가능한 라인 수 [[!DNL storefront popover]](quick-tour.md) 에서 구성할 수 있습니다. *관리자*.
![신규](../assets/new.svg) 베타 [PWA](https://developer.adobe.com/commerce/pwa-studio/) 호환성 [!DNL Live Search].
![신규](../assets/new.svg) 다음 [!DNL Live Search] 설치 프로세스가 고급 프로세스 변경 사항으로 업데이트됩니다.
![수정](../assets/fix.svg) [고급 검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) 상점 첫 번째 바닥글에서 링크가 제거되었습니다.
![버그](../assets/bug.svg) 다음 제품 속성은에서 지원하지 않습니다. [상거래 GraphQL API](https://developer.adobe.com/commerce/webapi/graphql/) PWA의 베타 릴리스와 관련하여 사용할 경우: `description`, `name`, `short_description`
![버그](../assets/bug.svg) 다음에 대한 PWA 베타 릴리스 [!DNL Live Search] 은(는) 을 지원하지 않습니다. [이벤트 처리](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![수정](../assets/fix.svg) [사용자 지정 가격 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) 로 구성된 경우 가 더 이상 오류를 반환하지 않습니다. [facet]({% 링크 live-search/facets-add.md %}).
![수정](../assets/fix.svg) 없을 때 오류가 발생하던 문제를 수정했습니다. [통화 기호](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`)을 사용할 수 있습니다.
![수정](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) 이제 다음을 표시합니다. [특별 가격](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (최소 최종 가격).

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![신규](../assets/new.svg) [성능](performance.md) 보고 대시보드는 쇼핑객이 사용하는 검색어에 대한 통찰력을 제공합니다.
![신규](../assets/new.svg) [!DNL Live Search] [Storefront 이벤트 SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 이벤트 게시 및 구독 서비스와 지표를 사용하여 공통 데이터 계층에 액세스할 수 있습니다.
![수정](../assets/fix.svg) 다음 [[!DNL Storefront popover]](storefront-popover.md) 새 항목 있음 `active` 클래스 `.search-autocomplete` 가시성을 제어하는 컨테이너입니다.
![수정](../assets/fix.svg) 상점 앞에서 [검색어](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) 바닥글 링크가 제거되고 해당 캐시가 비활성화됨 [!DNL Live Search] 설치.
![버그](../assets/bug.svg) 검색 어댑터용 패치가 중복 제품을 처리합니다.
![버그](../assets/bug.svg) [!DNL Live Search] 지원 [단일 소스](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) (가상) 여러 개의 물리적 재고 위치 [재고](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). 지금은 여러 인벤토리 소스가 지원되지 않습니다.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![신규](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) 쇼핑객이 검색 상자에 쿼리를 입력할 때 추천 제품 및 상위 검색 결과의 썸네일 이미지를 표시합니다.
![신규](../assets/new.svg) 상거래 *관리자* 키보드가 작동하지 않는 기간이 길어지면 세션이 열린 상태로 유지됩니다
![신규](../assets/new.svg) [!DNL Live Search] 온보딩 후 자동으로 활성화됨
![수정](../assets/fix.svg) 초기 인덱싱 시간은 1시간 이내입니다.
![수정](../assets/fix.svg) 거의 실시간으로 증분 제품 업데이트(설치 및 설정 후)
![수정](../assets/fix.svg) 동의어 편집기의 정렬 가능한 열
![수정](../assets/fix.svg) [!DNL Live Search] 검색 기준에 빈 정렬 순서 값이 포함된 경우 더 이상 오류가 발생하지 않습니다.
![수정](../assets/fix.svg) 속성 코드에 문자열 &quot;to&quot; 또는 &quot;from&quot;이 포함된 경우 범위 필터링이 더 이상 중단되지 않습니다.

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![버그](../assets/bug.svg) 다음 [!DNL Live Search] 서비스는 [기본 통화](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) Adobe Commerce 설치
![버그](../assets/bug.svg) Facet을 추가할 때으로 설정하면 제품 속성 피드가 올바르게 업데이트되지 않습니다. `Update on Save`. 이 문제를 방지하려면 [색인 관리](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) 및 제품 속성 피드 설정 `Update by Schedule`.
![버그](../assets/bug.svg) [!DNL Live Search] 동의어는 스토어 보기별로 정의되지만, 현재 웹 사이트별로 저장되고 `environmentId` 및 `storeViewCode`. 따라서 Adobe Commerce 설치 내의 모든 웹 사이트 및 스토어 보기는 동의어를 공유합니다. 저장소 보기에 대해 가장 최근에 생성된 동의어 집합이 우선합니다.
![버그](../assets/bug.svg) 동의어 용어에 여러 단어가 들어 있으면 각 단어는 별개의 동의어로 취급된다. 예를 들어 &quot;time piece&quot;를 &quot;watch&quot;의 동의어로 정의하면 &quot;time&quot;과 &quot;piece&quot;는 모두 watch의 동의어로 처리됩니다.

+++

## 설명서

자세한 내용은 다음을 참조하십시오.

* [Adobe Commerce 개발자 설명서](https://developer.adobe.com/commerce/docs)
* [Adobe Commerce 사용 안내서](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] 마켓플레이스에서](https://commercemarketplace.adobe.com/magento-live-search.html)
