---
title: 레거시 결제 서비스 구성
description: 설치 후 다음을 구성할 수 있습니다. [!DNL Payment Services] 저장소 구성의 관리자.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 366689fccdf3ae93700d458bf9cbcab63e4583a8
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 0%

---

# 레거시 [!DNL Payment Services] 구성

사용자 지정할 수 있습니다. [!DNL Payment Services] 을 참조하십시오.

를 구성할 때 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 관리에서 이러한 구성은 다음에 설정된 환경에만 적용됩니다. _[!UICONTROL Method]_필드_[!UICONTROL General Configuration]_. 구성 필드에서 변경한 내용은 _[!UICONTROL Method]_선택(selection) - 방법을 전환하면 선택 내용이 재설정되지 않습니다.

## 일반 구성

다음을 활성화할 수 있습니다. [!DNL Payment Services] 스토어에 대해 및 의 샌드박스 테스트 또는 라이브 결제를 활성화하십시오. _[!UICONTROL General Configuration]_섹션.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 선택 **[!UICONTROL Payment Methods]**.

   ![메서드 보기](assets/methods-view.png)

1. 확장 _[!UICONTROL Recommended Solutions]_섹션.
1. 다음에서 _[!UICONTROL [!DNL Payment Services]]_섹션을 확장합니다._[!UICONTROL General Configuration]_ 섹션.
1. 대상 **사용**, 다음으로 설정 `Yes` 활성화하려면 [!DNL Payment Services] 스토어용.
1. 대상 **방법**, 다음으로 설정 `Sandbox` 아직 테스트 중인 경우 [!DNL Payment Services] 스토어 또는 `Production` 라이브 결제를 활성화할 준비가 된 경우.

   >[!WARNING]
   >
   >사용자 _[!UICONTROL Sandbox Merchant ID]_및_[!UICONTROL Production Merchant ID]_ 는 자동으로 생성되며, 샌드박스 및/또는 프로덕션에 대한 온보딩을 마치면 각 필드에 표시됩니다. 이 ID를 제거하거나 변경하지 마십시오.

1. 대상 **소프트 설명자** (스토어/브랜드/카탈로그를 구분할 고객 거래 은행 거래 명세서에 표시되는 사용자 지정 값) 텍스트 필드에 사용자 지정 텍스트(최대 22자)를 추가하고 을 바꿉니다 `Custom descriptor` 또는 기존 값을 포함할 수 없습니다.
1. 클릭 **[!UICONTROL Save Config]** 변경 사항을 저장합니다.
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Flush Cache]** 잘못된 모든 캐시를 새로 고칩니다.

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Enable] | 웹 사이트 | 활성화 또는 비활성화 [!DNL Payment Services] 웹 사이트용. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | 스토어 뷰 | 스토어에 대한 메서드 또는 환경을 설정합니다. 옵션: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 스토어 뷰 | 샌드박스 온보딩 중 자동으로 생성되는 샌드박스 판매자 ID입니다. 이 ID를 변경하거나 변경하지 마십시오. |
| [!UICONTROL Production Merchant ID] | 스토어 뷰 | 샌드박스 온보딩 중 자동으로 생성되는 프로덕션 판매자 ID입니다. 이 ID를 변경하거나 변경하지 마십시오. |
| [!UICONTROL Soft Descriptor] | 웹 사이트 또는 스토어 보기 | 웹 사이트 및 스토어 보기에 부드러운 설명자를 추가하여 브랜드, 스토어 또는 제품 라인을 설명하는 고객 거래에 정보를 추가합니다. |

## [!UICONTROL Credit Card Fields]

다음 [!UICONTROL Credit Card Fields] 결제 옵션은 신용 카드 또는 직불 카드 결제 방법을 위한 간단하고 안전한 체크아웃을 제공합니다.

