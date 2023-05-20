---
title: 이벤트 컬렉션 확인
description: 동작 데이터가 Adobe Commerce으로 전송되고 있는지 확인하는 방법을 알아봅니다.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 이벤트 컬렉션 확인

이후 [설치 및 구성](install-configure.md) 다음 `magento/product-recommendations` 모듈에서 동작 데이터가 Adobe Commerce으로 전송되고 있는지 확인할 수 있습니다. Chrome에서 사용할 수 있는 개발자 도구를 사용하거나 Snowflow Chrome 확장 기능을 설치할 수 있습니다. 추가 도움이 필요한 경우 다음을 참조하십시오. [문제 해결 [!DNL Product Recommendations] 모듈](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 지원 기술 자료.

## Chrome에서 개발자 도구를 사용하여 확인

이벤트 수집기 JS 파일이 모든 사이트 페이지에 로드되도록 하려면 다음을 수행하십시오.

1. Chrome에서 **Google Chrome 사용자 지정 및 제어** 그런 다음 선택 **추가 도구** > **개발자 도구**.
1. 다음을 선택합니다. **네트워크** 탭을 선택한 다음 **JS** 유형.
1. 필터 대상 `ds.`
1. 페이지를 다시 로드합니다.
1. 다음이 표시됩니다. `ds.js` 또는 `ds.min.js` 다음에서 **이름** 열.

![이벤트 수집기 JS](assets/filter-ds.png)
_이벤트 수집기 JS_

이벤트가 사이트의 페이지(홈, 제품, 체크아웃 등)에서 실행되도록 하려면 다음을 수행합니다.

1. 브라우저에서 광고 차단기를 비활성화하고 사이트에서 쿠키를 허용하는지 확인하십시오.
1. Chrome에서 **Google Chrome 사용자 지정 및 제어** (브라우저의 오른쪽 위 모서리에 있는 세 개의 세로 점) 그런 다음 을 선택합니다 **추가 도구** > **개발자 도구**.
1. 다음을 선택합니다. **네트워크** 다음에 대한 탭 및 필터링 `tp2`.
1. 페이지를 다시 로드합니다.
1. 다음에 대한 호출이 표시됩니다. `tp2` 다음에서 **이름** 열.

![이벤트 실행](assets/filter-tp2.png)
_이벤트가 실행되고 있는지 확인_

## Snowplow Chrome 확장 기능을 사용하여 확인

설치 [Chrome용 Snowploy Analytics 디버거 확장 프로그램](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). 이 확장은 수집 및 Adobe Commerce으로 전송되는 이벤트를 표시합니다.

1. 브라우저에서 광고 차단기를 비활성화하고 사이트에서 쿠키를 허용하는지 확인하십시오.

1. Chrome에서 **Google Chrome 사용자 지정 및 제어** (브라우저의 오른쪽 위 모서리에 있는 세 개의 세로 점) 그런 다음 을 선택합니다 **추가 도구** > **개발자 도구**.

1. 다음을 선택합니다. **Snowploy Analytics 디버거** 탭.

1. 아래 **이벤트** 열에서 선택 **구조화된 이벤트**.

1. 표시될 때까지 아래로 스크롤합니다 **컨텍스트 데이터 _n_**. 에서 storefront 인스턴스를 찾습니다.**스키마**.

1. 다음을 확인합니다 [SaaS 데이터 공간 ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 가 올바르게 설정되었습니다.

![Snowploy 필터](assets/snowplow-filter.png)
_Snowploy 필터_

>[!NOTE]
>
> 값 `Data validity : NOT FOUND` 디버거에서 내부 스키마를 나타냅니다. Snowploy Chrome 플러그인은 내부 스키마로 이벤트를 확인할 수 없습니다. 이는 실제 기능에는 영향을 주지 않습니다.

## 이벤트가 올바르게 실행되는지 확인

지표에 사용된 이벤트가 올바로 실행되는지 확인하려면 `impression-render`, `view`, 및 `rec-click` Snowploy Analytics Debugger의 이벤트. 다음을 참조하십시오. [전체 이벤트 목록](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> If [쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 이 활성화되어 있으면 Adobe Commerce은 쇼핑객이 동의할 때까지 행동 데이터를 수집하지 않습니다. 쿠키 제한 모드 가 비활성화되면 기본적으로 동작 데이터가 수집됩니다.
