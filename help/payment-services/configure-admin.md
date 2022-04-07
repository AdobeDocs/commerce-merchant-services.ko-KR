---
title: 기존 결제 서비스 구성
description: 설치 후 다음을 구성할 수 있습니다 [!DNL Payment Services] 관리자(저장소 구성)를 참조하십시오.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: bfb2b6632fe494d6e392c214f5e3f5a11930c0b2
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# 기존 결제 서비스 구성

사용자 지정할 수 있습니다 [!DNL Payment Services] Admin Console에서 유용한 구성 옵션을 사용하여 필요에 맞게 구성할 수 있습니다.

구성 시 [!DNL Payment Services] Adobe Commerce 및 Magento Open Source의 경우 이러한 구성은 [!UICONTROL Method] 필드 [!UICONTROL General Configuration]. 구성 필드에서 수행하는 모든 변경 사항은 [!UICONTROL Method] 선택(selection) - 방법을 전환하면 선택 사항이 재설정되지 않습니다.

자세한 내용은 [[!UICONTROL General Configuration] 섹션](#general-configuration) 추가 정보.

## 일반 구성

다음을 활성화할 수 있습니다 [!DNL Payment Services] 를 사용하여 스토어에 대해 및 [!UICONTROL General Configuration] 섹션을 참조하십시오.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 **[!UICONTROL Payment Methods]**.

   ![메서드 보기](assets/methods-view.png)

1. 를 확장합니다. _[!UICONTROL Recommended Solutions]_섹션을 참조하십시오.
1. 에서 _[!UICONTROL [!DNL Payment Services]]_섹션에서_[!UICONTROL General Configuration]_ 섹션을 참조하십시오.
1. 대상 **활성화**&#x200B;으로 설정하고 `Yes` 활성화됨 [!DNL Payment Services] 내 가게에요
1. 대상 **메서드**&#x200B;으로 설정하고 `Sandbox` 아직 테스트 중이라면 [!DNL Payment Services] 스토어 또는 `Production` Live Payments를 사용할 준비가 된 경우

   >[!WARNING]
   >
   >사용자 [!UICONTROL Sandbox Merchant ID] 및 [!UICONTROL Production Merchant ID] 샌드박스 및/또는 프로덕션에 대한 온보딩을 완료하면 자동으로 생성되어 해당 분야의 고급 필드에 표시됩니다. 이러한 ID를 제거하거나 변경하지 마십시오.

1. 클릭 **[!UICONTROL Save Config]** 변경 사항을 저장하려면 을 클릭합니다.

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Enable] | 웹 사이트 | 활성화 또는 비활성화 [!DNL Payment Services] 참조하십시오. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 저장소 보기 | 스토어에 대한 메서드 또는 환경을 설정합니다. 옵션: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 저장소 보기 | 샌드박스 온보딩 중에 자동으로 생성되는 샌드박스 머천트 ID입니다. 이 ID를 변경하거나 변경하지 마십시오. |
| [!UICONTROL Production Merchant ID] | 저장소 보기 | 샌드박스 온보딩 중에 자동으로 생성되는 프로덕션 머천트 ID입니다. 이 ID를 변경하거나 변경하지 마십시오. |

## [!UICONTROL Credit Card Fields]

다음 [!UICONTROL Credit Card Fields] 결제 옵션은 신용 카드 또는 직불 카드 결제 방법에 대해 간단하고 안전한 체크아웃을 제공합니다.

자세한 내용은 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