다음을 참조하십시오 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 선택 **[!UICONTROL Payment Methods]**.
1. 확장 _[!UICONTROL Recommended Solutions]_섹션.
1. 다음에서 _[!UICONTROL Payment Services]_섹션을 확장합니다._[!UICONTROL Credit Card Fields]_ 섹션.
1. 대상 **[!UICONTROL Title]**&#x200B;필요한 경우 체크아웃 중에 표시된 대로 결제 방법의 이름을 변경할 텍스트를 입력합니다.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 선택 **[!UICONTROL Authorize]** 또는 **승인 및 캡처**.
1. 체크아웃 페이지에서 결제 방법의 우선 순위를 정하려면 `Numeric Only` 의 값 **[!UICONTROL Sort order]** 필드.
1. 대상 **[!UICONTROL Show on checkout page]**, 선택 `Yes` 체크아웃 페이지에서 신용 카드 필드를 활성화하려면
1. 대상 **[!UICONTROL Vault Enabled]**, 선택 `Yes` 체크아웃을 위해 신용 카드 보관을 활성화합니다.
1. 대상 **[!UICONTROL Vault Enabled in Admin]**, 선택 `Yes` 판매자가 저장된 신용 카드를 사용하여 고객에 대한 주문을 생성할 수 있도록 합니다.
1. 활성화하려면 **[!UICONTROL 3DS Secure authentication]** (`Off` 기본적으로) 다음을 선택합니다 `Always` 또는 `When required`.
1. 대상 **[!UICONTROL Debug Mode]**, 선택 `Yes` 디버그 모드를 활성화하려면 `No` 비활성화합니다.
1. 클릭 **[!UICONTROL Save Config]** 변경 사항을 저장합니다.
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Flush Cache]** 잘못된 모든 캐시를 새로 고칩니다.

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 스토어 뷰 | 체크아웃 중에 결제 방법 보기에서 이 결제 방법의 제목으로 표시할 텍스트를 추가합니다. 옵션: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [지불 조치](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) 지정된 결제 방법에 대해 참조할 수 있습니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | 스토어 뷰 | 체크아웃 페이지에서 지정된 결제 방법에 대한 정렬 순서. `Numeric Only` 값 |
| [!UICONTROL Show on checkout page] | 웹 사이트 | 체크아웃 페이지에서 신용 카드 필드를 활성화 또는 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | 스토어 뷰 | 활성화 또는 비활성화 [신용 카드 소산](vaulting.md). 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | 스토어 뷰 | 다음에 대한 기능 활성화 또는 비활성화 [머천트가 관리자에서 고객에 대한 주문을 완료할 수 있음](vaulting.md) 저장된 결제 방법 사용 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | 웹 사이트 | 활성화 또는 비활성화 [3DS 보안 인증](security.md#3ds). 옵션: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

다음 [!UICONTROL Apple Pay] 결제 옵션을 사용하면 가맹점이 구매 고객에게 Apple Pay를 제공할 수 있으며, 구매자는 디바이스에서 터치 ID를 사용하여 구매할 수 있습니다

다음을 참조하십시오 [결제 옵션](payments-options.md#apple-pay-button) 추가 정보.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 선택 **[!UICONTROL Payment Methods]**.
1. 확장 _[!UICONTROL Recommended Solutions]_섹션.
1. 다음에서 _[!UICONTROL Payment Services]_섹션을 확장합니다._[!UICONTROL Apple Pay]_ 섹션.
1. 대상 **[!UICONTROL Title]**&#x200B;필요한 경우 체크아웃 중에 표시된 대로 결제 방법의 이름을 변경할 텍스트를 입력합니다.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 선택 **[!UICONTROL Authorize]** 또는 **[!UICONTROL Authorize and Capture]**.
1. 표시 [!DNL Apple Pay] 체크아웃 페이지에서 `Yes` 대상: **[!UICONTROL Show buttons on checkout page]**.
1. 표시 [!DNL Apple Pay] 제품 세부 사항 페이지에서 `Yes` 대상: **[!UICONTROL Show buttons on product detail page]**.
1. 표시 [!DNL Apple Pay] 미니 장바구니 미리 보기에서 `Yes` 대상 **[!UICONTROL Show buttons in mini cart preview]**.
1. 표시 [!DNL Apple Pay] 장바구니 페이지에서 `Yes` 대상: **[!UICONTROL Show buttons on cart page]**.
1. 디버그 모드를 사용하려면 다음을 선택합니다. `Yes` 대상: **[!UICONTROL Debug Mode]** (`No` 사용 안 함)입니다.
1. 변경 사항을 저장하려면 를 클릭합니다. **[!UICONTROL Save Config]** .
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Flush Cache]** 잘못된 모든 캐시를 새로 고칩니다.

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 스토어 뷰 | 체크아웃 중에 결제 방법 보기에서 이 결제 방법의 제목으로 표시할 텍스트를 추가합니다. 옵션: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [지불 조치](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) 지정된 결제 방법에 대해 참조할 수 있습니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | 웹 사이트 | 활성화 또는 비활성화 [!DNL Apple Pay] 체크아웃 페이지에서 확인할 수 있습니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL Apple Pay] 제품 세부 사항 페이지에서 확인할 수 있습니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL Apple Pay] ( 미니 장바구니 미리 보기) 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL Apple Pay] 장바구니 페이지의 를 참조하십시오. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!DNL PayPal Smart Buttons]

