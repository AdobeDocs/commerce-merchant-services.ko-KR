---
title: '''[!DNL Product Recommendations] 릴리스 정보'
description: 의 최신 릴리스 정보 [!DNL Product Recommendations] Adobe Commerce에서.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: bf7dc316f7b7b702836441b35770403d75be6cfd
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 0%

---

# [!DNL Product Recommendations] 릴리스 정보

릴리스 노트에는 다음 내용에 대한 업데이트가 포함되어 있습니다 [!DNL Product Recommendations] 모듈:

* [!DNL Product Recommendations] 메타패키지: `magento/product-recommendations`
* 에서 페이지 빌더 지원 [!DNL Product Recommendations] (선택 사항) 모듈: `magento/module-page-builder-product-recommendations`
* 시각적 유사성 추천 유형 지원 대상 [!DNL Product Recommendations] (선택 사항) 모듈: `magento/module-visual-product-recommendations`

현재 주요 릴리스 버전에 대한 지원이 제공됩니다. 이전 버전에 대한 릴리스 노트는 참조를 위해 제공됩니다.
릴리스 노트는 다음과 같습니다.

![신규](../assets/new.svg) 새로운 기능
![수정](../assets/fix.svg) 수정 사항 및 향상된 기능
![버그](../assets/bug.svg) 알려진 문제

개발자 설명서 를 참조하여 다음을 수행합니다 [제품 지원에 대해 알아보기](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 호스팅된 서비스 업데이트

이 참고 사항에서는 버전 관리된 릴리스 외부에 게시된 업데이트 또는 호스팅된 서비스에 대한 개선 사항에 대해 설명합니다.

+++호스팅된 서비스 업데이트

_2023년 7월 18일_

![신규](../assets/new.svg) 제품 Recommendations에 이제 GraphQL이 포함됨 [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) 쿼리.

_2023년 4월 25일_

![신규](../assets/new.svg) 제품 Recommendations 고객은 이제 다음을 활용할 수 있습니다 [SaaS 가격 인덱싱](../price-index/index.md).

+++

## 현재 메이저 버전

### magento/제품 권장 사항 6.0.0

_2024년 2월 22일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 다음 [!DNL Catalog Sync Dashboard] 은(는) 현재 [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html). 이렇게 개선된 대시보드는 다음에 대한 데이터 스트림에 대한 통찰력을 제공합니다. [!DNL Product Recommendations], [!DNL Live Search], 및 [!DNL Catalog Service].
![수정](../assets/fix.svg) 제품 Recommendations에 대한 체크아웃 오류가 발생하는 문제를 해결했습니다.

### 이전 버전

+++5.0.0 및 이전

### magento/product-recommendations 5.0.1

_2023년 9월 15일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 를 지원하는 새 모듈이 추가되었습니다. [Saas 가격 인덱서](../price-index/index.md).
![신규](../assets/new.svg) 번들 제품 및 기프트 카드를 비롯한 더 많은 제품 유형 내보내기를 지원하기 위해 새로운 데이터 내보내기 모듈이 추가되었습니다.
![수정](../assets/fix.svg) 제품 및 가격 피드의 테이블 크기가 크게 줄었습니다. 표 `catalog_data_exporter_products` 및 `catalog_data_exporter_product_prices` 크기를 상당히 줄여야 합니다.

#### 알려진 제한 사항

* 다음 `websiteCode` 밑줄(_)이 포함된 경우 값이 잘못 반환됩니다.

### magento/product-recommendations 5.0.0

_2023년 3월 20일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) Adobe Commerce 2.4.6을 지원하도록 제품 Recommendations이 업데이트되었습니다.
![신규](../assets/new.svg) 주요 버전 릴리스입니다. [편집](install-configure.md#update) 루트 `composer.json` 프로젝트용 파일입니다.
![신규](../assets/new.svg) [!DNL Product Recommendations] 이제에서 전체 지원 [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) commerce(이전에는 MSI라고 함)의 기능. 전체 지원을 활성화하려면 다음을 수행해야 합니다 [업데이트](install-configure.md#update) 종속성 모듈 `commerce-data-export` 버전 102.2.0+에

### magento/제품 권장 사항 4.0.1

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) 이전에는 표시 통화가 기본값이 아닌 통화로 전환되면 제품 Recommendations에 오류가 표시되었습니다. 이제 통화 전환이 제대로 작동합니다.

### magento/제품 권장 사항 4.0.0

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 추가됨 [준비 지표](create.md) 각 추천 유형의 교육 진행률을 시각화하는 데 도움이 됩니다.
![신규](../assets/new.svg) 주요 버전 릴리스입니다. [편집](install-configure.md#update) 루트 `composer.json` 프로젝트용 파일입니다. 또한 이 릴리스에서는 Product Recommendations을 설치 및 구성할 때 두 개의 API 키를 제공해야 합니다. [프로덕션 키 및 샌드박스 키](../landing/saas.md).

#### 알려진 제한 사항

* 다음 `websiteCode` 밑줄(_)이 포함된 경우 값이 잘못 반환됩니다.

### magento/product-recommendations 3.3.7

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) PHP 8.1 지원이 추가됨
![신규](../assets/new.svg) 이미지 크기 조정이 참조 표시 템플릿에서 보다 일관되게 처리되도록 이미지 크기 조정 기능이 개선되었습니다

### magento/product-recommendations 3.3.6

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 최적화됨 [!DNL Product Recommendations] 종속성을 명시적으로 나열하여 메타패키지

### magento/product-recommendations 3.3.5

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 추가됨 [B2B 지원](onboarding.md#b2bsupport) 제품 Recommendations
![신규](../assets/new.svg) 에 새 피드를 추가했습니다. [카탈로그 데이터 동기화](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 명령줄을 통해 Commerce Services로

### magento/product-recommendations 3.3.3

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 새로 추가됨 [권장 사항 유형](type.md): 전환(장바구니로 보기), 전환(구매로 보기) 및 최근에 본 항목. 이러한 새로운 권장 사항 유형은 `magento/product-recommendations` 모듈 3.2.2 이상
![수정](../assets/fix.svg) Fastly의 WAF(Web Application Firewall)가 쿠키를 잘못 차단하던 문제를 해결했습니다
![수정](../assets/fix.svg) 기본이 아닌 스토어 보기에 할당된 제품이 _Recommendations 제품 미리보기_ 특정 스토어 보기에 대한 권장 사항을 만들 때 표시되는 패널
![수정](../assets/fix.svg) 페이지 빌더의 특정 추천 단위 이름이 추천 단위가 상점 앞에 표시되지 않도록 하는 문제가 해결되었습니다.

### magento/product-recommendations 3.3.2

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) B2B 지원에 대해 누락된 종속성이 수정되었습니다.

### magento/product-recommendations 3.3.1

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) B2B 고객 그룹 가격에 대한 지원이 추가되었습니다. 을(를) 설정할 때 [가격 필터](filters.md) 권장 사항 단위에서 로그인한 B2B 고객은 표시된 제품에 대해 설정된 고객 그룹 가격을 확인합니다.

### magento/product-recommendations 3.3.0

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) Adobe Commerce 기능 및 서비스 전반에 걸쳐 행동 데이터 수집을 표준화하기 위한 Adobe 클라이언트 데이터 레이어에 대한 지원을 추가했습니다. 다음을 참조하십시오. [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) 자세히 알아보십시오.

### magento/product-recommendations 3.2.6

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) JavaScript 모달 오류가 수정되었습니다.
![수정](../assets/fix.svg) Fastly의 WAF(Web Application Firewall)가 쿠키를 잘못 차단하던 문제를 해결했습니다

### magento/product-recommendations 3.2.5

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) Magento 서비스 이름이 변경됨 [상거래 서비스](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) 및 관리자의 유용성 개선

### magento/product-recommendations 3.2.4

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) 제품 속성을 색인화할 때 발생하는 &quot;구성 가능한 제품 옵션 데이터를 검색할 수 없음&quot; 오류를 수정했습니다

### magento/product-recommendations 3.2.3

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) 카탈로그 동기화 중 &quot;구성 가능한 제품 옵션 데이터를 검색할 수 없음&quot; 오류를 수정했습니다
![수정](../assets/fix.svg) &quot;URL에 스토어 코드 추가&quot; 구성을 활성화했을 때 스토어 코드가 올바르게 설정되지 않는 문제가 해결되었습니다
![수정](../assets/fix.svg) 관리 패널 구성 변경 사항의 감지를 개선하여 이러한 변경 사항이 카탈로그 동기화 데이터에 반영되도록 합니다.

### magento/product-recommendations 3.2.2

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 에 기능을 추가했습니다. [권장 사항 결과 미리 보기](create.md) 생성 시. 이렇게 하려면 모듈을 최신 버전으로 업데이트해야 할 수 있습니다.
![신규](../assets/new.svg) 에 기능을 추가했습니다. [모니터링 및 관리](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 관리자의 카탈로그 동기화 프로세스입니다.
![신규](../assets/new.svg) 추가됨 [필터](filters.md) 권장 사항에 표시되는 제품을 제어합니다.
![신규](../assets/new.svg) 을(를) 추가함 [시각적 유사성](type.md#visualsim) 권장 사항 유형.

### 페이지 빌더를 위한 magento/module-page-builder-product-recommendations 1.2.1

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 의 3.2.0+ 버전에 대한 지원을 추가했습니다. `magento/product-recommendations` 모듈

### magento/product-recommendations 3.1.0

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 에 기능을 추가했습니다. [재동기화](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 카탈로그를 명령줄을 통해 SaaS 서비스로 이동합니다.
![신규](../assets/new.svg) 데이터베이스 테이블 접두사에 대한 지원이 추가되었습니다
![수정](../assets/fix.svg) PHP 7.1 지원 제거됨

### magento/product-recommendations 3.0.8

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) 모듈이 구성되기 전에 데이터 수집을 위해 이벤트가 전송되어 잘못된 트래픽이 발생하는 문제를 해결했습니다

### magento/product-recommendations 3.0.6

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) **(베타)** 새로운 기능에 대한 지원 포함 [시각적 유사성](type.md#visualsim) 권장 사항 유형.

### magento/module-visual-product-recommendations 1.0.0

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) **(베타)** [시각적 유사성](type.md#visualsim). 포함 _시각적 유사성_ 권장 사항 유형에서는 보고 있는 제품과 시각적으로 유사한 제품을 표시하는 제품 세부 사항 페이지에 권장 사항 단위를 배포할 수 있습니다.

### magento/product-recommendations 3.0.5

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) 카탈로그 내보내기 중에 발생할 수 있는 &quot;제품 옵션 데이터를 검색할 수 없음&quot; 오류를 수정했습니다.
![수정](../assets/fix.svg) 의 통화 기호 _매출_ 의 열 _제품 Recommendations_ 이제 대시보드에 구성된 기본 통화가 올바르게 반영됩니다.

### magento/product-recommendations 3.0.4

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) Adobe Commerce 2.4.0에 대한 지원이 추가되었습니다.

### magento/product-recommendations 3.0.3

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) storefront 템플릿의 기호 구현 개선

### 페이지 빌더를 위한 magento/module-page-builder-product-recommendations 1.0.4

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 페이지 빌더 콘텐츠 유형을 편집할 때 제품 추천 이름이 추가되었습니다

### 3.0.2 magento/product-recommendations

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 페이지 빌더에서 추천 단위를 선택할 때 그리드에 상태 열이 추가되었습니다.
![수정](../assets/fix.svg) 제품 및 이미지 URL에서 잘못된 http/https 프로토콜 문제를 해결했습니다

### magento/product-recommendations 3.0.1

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

주요 버전 릴리스입니다. [편집](install-configure.md#update) 프로젝트의 루트 composer.json 파일.

![신규](../assets/new.svg) 가져오기 [!DNL Product Recommendations] 다른 SaaS 데이터 공간에서 생성할 수 있습니다. 이렇게 하면 다른 비프로덕션 환경의 제품 환경에서 계산된 제품 권장 사항을 사용할 수 있습니다. [SaaS 데이터 공간 전환](settings.md) 에서는 이 기능에 대해 자세히 설명합니다.

![수정](../assets/fix.svg) uBlock Origin을 사용하는 쇼핑객에 대해 체크아웃이 금지되던 문제를 수정했습니다
![수정](../assets/fix.svg) 관련 없는 장바구니 추가 이벤트를 전송하는 문제를 해결했습니다.

### 페이지 빌더를 위한 magento/module-page-builder-product-recommendations 1.0.3

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 페이지 빌더 지원. 페이지 빌더 통합을 사용하면 페이지 빌더가 작성한 콘텐츠의 임의 위치에 권장 사항 단위를 정확하고 세분화하여 배치할 수 있습니다. 머리글과 추천 단위 자체의 스타일을 지정할 수도 있습니다. 다음으로 이동 [페이지 빌더](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 추가 정보.

### magento/제품 권장 사항 2.0.0

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) 일반 공급 릴리스!

+++

## 설명서

에 대해 자세히 알아보기 [!DNL Product Recommendations] 및 [!DNL Product Recommendations] 개발:

* [사용 안내서](overview.md)
* [개발자 설명서](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html)
