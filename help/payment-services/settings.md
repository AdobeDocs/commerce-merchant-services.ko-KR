---
title: 결제 서비스 설정
description: 설치 후 다음을 구성할 수 있습니다 [!DNL Payment Services] '홈'
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 65787d91c098e8f5d4ae46cba4d5e226b6301ecc
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 0%

---

# 설정

사용자 지정할 수 있습니다 [!DNL Payment Services] 의 유용한 설정을 사용하여 [!DNL Payment Services] 집에

구성하려면 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] click **[!UICONTROL Settings]**. 이러한 구성 옵션은 _[!UICONTROL Payment mode]_필드_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> 다중 저장소 또는 레거시 구성의 경우 다음을 참조하십시오 [관리자에서 구성](configure-admin.md) 주제.

## 일반 설정 구성

다음 [!UICONTROL General] 설정은 결제 방법으로 Payment Services를 활성화 또는 비활성화하고, 고객 트랜잭션에 정보를 추가하여 웹 사이트 또는 스토어 뷰에 사용자 지정 정보를 표시하거나 접두어 추가하는 기능을 제공합니다.

### 결제 서비스 활성화

다음을 활성화할 수 있습니다 [!DNL Payment Services] 웹 사이트에 대해 샌드박스 테스트 또는 라이브 지급 중 하나를 활성화합니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![홈 보기](assets/payment-services-menu-small.png)

1. 클릭 **[!UICONTROL Settings]**. 자세한 내용은 [소개 [!DNL Payment Services] 홈](payments-home.md) 추가 정보.

   다음 _[!UICONTROL General]_섹션에는 사용 가능한 설정이 포함되어 있습니다. [!DNL Payment Services] 를 결제 방법으로 사용할 수 있습니다.

1. 활성화하려면 [!DNL Payment Services] 매장에 대한 결제 방법으로 _[!UICONTROL General]_섹션, 전환&#x200B;**[!UICONTROL Enable Payment Services as payment method]**to `Yes`.

1. 아직 테스트 중인 경우 [!DNL Payment Services] 스토어에 대해 **결제 모드** to `Sandbox`. Live Payments를 사용할 준비가 된 경우 로 설정합니다. `Production`.

   >[!NOTE]
   >
   >사용자 _[!UICONTROL Sandbox Merchant ID]_및_[!UICONTROL Production Merchant ID]_ 샌드박스 및/또는 프로덕션에 대한 온보딩을 마치면 자동으로 생성되어 해당 어량 필드에 표시됩니다.

1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

이제 의 기본 설정을 계속 변경할 수 있습니다 [결제 옵션](#configure-payment-options) 함수 및 저장소 표시.

### 소프트 설명자 추가

을(를) 추가할 수 있습니다 [!UICONTROL Soft Descriptor] 웹 사이트 또는 개별 스토어 보기 구성에 매핑합니다. 소프트 설명자는 고객 거래 은행 명세서에 표시됩니다. 예를 들어 매장/브랜드/카탈로그가 여러 개 있는 경우, 사용자 지정 텍스트를에 추가하여 두 저장소 간에 쉽게 구분할 수 있습니다 [!UICONTROL Soft Descriptor] 필드.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![홈 보기](assets/payment-services-menu-small.png)

1. 클릭 **[!UICONTROL Settings]**. 자세한 내용은 [소개 [!DNL Payment Services] 홈](payments-home.md) 추가 정보.
1. 웹 사이트 또는 저장소 보기를 선택합니다. **[!UICONTROL Scope]** 소프트 설명자를 생성할 드롭다운 메뉴 초기 설정의 경우 다음 상태로 둡니다. **[!UICONTROL Default]** 기본값을 설정하려면 다음을 수행하십시오.
1. 텍스트 필드에 사용자 지정 텍스트(최대 22자)를 추가하고 `Custom descriptor`.
1. 클릭 **[!UICONTROL Save]**.
1. 웹 사이트 또는 저장소 보기에 대해 구성된 기본값 이외의 소프트 설명자를 생성하려면 다음을 수행합니다.
   1. 웹 사이트 또는 저장소 보기를 선택합니다. **[!UICONTROL Scope]** 소프트 설명자를 생성할 드롭다운 메뉴
   1. 전환 *해제* **[!UICONTROL Use website]** 또는 **[!UICONTROL Use default]**, 선택한 범위에 따라 다름).
   1. 텍스트 필드에 사용자 지정 텍스트를 추가합니다.
   1. 클릭 **[!UICONTROL Save]**.
