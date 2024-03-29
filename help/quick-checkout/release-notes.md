---
title: '[!DNL Quick Checkout] 릴리스 정보'
description: 모든 항목에 대한 자세한 내용은 릴리스 정보 를 참조하십시오 [!DNL Quick Checkout] 릴리스.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
feature: Release Notes, Services, Checkout
source-git-commit: b0f9aee6603ecbc0c711190adb52440d05219368
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 0%

---

# 릴리스 정보

이 릴리스 노트는 의 초기 릴리스에 대해 설명합니다. [!DNL Quick Checkout] 및 포함:

![신규](../assets/new.svg) 새로운 기능
![해결된 문제](../assets/fix.svg) 수정 사항 및 향상된 기능
![알려진 문제](../assets/bug.svg) 알려진 문제

다음을 참조하십시오 [예정된 릴리스](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 릴리스 일정 및 지원에 대해 알아봅니다.

다음을 참조하십시오 [가용성](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) 제품 호환성에 대해 알아보려면 개발자 설명서에서 를 참조하십시오.

## 관리 패널 업데이트

이러한 릴리스 노트는 관리 패널의 일반 버전 기능 릴리스 외부에서 발생하거나 릴리스된 기능 변경 사항 및 수정 사항에 대해 설명합니다.

+++관리 패널 업데이트

2023년 5월 23일_

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-489 --> 이제 **새 계정** 의 구성 요소 [!DNL Quick Checkout] 보고 페이지에 Spectrum 포함 [워크플로 아이콘](https://react-spectrum.adobe.com/react-spectrum/workflow-icons.html){target=_blank}.

_2023년 4월 25일_

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-452 --> 다음 [!DNL Quick Checkout] **둘러보기** 이제 단추를 마우스로 가리키면 클릭 가능한 손 커서가 표시됩니다.

_2023년 4월 19일_

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-596 --> 다음 [!DNL Quick Checkout] 이제 보고서 페이지에 ISO 8601 형식으로 날짜를 구문 분석할 때 새 계정 차트가 올바르게 표시됩니다.

_2022년 12월 14일_

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-524 --> 다음 [!DNL Quick Checkout] 이제 관리 패널에 올바른 총 주문 수 및 업데이트된 보고 정보가 표시됩니다.

_2022년 11월 30일_

![신규](../assets/new.svg)<!-- Issue BOLT-502 --> 이제 [보고](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 탭에는 새로운 &quot;작년&quot; 사전 설정이 있습니다.

![신규](../assets/new.svg)<!-- Issue BOLT-471 --> 의 사용자 경험 개선 사항 [!DNL Quick Checkout] 관리 패널에 추가 정보 표시 [툴팁](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-514 --> 의 사용자 경험 개선 사항 [!DNL Quick Checkout] 관리 패널에는 모든 차트에 대한 올바른 총 주문 수, 색상의 일관성 및 올바른 범례가 표시됩니다.

_2022년 11월 2일_

![신규](../assets/new.svg)<!-- Issue BOLT-293 --> 이제 [보고](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 의 탭 [!DNL Quick Checkout] 관리 패널에는 스토어의 체크아웃 경험 통계에 대한 차트 및 보고 정보가 표시됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-422 --> 다음 [_개요_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) 보고서 항목 섹션의 섹션은 평균 체크아웃 시간, 체크아웃 중에 생성된 새 계정, 체크아웃 포기를 포함하여 스토어의 체크아웃 성능에 대한 자세한 정보를 보여줍니다.

![신규](../assets/new.svg)<!-- Issue BOLT-423 --> 다음 [_트렌드_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) 보고서 탭의 섹션에는 계정 유형별로 필터링된 체크아웃 경험 트렌드와 체크아웃 중에 작성된 새 계정이 표시됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-439 --> 다음 **보고서** 탭이 표시됩니다. [기본 필터 사전 설정](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) 특정 데이터 범위를 표시하는 데 사용할 수 있습니다.

![신규](../assets/new.svg)<!-- Issue BOLT-433 --> 이제 다음을 볼 수 있습니다. _사용 가능한 데이터 없음_ 요청이 데이터를 반환하지 않는 경우 차트에 대한 경고.

![신규](../assets/new.svg)<!-- Issue BOLT-473 --> 의 사용자 경험 개선 사항 [!DNL Quick Checkout] 관리 패널에는 를 활성화하는 기능이 포함되어 있습니다. [체크아웃 추적](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 를 설정하는 경우 Adobe Commerce이 Bolt와 보고 정보를 공유할 수 있습니다.

_2022년 10월 5일_

![신규](../assets/new.svg)<!-- Issue BOLT-379 --> 이제 새로운 판매자가 [!DNL Quick Checkout] 처음으로 사용 가능한 관리 패널 [gainsight에서 제공하는 기능 투어](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 가 표시됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-377 --> 다음 **보고서** 의 탭 [!DNL Quick Checkout] 관리 패널에 차트 및 보고 분석이 표시됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-377 --> 다음 **보고서** 의 탭 [!DNL Quick Checkout] 관리 패널에는 차트 및 보고 분석에 대한 날짜 범위 및 필터 사전 설정이 표시됩니다.

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-369 --> 이제 [[!DNL Quick Checkout] 관리 패널](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 바닥글에 앱 버전을 표시합니다.

+++

## v1.8.0

_2023년 2월 24일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue BOLT-520 --> 일반 가용성 릴리스—[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 는 이제 Adobe Commerce Cloud 버전 2.4.6 이상에 사전 설치됩니다.

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-592 --> 에서 주문 시 사용자 경험 개선 사항 [관리 패널](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) 사용 [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) 결제 수단으로 사용됩니다. 이 기능을 사용하면 체크아웃 시 결제 수단으로 Braintree을 주문할 수 있습니다. [!DNL Quick Checkout] 이(가) 활성화되었습니다.

## v1.7.0

_2023년 2월 22일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue AC-8002 --> 를 사용하여 주문할 때의 사용자 경험 개선 사항 [다중 배송](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) 메서드를 사용합니다. 이 기능을 사용하면 체크아웃 중에 다음과 같은 결제 방법을 표시할 수 있습니다 [!DNL Quick Checkout] 이(가) 활성화되었습니다.

## v1.6.0

_2023년 2월 9일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-567 --> 다음과 같은 경우 사용자 경험 개선 [주문](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 사용 [매장 내 배달](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) 을 사용하는 메서드 [!DNL Quick Checkout] 비활성화되었습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-569 --> 쇼핑객이 다음을 수행할 수 있도록 로그아웃 기능이 개선되었습니다. [볼트 네트워크에서 로그아웃](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_2023년 1월 18일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue BOLT-522 --> 새 구성을 활성화/비활성화하여 다음을 감지할 수 있습니다 [쇼핑객](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) 볼트에 자동으로 로그인할 수 있습니다.

![신규](../assets/new.svg)<!-- Issue BOLT-523 --> 판매자가 두 네트워크 모두에 자동으로 로그인할 수 있는지 또는 볼트 네트워크에만 자동으로 로그인할 수 있는지 여부를 지정할 수 있는 새 구성을 활성화/비활성화할 수 있습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-542 --> 다음과 같은 경우 사용자 경험 개선 [볼트 계정에 카드 또는 주소 저장](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) 구매자가 이메일을 제공하는 경우.

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-550 --> 의 사용자 경험 개선 사항 [자동 로그인](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) Bolt 사용자가 이메일을 제공하는 경우

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-544 --> 호환성 개선 사항 [콜백 URL](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) 포함 [다중 사이트](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) 볼트에요

## v1.4.0

_2022년 11월 30일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue BOLT-513 --> 이제 Adobe Commerce 고객이 체크아웃 프로세스 중에 스토어에 로그인하고 Bolt 계정이 있으면 구매자의 Bolt 계정에 로그인하는 옵션이 표시됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-512 --> 새로운 구성은 로그인한 쇼핑객이 Bolt에도 로그인할 수 있는지 자동으로 감지합니다.

![신규](../assets/new.svg)<!-- Issue BOLT-480 --> 의 새 구성 [!DNL Quick Checkout] 관리 패널에서는 기본 탐색 플로우를 로 변경할 수 있습니다. **배송** Bolt 고객이 로그인하면 페이지를 표시합니다. 기본적으로 **결제** 페이지를 가리키도록 업데이트하는 중입니다.

## v1.3.0

_2022년 11월 2일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue BOLT-293 --> 자, [!DNL Quick Checkout] 을(를) 활성화하는 기능 포함 [체크아웃 추적](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) 를 설정하는 경우 Adobe Commerce이 Bolt와 보고 정보를 공유할 수 있습니다.

![신규](../assets/new.svg)<!-- Issue BOLT-461 --> 이제 경고 메시지가 표시됩니다. [!DNL Quick Checkout] 다음의 경우 관리 패널 [체크아웃 추적](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) 구성이 비활성화되었습니다.

## v1.2.0

_2022년 9월 8일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue BOLT-341 --> 일반 가용성 릴리스—[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 는 이제 Adobe Commerce 버전 2.4.5와 호환됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] Adobe Commerce 및 Magento Open Source의 경우 [관리 패널 보기](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 확장을 설정하고 사용하는 데 필요한 모든 정보를 제공합니다.

![신규](../assets/new.svg)<!-- Issue BOLT-364 --> 관리자 사용자 [사용자 역할 및 권한을 설정할 수 있음](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) 다른 사용자가 [!DNL Quick Checkout] 관리 패널.

![신규](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] 이제 관리 패널에는 다음과 같은 특정 섹션이 포함된 페이지 헤더가 포함됩니다. **개요**, **보고서**, 및 **설정**.

![신규](../assets/new.svg)<!-- Issue BOLT-379 --> 새 판매자가 [!DNL Quick Checkout] 기능 둘러보기를 제공하는 시작 위젯이 처음 표시되는 경우 [관리 패널]입니다.

![신규](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [관리 패널 보기](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 를 포함합니다. **구성** api 및 게시 가능한 키가 [설정](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 보기.

![신규](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [관리 패널 보기](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 를 포함합니다. **리소스** 섹션은 온보딩 단계에 따라 변경됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [관리 패널 보기](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) 다음 포함: **도움말 및 지원** 섹션.

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-369 --> 다음 [[!DNL Quick Checkout] 관리 패널](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 이제 바닥글에 확장 버전이 표시됩니다.

## v1.1.0

_2022년 8월 12일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-375 --> 의 사용자 경험 개선 사항 [[!DNL Quick Checkout] 관리 패널](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 이제 확장이 활성화될 때 보고 확인하는 매개 변수만 포함합니다.

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-349 --> 기존 배송 주소의 볼트 지갑에 대한 호환성이 개선되었습니다.

## v1.0.0

_2022년 8월 9일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue BOLT-341 --> 일반 가용성 릴리스—[[!DNL Quick Checkout]](https://commercemarketplace.adobe.com/magento-quick-checkout.html) 는 이제 Adobe Commerce 버전 2.4.1 ~ 2.4.4와 호환됩니다.

![신규](../assets/new.svg)<!-- Issue BOLT-340 --> 다음 [!DNL Quick Checkout] Adobe Commerce용 은 Adobe Commerce에 대해 설치할 수 있습니다 [클라우드 인프라에서](install.md#adobe-commerce-on-cloud-infrastructure) 또는 [온-프레미스](install.md#on-premises) 인스턴스. 이러한 메서드는 명령줄 인터페이스를 사용해야 합니다.

![신규](../assets/new.svg)<!-- Issue BOLT-1 --> 다음 [!DNL Quick Checkout] Adobe Commerce용 은 을(를) 허용하는 최적화된 상점을 제공합니다. [한 번의 클릭으로 체크아웃 경험](overview.md) 소비자에게 필수 입력 필드가 없습니다.

![신규](../assets/new.svg)<!-- Issue BOLT-1 --> 다음 [!DNL Quick Checkout] for Adobe Commerce은 네트워크의 각 쇼핑객을에 대해 자동으로 인식합니다. [원클릭 구매](checkout-flow.md) 바로 사이트에 있습니다.

![신규](../assets/new.svg)<!-- Issue BOLT-1 --> 다음 [!DNL Quick Checkout] Adobe Commerce의 경우 쇼핑객이 동시에 [Adobe Commerce 및 Bolt 네트워크에 모두 로그인했습니다.](checkout-flow.md/#quick-checkout-use-cases) 더 나은 것을 제공하다 `one-click checkout` 경험.

![신규](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] Adobe Commerce용 는 [샌드박스 계정](testing.md#testing-in-sandbox) 상인이 테스트 모드에서 확장을 평가할 수 있도록 해줍니다.

![신규](../assets/new.svg)<!-- Issue BOLT-780 --> 쇼핑객은 다음을 통해 체크아웃할 수 있습니다. [[!DNL Quick Checkout]](checkout-page.md) 확장 또는 를 통해 [수동 주문 생성](create-order-admin.md).

![신규](../assets/new.svg)<!-- Issue BOLT-666 --> 판매자는 다음을 구성할 수 있습니다. [!DNL Quick Checkout] 다음과 같은 기본 지급 조치 사용 [`Authorize and Capture` 또는 `Authorize`](onboarding.md#complete-admin-configuration), 또는 샌드박스와 프로덕션 환경 간 전환.

![신규](../assets/new.svg)<!-- Issue BOLT-288 --> 사용자 정의 [사용자 세션 수명](user-session-lifetime.md) 대상 [!DNL Quick Checkout] Adobe Commerce용

![해결된 문제](../assets/fix.svg)<!-- Issue BOLT-375 --> 의 사용자 경험 개선 사항 [[!DNL Quick Checkout] 관리 패널](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) 모든 필수 매개 변수가 제공된 경우 구성을 저장할 수 있습니다.

![알려진 문제](../assets/bug.svg)<!-- Issue BOLT-342 --> 공통 [문제 해결](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) 설치 도중 문제 발생 [!DNL Quick Checkout].
