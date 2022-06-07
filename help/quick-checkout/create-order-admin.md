---
title: '"주문 만들기 [!DNL Quick Checkout] 관리자'
description: '"관리자는 [!DNL Quick Checkout] 지원이 필요한 고객을 위해 상인이 직접 관리자에게 문의합니다."'
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 1%

---

# 주문 만들기 [!DNL Quick Checkout]

다음을 구성할 수 있습니다 [!DNL Quick Checkout] 필요에 맞게 Adobe Commerce 관리자의 옵션을 사용합니다.

[!DNL Quick Checkout] Adobe Commerce 및 Magento Open Source의 경우 지원이 필요한 고객을 위해 관리자로부터 직접 주문을 받을 수 있습니다. 다음 **[!UICONTROL Create New Order]** 양식에는 신용 카드 정보를 캡처하기 위한 보안 신용 카드 양식을 포함하여 일반적인 체크아웃 프로세스를 완료하는 데 필요한 모든 정보가 포함됩니다. 자세한 내용은 [주문 만들기](https://docs.magento.com/user-guide/customers/customer-account-create-order.html){target=&quot;_blank&quot;} 을 참조하십시오.

## 호스팅된 신용 카드 필드

고객을 대신하여 주문을 할 때 [!DNL Quick Checkout] 은 사용 가능한 결제 방법 옵션 중 하나로 나타납니다.

1. 설정 _관리_ 사이드바, 확장 **[!UICONTROL Sales]** 및 **[!UICONTROL Orders]**.
1. 클릭 **[!UICONTROL Create New Order]**.
1. 주문에 대해 필요한 섹션을 완료합니다(자세한 내용은 [주문 만들기](https://docs.magento.com/user-guide/customers/customer-account-create-order.html){target=&quot;_blank&quot;}).
1. 에서 _[!UICONTROL Payment Method]_섹션에서 [!DNL Quick Checkout] 결제 방법으로 사용
1. 클릭 **[!UICONTROL Submit Order]**.

>[!IMPORTANT]
>
> EAP(Early Adopter Program) 동안 사용자는 OTP 로그인을 사용하여 배송 및 결제 세부 정보를 자동으로 입력할 수 없습니다.