1. 웹 사이트 또는 저장소 보기에 대해 사용하려면 기본 소프트 설명자를 참조하십시오 *또는* 상위 웹 사이트에 사용되는 소프트 설명자:
   1. 웹 사이트 또는 저장소 보기를 선택합니다. **[!UICONTROL Scope]** 기존 소프트 설명자를 활성화할 드롭다운 메뉴
   1. 전환 *on* **[!UICONTROL Use website]** 또는 **[!UICONTROL Use default]**, 선택한 범위에 따라 다름).
   1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Enable] | 웹 사이트 | 활성화 또는 비활성화 [!DNL Payment Services] 참조하십시오. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | 저장소 보기 | 스토어에 대한 메서드 또는 환경을 설정합니다. 옵션: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | 저장소 보기 | 샌드박스 온보딩 중에 자동으로 생성되는 샌드박스 머천트 ID입니다. |
| [!UICONTROL Production Merchant ID] | 저장소 보기 | 샌드박스 온보딩 중에 자동으로 생성되는 프로덕션 머천트 ID입니다. |
| [!UICONTROL Soft Descriptor] | 웹 사이트 또는 스토어 보기 | 웹 사이트 및 저장소 보기에 소프트 설명자를 추가하여 브랜드, 저장소 또는 제품 라인을 설명하는 고객 트랜잭션에 정보를 추가합니다. 다음 [!UICONTROL Use website] 토글은 웹 사이트 수준에 추가된 소프트 설명자를 적용합니다. 다음 [!UICONTROL Use default] 토글(toggle)은 기본값으로 추가된 소프트 설명자를 적용합니다. |

## 결제 옵션 구성

웹 사이트에 대해 결제 서비스를 활성화했으므로, 결제 기능 및 상점 표시에 대한 기본 설정을 변경할 수 있습니다.

### 신용 카드 필드

다음 _[!UICONTROL Credit Card Fields]_설정은 신용 카드 또는 직불 카드 결제 방법에 대해 간단하고 안전한 체크아웃 옵션을 제공합니다.

