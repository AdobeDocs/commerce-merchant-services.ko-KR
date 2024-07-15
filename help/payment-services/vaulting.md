---
title: 신용 카드 보관
description: 구매자는 향후 구매를 위해 신용 카드 세부 정보를 저장(저장)할 수 있습니다.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# 신용 카드 보관

신용 카드 소산을 통해 일회성 고객을 단골 쇼핑객으로 전환합니다. 구매자는 체크아웃 중에 신용 카드 자격 증명을 저장(또는 &quot;자격 증명 모음&quot;)하여 동일한 가맹점 계정 내에서 나중에 동일한 또는 다른 용도로 사용할 수 있습니다.

![나중에 사용할 수 있도록 신용 카드 저장](assets/save-card-for-later.png){width="400" zoomable="yes"}

구매자는 저장된 토큰을 사용하여 저장된 신용 카드 정보로 향후 체크아웃을 완료합니다.

![나중에 구입할 수 있도록 저장된 자격 증명 사용](assets/use-stored-card.png){width="400" zoomable="yes"}

또한 저장된 신용 카드를 내 계정의 [저장된 결제 방법](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html)에서 쉽게 삭제할 수 있습니다.

![내 계정에 저장된 결제 방법](assets/stored-payment-methods.png){width="400" zoomable="yes"}

>[!WARNING]
>
>PayPal은 현재 최대 5개의 저장된 카드를 저장할 수 있습니다.

## 보관 사용

[!DNL Payment Services] [설정](settings.md#card-vaulting)의 상점에 대해 관리자의 고객 _및_ 가맹점에 대해 신용 카드 보관 기능을 활성화할 수 있습니다.

## 관리자에서 보관 사용

고객이 이전에 저장된 신용 카드를 보유한 경우, 머천트는 저장된 결제 방법을 사용하여 관리자에서 해당 고객에 대한 후속 주문을 생성할 수 있습니다.

고객이 기존 계정과 이전에 완료된 결제 후 시스템에 저장된 유효한 토큰이 모두 있는 경우에만 관리자의 저장된 카드를 사용할 수 있습니다.

저장된 신용 카드를 사용하는 고객을 위해 관리자에서 주문을 생성하려면:

1. [주문을 만들고 제품을 추가](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html)합니다.
1. _[!UICONTROL Payment & Shipping Information]_에서&#x200B;**[!UICONTROL Stored Cards]**을(를) 결제 방법으로 선택합니다.
1. 원하는 저장된 신용 카드 결제 방법을 선택합니다.
1. 주문에 필요한 다른 단계를 완료한 후 [제출하세요](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![고객을 위해 관리자의 저장된 신용 카드 사용](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## 보안

최소 신용 카드 정보는 쇼핑객과 공유됩니다. 쇼핑객은 저장한 신용 카드의 마지막 네 자리, 만료일 및 브랜드만 볼 수 있습니다. 신용 카드 정보는 [PCI](security.md#PCI-compliance) 준수 표준을 충족하도록 결제 공급자와 함께 저장됩니다.
