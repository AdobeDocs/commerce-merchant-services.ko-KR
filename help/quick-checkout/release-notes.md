---
title: '''[!DNL Quick Checkout] 릴리스 정보'''
description: 모든 정보에 대해서는 릴리스 노트 를 검토하십시오 [!DNL Quick Checkout] 릴리스.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 6162141e1ddf4428126178bd172e8d9bd250c485
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 1%

---

# 릴리스 정보

이러한 릴리스 노트는 [!DNL Quick Checkout] 다음을 포함합니다.

![새로 만들기](../assets/new.svg) 새로운 기능
![해결된 문제](../assets/fix.svg) 수정 사항 및 향상된 기능
![알려진 문제](../assets/bug.svg) 알려진 문제

자세한 내용은 [예정된 릴리스](https://devdocs.magento.com/release/) 릴리스 일정 및 지원에 대해 알아보십시오.

자세한 내용은 [사용 가능](https://devdocs.magento.com/release/availability.html) 개발자 설명서에서 제품 호환성에 대해 알아봅니다.

## v1.0.0

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-341 --> 일반 공급 릴리스—[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) 는 이제 Adobe Commerce 버전 2.4.1과 2.4.4와 호환됩니다.

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-340 --> 다음 [!DNL Quick Checkout] Adobe Commerce용 은 Adobe Commerce용으로 설치할 수 있습니다 [클라우드 인프라](install.md#adobe-commerce-on-cloud-infrastructure) 또는 [온-프레미스](install.md#on-premises) 인스턴스. 이러한 메서드는 명령줄 인터페이스를 사용해야 합니다.

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-1 --> 다음 [!DNL Quick Checkout] Adobe Commerce용 는 [한 번의 클릭으로 체크아웃 경험](overview.md) 소비자에게 필요한 필드를 채우지 않고 있습니다.

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-1 --> 다음 [!DNL Quick Checkout] Adobe Commerce은 네트워크상의 각 구매자를 [원클릭 구매](checkout-flow.md) 바로 사용할 수 있습니다.

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-1 --> 다음 [!DNL Quick Checkout] Adobe Commerce의 경우 쇼핑객이 동시에 [Adobe Commerce 및 볼트 네트워크 모두에 로그인됨](checkout-flow.md/#quick-checkout-use-cases) 더 나은 서비스를 제공하다 `one-click checkout` 경험으로 제어됩니다.

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] Adobe Commerce용 은 [샌드박스 계정](testing.md#testing-in-sandbox) 판매자는 테스트 모드에서 확장을 평가할 수 있습니다.

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-780 --> 쇼핑하시는 분들은 [[!DNL Quick Checkout]](checkout-page.md) 확장 또는 [수동 주문 생성](create-order-admin.md).

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-666 --> 상인은 다음을 구성할 수 있습니다 [!DNL Quick Checkout] 과 같은 기본 결제 작업 사용 [`Authorize and Capture` 또는 `Authorize` ](onboarding.md#complete-admin-configuration), 샌드박스와 프로덕션 환경 간에 전환 등을 수행할 수 있습니다.

![새로 만들기](../assets/new.svg)<!-- Issue BOLT-288 --> 사용자 지정 [사용자 세션 라이프타임](user-session-lifetime.md) 대상 [!DNL Quick Checkout] Adobe Commerce용.

![알려진 문제](../assets/bug.svg)<!-- Issue BOLT-342 --> 사용 [잘못된 작성기 키](https://support.magento.com/hc/en-us/articles/6909450342541) 설치 중 [!DNL Quick Checkout] 사용자가 [인증](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 올바른 `MAGEID`.
