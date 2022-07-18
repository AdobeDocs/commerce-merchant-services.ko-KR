---
title: 결제 서비스 설정
description: 설치 후 다음을 구성할 수 있습니다 [!DNL Payment Services] '홈'
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 7c02bb8dcb7b5daa68664bd12672ac389f84cfa1
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---

# 설정

사용자 지정할 수 있습니다 [!DNL Payment Services] 의 유용한 설정을 사용하여 [!DNL Payment Services] 집에

구성하려면 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] click **[!UICONTROL Settings]**. 이러한 구성 옵션은 _[!UICONTROL Payment mode]_일반 설정의 필드.

자세한 내용은 [[!UICONTROL General] 설정 섹션](#general-settings) 추가 정보.

>[!IMPORTANT]
>
> 다중 저장소 또는 레거시 구성의 경우 다음을 참조하십시오 [관리자에서 구성](configure-admin.md) 주제.

## 결제 서비스 활성화

다음을 활성화할 수 있습니다 [!DNL Payment Services] 웹 사이트에 대해 를 설정하고, [!UICONTROL General] 섹션을 참조하십시오.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![홈 보기](assets/payment-services-menu-small.png)

1. 클릭 **[!UICONTROL Settings]**. 자세한 내용은 [소개 [!DNL Payment Services] 홈](payments-home.md) 추가 정보.

   다음 _[!UICONTROL General]_섹션에는 사용 가능한 설정이 포함되어 있습니다. [!DNL Payment Services] 를 결제 방법으로 사용할 수 있습니다.

1. 활성화하려면 [!DNL Payment Services] 스토어에 대한 결제 방법으로 전환(**[!UICONTROL Enable Payment Services as payment method]**) `Yes`.

1. 아직 테스트 중인 경우 [!DNL Payment Services] 스토어에 대해 **결제 모드** to `Sandbox`. Live Payments를 사용할 준비가 된 경우 로 설정합니다. `Production`.

   >[!WARNING]
   >
   >사용자 _[!UICONTROL Sandbox Merchant ID]_및_[!UICONTROL Production Merchant ID]_ 샌드박스 및/또는 프로덕션에 대한 온보딩을 마치면 자동으로 생성되어 해당 어량 필드에 표시됩니다. 이러한 ID를 제거하거나 변경하지 마십시오.

1. 저장소 보기에서 **[!UICONTROL Scope]** 드롭다운 메뉴에서 결제 방법을 사용할 수 있습니다.
1. 결제 기능 및 상점 표시에 대한 기본 설정을 변경하려면 필요에 따라 추가 옵션을 설정합니다.

   - [신용 카드 필드](#credit-card-fields)
   - [결제 단추](#payment-buttons)
   - [단추 스타일](#button-style)

1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

### 신용 카드 필드

다음 _[!UICONTROL Credit Card Fields]_설정은 신용 카드 또는 직불 카드 결제 방법에 대해 간단하고 안전한 체크아웃 옵션을 제공합니다.

자세한 내용은 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

1. 체크아웃 중에 표시되는 결제 방법의 이름을 변경하려면 **[!UICONTROL Checkout title]** 필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 전환 **[!UICONTROL Payment action]** to `Authorize` 또는 `Authorize and Capture`.
1. 디버그 모드를 활성화하려면 **[!UICONTROL Debug Mode]** 선택기.

   디버그 모드를 활성화하면 신용 카드 결제에 대한 추가 디버깅 정보가 `var/log/payment.log` 파일. 이 정보를 통해 문제를 해결하는 데 도움이 되도록 특정 지급에 대한 자세한 통찰력을 얻을 수 있습니다.

1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

### 결제 단추

다음 [!DNL PayPal Smart Buttons] 결제 옵션은 고객을 위한 간단하고 빠르고 안전한 체크아웃 프로세스를 제공합니다. 자세한 내용은 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

지급 버튼을 활성화하고 구성할 수 있습니다.

1. 체크아웃 중에 표시된 대로 결제 방법의 이름을 변경하려면 **[!UICONTROL Checkout Title]** 필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 전환 **[!UICONTROL Payment action]** to `Authorize` 또는 `Authorize and Capture`.
1. 토글 선택기를 사용하여 활성화하거나 비활성화합니다 [!DNL PayPal smart button] 디스플레이 기능:
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons on mini cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show Venmo button]**

1. 를 변경하려면 [나중에 메시지 결제](payments-options.md#pay-later-button), 전환 **[!UICONTROL Show PayPal Pay Later message]** 선택 사항입니다.
1. 디버그 모드를 활성화하려면 **[!UICONTROL Debug Mode]** 선택기.

   디버그 모드를 활성화하면 PayPal 결제에 대한 추가 디버깅 정보가 `var/log/payment.log` 파일. 이 정보를 통해 문제를 해결하는 데 도움이 되도록 특정 지급에 대한 자세한 통찰력을 얻을 수 있습니다.

1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

#### 단추 스타일

를 구성할 수도 있습니다 _[!UICONTROL Button style]_결제 버튼의 옵션:

1. 를 변경하려면 **[!UICONTROL Layout]**, 선택 `Vertical` 또는 `Horizontal`.

   >[!NOTE]
   >
   > 단추 스타일이 `Horizontal` 그리고 스토어에 여러 개의 결제 버튼이 표시되도록 구성되었으며, 제품 페이지, 체크아웃 페이지, 미니 장바구니에 표시되는 버튼이 두 개, 장바구니에 표시되는 버튼이 한 개만 표시될 수 있습니다.

1. 가로 레이아웃에서 태그라인을 활성화하려면 **[!UICONTROL Show tagline]** 선택기.
1. 를 수정하려면 **[!UICONTROL Color]**&#x200B;원하는 색상 옵션을 선택합니다.
1. 를 수정하려면 **[!UICONTROL Shape]**, 선택 `Pill` 또는 `Rect`.
1. 단추 높이 선택기를 활성화하려면 **[!UICONTROL Responsive button height]** 선택기.
1. 를 수정하려면 **[!UICONTROL Label]**&#x200B;원하는 레이블 옵션을 선택합니다.
1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

다음을 구성할 수 있습니다 [!DNL PayPal Smart Buttons] 관리자 또는 [!DNL Payment Services Home]. 자세한 내용은 [PayPal 단추 스타일 가이드](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 추가 정보.
