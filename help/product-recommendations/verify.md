---
title: 이벤트 컬렉션 확인
description: 동작 데이터가 Adobe Commerce으로 전송되고 있는지 확인하는 방법을 알아봅니다.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: 7d9cef7a81196921b465ccf2dcd58d98b66d6598
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# 이벤트 컬렉션 확인

다음에 [설치 및 구성](install-configure.md) a `magento/product-recommendations` 모듈에서는 동작 데이터가 Adobe Commerce으로 전송되고 있는지 확인할 수 있습니다. Chrome에서 사용할 수 있는 개발자 도구를 사용하거나 Snowfaul Chrome 확장을 설치할 수 있습니다. 추가 도움이 필요한 경우 [문제 해결 [!DNL Product Recommendations] 모듈](https://support.magento.com/hc/en-us/articles/360042224851) 지원 기술 자료에서

## Chrome에서 개발자 도구를 사용하여 확인

이벤트 수집기 JS 파일이 모든 사이트 페이지에서 로드되는지 확인하려면:

1. Chrome에서 **Google Chrome 사용자 지정 및 제어** 을(를) 선택합니다. **추가 도구** > **개발자 도구**.
1. 을(를) 선택합니다 **네트워크** 탭을 선택한 다음 **JS** 유형.
1. 필터 대상 `ds.`
1. 페이지를 다시 로드합니다.
1. 이제 `ds.js` 또는 `ds.min.js` 에서 **이름** 열.

![이벤트 수집기 JS](assets/filter-ds.png)
_이벤트 수집기 JS_

이벤트가 사이트(홈, 제품, 체크아웃 등)의 페이지에서 실행되는지 확인하려면:

1. 브라우저에서 광고 차단기를 비활성화하고 사이트에서 쿠키를 허용하는지 확인하십시오.
1. Chrome에서 **Google Chrome 사용자 지정 및 제어** (브라우저의 오른쪽 위 모서리에 있는 세 개의 세로 점) 그런 다음 을 선택합니다 **추가 도구** > **개발자 도구**.
1. 을(를) 선택합니다 **네트워크** 에 대한 탭 및 필터 `tp2`.
1. 페이지를 다시 로드합니다.
1. 아래에 호출이 표시됩니다 `tp2` 에서 **이름** 열.

![이벤트 실행](assets/filter-tp2.png)
_이벤트가 실행 중인지 확인_

## Snowfaul Chrome 확장을 사용하여 확인

설치 [Chrome용 Snowfail Analytics Debugger 확장 프로그램](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). 이 확장은 수집되고 Adobe Commerce으로 전송되는 이벤트를 표시합니다.

1. 브라우저에서 광고 차단기를 비활성화하고 사이트에서 쿠키를 허용하는지 확인하십시오.

1. Chrome에서 **Google Chrome 사용자 지정 및 제어** (브라우저의 오른쪽 위 모서리에 있는 세 개의 세로 점) 그런 다음 을 선택합니다 **추가 도구** > **개발자 도구**.

1. 을(를) 선택합니다 **Snowfaul Analytics Debugger** 탭.

1. 아래에 **이벤트** 열, 선택 **구조화된 이벤트**.

1. 표시될 때까지 아래로 스크롤합니다. **컨텍스트 데이터 _n_**. 에서 저장소 인스턴스를 찾습니다.**스키마**.

1. 다음 사항을 확인합니다. [SaaS 데이터 공간 ID](https://docs.magento.com/user-guide/configuration/services/saas.html) 가 올바르게 설정되어 있습니다.

![제설기 필터](assets/snowplow-filter.png)
_제설기 필터_

>[!NOTE]
>
> 값 `Data validity : NOT FOUND` 디버거에서 는 내부 스키마를 나타냅니다. Snowfaul Chrome 플러그인은 내부 스키마를 사용하여 이벤트의 유효성을 검사할 수 없습니다. 실제 기능에는 영향을 주지 않습니다.

## 이벤트가 올바르게 실행되는지 확인

지표에 사용된 이벤트가 올바르게 실행되는지 확인하려면 `impression-render`, `view`, 및 `rec-click` Snowfall Analytics Debugger의 이벤트. 자세한 내용은 [전체 이벤트 목록](https://devdocs.magento.com/recommendations/events.html).

>[!NOTE]
>
> If [쿠키 제한 모드](https://docs.magento.com/user-guide/stores/compliance-cookie-restriction-mode.html) 이 활성화되어 있으면 Adobe Commerce은 쇼핑객이 동의하기 전까지 행동 데이터를 수집하지 않습니다. 쿠키 제한 모드가 비활성화되면 기본적으로 동작 데이터가 수집됩니다.
