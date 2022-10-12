---
title: 릴리스 정보
description: 에 대한 최신 릴리스 정보 [!DNL Product Recommendations] Adobe Commerce에서 가져옵니다.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: ab7bb72826ff3aee1ce93d30dde0a752ef8069de
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# 릴리스 정보

릴리스 노트에는 다음에 대한 업데이트가 포함되어 있습니다 [!DNL Product Recommendations] 모듈:

* 2021년 3월 현재 [!DNL Product Recommendations] 이제에서 지원됩니다. [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) 상점 전구.
* [!DNL Product Recommendations] mexackage: `magento/product-recommendations`
* 에서 Page Builder 지원 [!DNL Product Recommendations] (선택 사항) 모듈: `magento/module-page-builder-product-recommendations`
* 에 대한 시각적 유사성 권장 사항 유형 지원 [!DNL Product Recommendations] (선택 사항) 모듈: `magento/module-visual-product-recommendations`

릴리스 노트는 다음과 같습니다.

* ![새로 만들기](../assets/new.svg) - 새로운 기능
* ![수정](../assets/fix.svg) - 수정 사항 및 향상된 기능

개발자 설명서에서 다음 작업을 참조하십시오. [제품 호환성에 대해 알아보기](https://devdocs.magento.com/release/availability.html).

## Adobe Commerce 2.3.x 및 2.4.x

## magento/product-recommendations 4.0.0

* ![새로 만들기](../assets/new.svg) - 추가됨 [준비 지표](create.md) 각 권장 사항 유형의 교육 진행 상황을 시각화하는 데 도움이 됩니다.
* ![새로 만들기](../assets/new.svg) - 주요 버전 릴리스입니다. 다음을 수행해야 합니다. [편집](install-configure.md#update) 루트 `composer.json` 파일을 만들 수 있습니다. 또한 이 릴리스에서는 Product Recommendations을 설치 및 구성할 때 두 개의 API 키를 제공해야 합니다. [프로덕션 키 및 샌드박스 키](../landing/saas.md).

### 알려진 제한 사항

* 다음 `websiteCode` 밑줄(_)이 포함된 경우 값이 잘못 반환됩니다.

## magento/product-recommendations 3.3.7

* ![새로 만들기](../assets/new.svg) - PHP 8.1 지원이 추가되었습니다.
* ![새로 만들기](../assets/new.svg) - 참조 표시 템플릿에서 다른 크기의 이미지를 더 일관되게 처리하도록 이미지 크기 조정 기능이 개선되었습니다

## magento/product-recommendations 3.3.6

* ![새로 만들기](../assets/new.svg) - 최적화 [!DNL Product Recommendations] 종속성을 명시적으로 나열하여 methoxackage

### magento/product-recommendations 3.5

* ![새로 만들기](../assets/new.svg) - 추가됨 [B2B 지원](onboarding.md#b2bsupport) 제품 Recommendations
* ![새로 만들기](../assets/new.svg) - 새 피드가 추가됨 [카탈로그 데이터 동기화](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) 명령줄에서 Commerce Services로

### magento/product-recommendations 3.3

* ![새로 만들기](../assets/new.svg) - 새로 추가됨 [추천 유형](type.md): 전환(장바구니에 보기), 전환(구매로 보기) 및 최근에 본 항목. 이러한 새 권장 사항 유형은 `magento/product-recommendations` 모듈 3.2.2 이상.
* ![수정](../assets/fix.svg) - Apple의 웹 애플리케이션 방화벽(WAF)에서 쿠키를 잘못 차단하는 문제가 해결되었습니다
* ![수정](../assets/fix.svg) - 기본이 아닌 스토어 보기에 지정된 제품이 _Recommendations 제품 미리 보기_ 특정 저장소 보기에 대한 권장 사항을 만들 때 패널
* ![수정](../assets/fix.svg) - Page Builder의 특정 권장 사항 단위 이름이 storefront에 표시되지 않는 문제가 해결되었습니다

### magento/product-recommendations 3.2

* ![수정](../assets/fix.svg) - B2B 지원에 대한 누락된 종속성이 수정되었습니다.

### magento/product-recommendations의 3.3.1

* ![새로 만들기](../assets/new.svg) - B2B 고객 그룹 가격에 대한 지원을 추가했습니다. 을(를) 설정할 때 [가격 필터](filters.md) 권장 사항 유닛에서 로그인한 B2B 고객은 표시된 제품에 대한 고객 그룹 가격책정 세트를 참조하십시오.

### magento/product-recommendations 3.3.0

* ![새로 만들기](../assets/new.svg) - Adobe Commerce 기능 및 서비스에서 행동 데이터 수집을 표준화하기 위해 Adobe 클라이언트 데이터 계층에 대한 지원을 추가했습니다. 자세한 내용은 [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) 추가 정보

### magento/product-recommendations 3.2.6

* ![수정](../assets/fix.svg) - JavaScript 모달 오류가 수정되었습니다.
* ![수정](../assets/fix.svg) - Apple의 웹 애플리케이션 방화벽(WAF)에서 쿠키를 잘못 차단하는 문제가 해결되었습니다

### magento/product-recommendations 3.2.5

* ![새로 만들기](../assets/new.svg) - Magento 서비스 이름이 [상거래 서비스](https://docs.magento.com/user-guide/system/saas.html) 및 관리자의 유용성 개선

### magento/product-recommendations 3.2.4

* ![수정](../assets/fix.svg) - 제품 속성을 인덱싱할 때 &quot;구성 가능한 제품 옵션 데이터를 검색할 수 없습니다.&quot; 오류가 수정되었습니다

### magento/product-recommendations 3.2.3

* ![수정](../assets/fix.svg) - 카탈로그 동기화 중에 &quot;구성 가능한 제품 옵션 데이터를 검색할 수 없음&quot; 오류를 수정했습니다
* ![수정](../assets/fix.svg) - &quot;URL에 스토어 코드 추가&quot; 구성을 활성화했을 때 스토어 코드가 올바르게 설정되지 않는 문제가 수정되었습니다
* ![수정](../assets/fix.svg) - 이러한 변경 사항이 카탈로그 동기화 데이터에 반영되도록 관리 패널 구성 변경 사항 감지를 개선했습니다

### magento/product-recommendations 3.2.2

* ![새로 만들기](../assets/new.svg) - 다음 기능이 추가되었습니다. [추천 결과 미리 보기](create.md) 생성 시. 따라서 모듈을 최신 버전으로 업데이트해야 할 수 있습니다.
* ![새로 만들기](../assets/new.svg) - 다음 기능이 추가되었습니다. [모니터링 및 관리](https://docs.magento.com/user-guide/system/catalog-sync.html) 관리자의 카탈로그 동기화 프로세스입니다.
* ![새로 만들기](../assets/new.svg) - 추가됨 [필터](filters.md) 를 눌러 권장 사항에 표시되는 제품을 제어합니다.
* ![새로 만들기](../assets/new.svg) - 을 추가했습니다. [시각적 유사성](type.md#visualsim) 권장 사항 유형.

### magento/module-page-builder-product-recommendations 페이지 빌더에 대한 1.2.1

* ![새로 만들기](../assets/new.svg) - 의 3.2.0+ 버전에 대한 지원을 추가했습니다. `magento/product-recommendations` 모듈

### magento/product-recommendations 3.1.0

* ![새로 만들기](../assets/new.svg) - 다음 기능이 추가되었습니다. [다시 동기화](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) 명령줄 을 통해 SaaS 서비스에 대한 카탈로그
* ![새로 만들기](../assets/new.svg) - 데이터베이스 테이블 접두사에 대한 지원이 추가됨
* ![수정](../assets/fix.svg) - PHP 7.1 지원이 제거됨

### magento/product-recommendations 3.0.8

* ![수정](../assets/fix.svg) - 모듈이 구성되기 전에 데이터 수집에 대해 이벤트가 전송되어 잘못된 트래픽이 발생하는 문제를 해결했습니다

### magento/product-recommendations 3.0.6

* ![새로 만들기](../assets/new.svg) - **(베타)** 신규 지원 포함 [시각적 유사성](type.md#visualsim) 권장 사항 유형.

### magento/module-visual-product-recommendations 1.0.0

* ![새로 만들기](../assets/new.svg) - **(베타)** [시각적 유사성](type.md#visualsim). 사용 _시각적 유사성_ 권장 사항 유형에서는 보고 있는 제품과 시각적으로 유사한 제품을 표시하는 제품 세부 사항 페이지에 권장 사항 단위를 배포할 수 있습니다.

### magento/product-recommendations 3.0.5

* ![수정](../assets/fix.svg) - 카탈로그 내보내기 중에 발생할 수 있는 &quot;제품 옵션 데이터를 검색할 수 없음&quot; 오류를 수정했습니다.
* ![수정](../assets/fix.svg) - 통화 기호의 _매출_ 열 _제품 Recommendations_ 이제 대시보드에 구성된 기본 통화가 올바르게 반영됩니다.

### magento/product-recommendations 3.0.4

* ![수정](../assets/fix.svg) - Adobe Commerce 2.4.0에 대한 지원이 추가됨

### magento/product-recommendations 3.0.3

* ![수정](../assets/fix.svg) - storefront 템플릿의 심볼 구현 개선

### magento/module-page-builder-product-recommendations 페이지 빌더에 대한 1.0.4

* ![새로 만들기](../assets/new.svg) - 페이지 빌더 컨텐츠 유형을 편집할 때 제품 권장 사항 이름이 추가되었습니다

### 3.0.2 magento/product-recommendations

* ![새로 만들기](../assets/new.svg) - Page Builder에서 권장 사항 단위를 선택할 때 그리드에 상태 열이 추가되었습니다
* ![수정](../assets/fix.svg) - 제품 및 이미지 URL에서 잘못된 http/https 프로토콜 문제를 해결했습니다

### magento/product-recommendations 3.0.1

주요 버전 릴리스입니다. 다음을 수행해야 합니다. [편집](install-configure.md#update) 프로젝트의 루트 composer.json 파일입니다.

* ![새로 만들기](../assets/new.svg) - 가져오기 [!DNL Product Recommendations] 대체 SaaS 데이터 스페이스에서 액세스 이렇게 하면 제품 환경에서 계산된 제품 권장 사항을 다른 비프로덕션 환경에서 사용할 수 있습니다. [SaaS 데이터 공간 전환](settings.md) 이 기능에 대해 자세히 설명합니다.

* ![수정](../assets/fix.svg) - 블록 원본을 사용하는 구매자에 대해 체크아웃이 억제되는 문제가 해결되었습니다
* ![수정](../assets/fix.svg) - 장바구니에 추가 필요 없는 이벤트를 전송하는 문제를 수정했습니다

### Page Builder용 magento/module-page-builder-product-recommendations 1.0.3

* ![새로 만들기](../assets/new.svg) - Page Builder 지원. Page Builder 통합을 사용하면 Page Builder가 작성된 컨텐츠의 임의의 위치에 권장 사항 단위를 정확하고 세부적으로 배치할 수 있습니다. 제목 및 권장 사항 단위 자체를 스타일을 지정할 수도 있습니다. 이동 [페이지 빌더](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) 추가 정보.

### magento/product-recommendations 2.0.0

* ![새로 만들기](../assets/new.svg) - 일반 출시 릴리스!

## 설명서

에 대해 자세히 알아보려면 [!DNL Product Recommendations] 및 [!DNL Product Recommendations] 개발:

* [사용 안내서](overview.md)
* [개발자 설명서](https://devdocs.magento.com/recommendations/product-recs.html)
