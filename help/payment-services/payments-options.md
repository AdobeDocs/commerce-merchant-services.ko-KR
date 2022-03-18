---
title: 결제 옵션
description: 결제 옵션을 설정하여 스토어 고객에게 사용 가능한 방법을 사용자 정의합니다.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 9aa701e006a7f107775679f156f84d3e2fdc153b
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---

# 결제 옵션

Adobe Commerce 및 Magento Open Source 사용 [!DNL Payment Services], 여러 가지 결제 옵션을 사용할 수 있습니다. 관리자 저장소 구성에서 이러한 옵션을 설정합니다(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)**[!UICONTROL Sales]**, 선택&#x200B;**[!UICONTROL Payment Method]s**그리고_[!UICONTROL Recommended Solutions]_ 클릭합니다.

![결제 방법 보기](assets/methods-view.png)

체크아웃 프로세스 위치에 따라 각 결제 방법에 대해 다양한 동작이 있습니다.

* 제품 페이지 - 항목의 제품 페이지입니다
* Mini-cart - 제품이 장바구니에 추가되면 장바구니 아이콘을 클릭하면 사용할 수 있습니다
* 장바구니 - _장바구니 보기 및 편집_ 미니 카트에서
* 체크 아웃 뷰 - 를 클릭하면 사용할 수 있습니다. _체크아웃으로 이동_ 미니 장바구니 또는 장바구니에서

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] 신용 카드 또는 직불 카드 결제 방법에 대해 간단하고 안전한 체크아웃을 제공합니다. 쇼핑객이 신용 카드 필드를 사용하여 체크아웃할 때, 주문하기 위해 이름, 청구 주소 및 신용 또는 직불 카드 정보를 입력합니다. 이 고객의 고객 정보는 구매 세션 중에 안전하게 사용되어 체크아웃 플로우를 원활하게 안내합니다.

