---
title: 신용 카드 보관
description: 구매자는 향후 구매를 위해 신용 카드 세부 정보를 저장(저장)할 수 있습니다.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# 신용 카드 보관

신용 카드 소산을 통해 일회성 고객을 단골 쇼핑객으로 전환합니다. 구매자는 체크아웃 중에 신용 카드 자격 증명을 저장(또는 &quot;자격 증명 모음&quot;)하여 동일한 가맹점 계정 내에서 나중에 동일한 또는 다른 용도로 사용할 수 있습니다.

![나중에 사용할 수 있도록 신용 카드 보관](assets/save-card-for-later.png)

구매자는 저장된 토큰을 사용하여 저장된 신용 카드 정보로 향후 체크아웃을 완료합니다.

![저장된 자격 증명을 사용하여 향후 구매](assets/use-stored-card.png)

또한 저장된 신용 카드도 쉽게 삭제할 수 있습니다. [저장된 결제 방법](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 내 계정에 있어야 합니다.

![내 계정에 저장된 결제 방법](assets/stored-payment-methods.png)

## 보관 사용

고객에 대해 신용 카드 소산을 활성화할 수 있습니다 _및_ 관리자의 판매자—의 스토어에 대한 [!DNL Payment Services] [설정](settings.md#card-vaulting).

## 관리자에서 보관 사용

고객이 이전에 저장된 신용 카드를 보유한 경우, 머천트는 저장된 결제 방법을 사용하여 관리자에서 해당 고객에 대한 후속 주문을 생성할 수 있습니다.

고객이 기존 계정과 이전에 완료된 결제 후 시스템에 저장된 유효한 토큰이 모두 있는 경우에만 관리자의 저장된 카드를 사용할 수 있습니다.

저장된 신용 카드를 사용하는 고객을 위해 관리자에서 주문을 생성하려면:

1. [주문 만들기 및 제품 추가](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. 위치 _[!UICONTROL Payment & Shipping Information]_, 선택&#x200B;**[!UICONTROL Stored Cards]**를 결제 방법으로 사용하십시오.
1. 원하는 저장된 신용 카드 결제 방법을 선택합니다.
1. 주문에 필요한 다른 단계를 완료한 후, [제출](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![고객을 위해 Admin에서 저장된 신용 카드 사용](assets/admin-vaultedcard.png)

## 보안

최소 신용 카드 정보는 쇼핑객과 공유됩니다. 쇼핑객은 저장한 신용 카드의 마지막 네 자리, 만료일 및 브랜드만 볼 수 있습니다. 신용 카드 정보는 결제 제공업체에 저장되어 충족됩니다 [PCI](security.md#PCI-compliance) 규정 준수 표준.
