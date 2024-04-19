---
title: 결제 옵션
description: 스토어 고객이 사용할 수 있는 방법을 사용자 지정하려면 결제 옵션을 설정하십시오.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 5c4fe370507e4154d4495d4c09e2ff8705e53191
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---

# 결제 옵션

포함 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] [!DNL Payment Services], 여러 결제 옵션을 사용할 수 있습니다.

다음에서 이러한 결제 옵션을 구성할 수 있습니다. [홈 설정](payments-home.md) 또는 [구성 저장](configure-admin.md) (기존 결제 옵션 또는 다중 스토어 설정에 권장됨).

체크아웃 프로세스의 위치에 따라 각 결제 방법마다 다른 동작이 있습니다.

* 제품 페이지 - 항목에 대한 제품 페이지
* 미니 장바구니 - 제품이 장바구니에 추가되었을 때 장바구니 아이콘을 클릭하면 사용할 수 있습니다.
* 장바구니 - 클릭 시 사용 가능 _장바구니 보기 및 편집_ 미니 장바구니에서
* 체크아웃 보기 - 다음 클릭 시 사용 가능 _체크아웃 진행_ 미니 카트 또는 장바구니에서

>[!IMPORTANT]
>
>[!DNL Payment Services] 결제를 처리하려면 먼저 온보딩을 완료해야 합니다.

## 표준 및 고급 결제 경험 비교

[!DNL Payment Services] 다음을 제공합니다 **고급** (완전히 지원됨) 및 **표준** (Express Checkout) 결제 옵션 및 온보딩 플로우는 운영하는 국가에 따라 다릅니다.

