---
title: "[!DNL Payment Services] 릴리스 노트"
description: 모든 항목에 대한 자세한 내용은 릴리스 정보 를 참조하십시오 [!DNL Payment Services] 릴리스.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 978340c03e05d29bae6ee872ae9c7332edcd7251
workflow-type: tm+mt
source-wordcount: '2434'
ht-degree: 0%

---

# 릴리스 정보

이 릴리스 노트는 의 초기 릴리스에 대해 설명합니다. [!DNL Payment Services] 및 포함:

![신규](../assets/new.svg) 새로운 기능
![해결된 문제](../assets/fix.svg) 수정 사항 및 향상된 기능
![알려진 문제](../assets/bug.svg) 알려진 문제

일반 기능 릴리스 버전 외부에서 릴리스된 기능 변경 및 수정 사항에 대해서는 _호스팅된 서비스 업데이트_ 섹션.

예정된 릴리스, 제품 지원 및 결제 서비스 확장을 지원하는 Adobe Commerce 버전에 대한 자세한 내용은 Adobe Commerce 를 참조하십시오. [릴리스 일정](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) 및 [제품 가용성](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) 주제.

## 호스팅된 서비스 업데이트

이러한 릴리스 노트는 호스팅 서비스에 대한 일반 기능 릴리스 외부에서 발생하거나 릴리스된 기능 변경 사항 및 수정 사항에 대해 설명합니다.

+++호스팅된 서비스 업데이트

_2024년 3월 5일_

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-5252 --> 이제 판매자는 단일 셀의 콘텐츠를 선택하여 대시보드 그리드에서 데이터를 복사할 수 있습니다.

_2023년 10월 10일_

![새 문제](../assets/fix.svg)<!-- Issue PAY-4888 --> 이제 가맹점은 신용카드 및 직불카드 거래를 카드 번호의 마지막 네 자리까지 필터링할 수 있습니다. [거래 보고서](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_2023년 7월 12일_

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-4587 --> 결제 서비스 2.1.0 릴리스에서 이전 확장 버전에서 가져온 인증 공백이 방지되던 문제가 이제 해결되었습니다. 모든 버전의 결제 서비스를 사용하는 가맹점은 승인을 무효화할 수 있습니다.

_2023년 6월 9일_

![신규](../assets/new.svg)<!-- Issue PAY-4288 --> 상인들은 이제 [구성 _전용_ PayPal 결제 단추](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)- 및 _아님_ payPal 신용카드 결제 옵션을 사용합니다. 이를 통해 가맹점은 벤모와 페이팔 결제 버튼 등 다양한 결제 옵션을 제공하고, 페이팔 신용카드 결제 옵션 대신 기존 신용카드 제공업체를 이용할 수 있다.

![신규](../assets/new.svg)<!-- Issue PAY-4050 --> 을(를) 추가함 [데이터 시각화 보기](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view)주문 결제 상태 보고서에 대해 결제 서비스 홈에 표시됩니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-4486--> 이전에는 PayPal PayLater 단추가 영국 상인의 체크아웃에 표시되지 않았습니다. 해당 문제는 해결되었습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-4485--> 이제 결제 서비스를 사용하지 않도록 설정한 경우 보고서 데이터 시각화 보기가 결제 서비스 홈에 표시됩니다.

_2023년 1월 25일_

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-4102 --> 새로 설치한 결제 서비스에서 상거래 서비스를 구성할 수 없어 결제 서비스를 사용할 수 없습니다. 이 문제를 해결하려면 결제 서비스 확장을 버전 1.5.3으로 업데이트하십시오.

_2022년 9월 12일_

![신규](../assets/new.svg)<!-- Issue PAY-3705 --> 다음 `increment_id` 는 이제 외부 ERP 시스템에서 급여 조정에 사용할 수 있습니다. 이 변수는 [`custom_id` _및_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system)페이팔 웹훅 및 지급의 판매자 활동 세부 정보에 모두 표시됩니다.

_2022년 8월 31일_

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3629 --> 새 판매자가 결제 서비스 홈에 처음 액세스하면 이제 페이지가 즉시 로드되어 페이지를 새로 고치지 않고 콘텐츠를 표시합니다.

_2021년 8월 9일_

![신규](../assets/new.svg)<!-- Issue PAY-3420 --> 이제 Apple Pay를 PayPal 스마트 버튼으로 사용할 수 있습니다. 이 [지불 옵션](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) 고객이 iOS 또는 macOS 장치에서 Touch ID 기능을 사용하여 Apple Pay를 선택할 수 있도록 합니다. Apple Pay는 디바이스에 저장된 신용 및 직불 카드 결제 자격 증명을 사용하여 결제를 처리합니다.

_2021년 6월 28일_

![신규](../assets/new.svg)<!-- Issue PAY-1720 --> 스토어 주문에 대한 분쟁은 이제 다음에서 사용할 수 있습니다. [주문 결제 상태 보고서](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). 다음에서 PayPal 해결 센터로 직접 이동하여 분쟁을 해결할 수 있습니다. [!DNL Payment Services].

![신규](../assets/new.svg)<!-- Issue PAY-2854 --> 의 사용자 경험 개선 사항 [!DNL Payment Services] 홈에는 현재 상속 수준에서 구성을 수정하는 기능과 헤더 및 탐색 표시에 대한 개선 사항이 포함되어 있습니다.

![신규](../assets/new.svg)<!-- Issue PAY-2854 --> 이제 샌드박스 모드에서 프로덕션 모드로 전환하고 저장되지 않은 업데이트가 있는 보기에서 나가려고 하면 경고가 표시됩니다.

![신규](../assets/new.svg)<!-- Issue PAY-2761 --> 이제에 표시되는 데이터를 사용자 지정할 수 있습니다 [주문 결제 상태 보고서](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) 및 [지급 보고서](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) 열 설정 컨트롤을 사용하여 열을 표시하거나 숨깁니다.

+++

## v2.4.1

2024년 4월 5일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg)<!-- PAY-5322 --> 최신 Adobe Commerce 릴리스의 PCI 호환성 문제를 해결했습니다. 이제 결제 서비스는 결제 옵션으로 Adobe Commerce의 요구 사항을 체크아웃하도록 조정되었습니다.

