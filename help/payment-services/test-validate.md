---
title: 테스트 및 유효성 검사
description: 테스트 및 유효성 검사 기능을 통해 [!DNL Payment Services] 함수는 예상대로 작동하며 고객에게 최상의 결제 옵션을 제공합니다
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# 테스트 및 유효성 검사

노출되기 전에 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 고객에게 샌드박스 환경에서 테스트하는 것이 좋습니다 _및_ 제작 중입니다. 테스트 및 유효성 검사 기능을 통해 [!DNL Payment Services] 함수는 예상대로 작동하며 스토어 및 고객을 위한 최상의 결제 옵션을 제공합니다.

## 샌드박스 환경에서 테스트

테스트 [!DNL Payment Services] 샌드박스 환경에서는 실제 은행과 상인이 아닌 PayPal 샌드박스에만 연결된 시뮬레이션된 환경이지만 중요한 유효성 검사 단계입니다.

1. 다음 중 하나를 사용하여 저장소에서 성공적인 체크아웃을 완료합니다 [신용 카드 필드](payments-options.md#credit-card-fields) 또는 [PayPal 스마트 단추](payments-options.md#paypal-smart-buttons). 자세한 내용은 [자격 증명 테스트](#testing-credentials) 를 참조하십시오.
1. 캡처(결제 작업이 [설정 `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [환급](refunds.md), 또는 [void](voids.md) 방금 완료된 주문입니다. 또한 간단하게 [송장 생성](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} 주문의 경우, 지급 조치가 `Authorize` 대신 `Authorize and Capture`.
1. 24-48시간 이내에 [결제 보고서](payouts.md).
1. 주문 세부 사항을 [주문 결제 상태 보고서](order-payment-status.md).

### 자격 증명 테스트

샌드박스를 테스트하고 확인할 때 기존 신용 카드 계정에 실제 비용을 생성하지 않도록 위조 신용 카드 번호를 사용해야 합니다.

PayPal 신용 카드 생성기를 사용하여 다음을 수행할 수 있습니다 [임의 신용 카드 정보 생성](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) 테스트 대상입니다.

샌드박스 모드에서 Apple Pay를 테스트하려면 다음을 수행해야 합니다 [Apple 개발자 계정](https://developer.apple.com/programs/enroll/)와 함께 신용 카드 및 청구 정보를 위조하십시오.

>[!NOTE]
>
>PayPal의 샌드박스 결제 처리 속도가 느려질 수 있으며 가끔 서비스가 중단되기도 합니다. 이 상황은 라이브제품 결제 처리 속도와 효율성을 나타내지 않습니다.

## 프로덕션 테스트

테스트하는 것이 좋습니다 [!DNL Payment Services] 실제 신용카드 및 은행과 함께 운영 중인 Dell Mobile Services에서 이 기능을 구매자에게 노출하기 전에 테스트 후에도 [!DNL Payment Services] 샌드박스에서 테스트하는 것이 중요하며, 프로덕션에서 테스트하는 것이 가장 어리석은 방법입니다 [!DNL Payment Services] 는 예상대로 작동합니다.

테스트를 수행할 수 있습니다 [!DNL Payment Services] 다음 두 가지 방법 중 하나로 프로덕션에서 사용할 수 있습니다.

* 쇼핑하는 사람이 주문을 하지 않을 때를 선택하세요.
* 일시적으로 구매자가 액세스할 수 없지만 테스트를 위해 액세스할 수 있는 웹 스토어를 사용합니다.

실제 신용 카드 및 PayPal 계정을 사용하여 프로덕션 테스트를 완료하고 캡처 및 환불을 포함한 전체 지급 수명 주기를 테스트합니다. 테스트 중에 전체 체크아웃 및 결제 흐름을 완료하면 사용자의 [!DNL Payment Services] 라이브 쇼핑 고객이 이 기능을 사용하면 기능이 작동합니다.

또한 생산 테스트에 사용하는 지급 방법에 대한 은행 명세서에 표시되는 정보가 올바르고 예상된(업무 내용 포함)인지 확인해야 합니다.

>[!NOTE]
>
>Apple Pay에 대한 프로덕션 테스트를 완료하려면 영업 팀에 연락하여 프로덕션 환경에 Apple Pay를 사용하도록 설정해야 합니다.