* **고급** - 모두 사용 가능 [결제 옵션](../payment-services/payments-options.md) 현재에 사용 가능 [완전히 지원되는 국가](../payment-services/overview.md#availability). 실시간 결제를 활성화하려면 온보딩 중에 [고급 온보딩 옵션](../payment-services/production.md#advanced-onboarding).
* **표준** - 일부 결제 옵션(Express Checkout) - PayPal 신용 카드 및 직불 카드는 지원되는 다른 국가에서 사용할 수 있습니다. [신용 카드 필드](#credit-card-fields) 및 [Apple 페이](#apple-pay-button) 이 온보딩 옵션에는 사용할 수 없습니다. 실시간 결제를 활성화하려면 온보딩 중에 [표준 온보딩 옵션](../payment-services/production.md#standard-onboarding).

다음을 참조하십시오 [사용 [!DNL Payment Services] 프로덕션용](../payment-services/production.md#complete-merchant-onboarding) 고급 및 표준 온보딩 완료에 대한 자세한 정보.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] 신용 카드 또는 직불 카드 결제 방법을 위한 간단하고 안전한 체크아웃을 제공합니다. 쇼핑객이 신용 카드 필드를 사용하여 체크아웃할 때 구매자의 이름, 청구 주소 및 신용 또는 직불 카드 정보를 입력하여 주문합니다. 고객 정보는 구매 세션 중에 안전하게 사용되어 체크아웃 흐름을 원활하게 안내합니다.

![체크아웃 시 신용 카드 필드](assets/credit-card-fields.png){width="500" zoomable="yes"}

사용 [신용 카드 소산](#vaulting) 스토어에서 구매자가 나중에 빠른 체크아웃을 위해 신용 카드 정보를 저장(저장)할 수 있도록 할 수 있습니다.

다음을 구성할 수 있습니다. [!UICONTROL Credit Card Fields] 저장소 구성 또는 [!DNL Payment Services] 집. 다음을 참조하십시오 [설정](settings.md#credit-card-fields) 추가 정보.

신용 카드 필드의 레이아웃, 너비, 높이 및 외부 스타일을 변경할 수도 있습니다. 다음을 참조하십시오 [PayPal 설명서](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) 추가 정보.

## [!DNL Apple Pay] 단추

고객은 다음을 사용할 수 있습니다 [[!DNL Apple Pay]](https://www.apple.com/apple-pay/)- iOS 또는 macOS 장치에 저장된 신용 카드 및 직불 카드 결제 자격 증명을 사용하여 구매합니다.

[!DNL Apple Pay] 는 Safari 브라우저에서만 사용할 수 있습니다. 가맹점은 가맹점 계좌당 최대 99개의 도메인을 추가할 수 있다.

![미니카트의 Apple 결제 버튼](assets/applepay-button.png){width="500" zoomable="yes"}

다음 [!DNL Apple Pay] 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 버튼이 표시됩니다.

>[!NOTE]
>
> 사용 [!DNL Apple Pay] 스토어의 경우, 완료 [을 사용한 자가 등록 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_라이브 도메인 등록_ 섹션만 해당) 및 [스토어에 맞게 구성 [!DNL Payment Services]](settings.md#payment-buttons).

다음을 구성할 수 있습니다. [!UICONTROL Apple Pay] 저장소 구성 또는 결제 서비스 홈에서 사용할 수 있습니다. 다음을 참조하십시오 [설정](settings.md#apple-pay) 추가 정보.

## [!DNL Google Pay] 단추

고객은 다음을 사용할 수 있습니다 [[!DNL Google Pay]](https://pay.google.com/about/) Google 계정에 결제 세부 사항을 추가하여 안전하게 저장함으로써 원활한 체크아웃 환경을 제공할 수 있습니다.

[!DNL Google Pay] 는 특정 국가 또는 지역 및 특정 디바이스에서만 사용할 수 있습니다. 다음을 참조하십시오 [[!DNL Google Pay] 설명서](https://developer.paypal.com/docs/checkout/apm/google-pay/#link-googlepayintegration) 추가 정보.

![체크아웃 시 Google 결제 버튼](assets/google-pay-button.png){width="500" zoomable="yes"}

다음 [!DNL Google Pay] 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 버튼이 표시됩니다.

다음을 구성할 수 있습니다. [!UICONTROL Google Pay] 저장소 구성 또는 결제 서비스 홈에서 사용할 수 있습니다. 다음을 참조하십시오 [설정](configure-admin.md) 추가 정보.

>[!NOTE]
>
> 다음 [!DNL Google Pay] API는 보안 컨텍스트의 웹 사이트에서만 사용할 수 있습니다. 다음을 참조하십시오 [문제 해결](https://developers.google.com/pay/api/web/support/troubleshooting) 설명서 를 참조하십시오.

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons]: PayPal을 사용하여 구매를 완료하고 나중에 사용할 수 있도록 쇼핑객의 배송 주소, 청구 주소 및 결제 세부 정보를 저장합니다. 쇼핑객은 PayPal에서 이전에 저장하거나 제공하는 결제 방법을 사용할 수 있습니다.

![PayPal 단추](assets/paypal-button.png){width="350" zoomable="yes"}

다음을 구성할 수 있습니다. [!UICONTROL PayPal payment buttons] 저장소 구성 또는 [!DNL Payment Services] 집. 다음을 참조하십시오 [설정](settings.md#payment-buttons) 추가 정보.

PayPal에서 국가별 결제 방법을 사용할 수 있는지 알아보기 [결제 방법 설명서](https://developer.paypal.com/docs/checkout/payment-methods/).

### [!DNL PayPal] 단추

고객은 PayPal 버튼을 사용하여 쉽고 안전하게 체크아웃할 수 있습니다.

다음 [!DNL PayPal] 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 버튼이 표시됩니다.

### [!DNL Venmo] 단추

고객은 다음을 사용하여 체크아웃할 수 있습니다 [벤모](https://venmo.com/) 단추를 클릭합니다.

다음 [!DNL Venmo] 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 버튼이 표시됩니다.

### PayPal 직불 또는 신용카드 단추

고객은 PayPal 직불 또는 신용카드 버튼을 사용하여 체크아웃할 수 있습니다.

PayPal 직불 또는 신용 카드 버튼은 체크아웃 페이지에서 볼 수 있습니다.

이 옵션은 신용카드 통합에 대한 대안으로 PayPal 호스팅 버튼을 사용하여 구매자에게 직불 또는 신용카드 결제 옵션을 제공하는 데 사용할 수 있습니다.

### [!DNL Pay Later] 단추

고객에게 단기, 무이자 결제 및 기타 금융 옵션을 제공하여 지금 구입하고 나중에 다음과 같이 결제할 수 있도록 하십시오. [!DNL Pay Later] 단추를 클릭합니다.

다음 [!DNL Pay Later] 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 버튼이 표시됩니다.

다음에서 나중에 결제 오퍼에 대한 정보를 참조하십시오. [PayPal의 Pay Later 오퍼 설명서](https://developer.paypal.com/docs/checkout/pay-later/us/). 사용 **국가 또는 지역** 드롭다운을 통해 관심 영역을 선택합니다.

을(를) 비활성화하거나 활성화하는 방법에 대해 알아보기 [!DNL Pay Later] 를 업데이트하여 메시지 보내기 [설정](settings.md#payment-buttons) 구성.

## PayPal 결제 버튼만 사용

스토어를 프로덕션 모드로 빠르게 전환하려면 다음을 구성할 수 있습니다. _전용_ PayPal 결제 단추(Venmo, PayPal 등)—PayPal 신용카드 결제 옵션을 사용하지 않습니다.

이를 통해 다음을 수행할 수 있습니다.

* Venmo 및 PayPal 결제 버튼을 포함하여 고객을 위한 다양한 결제 옵션을 제공하고, PayPal 호스팅 카드 필드를 끄고 기존 신용카드 제공업체를 사용할 수 있는 옵션을 제공합니다.
* PayPal의 기타 결제 옵션을 사용하면서 신용 카드 결제를 위해 기존 신용카드 제공업체를 이용하십시오.
* PayPal이 신용 카드를 지원하지 않는 지역의 PayPal 결제 버튼을 결제 옵션으로 사용합니다.

종료 **다음을 사용하여 결제 캡처 _전용_ PayPal 결제 단추(_아님_ payPal 신용카드 결제 옵션)**:

1. 저장소가 다음과 같은지 확인합니다. [프로덕션 모드에서](settings.md#enable-payment-services).
1. [원하는 PayPal 결제 버튼 구성](settings.md#payment-buttons) 설정 을 참조하십시오.
1. 회전 _끔_ 다음 **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** 의 옵션 _[!UICONTROL Payment buttons]_섹션.

종료 **기존 신용 카드 공급자로 결제 캡처 _및_ PayPal 결제 단추**:

1. 저장소가 다음과 같은지 확인합니다. [프로덕션 모드에서](settings.md#enable-payment-services).
1. [원하는 PayPal 결제 버튼 구성](settings.md#payment-buttons).
1. 회전 _끔_ 다음 **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** 의 옵션 _[!UICONTROL Payment buttons]_섹션.
1. 회전 _끔_ 다음 **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** 의 옵션 _[!UICONTROL Credit card fields]_섹션 및 사용 [기존 신용카드 제공업체 계정](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## 주문 다시 계산

고객이 미니 장바구니, 장바구니 또는 제품 페이지에서 체크아웃 플로우를 입력하면 PayPal 팝업 창에서 선택한 배송 주소를 볼 수 있는 주문 검토 페이지로 이동합니다. 고객이 배송 방법을 선택한 후 주문 금액이 적절하게 재계산되어 배송비와 세금을 볼 수 있습니다.

고객이 체크아웃 페이지에서 체크아웃 플로우를 입력하면 시스템에서 배송 주소와 최종 계산된 금액을 이미 알고 있으며 합계가 적절히 표시됩니다.

납세의무자, 운송비, 판매세는 장소마다 매우 다양할 수 있다. 다음 이후 [!DNL Payment Services] 배송 주소 및 요금을 받으면 적용 가능한 모든 비용을 빠르게 다시 계산하고 체크아웃 마지막 단계에서 적절하게 표시합니다.

## 신용 카드 보관

구매자는 웹 사이트 수준(동일한 가맹점 계정 내 모든 매장)에서 향후 구매를 위해 신용 카드 정보를 저장(저장)할 수 있습니다.

다음을 참조하십시오 [신용 카드 보관](vaulting.md) 추가 정보.

## 보안

다음을 참조하십시오 [PCI 준수](security.md#pci-compliance) 추가 정보.