![수정](../assets/fix.svg)<!-- PAY-5323 --> PayLater 및 Venmo가 Adobe Commerce에 올바르게 표시됩니다. 관리자가 PayLater 및 Venmo 전환 옵션을 표시할 수 없는 오류를 수정했습니다.

## v2.4.0

_2024년 3월 20일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- PAY-4868 --> 판매자가 성공할 수 있음 [구매 경험 전체에서 Google Pay 구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html): 관리자를 통한 결제 서비스의 다른 결제 버튼과 유사합니다.

![신규](../assets/new.svg)<!-- PAY-4381 --> [결제 서비스는 GraphQL을 통해 Google 페이를 지원합니다](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) 상인이 Google 페이 결제 방법을 사용하여 headless 상거래 경험을 할 수 있도록 허용합니다.

![신규](../assets/new.svg)<!-- PAY-4878 --> 이제 결제 서비스 기본 체크아웃 기능이 Adobe Commerce 및 Magento Open Source 판매자용으로 번들로 제공됩니다. 결제 서비스는 이제 전 세계 200개 지역 중 어느 곳에서든 비즈니스를 가진 상인을 지원할 수 있습니다. 결제 서비스 기본 체크아웃은 셀프 서비스 온보딩에서 차변/신용, PayPal, Venmo(사용 가능한 경우) 및 PayLater(사용 가능한 경우) 옵션을 제공합니다.

![수정](../assets/fix.svg)<!-- PAY-5291 --> 일부 거래에 대한 결제 확인 수령이 지연될 수 있습니다. 이 경우 이제 가맹점은 주문에 대해 업데이트된 결제 상태를 받을 수 있습니다. [결제 서비스는 결제 거래의 보류 상태를 감지합니다.](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) 대기 중인 트랜잭션을 감지하고 이러한 트랜잭션을 사전에 모니터링한 후 대기 중 상태가 캡처되면 업데이트하여 순서대로 표시합니다.

## v2.3.4

_2024년 3월 1일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- PAY-5244 --> 비동기 체크아웃 호환성을 수정했습니다.

