---
title: 결제 서비스 설정
description: 설치 후 다음을 구성할 수 있습니다. [!DNL Payment Services] 홈에서.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: f14b4a1abe9c0f85dc9f070467f94819c1fe89e6
workflow-type: tm+mt
source-wordcount: '1909'
ht-degree: 0%

---

# 설정

사용자 지정할 수 있습니다. [!DNL Payment Services] 에서 유용한 설정을 사용하여 필요에 맞게 [!DNL Payment Services] 집.

구성하려면 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 클릭 **[!UICONTROL Settings]**. 이러한 구성 옵션은 _[!UICONTROL Payment mode]_필드[_&#x200B;일반&#x200B;_구성 옵션](#configure-general-settings).

다중 스토어 또는 레거시 구성의 경우 다음을 참조하십시오. [관리에서 구성](configure-admin.md).

## 일반 설정 구성

다음 [!UICONTROL General] 설정은 결제 방법으로 결제 서비스를 활성화 또는 비활성화하고 고객 거래에 정보를 추가하여 웹 사이트 또는 스토어 보기를 사용자 지정 정보로 표시하거나 접두화하는 기능을 제공합니다.

### 결제 서비스 활성화

다음을 활성화할 수 있습니다. [!DNL Payment Services] 웹 사이트에 대해 샌드박스 테스트 또는 라이브 결제를 활성화하십시오.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![홈 보기](assets/payment-services-menu-small.png)

1. 클릭 **[!UICONTROL Settings]**. 다음을 참조하십시오 [소개 [!DNL Payment Services] 홈](payments-home.md) 추가 정보.

   다음 _[!UICONTROL General]_섹션에는 활성화하는 데 사용되는 설정이 포함되어 있습니다. [!DNL Payment Services] 를 결제 방법으로 사용하십시오.

1. 활성화하려면 [!DNL Payment Services] 스토어의 결제 방법으로, _[!UICONTROL General]_섹션, 전환&#x200B;**[!UICONTROL Enable Payment Services as payment method]**끝 `Yes`.

1. 아직 테스트 중인 경우 [!DNL Payment Services] 스토어에 대해 다음을 설정합니다. **결제 모드** 끝 `Sandbox`. 라이브 결제를 활성화할 준비가 되면 다음으로 설정하십시오. `Production`.

   >[!NOTE]
   >
   >사용자 _[!UICONTROL Sandbox Merchant ID]_및_[!UICONTROL Production Merchant ID]_ 는 자동으로 생성되며 샌드박스 및/또는 프로덕션에 대한 온보딩을 마치면 각 필드에 표시됩니다.

1. 클릭 **[!UICONTROL Save]**.

   변경 내용을 저장하지 않고 이 보기에서 나가려고 하면 변경 내용을 취소하거나, 편집을 유지하거나, 변경 내용을 저장하라는 모달이 나타납니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 및 클릭 **[!UICONTROL Flush Cache]** 잘못된 모든 캐시를 새로 고칩니다.

이제 의 기본 설정을 계속 변경할 수 있습니다. [결제 옵션](#configure-payment-options) 기능 및 상점 첫 화면 디스플레이.

### 소프트 설명자 추가

다음을 추가할 수 있습니다. [!UICONTROL Soft Descriptor] 웹 사이트 또는 개별 스토어 뷰 구성. 고객 거래 은행 거래 명세서에 소프트 설명자가 표시됩니다. 예를 들어 여러 스토어/브랜드/카탈로그가 있는 경우 [!UICONTROL Soft Descriptor] 필드.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![홈 보기](assets/payment-services-menu-small.png)

1. 클릭 **[!UICONTROL Settings]**. 다음을 참조하십시오 [소개 [!DNL Payment Services] 홈](payments-home.md) 추가 정보.
1. 에서 웹 사이트 또는 스토어 보기를 선택합니다. **[!UICONTROL Scope]** 드롭다운 메뉴. 여기에 사용할 소프트 설명자를 만듭니다. 초기 설정의 경우 다음과 같이 둡니다. **[!UICONTROL Default]** 을 클릭하여 기본값을 설정합니다.
1. 텍스트 필드에 사용자 정의 텍스트(최대 22자)를 추가하고 을 바꿉니다 `Custom descriptor`.
1. 클릭 **[!UICONTROL Save]**.
1. 웹 사이트 또는 스토어 보기에 대해 구성된 기본값 이외의 소프트 설명자를 만들려면 다음 작업을 수행하십시오.
   1. 에서 웹 사이트 또는 스토어 보기를 선택합니다. **[!UICONTROL Scope]** 드롭다운 메뉴. 여기에 사용할 소프트 설명자를 만듭니다.
   1. 전환 _끔_ **[!UICONTROL Use website]** (또는 **[!UICONTROL Use default]**, 선택한 범위에 따라 다릅니다.
   1. 텍스트 필드에 사용자 정의 텍스트를 추가합니다.
   1. 클릭 **[!UICONTROL Save]**.
1. 웹 사이트 또는 스토어에 대해 활성화하려면 기본 소프트 설명자 보기 _또는_ 상위 웹 사이트에 사용되는 소프트 설명자:
   1. 에서 웹 사이트 또는 스토어 보기를 선택합니다. **[!UICONTROL Scope]** 드롭다운 메뉴. 기존 소프트 설명자를 활성화할 수 있습니다.
   1. 전환 _날짜_ **[!UICONTROL Use website]** (또는 **[!UICONTROL Use default]**, 선택한 범위에 따라 다릅니다.
   1. 클릭 **[!UICONTROL Save]**.

   변경 내용을 저장하지 않고 이 보기에서 나가려고 하면 변경 내용을 취소하거나, 편집을 유지하거나, 변경 내용을 저장하라는 모달이 나타납니다.

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Enable] | 웹 사이트 | 활성화 또는 비활성화 [!DNL Payment Services] 웹 사이트용. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | 스토어 뷰 | 스토어에 대한 메서드 또는 환경을 설정합니다. 옵션: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 스토어 뷰 | 샌드박스 온보딩 중 자동으로 생성되는 샌드박스 판매자 ID입니다. |
| [!UICONTROL Production Merchant ID] | 스토어 뷰 | 샌드박스 온보딩 중 자동으로 생성되는 프로덕션 판매자 ID입니다. |
| [!UICONTROL Soft Descriptor] | 웹 사이트 또는 스토어 보기 | 웹 사이트 및 스토어 보기에 부드러운 설명자를 추가하여 브랜드, 스토어 또는 제품 라인을 설명하는 고객 거래에 정보를 추가합니다. 다음 [!UICONTROL Use website] toggle은 웹 사이트 수준에서 추가된 모든 소프트 설명자를 적용합니다. 다음 [!UICONTROL Use default] toggle은 기본값으로 추가된 모든 소프트 설명자를 적용합니다. |

## 결제 옵션 구성

활성화했으므로 [!UICONTROL Payment Services] 웹 사이트의 경우 결제 기능 및 상점 표시에 대한 기본 설정을 변경할 수 있습니다.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![홈 보기](assets/payment-services-menu-small.png)

1. 클릭 **[!UICONTROL Settings]**. 다음을 참조하십시오 [소개 [!DNL Payment Services] 홈](payments-home.md) 추가 정보.
1. 다음에 대한 결제 옵션 구성 [신용 카드](#credit-card-fields), [결제 버튼](#payment-buttons), 및 [단추 스타일](#button-style), 다음 섹션에 따라 사용하십시오.

### 신용 카드 필드

다음 _[!UICONTROL Credit Card Fields]_설정은 신용 카드 또는 직불 카드 결제 방법을 위한 간단하고 안전한 체크아웃 옵션을 제공합니다.

다음을 참조하십시오 [결제 옵션](payments-options.md#credit-card-fields) 추가 정보.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![홈 보기](assets/payment-services-menu-small.png)

1. 에서 스토어 보기를 선택합니다. **[!UICONTROL Scope]** 드롭다운 메뉴. 결제 방법을 사용할 수 있도록 설정합니다.
1. 체크아웃 중에 표시되는 결제 방법의 이름을 변경하려면 **[!UICONTROL Checkout title]** 필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 전환 **[!UICONTROL Payment action]** 끝 `Authorize` 또는 `Authorize and Capture`.
1. 활성화하려면 [3DS 보안 인증](security.md#3ds) (`Off` 기본적으로) **[!UICONTROL 3DS Secure authentication]** 선택기 `Always` 또는 `When required`.
1. 체크아웃 페이지에서 신용 카드 필드를 활성화하거나 비활성화하려면 **[!UICONTROL Show on checkout page]** 선택기.
1. 활성화 또는 비활성화하기 [카드 보관](#card-vaulting), 전환 **[!UICONTROL Vault enabled]** 선택기.
1. 활성화 또는 비활성화하기 [관리자의 저장된 결제 방법](#card-vaulting) (판매자가 저장된 결제 방법을 사용하여 관리자의 고객에 대한 주문을 완료할 수 있도록) **[!UICONTROL Show vaulted methods in Admin]** 선택기.
1. 디버그 모드를 활성화하거나 비활성화하려면 **[!UICONTROL Debug Mode]** 선택기.
1. 클릭 **[!UICONTROL Save]**.

   변경 내용을 저장하지 않고 이 보기에서 나가려고 하면 변경 내용을 취소하거나, 편집을 유지하거나, 변경 내용을 저장하라는 모달이 나타납니다.

1. [캐시 초기화](#flush-the-cache).

#### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 스토어 뷰 | 체크아웃 중에 결제 방법 보기에서 이 결제 방법의 제목으로 표시할 텍스트를 추가합니다. 옵션: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [지불 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 지정된 결제 방법에 대해 참조할 수 있습니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL 3DS Secure authentication] | 웹 사이트 | 활성화 또는 비활성화 [3DS 보안 인증](security.md#3ds). 옵션: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | 웹 사이트 | 신용 카드 필드가 체크아웃 페이지에 표시되도록 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | 스토어 뷰 | 활성화 또는 비활성화 [신용 카드 소산](vaulting.md). 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show vaulted payment methods in Admin] | 스토어 뷰 | 관리자가 판매자가 고객에 대한 주문을 완료할 수 있는 기능을 활성화 또는 비활성화합니다. [적립된 결제 방법 사용](vaulting.md). 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |

### 결제 버튼

다음 [!DNL PayPal Smart Buttons] 결제 옵션은 고객에게 간편하고 빠르고 안전한 체크아웃 프로세스를 제공합니다. 다음을 참조하십시오 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

PayPal 스마트 단추 결제 옵션을 활성화하고 구성할 수 있습니다.

1. 에서 스토어 보기를 선택합니다. **[!UICONTROL Scope]** 드롭다운 메뉴. 결제 방법을 사용할 수 있도록 설정합니다.
1. 체크아웃 시 표시된 대로 결제 방법의 이름을 변경하려면 **[!UICONTROL Checkout Title]** 필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 전환 **[!UICONTROL Payment action]** 끝 `Authorize` 또는 `Authorize and Capture`.
1. 토글 선택기를 사용하여 활성화 또는 비활성화 [!DNL PayPal smart button] 기능 표시:
   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Apple을 사용하려면 다음 작업을 수행하십시오 [은(는) Apple 샌드박스 테스터 계정이 있어야 합니다.](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) (가짜 신용 카드 및 청구 정보로 완료) 테스트하십시오. 샌드박스에서 Apple Pay를 사용할 준비가 되면 _또는_ 프로덕션 모드, 완료 후 [테스트 및 유효성 검사](test-validate.md#test-in-sandbox-environment), 완료 [을 사용한 자가 등록 [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_라이브 도메인 등록_ 섹션만 해당) 및 [스토어에 맞게 구성 [!DNL Payment Services]](settings.md#payment-buttons).

      가시성을 결제 버튼 또는 PayPal 나중에 결제 메시지로 전환하면 설정 페이지 하단에 해당 구성의 시각적 미리보기가 표시됩니다.

1. 디버그 모드를 활성화하려면 **[!UICONTROL Debug Mode]** 선택기.
1. 클릭 **[!UICONTROL Save]**.

   변경 내용을 저장하지 않고 이 보기에서 나가려고 하면 변경 내용을 취소하거나, 편집을 유지하거나, 변경 내용을 저장하라는 모달이 나타납니다.

1. [캐시 초기화](#flush-the-cache).

#### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 스토어 뷰 | 체크아웃 중에 결제 방법 보기에서 이 결제 방법의 제목으로 표시할 텍스트를 추가합니다. 옵션: 텍스트 필드 |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [지불 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 지정된 결제 방법에 대해 참조할 수 있습니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on checkout page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 체크아웃 페이지에서 확인할 수 있습니다. 옵션: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 제품 세부 사항 페이지에서 확인할 수 있습니다. 옵션: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] ( 미니 장바구니 미리 보기) 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | 스토어 뷰 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 장바구니 페이지에서 확인할 수 있습니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | 스토어 뷰 | 지급 버튼이 표시되는 나중에 지급 옵션 표시를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | 웹 사이트 | 장바구니, 제품 페이지, 미니 장바구니에서, 그리고 체크아웃 흐름 동안 나중에 결제 메시지를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | 스토어 뷰 | 결제 버튼이 표시되는 Venmo 결제 옵션을 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | 스토어 뷰 | 결제 버튼이 표시되는 Apple 결제 옵션을 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |

### 단추 스타일

다음을 구성할 수도 있습니다 _[!UICONTROL Button style]_payPal 스마트 단추 옵션:

1. 을(를) 변경하려면 **[!UICONTROL Layout]**, 선택 `Vertical` 또는 `Horizontal`.

   >[!NOTE]
   >
   > 단추 스타일이 다음으로 구성된 경우 `Horizontal` 또한 스토어는 여러 개의 PayPal 스마트 단추를 표시하도록 구성되어 있으므로 제품 페이지, 체크아웃 페이지 및 미니 카트에 표시된 두 개의 단추와 카트에 표시된 하나의 단추만 볼 수 있습니다.

1. 가로 레이아웃에서 태그 라인을 활성화하려면 **[!UICONTROL Show tagline]** 선택기.
1. 을 수정하려면 다음을 수행합니다 **[!UICONTROL Color]**&#x200B;원하는 색상 옵션을 선택합니다.
1. 을 수정하려면 다음을 수행합니다 **[!UICONTROL Shape]**, 선택 `Pill` 또는 `Rectangle`.
1. 단추 높이 선택기를 활성화하려면 **[!UICONTROL Responsive button height]** 선택기.
1. 을 수정하려면 다음을 수행합니다 **[!UICONTROL Label]**&#x200B;원하는 레이블 옵션을 선택합니다.

   레이아웃, 색상, 모양, 높이 및 레이블에 대한 구성 옵션을 변경하면 설정 페이지 하단에 해당 구성의 시각적 미리보기가 표시됩니다.

1. 클릭 **[!UICONTROL Save]**.

   변경 내용을 저장하지 않고 이 보기에서 나가려고 하면 변경 내용을 취소하거나, 편집을 유지하거나, 변경 내용을 저장하라는 모달이 나타납니다.

1. [캐시 초기화](#flush-the-cache).

다음을 구성할 수 있습니다. [!DNL PayPal Smart Buttons] 스타일링 [관리자 의 레거시 구성에서](configure-admin.md#configure-paypal-smart-buttons) 또는 여기 위치 [!DNL Payment Services Home]. 다음을 참조하십시오 [PayPal의 단추 스타일 가이드](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 옵션에 대한 자세한 내용을 보려면 를 참조하십시오.

#### 구성 옵션

| 필드 | 범위 | 설명 |
|--- |--- |--- |
| [!UICONTROL Layout] | 스토어 뷰 | 결제 버튼에 대한 레이아웃 스타일을 정의합니다. 옵션: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | 스토어 뷰 | 태그 라인 활성화/비활성화. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | 스토어 뷰 | 결제 버튼의 색상을 정의합니다. 옵션: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 스토어 뷰 | 결제 버튼의 모양을 정의합니다. 옵션: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | 스토어 뷰 | 결제 단추에서 기본 높이를 사용하는지 여부를 정의합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 스토어 뷰 | 결제 버튼의 높이를 정의합니다. 기본값: 없음 |
| [!UICONTROL Label] | 스토어 뷰 | 결제 버튼에 표시되는 레이블을 정의합니다. 옵션: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## 캐시 초기화

에서 구성을 변경하는 경우 _설정_&#x200B;예를 들어 Apple Pay, Venmo 또는 PayPal PayLater 버튼을 토글하는 경우 저장소에서 최신 구성을 표시하도록 캐시를 수동으로 플러시합니다.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. 클릭 **[!UICONTROL Flush Cache]** 잘못된 모든 캐시를 새로 고칩니다.

캐시 관리 테이블의 캐시 유형에 `INVALIDATED` 상태: 저장소에 해당 항목에 대한 최신 구성이 표시되지 않을 수 있습니다. 최신 구성을 표시하도록 저장소를 업데이트하려면 캐시를 플러시하십시오.

저장소에 올바른 구성이 표시되는지 정기적으로 확인합니다. [캐시 초기화](https://docs.magento.com/user-guide/system/cache-management.html).

## 카드 보관

고객이 향후 구매를 위해 내 계정에 자신의 신용 카드 정보를 저장(저장)할 수 있는 기능을 활성화할 수 있습니다.

또한 관리자의 카드 보관을 사용하여 기존 고객에 대한 후속 주문을 완료할 수 있습니다.

에서 카드 보관 사용 또는 사용 안 함 [신용 카드 필드 설정](#credit-card-fields).

다음을 참조하십시오 [신용 카드 보관](vaulting.md) 추가 정보.

## 3DS

3DS는 고객 및 상인의 매장 내 사기 행위를 방지하고 유럽 연합(EU) 표준을 준수할 수 있도록 해줍니다.

에서 3DS 활성화 또는 비활성화 [신용 카드 필드 설정](#credit-card-fields).

다음을 참조하십시오 [3DS 보안](security.md#3ds) 추가 정보.

## 여러 PayPal 계정 사용

위치 [!UICONTROL Payment Services], 내에서 여러 PayPal 계정을 사용할 수 있습니다. **1** 웹 사이트 수준의 판매자 계정. 예를 들어 서로 다른 국가를 사용하는 여러 국가에서 스토어를 운영하고 있는 경우 [통화](https://docs.magento.com/user-guide/stores/currency.html)) 또는 비즈니스 일부에 Adobe Commerce을 사용하고 싶지만 사용하지 않는 경우 _모두_, 판매자 계정을 설정하여 여러 PayPal 계정을 사용할 수 있습니다.

다음을 참조하십시오 [사이트, 스토어 및 보기 범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 웹 사이트, 스토어 및 스토어 조회수의 계층에 대한 자세한 정보.

영업 담당자가 새 를 만들 수 있습니다. [범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 판매자 계정 및 PayPal을 사용하여 추가 사이트를 온보딩하여 표시하도록 구성한 PayPal 버튼이 사이트에 표시되도록 할 수 있습니다. 웹 사이트에서 여러 PayPal 계정을 사용하는 데 도움이 필요하면 영업 담당자에게 문의하십시오.