자세한 내용은 [결제 옵션](payments-options.md#credit-card-fields) 추가 정보.

1. 저장소 보기에서 **[!UICONTROL Scope]** 드롭다운 메뉴에서 결제 방법을 사용할 수 있습니다.
1. 체크아웃 중에 표시되는 결제 방법의 이름을 변경하려면 **[!UICONTROL Checkout title]** 필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 전환 **[!UICONTROL Payment action]** to `Authorize` 또는 `Authorize and Capture`.
1. 디버그 모드를 활성화하려면 **[!UICONTROL Debug Mode]** 선택기.
1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

#### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 저장소 보기 | 체크아웃하는 동안 결제 방법 보기에서 이 결제 옵션의 제호로 표시할 텍스트를 추가합니다. 옵션: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [결제 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions)지정한 결제 방법에 대한 {target=&quot;_blank&quot;} 입니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |

### 결제 단추

다음 [!DNL PayPal Smart Buttons] 결제 옵션은 고객을 위한 간단하고 빠르고 안전한 체크아웃 프로세스를 제공합니다. 자세한 내용은 [결제 옵션](payments-options.md#paypal-smart-buttons) 추가 정보.

PayPal 스마트 단추 결제 옵션을 활성화하고 구성할 수 있습니다.

1. 저장소 보기에서 **[!UICONTROL Scope]** 드롭다운 메뉴에서 결제 방법을 사용할 수 있습니다.
1. 체크아웃 중에 표시된 대로 결제 방법의 이름을 변경하려면 **[!UICONTROL Checkout Title]** 필드.
1. 종료 [결제 조치 설정](production.md#set-payment-services-as-payment-method), 전환 **[!UICONTROL Payment action]** to `Authorize` 또는 `Authorize and Capture`.
1. 토글 선택기를 사용하여 활성화하거나 비활성화합니다 [!DNL PayPal smart button] 디스플레이 기능:
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Apple Pay를 사용하려면 [Apple 개발자 계정이 있어야 합니다.](test-validate.md#test-in-sandbox-environment) (가짜 신용 카드 및 결제 정보 포함)를 테스트해 보십시오. 샌드박스에서 Apple Pay를 사용할 준비가 되면 *또는* 프로덕션 모드 [테스트 및 유효성 검사](test-validate.md)를 활성화하려면 영업 담당자에게 문의하십시오.

      지급 단추나 PayPal 나중에 지급 메시지에 대한 표시/해제를 켜거나 끌 때 해당 구성의 시각적 미리 보기가 설정 페이지 하단에 표시됩니다.

1. 디버그 모드를 활성화하려면 **[!UICONTROL Debug Mode]** 선택기.
1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

#### 구성 옵션

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 저장소 보기 | 체크아웃하는 동안 결제 방법 보기에서 이 결제 옵션의 제호로 표시할 텍스트를 추가합니다. 옵션: 텍스트 필드 |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [결제 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions)지정한 결제 방법에 대한 {target=&quot;_blank&quot;} 입니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | 저장소 보기 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 를 클릭합니다. 옵션: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | 저장소 보기 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 를 클릭합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | 저장소 보기 | 활성화 또는 비활성화 [!DNL PayPal Smart Buttons] 참조하십시오. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | 저장소 보기 | 지급 버튼이 표시되는 이후 지급 옵션 모양을 사용하거나 사용 안함으로 설정합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | 웹 사이트 | 장바구니, 제품 페이지, 미니 장바구니 및 체크아웃 흐름 중에 나중에 결제 메시지를 활성화 또는 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | 저장소 보기 | 지급 버튼이 표시되는 벤 지급 옵션을 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | 저장소 보기 | 지급 버튼이 표시되는 Apple 지급 옵션을 활성화 또는 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |

### 단추 스타일

를 구성할 수도 있습니다 _[!UICONTROL Button style]_PayPal 스마트 단추의 옵션:

1. 를 변경하려면 **[!UICONTROL Layout]**, 선택 `Vertical` 또는 `Horizontal`.

   >[!NOTE]
   >
   > 단추 스타일이 `Horizontal` 그리고 스토어에 여러 개의 PayPal 스마트 단추가 표시되도록 구성되며, 제품 페이지, 체크아웃 페이지, 미니 장바구니에 표시되는 버튼이 두 개, 장바구니에 표시되는 버튼이 한 개만 표시될 수 있습니다.

1. 가로 레이아웃에서 태그라인을 활성화하려면 **[!UICONTROL Show tagline]** 선택기.
1. 를 수정하려면 **[!UICONTROL Color]**&#x200B;원하는 색상 옵션을 선택합니다.
1. 를 수정하려면 **[!UICONTROL Shape]**, 선택 `Pill` 또는 `Rectangle`.
1. 단추 높이 선택기를 활성화하려면 **[!UICONTROL Responsive button height]** 선택기.
1. 를 수정하려면 **[!UICONTROL Label]**&#x200B;원하는 레이블 옵션을 선택합니다.

   레이아웃, 색상, 모양, 높이 및 레이블에 대한 구성 옵션을 변경하면 해당 구성의 시각적 미리 보기가 설정 페이지 하단에 표시됩니다.

1. 클릭 **[!UICONTROL Save]**.

   변경 사항을 저장하지 않고 이 보기에서 멀리 이동하려고 하면 변경 사항을 취소, 편집 유지 또는 저장하라는 모달이 표시됩니다.

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

다음을 구성할 수 있습니다 [!DNL PayPal Smart Buttons] 스타일링 [의 경우](configure-admin.md#configure-paypal-smart-buttons) 또는 여기에서 [!DNL Payment Services Home]. 자세한 내용은 [PayPal 단추 스타일 가이드](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) 를 참조하십시오.

#### 구성 옵션

| 필드 | 범위 | 설명 |
|--- |--- |--- |
| [!UICONTROL Layout] | 저장소 보기 | 결제 버튼의 레이아웃 스타일을 정의합니다. 옵션: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | 저장소 보기 | 태그라인을 활성화/비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | 저장소 보기 | 결제 버튼의 색상을 정의합니다. 옵션: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | 저장소 보기 | 결제 버튼의 모양을 정의합니다. 옵션: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | 저장소 보기 | 결제 단추에서 기본 높이를 사용하는지 여부를 정의합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | 저장소 보기 | 지급 버튼의 높이를 정의합니다. 기본값: 없음 |
| [!UICONTROL Label] | 저장소 보기 | 결제 버튼에 표시되는 레이블을 정의합니다. 옵션: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## 여러 PayPal 계정 사용

Payment Services에서 내에서 여러 PayPal 계정을 사용할 수 있습니다 **하나** 웹 사이트 수준의 머천트 계정. 예를 들어, 여러 국가(서로 다른 사용)에서 저장소를 운영하고 있는 경우 [통화](https://docs.magento.com/user-guide/stores/currency.html)) 또는 비즈니스 일부 부분에 Adobe Commerce을 사용하지만 *모두*&#x200B;여러 PayPal 계정을 사용하도록 머천트 계정을 설정할 수 있습니다.

자세한 내용은 [사이트, 저장 및 보기 범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) 웹 사이트, 스토어 및 저장소 보기의 계층 구조에 대한 자세한 정보.

영업 담당자가 [범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) PayPal을 사용하여 추가 사이트에 머천트 계정을 설정하고 온보딩하는 경우, 사용자가 구성하도록 구성한 PayPal 단추가 사이트에 표시되도록 합니다. 웹 사이트에 대해 여러 PayPal 계정을 사용하는 데 도움이 필요하면 영업 담당자에게 문의하십시오.
