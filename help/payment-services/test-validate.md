---
title: 테스트 및 유효성 검사
description: 테스트 및 유효성 검사는 다음을 수행하는 데 도움이 됩니다. [!DNL Payment Services] 기능은 예상대로 작동하며 고객에게 최상의 결제 옵션을 제공합니다.
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# 테스트 및 유효성 검사

노출하기 전에 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 쇼핑객에게는 샌드박스 환경에서 테스트하는 것이 좋습니다 _및_ 프로덕션에서. 테스트 및 유효성 검사는 다음을 수행하는 데 도움이 됩니다. [!DNL Payment Services] 기능은 예상대로 작동하며 상점 및 고객에게 최상의 결제 옵션을 제공합니다.

## 샌드박스 환경에서 테스트

테스트 [!DNL Payment Services] 샌드박스 환경에서는 실제 은행 및 가맹점이 아닌 PayPal 샌드박스에만 연결된 시뮬레이션된 환경이지만 중요한 유효성 검사 단계입니다.

1. 다음 중 하나를 사용하여 저장소에서 성공적으로 체크아웃을 완료합니다. [신용 카드 필드](payments-options.md#credit-card-fields) 또는 다음 중 하나 [PayPal 스마트 단추](payments-options.md#paypal-smart-buttons). 다음을 참조하십시오 [자격 증명 테스트](#testing-credentials) 테스트를 위해 가짜 신용 카드를 사용하는 방법에 대한 자세한 정보.
1. 캡처(결제 액션이 다음과 같은 경우) [을 로 설정 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [환불](refunds.md), 또는 [무효](voids.md) 방금 완료된 주문. 다음을 간단히 수행할 수도 있습니다. [송장 만들기](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 주문의 경우, 지급 조치가 다음으로 설정된 경우 `Authorize` 대신 `Authorize and Capture`.
1. 24-48시간 이내에 트랜잭션 및 기타 정보를 [지급 보고서](payouts.md).
1. 다음에서 주문 세부 사항 보기: [주문 결제 상태 보고서](order-payment-status.md).

### 자격 증명 테스트

샌드박스를 테스트하고 확인할 때 기존 신용카드 계정에 실제 요금을 부과하지 않도록 가짜 신용카드 번호를 사용해야 합니다.

PayPal의 신용 카드 생성기 사용 [임의 신용카드 정보 생성](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) 테스트용입니다.

샌드박스 모드에서 Apple Pay를 테스트하려면 다음을 수행하십시오.

* 만들기 [Apple 샌드박스 테스터 계정](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account)가짜 신용 카드 및 청구 정보와 함께 작성합니다.
* [샌드박스 도메인 등록](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>PayPal의 샌드박스 결제 처리가 느려지고 서비스가 가끔 다운될 수 있습니다. 이러한 상황은 실시간 상품 결제 처리의 신속성과 효율성을 나타내는 것이 아니다.

## 프로덕션에서 테스트

테스트하는 것이 좋습니다. [!DNL Payment Services] 실제 신용 카드와 은행으로 생산 시 이 기능을 쇼핑객에게 노출하기 전에. 테스트라도 [!DNL Payment Services] 샌드박스에서 는 중요합니다. 프로덕션에서 테스트하는 것은 품질을 보장하기 위한 가장 어리석은 방법입니다 [!DNL Payment Services] 예상대로 작동합니다.

테스트할 수 있습니다. [!DNL Payment Services] 다음 두 가지 방법 중 하나로 프로덕션에서:

* 구매자가 주문을 하지 않을 때를 선택합니다.
* 일시적으로 쇼핑객에게 액세스할 수 없지만 테스트를 위해 액세스할 수 있는 웹 스토어를 사용하십시오.

실제 신용 카드 및 PayPal 계정으로 프로덕션 테스트를 완료하고 캡처 및 환불을 포함한 전체 결제 라이프사이클을 테스트합니다. 테스트 중에 전체 체크아웃 및 결제 플로우를 완료하면 의 방법을 가장 명확하게 파악할 수 있습니다. [!DNL Payment Services] 기능은 라이브 쇼핑객이 사용할 때 작동합니다.

또한 생산 테스트에 사용하는 결제 방법에 대한 은행 거래 명세서에 표시되는 정보가 정확하고 예상되는지 확인해야 합니다(비즈니스 설명 포함).

프로덕션 모드에서 Apple 페이를 테스트하려면 다음을 수행해야 합니다 [프로덕션 도메인 등록](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