### 신용 카드 필드 구성

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 **[!UICONTROL Payment Methods]**.
1. 를 확장합니다. _[!UICONTROL Recommended Solutions]_섹션을 참조하십시오.
1. 에서 _[!UICONTROL Payment Services]_섹션에서_[!UICONTROL Credit Card Fields]_ 섹션을 참조하십시오.
1. 대상 **[!UICONTROL Title]**&#x200B;체크 아웃 중에 표시된 대로 결제 방법의 이름을 변경하려면 텍스트(필요한 경우)를 입력합니다.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 선택 **[!UICONTROL Authorize]** 또는 **권한 부여 및 캡처**.
1. 대상 **디버그 모드**, 선택 `Yes` 디버그 모드를 활성화하거나 `No` 사용 안 함).
1. 클릭 **[!UICONTROL Save Config]** 변경 사항을 저장하려면 을 클릭합니다.

#### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 저장소 보기 | 체크아웃하는 동안 결제 방법 보기에서 이 결제 옵션의 제호로 표시할 텍스트를 추가합니다. 옵션: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [결제 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions)지정한 결제 방법에 대한 {target=&quot;_blank&quot;} 입니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

다음 [!DNL PayPal Smart Buttons] 결제 옵션은 고객을 위한 간단하고 빠르고 안전한 체크아웃 프로세스를 제공합니다.

자세한 내용은 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

### Configure [!DNL PayPal Smart Buttons]

관리자 내에서 PayPal 스마트 단추 결제 옵션을 활성화하고 구성할 수 있습니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 **[!UICONTROL Payment Methods]**.
1. 를 확장합니다. _[!UICONTROL Recommended Solutions]_섹션을 참조하십시오.
1. 에서 _[!UICONTROL Payment Services]_섹션에서_[!UICONTROL PayPal Smart Buttons]_ 섹션을 참조하십시오.
1. 체크 아웃 중에 표시된 대로 결제 방법의 이름을 변경하려면 _[!UICONTROL Title]_필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 선택 **[!UICONTROL Authorize]** 또는 **[!UICONTROL Authorize and Capture]**.
1. 를 비활성화하려면 [나중에 메시지 결제](payments-options.md#pay-later-button) (원하는 경우) 을 선택합니다. `No` 대상 **[!UICONTROL Display Pay Later Message]**.
1. 디버그 모드를 활성화하려면 `Yes` 대상 **[!UICONTROL Debug Mode]** (`No` 사용 안 함).
1. 변경 사항을 저장하려면 **[!UICONTROL Save Config]** .

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 저장소 보기 | 체크아웃하는 동안 결제 방법 보기에서 이 결제 옵션의 제호로 표시할 텍스트를 추가합니다. 옵션: 텍스트 필드 |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [결제 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions)지정한 결제 방법에 대한 {target=&quot;_blank&quot;} 입니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | 웹 사이트 | 장바구니, 제품 페이지, 미니 장바구니 및 체크아웃 흐름 중에 나중에 결제 메시지를 활성화 또는 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | 저장소 보기 | 지급 버튼이 표시되는 벤 지급 옵션을 활성화 또는 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | 저장소 보기 | 지급 버튼이 표시되는 이후 지급 옵션 모양을 사용하거나 사용 안함으로 설정합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | 저장소 보기 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 를 클릭합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini cart preview] | 저장소 보기 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] minicart 미리 보기에서. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | 저장소 보기 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 참조하십시오. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] 스타일 지정 옵션

| 필드 | [범위]({% 링크 configuration/scope.md %}) | 설명 |
|--- |--- |--- |
| [!UICONTROL Layout] | 저장소 보기 | Paypal 스마트 단추의 레이아웃 스타일을 정의합니다. 옵션: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | 저장소 보기 | Paypal 스마트 단추의 색상을 정의합니다. 옵션: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 저장소 보기 | Paypal 스마트 단추의 모양을 정의합니다. 옵션: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | 저장소 보기 | PayPal 스마트 단추에서 기본 높이를 사용하는지 여부를 정의합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 저장소 보기 | PayPal 스마트 단추의 높이를 정의합니다. 기본값: 없음 |
| [!UICONTROL Label] | 저장소 보기 | PayPal 스마트 단추에 표시되는 레이블을 정의합니다. 옵션: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | 저장소 보기 | 태그라인을 활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