![수정](../assets/fix.svg)<!-- PAY-5253 --> 결제 서비스에 속하지 않는 자격 증명 모음 토큰을 삭제할 수 없는 오류를 해결했습니다.

## v2.3.3

_2024년 2월 14일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- PAY-5048 --> PHP 8.3에 대한 지원이 추가되었습니다.

![수정](../assets/fix.svg)<!-- PAY-5048 --> 의 오류를 수정했습니다. `is_deleted` 플래그. 이제 주문은 다음과 같은 이유로 실패하지 않습니다. `Rejected` 확장에서 보낸 상태.

## v2.3.2

_2024년 1월 26일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg)<!-- PAY-5183 --> REST/GraphQL 성능 문제가 해결되었습니다. 이제 API를 통해 가져올 때 신용 카드 버튼이 렌더링됩니다.

## v2.3.1

_2023년 12월 7일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- PAY-5047 --> 이제 다음 위치에서 신용/직불 카드 브랜드 또는 결제 방법 유형을 사용할 수 있습니다.
- 상점 첫 화면의 고객 주문 페이지
- 구매자에게 전송된 주문 확인 이메일
- 다음에서 [주문 세부 사항 보기](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) Commerce 관리자

## v2.3.0

_2023년 12월 1일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- PAY-4381 --> [이제 결제 서비스에서 GraphQL 통합을 지원합니다.](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). 이제 GraphQL에서 PayPal 결제 버튼, 호스팅 필드 및 Apple Pay를 지원하므로 결제 서비스는 Headless 상거래 설정을 지원합니다.

## v2.2.1

_2023년 9월 27일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-4870 --> 확장 버전을 최신 릴리스로 보낼 때 Storefront에서 새 헤더 속성을 올바르게 잘못 입력하던 문제를 수정했습니다. 이전에는 `1.3.0` 상거래 서비스 커넥터의 릴리스이므로 를 확장할 수 없습니다. `User-Agent header` 결제 서비스 확장.

## v2.2.0

_2023년 8월 30일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- PAY-4638 --> 을(를) 추가함 [Signifyd와의 통합](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html)자동화된 사기 방지 서비스를 제공합니다.

![신규](../assets/new.svg)<!-- PAY-3981 --> [Apple Pay를 별도의 결제 옵션으로 승격](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button)를 사용하여 PayPal 결제 버튼 외부에서 결제 옵션의 구매자 가시성을 높이고 가맹점이 Apple Pay의 배치 및 스타일을 제어할 수 있습니다.

![신규](../assets/new.svg)<!-- PAY-4002 --> 결제 아이콘 추가와 같은 스타일 개선 사항을 포함하여 신용카드 필드 체크아웃의 사용자 경험을 개선하여 쇼핑객 인지 부하를 줄이고 전환을 증가시켰습니다.

![신규](../assets/new.svg)<!-- PAY-4002 --> 판매자가 다음을 수행할 수 있는 기능이 추가되었습니다. [결제 옵션 순서 정렬](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) 특정 결제 옵션의 우선 순위를 지정합니다. 이 기능을 사용하면 체크아웃 대화율이 높아집니다.

![신규](../assets/new.svg)<!-- PAY-4035 --> 상인은 이제 상점의 상태를 효율적으로 모니터링하고 새로운 기능을 사용하여 모든 거래 문제를 식별할 수 있습니다 [거래 보고서](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) 결제 서비스 관리자 홈 페이지에서 사용할 수 있습니다. 보고서는 거래 승인률과 부정적 거래 추세에 대한 자료도 제시한다.

## v2.1.0

_2023년 6월 9일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue xxx --> Adobe Commerce 2.4.7-beta1에 대한 지원이 추가되었습니다.

![신규](../assets/new.svg)<!-- Issue xxx --> 추가됨 [다음 국가 및 관련 통화의 가용성](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): 호주, 프랑스, 영국.

![신규](../assets/new.svg)<!-- Issue PAY-4296 --> 추가됨 [관리자 역할을 위한 리소스 확장](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) 를 사용하면 관리자가 고객에 대한 주문을 만들고 관리할 수 있으며 판매 메뉴에서 결제 서비스를 볼 수 있습니다.

