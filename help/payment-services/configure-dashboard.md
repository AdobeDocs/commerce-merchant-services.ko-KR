---
title: 대시보드에서 구성
description: 설치 후 다음을 구성할 수 있습니다 [!DNL Payment Services] 을 클릭합니다.
role: Admin, User
level: Intermediate
exl-id: 015c5c8c-8184-45c1-932a-f4365ddf5a30
source-git-commit: 44e97a0299e980656aef557eb5c2bac9b6443452
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# 대시보드에서 구성

사용자 지정할 수 있습니다 [!DNL Payment Services] 대시보드에서 유용한 구성 옵션을 사용하여 필요한 사항을 제공합니다.

를 클릭하면 [!UICONTROL Settings] 대시보드에서 를 빠르게 구성할 수 있습니다 [!DNL Payment Services] Adobe Commerce 및 Magento Open Source용. 이러한 구성 옵션은 [!UICONTROL Payment mode] 일반 설정의 필드.

자세한 내용은 [[!UICONTROL General] 설정 섹션](#general-settings) 추가 정보.

>[!IMPORTANT]
>
> 다중 저장소 또는 레거시 구성의 경우 다음을 참조하십시오 [관리자에서 구성](configure-admin.md) 주제.

## 결제 서비스 구성

다음을 활성화할 수 있습니다 [!DNL Payment Services] 웹 사이트에 대해 를 설정하고, [!UICONTROL General] 설정 섹션을 참조하십시오.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![대시보드 보기](assets/payment-services-menu-small.png)

1. 대시보드에서 **[!UICONTROL Settings]** 을 클릭합니다.

   다음 _[!UICONTROL General]_섹션에는 설정하는 데 사용되는 구성 옵션이 포함되어 있습니다 [!DNL Payment Services] 결제 방법으로 사용

1. 맨 위에 있는 전환 옵션의 경우&#x200B;**[!UICONTROL Enable Payment Services as payment method]**). `Yes` 활성화됨 [!DNL Payment Services] 참조하십시오.

1. 대상 **결제 모드**&#x200B;으로 설정하고 `Sandbox` 아직 테스트 중이라면 [!DNL Payment Services] 스토어 또는 `Production` Live Payments를 사용할 준비가 된 경우

   >[!WARNING]
   >
   >사용자 [!UICONTROL Sandbox Merchant ID] 및 [!UICONTROL Production Merchant ID] 샌드박스 및/또는 프로덕션에 대한 온보딩을 완료하면 자동으로 생성되어 해당 분야의 고급 필드에 표시됩니다. 이러한 ID를 제거하거나 변경하지 마십시오.

1. 결제 기능 및 상점 표시에 대한 기본 설정을 변경하려면 필요에 따라 추가 옵션을 설정합니다.

   - [신용 카드 필드](#credit-card-fields)
   - [PayPal 스마트 단추](#paypal-smart-buttons)
   - [단추 스타일](#button-style)

1. 변경 사항을 저장하려면 **[!UICONTROL Save]** 을 클릭합니다.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

### 신용 카드 필드

다음 [!UICONTROL Credit Card Fields] 결제 옵션은 신용 카드 또는 직불 카드 결제 방법에 대해 간단하고 안전한 체크아웃을 제공합니다.

자세한 내용은 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

1. 대상 **[!UICONTROL Checkout title]**&#x200B;를 입력하여 체크 아웃 중에 표시되는 결제 방법의 이름을 변경할 수 있습니다.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 설정 **[!UICONTROL Payment action]** to `Authorize` 또는 `Authorize and Capture`.
1. 대상 **[!UICONTROL Debug Mode]**&#x200B;을 눌러 선택기를 전환하여 디버그 모드를 활성화합니다.
1. 변경 사항을 저장하려면 **[!UICONTROL Save]** 을 클릭합니다.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

### PayPal 스마트 단추

다음 [!DNL PayPal Smart Buttons] 결제 옵션은 고객을 위한 간단하고 빠르고 안전한 체크아웃 프로세스를 제공합니다. 자세한 내용은 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

대시보드에서 PayPal 스마트 단추 결제 옵션을 활성화할 수 있습니다.

1. 체크아웃 중에 표시된 대로 결제 방법의 이름을 변경하려면 **[!UICONTROL Checkout Title]** 필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 설정 **[!UICONTROL Payment action]** to `Authorize` 또는 `Authorize and Capture`.
1. 토글 선택기를 사용하여 활성화하거나 비활성화합니다 [!DNL PayPal smart button] 디스플레이 기능:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** 를 클릭하여 체크아웃하는 동안 단추를 표시하는 옵션을 활성화합니다.

1. 를 변경하려면 [나중에 메시지 결제](payments-options.md#pay-later-button) (원하는 경우), 을 전환합니다. **[!UICONTROL Display Pay Later message]** 선택 사항입니다.
1. 디버그 모드를 활성화하려면 **[!UICONTROL Debug Mode]**,
1. 변경 사항을 저장하려면 **[!UICONTROL Save]** 을 클릭합니다.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

### 단추 스타일

를 구성할 수도 있습니다 _[!UICONTROL Button style]_대시보드 내의 PayPal 스마트 버튼 옵션:

1. 를 변경하려면 **[!UICONTROL Layout]**, 선택 `Vertical` 또는 `Horizontal`.
1. 가로 레이아웃에서 태깅을 사용하려면 **[!UICONTROL Show tagline]**.
1. 를 수정하려면 **[!UICONTROL Color]**&#x200B;원하는 색상 옵션을 선택합니다.
1. 를 변경하려면 **[!UICONTROL Shape]**, 선택 `Pill` 또는 `Rect`.
1. 단추 높이 선택기를 활성화하려면 **[!UICONTROL Responsive button height]**.
1. 를 수정하려면 **[!UICONTROL Label]**&#x200B;원하는 레이블 옵션을 선택합니다.
1. 변경 사항을 저장하려면 **[!UICONTROL Save]** 을 클릭합니다.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

다음을 구성할 수 있습니다 [!DNL PayPal Smart Buttons] 관리 또는 대시보드에서 스타일을 지정합니다. 자세한 내용은 [PayPal 단추 스타일 가이드](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 추가 정보.