다음을 구성할 수 있습니다 [!UICONTROL Credit Card Fields] 관리자. 자세한 내용은 [구성 [!DNL Payment Services]](configure-admin.md#configure-credit-card-fields) 추가 정보.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons]- PayPal을 사용하여 구매를 완료하고, 구매자의 배송 주소, 청구 주소 및 결제 세부 정보를 저장하여 나중에 사용할 수 있습니다. 쇼핑객은 이전에 PayPal에서 저장하거나 제공하는 모든 결제 방법을 사용할 수 있습니다.

다음을 구성할 수 있습니다 [!DNL PayPal Smart Buttons] 관리자. 자세한 내용은 [구성 [!DNL Payment Services]](configure-admin.md#configure-paypal-smart-buttons) 추가 정보.

### PayPal 단추

고객은 PayPal 버튼을 사용하여 쉽고 편리하게 체크아웃할 수 있습니다.

PayPal 단추는 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 볼 수 있습니다.

### 벤 단추

고객은 를 사용하여 체크아웃할 수 있습니다. [벤](https://venmo.com/) 버튼을 클릭합니다.

벤 단추는 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 볼 수 있습니다.

### [!DNL Pay Later] 버튼

고객에게 단기, 무이자 결제 및 기타 금융 옵션을 제공하여 고객이 지금 구입하여 나중에 [!DNL Pay Later] 버튼을 클릭합니다.

다음 [!DNL Pay Later] 버튼은 제품 페이지, 미니 장바구니, 장바구니 및 체크아웃 보기에서 볼 수 있습니다.

다음과 같은 두 가지 결제 옵션이 있습니다 [!DNL Pay Later] 버튼:

* **4달러 결제**- 고객은 초기 다운결제 후 4개의 무이자 지급(2주마다)으로 주문 잔액을 지급할 수 있습니다. 자세한 내용은 [4개의 문서로 결제](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) 추가 정보.
* **PayPal 신용**—고객이 6개월 동안 주문 잔액을 전액 상환하여 무이자 혜택을 받을 수 있습니다. 자세한 내용은 [PayPal 신용 문서](https://www.paypal.com/us/webapps/mpp/paypal-credit) 추가 정보.

### [!DNL Pay Now] 버튼

다음 [!DNL Pay Now] 고객이 결제 화면에서 결제 버튼을 클릭하면 PayPal 팝업 창에 버튼이 표시됩니다.

최종 주문 금액이 아직 알려지지 않은 경우(배송 주소 정보가 아직 없는 경우 등) 고객이 제품 페이지, 미니 장바구니 또는 장바구니에서 체크아웃 중인 경우, _계속_ 버튼을 대신 사용할 수 있습니다. 고객이 클릭하면 _계속_&#x200B;를 설정하고 결제 방법을 확인한 후 체크아웃을 완료하기 전에 필요한 세부 정보를 수집하도록 주문 검토 페이지로 이동합니다.

## [!DNL Pay Later] 메시지

고객이 이러한 옵션을 잠재적인 결제 옵션으로 식별하도록 지원하려면 [!DNL Pay Later] 메시징은 제품 페이지, 미니 장바구니 및 장바구니에서, 체크아웃 중에 표시됩니다.

* **고객이 $30에서 $600 사이의 제품을 선택하는 경우**, PayPal 및 [!DNL Pay Later] 버튼은 4개의 지급 옵션에 대한 자세한 정보를 고객에게 제공합니다. 고객이 **추가 정보** &quot;4인 지불&quot; 옵션에 대해 알아보기 _또는_ 팝업에서 &quot;6개월 특별 자금 조회&quot; 텍스트를 클릭하여 PayPal 신용 옵션에 대해 알아보고 적용합니다.
* **고객이 $98.99를 초과하는 제품 또는 제품을 선택한 경우**, PayPal 및 [!DNL Pay Later] 버튼은 PayPal 신용 결제 옵션에 대한 자세한 정보를 고객에게 제공합니다. 고객이 **추가 정보** PayPal 신용 옵션에 대해 알아보고 신청하려면 _또는_ 팝업에서 &quot;Or see Pay in 4&quot; 텍스트를 클릭하여 Pay in 4 옵션에 대해 알아봅니다.

   >[!NOTE]
   >
   >위에 나열된 금액은 변경될 수 있습니다.

자세한 내용은 [구성 [!DNL Payment Services]](configure-admin.md#configure-paypal-smart-buttons) 를 비활성화하거나 활성화하는 방법을 알아봅니다. [!DNL Pay Later] 메시지를 표시합니다.

## 주문 재계산

고객이 미니 장바구니, 장바구니 또는 제품 페이지에서 체크아웃 플로우를 입력하면 PayPal 팝업 창에서 선택한 배송 주소를 볼 수 있는 주문 검토 페이지로 이동합니다. 고객이 운송 방법을 선택하면 주문 금액이 적절하게 재계산되며 고객이 운송 비용과 세금을 볼 수 있습니다.

고객이 체크아웃 페이지에서 체크아웃 플로우를 입력하면 시스템은 이미 배송 주소와 최종 계산된 금액을 알고 있으며 합계가 적절히 표시됩니다.

공휴일, 배송비, 판매세는 위치마다 다를 수 있다. 후 [!DNL Payment Services] 배송 주소와 비율을 받으면 적용 가능한 모든 비용을 빠르게 다시 계산하여 체크아웃의 마지막 단계 동안 적절히 표시합니다.

## 제품 페이지에서 체크아웃

고객이 제품 페이지에서 직접 체크 아웃할 때 PayPal 또는 [!DNL Pay Later] 버튼만, 현재 제품 페이지에 표시되는 항목만 구매됩니다. 고객의 장바구니에 이미 있는 항목은 체크아웃 흐름에 추가되지 않으며 구매되지 않습니다.

고객이 주문을 취소하면 현재 제품 페이지의 항목이 고객의 장바구니에 추가되어 장바구니에 있는 다른 모든 항목에 연결됩니다. 이 기능을 사용하면 제품을 검색할 때 이전에 장바구니에 추가한 다른 항목을 그대로 유지하면서 현재 보고 있는 항목을 빠르게 구매할 수 있습니다.

고객이 제품 페이지에서 체크아웃 플로우를 입력하면 체크아웃 페이지가 단순화됩니다. 이 보기에는 주문 관련 데이터 및 옵션만 표시됩니다.

## 보안

자세한 내용은 [PCI 규정 준수](security.md#pci-compliance) 추가 정보.