다음 [!DNL PayPal Smart Buttons] 결제 옵션은 고객에게 간편하고 빠르고 안전한 체크아웃 프로세스를 제공합니다.

다음을 참조하십시오 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

Configure [!DNL PayPal Smart Buttons]

관리자 내에서 PayPal 스마트 단추 결제 옵션을 활성화하고 구성할 수 있습니다.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 선택 **[!UICONTROL Payment Methods]**.
1. 확장 _[!UICONTROL Recommended Solutions]_섹션.
1. 다음에서 _[!UICONTROL Payment Services]_섹션을 확장합니다._[!UICONTROL PayPal Smart Buttons]_ 섹션.
1. 체크아웃 중에 표시된 대로 결제 방법의 이름을 변경하려면 다음을 편집합니다. _[!UICONTROL Title]_필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 선택 **[!UICONTROL Authorize]** 또는 **[!UICONTROL Authorize and Capture]**.
1. 체크아웃 페이지에서 결제 방법의 우선 순위를 정하려면 `Numeric Only` 의 값 **[!UICONTROL Sort order]** 필드.
1. 활성화/비활성화하려면 [나중에 결제 메시지](payments-options.md#pay-later-button), 선택 `Yes`/`No` 대상 **[!UICONTROL Display Pay Later Message]**.
1. 체크아웃 페이지에 PayPal 스마트 단추를 표시하려면 다음을 선택합니다. `Yes` 대상: **[!UICONTROL Show buttons on checkout page]**.
1. 제품 세부 사항 페이지에 PayPal 스마트 단추를 표시하려면 `Yes` 대상: **[!UICONTROL Show buttons on product detail page]**.
1. 미니 장바구니 미리 보기에 PayPal 스마트 단추를 표시하려면 다음을 선택합니다. `Yes` 대상 **[!UICONTROL Show buttons in mini cart preview]**.
1. 장바구니 페이지에 PayPal 스마트 단추를 표시하려면 다음을 선택합니다 `Yes` 대상: **[!UICONTROL Show buttons on cart page]**.
1. Venmo를 결제 옵션으로 사용하려면 을 선택합니다. `Yes` 대상 **[!UICONTROL Venmo Enabled]**.
1. 신용 카드와 직불 카드를 결제 옵션으로 사용하려면(PayPal 스마트 단추) 다음을 선택합니다. `Yes` 대상 **[!UICONTROL Credit and Debit Card Enabled]**.
1. 활성화/비활성화하려면 [PayPal 나중에 결제](payments-options.md#pay-later-button) 결제 옵션, 선택 `Yes`/`No` 대상 **[!UICONTROL PayPal Pay Later Enabled]**.
1. 디버그 모드를 사용하려면 다음을 선택합니다. `Yes` 대상: **[!UICONTROL Debug Mode]** (`No` 사용 안 함)입니다.
1. 변경 사항을 저장하려면 를 클릭합니다. **[!UICONTROL Save Config]** .
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Flush Cache]** 잘못된 모든 캐시를 새로 고칩니다.

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 스토어 뷰 | 체크아웃 중에 결제 방법 보기에서 이 결제 방법의 제목으로 표시할 텍스트를 추가합니다. 옵션: 텍스트 필드 |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [지불 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 지정된 결제 방법에 대해 참조할 수 있습니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | 웹 사이트 | 장바구니, 제품 페이지, 미니 장바구니에서, 그리고 체크아웃 흐름 동안 나중에 결제 메시지를 활성화하거나 비활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 체크아웃 페이지에서 확인할 수 있습니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 제품 세부 사항 페이지에서 확인할 수 있습니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] ( 미니 장바구니 미리 보기) 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 장바구니 페이지의 를 참조하십시오. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | 스토어 뷰 | 결제 버튼이 표시되는 Venmo 결제 옵션을 활성화하거나 비활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | 스토어 뷰 | 결제 버튼이 표시되는 신용 카드 및 직불 카드 옵션을 활성화하거나 비활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | 스토어 뷰 | 결제 버튼이 표시되는 PayPal Pay Later 결제 옵션 모양을 활성화하거나 비활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## 단추 스타일

다음을 구성할 수도 있습니다 _[!UICONTROL Button style]_결제 버튼 옵션:

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Sales]** 및 선택 **[!UICONTROL Payment Methods]**.
1. 확장 _[!UICONTROL Recommended Solutions]_섹션.
1. 다음에서 _[!UICONTROL [!DNL Payment Services]]_섹션을 확장합니다._[!UICONTROL PayPal Smart Button Styling]_ 섹션.
1. 레이아웃을 설정하려면 다음을 선택합니다. `Vertical` 또는 `Horizontal` 대상 **[!UICONTROL Layout]**
1. 색상을 설정하려면 의 사용 가능한 색상 중에서 선택합니다 **[!UICONTROL Color]**.
1. 모양을 설정하려면 를 선택합니다 `Rectangular` 또는 `Pill` 대상 **[!UICONTROL Shape]**.
1. 기본 높이를 사용하려면 을 선택합니다 `Yes` 또는 `No` 대상 **[!UICONTROL Use Default Height]**.
1. 사용자 지정 높이를 설정하려면 원하는 픽셀 높이를 추가합니다. **[!UICONTROL Height]**.
1. 태그 라인을 설정하려면 다음을 선택합니다 `Yes` 또는 `No` 대상 **[!UICONTROL Tagline]**.
1. 변경 사항을 저장하려면 를 클릭합니다. **[!UICONTROL Save Config]** .
1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**&#x200B;을 클릭한 다음 을 클릭합니다 **[!UICONTROL Flush Cache]** 잘못된 모든 캐시를 새로 고칩니다.

결제 버튼 스타일을 구성할 수도 있습니다 [설정에서](settings.md#button-style) 결제 서비스 홈에서.

### 구성 옵션

| 필드 | 범위 | 설명 |
|--- |--- |--- |
| [!UICONTROL Layout] | 스토어 뷰 | Paypal 스마트 단추의 레이아웃 스타일을 정의합니다. 옵션: `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | 스토어 뷰 | Paypal 스마트 단추의 색상을 정의합니다. 옵션: [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | 스토어 뷰 | Paypal 스마트 단추의 모양을 정의합니다. 옵션: `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | 스토어 뷰 | PayPal 스마트 단추에서 기본 높이를 사용하는지 여부를 정의합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | 스토어 뷰 | PayPal 스마트 단추의 높이를 정의합니다. 기본값: 없음 |
| [!UICONTROL Label] | 스토어 뷰 | PayPal 스마트 단추에 표시되는 레이블을 정의합니다. 옵션: `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | 스토어 뷰 | 태그 지정을 활성화합니다. 옵션: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## 캐시 초기화

구성을 변경하면 [수동으로 캐시 플러시](/help/payment-services/settings.md#flush-the-cache) 최신 구성 설정을 스토어에 표시할 수 있습니다.