![신규](../assets/new.svg)<!-- Issue PAY-4236 --> 추가됨 [체크아웃 중에 오류가 발생하는 주문에 대한 자동 무효화](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![신규](../assets/new.svg)<!-- Issue PAY-4183 --> 이(가) 기능을 만든 대상: [신용/직불 카드 결제 옵션 버튼 표시](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) 체크아웃 페이지에서 확인할 수 있습니다.

## v2.0.0

_2023년 3월 10일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-4152 --> PHP 8.2 및 Adobe Commerce 2.4.6에 대한 지원이 추가되었습니다. PHP 7.x와 호환되지 않습니다.

## v1.6.1

_2023년 3월 10일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg)<!-- Issue PAY-4226 --> 새 결제 서비스 판매자가 관리자에서 체크아웃을 사용할 수 없는 문제를 해결했습니다. 결제 서비스는 이전에 새 고객에 대해 존재하지 않는 상거래 고객 ID를 사용했습니다.

![수정](../assets/fix.svg)<!-- Issue PAY-4205 --> 를 사용하여 체크아웃하는 동안 지정된 배송 주소 상태가 기본 세금 설정의 상태로 대체되는 문제를 해결했습니다. [PayPal 옵션](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). 이제 고객은 머천트의 세금 설정에서 기본값으로 구성된 상태 이외의 상태로 주문을 출하할 수 있습니다.

![수정](../assets/fix.svg)<!-- Issue PAY-4202 --> 고객이 카드 보관을 사용하여 구매를 완료하거나 스토어에 대해 보관된 결제 방법을 삭제하지 못하는 문제를 해결했습니다 [사용 `Authorize and Capture` 지불 조치](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). 이전에는 고객이 저장된 신용 카드를 사용하거나 수정하려고 할 때 &quot;Provider Vault ID를 찾을 수 없음&quot; 오류가 표시되었습니다.

## v1.6.0

_2023년 2월 17일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-3540 --> 추가됨 [유럽 연합(EU) 및 영국에서 거래하는 판매자를 위한 PCI 3DS 규정 준수 기능](security.md#3ds). 구매자가 신용 카드 발급자를 인증해야 하는 이 추가 보안 계층은 온라인 사기 예방에 도움이 되며 유럽 연합(EU) 규정 준수 규칙의 일부로 필요합니다.

![신규](../assets/new.svg)<!-- Issue PAY-3609 --> 에 기능을 추가했습니다. [관리자에서 카드 보관 사용](vaulting.md#use-vaulting-in-the-admin). 이를 통해 판매자는 저장된 결제 방법을 사용하여 관리자에서 고객에 대한 주문을 생성할 수 있습니다.

## v1.5.4

_2023년 1월 29일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-4110 --> 구매자가 제품 페이지, 미니 장바구니 및 장바구니의 결제 버튼을 사용하여 주문할 수 없는 문제를 해결했습니다. 이제 구매자가 주문을 성공적으로 완료할 수 있습니다.

## v1.5.3

_2023년 1월 25일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-4102 --> 이전에 호환되지 않은 알려진 문제에 대한 수정 사항이 릴리스되었습니다. 이 릴리스에서는 서비스 ID 확장 버전을 최신 안정된 버전으로 잠가서 새 결제 서비스 설치를 통해 Commerce Services를 구성할 수 있습니다.

## v1.5.2

_2022년 12월 22일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3992 --> 결제 방법이 거부된 경우 결제 서비스의 송장 발행을 개선했습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3999 --> 이제 Payment Services가 다음을 사용하는 가맹점에 대해 PayPal 결제 버튼을 올바르게 표시합니다. [체크아웃 실행](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} 체크아웃 페이지에 대한 사용자 지정 템플릿입니다. 이전에는 미니마트에서 버튼이 간헐적으로 표시되었습니다.

## v1.5.1

_2022년 11월 23일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-3923 --> 이제 결제 서비스는 사용자 에이전트 헤더에 버전 번호를 포함하므로 요청이 사용하지 않은 끝점을 추적, 필터링 또는 사용하지 않도록 할 수 있습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3968 --> 이제 결제 버튼을 사용하여 제품 페이지에서 주문이 이루어지면 결제 서비스에 주문 데이터가 올바르게 표시됩니다.

## v1.5.0

_2022년 11월 18일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-3880 --> 이제 쇼핑객은 [체크아웃 중에 신용 카드 정보를 저장(저장)합니다.](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) 동일한 판매자 계정 내에서 동일한 또는 다른 스토어의 이후 구매에서 사용.

![신규](../assets/new.svg)<!-- Issue PAY-3950 --> 판매자가 이제 [즉시 구매 상거래 기능](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) 쇼핑객이 사용할 수 있도록 상점 용 [저장된 신용 카드 정보](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) 신속하게 체크아웃할 수 있습니다.

## v1.4.1

_2022년 10월 14일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg)<!-- Issue PAY-3766 --> 고객의 결제 방법이 거부된 경우 표시되는 오류 메시지가 더 설명적입니다. 고객이 결제 정보를 다시 입력하고 다시 시도하거나 다른 결제 수단을 시도하거나 거래 거절에 대해 해당 은행에 문의하라고 조언한다.

## v1.4.0

_2022년 9월 30일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-784 --> 이제 결제 서비스에는 다음과 같은 가맹점 계정을 설정할 수 있는 기능이 포함됩니다. [여러 PayPal 비즈니스 계정 사용](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). 이를 통해 판매자는 다양한 통화를 사용하여 여러 국가에서 스토어를 운영하거나 비즈니스의 일부로 Adobe Commerce을 사용할 수 있습니다.

![신규](../assets/new.svg)<!-- Issue PAY-3231 --> 판매자는 [추가 [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) 브랜드, 스토어 또는 제품 라인을 설명하기 위해 고객 거래 은행 거래 명세서에 표시되는 웹 사이트 또는 개별 스토어 조회수 구성

![신규](../assets/new.svg)<!-- Issue PAY-3707 --> [신용 카드 필드 및 PayPal 결제 버튼 활성화 또는 비활성화](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) 결제 서비스 설정에서 체크아웃할 경우.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3546 --> 고객이 클릭 시 **[!UICONTROL Edit cart]**: 페이지가 장바구니 페이지로 리디렉션되고 빈 장바구니를 표시하는 대신 업데이트된 항목이 표시됩니다.

## v1.3.1

_2022년 9월 6일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3663 --> 이제 머천트 스토어에서 비글로벌 통화로 승인된 주문을 캡처할 때 캡처 프로세스가 완료되고 오류가 표시되지 않습니다.

## v1.3.0

_2022년 8월 9일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-XX --> 일반 가용성 릴리스—[!DNL Payment Services] 현재 [지원한 사람 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 버전 2.4.0에서 2.4.5로](https://devdocs.magento.com/release/availability.html#compatibility).

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay는 이제 모바일 및 데스크탑에서 Safari 브라우저 v15.5와 호환됩니다.

## v1.2.0

_2022년 6월 29일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-x --> Apple Pay는 모바일 및 데스크탑에서 Safari 브라우저 v15.5와 호환되지 않습니다. Safari 버전 15.5를 사용하는 경우 Apple Pay로 체크아웃을 완료할 수 없습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3264 --> 이전에는 로그인한 사용자가 계정에 대한 기본 주소가 아닌 청구/배송 주소를 선택할 때 체크아웃하지 못했습니다. 이제 선택한 청구/배송 주소가 (저장된 기본 주소 대신) 전송되고 체크아웃이 성공적으로 완료되었습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3314 --> 체크아웃을 위해 PayPal 결제 버튼을 사용하지 않도록 설정하면 오류가 표시되지 않습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3330 --> 게스트 사용자가 대시가 포함된 전화 번호를 입력하면 체크아웃 중에 결제가 더 이상 실패하지 않습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Commerce Services 자격 증명이 유효하지 않은 경우 이제 결제 서비스에서 자격 증명 오류를 표시함으로써 알림을 보냅니다. [!DNL Payment Services] 관리자의 홈.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] 은(는) 과(와) 호환되지 않습니다. `commerce-data-export` v101.20 이상: 와 호환되지 않음 [[!DNL Channel manager] 확장](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_2022년 3월 31일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-2127 --> 일반 가용성 릴리스—[!DNL Payment Services] 현재 [지원한 사람 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 버전 2.4.0에서 2.4.4로](https://devdocs.magento.com/release/availability.html#compatibility).

![신규](../assets/new.svg)<!-- Issue PAY-2682 --> 다음 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 는 이제 캐나다 상인들이 이용할 수 있습니다. 판매자는 다음 중 하나에서 결제 구성을 볼 수 있습니다. [프랑스어](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) 또는 [영어](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![신규](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 지원 [캐나다 달러(CAD)](overview.md#accepted-credit-cards-and-currencies) 신용 카드 및 PayPal 거래.

![신규](../assets/new.svg)<!-- Issue PAY-2680 --> 판매자는 [온보드 [!DNL Payment Services]](onboard.md) 영어 또는 프랑스어 확장.

![신규](../assets/new.svg)<!-- Issue PAY-2678 --> 상인은 이제 재무 보고서를 볼 수 있습니다. [주문 결제 상태](order-payment-status.md) 및 [지급 보고서](payouts.md), 캐나다 달러(CAD) 단위.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 은(는) 이제 과(와) 호환됩니다. [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3017 --> 여러 스토어에 적절한 경고를 표시하도록 샌드박스 모드 경고가 개선되었습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2742 --> 이제 스토어 보기 수준에서 Venmo와 같은 사용 가능한 결제 방법을 활성화 및 비활성화할 수 있습니다. 이전에는 웹 사이트당 결제 방법만 구성할 수 있었습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2277 --> 이제 선택적으로 [개별 PayPal 결제 버튼 활성화 또는 비활성화](settings.md#payment-buttons).

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2561 --> 이전에 제거된 제품은 의 장바구니에 표시되지 않습니다. _주문 검토_ 페이지를 가리키도록 업데이트하는 중입니다.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2842 --> 신용 카드 거래 테스트 [PayPal 실패](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) 샌드박스 환경에서 결제를 처리하는 경우.

## v1.0.0

_2021년 11월 29일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg)<!-- Issue PAY-2127 --> 일반 가용성 릴리스—[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) 은(는) 이제 다음에서 지원합니다. [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 버전 2.4.0부터 2.4.3-p1까지.

![신규](../assets/new.svg)<!-- Issue PAY-124 --> 다음 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 다음 기간 동안 설치할 수 있습니다 [[!DNL Adobe Commerce] 클라우드 인프라에서](install.md#adobe-commerce-on-cloud-infrastructure) 또는 [온-프레미스](install.md#on-premises) 인스턴스. 이러한 메서드는 명령줄 인터페이스를 사용해야 합니다.

![신규](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 지원: [샌드박스 계정](sandbox.md) 상인이 테스트 모드에서 확장을 평가할 수 있도록 해줍니다.

![신규](../assets/new.svg)<!-- Issue PAY-666 --> 판매자는 [결제 서비스 구성](settings.md) 사용 등 기본 결제 행동을 사용한 확장 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 샌드박스 또는 프로덕션 환경 간 전환.

![신규](../assets/new.svg)<!-- Issue PAY-780 --> 쇼핑객은 다음으로 체크아웃할 수 있습니다 [!DNL Payment Services] 또는 를 통해 [수동 주문 생성](create-order.md).

![신규](../assets/new.svg)<!-- Issue PAY-1856 --> 다음을 통해 포괄적인 보고 [주문 결제 상태](order-payment-status.md) 및 [지급 보고서](payouts.md), 다음에 사용 가능: [!DNL Payment Services] 스토어의 주문 및 관련 결제에 대해 명확하게 보기 위해.

![신규](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 는 모든 판매자에게 적용되는 총 처리 용량을 기반으로 유연한 계층형 가격 정책을 지원합니다.

![신규](../assets/new.svg)<!-- Issue PAY-1443 --> 쉽게 할 수 있습니다 [모양 및 느낌 맞춤화](payments-options.md) 의 PayPal 결제 버튼 및 신용 카드 필드 [!DNL Payment Services] 확장명.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2473 --> 사용 [잘못된 작성기 키](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) 확장을 설치하는 동안 사용자가 [인증](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 를 정확히 `MAGEID`.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 보고서 [즉시 동기화할 수 없음](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2475 --> 사용자 [PayPal 샌드박스 계정](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) 대상 [!DNL Payment Services] 온보딩 중에 해당 계정을 만든 경우 확인할 수 없습니다.
