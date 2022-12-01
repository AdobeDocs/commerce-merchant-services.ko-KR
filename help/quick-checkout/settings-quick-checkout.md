---
title: 구성 [!DNL Quick Checkout] Adobe Commerce 확장 프로그램
description: 에 대한 구성 옵션을 알아봅니다 [!DNL Quick Checkout] 확장을 성공적으로 온보드 및 설정하는 방법.
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
source-git-commit: 1f2305df7566cd77a6be161cc9d1265c0291171c
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# [!DNL Quick Checkout] 설정

[!DNL Quick Checkout] Adobe Commerce 및 Magento Open Source의 경우 확장을 설정하는 데 필요한 모든 정보가 있는 구성 보기를 제공합니다.

이러한 구성 설정에 액세스하려면

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **스토어** > _설정_ > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **영업** 을(를) 선택합니다. **체크아웃**.

   ![빠른 체크아웃](assets/quick-checkout-main-view-admin.png)

자세한 내용은 [온보딩](../quick-checkout/onboarding.md) 구성 방법에 대한 자세한 내용은 항목을 참조하십시오 [!DNL Quick Checkout] Adobe Commerce용.

## 확장 활성화

![빠른 체크아웃](assets/enable-method.png)

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Enable] | 웹 사이트 | 활성화 또는 비활성화 [!DNL Quick Checkout] 참조하십시오. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 웹 사이트 | 에 대해 메서드 또는 환경을 설정합니다. [!DNL Quick Checkout]. 옵션: [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style=&quot;table-layout:auto&quot;}

## 계정 자격 증명

![빠른 체크아웃](assets/account-creds.png)

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL API key] | 웹 사이트 | 백 엔드가 상호 작용하는 데 사용하는 개인 키 [!DNL Bolt] API. |
| [!UICONTROL Publishable key] | 웹 사이트 | 선단이 상호 작용하는 데 사용하는 키 [!DNL Bolt] API. |
| [!UICONTROL Signing secret] | 웹 사이트 | 에서 받은 요청에 대한 서명 확인에 사용됩니다. [!DNL Bolt]. |

{style=&quot;table-layout:auto&quot;}

## 서비스 설정

![빠른 체크아웃](assets/service-settings.png)

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 저장소 보기 | 체크아웃하는 동안 결제 방법 보기에서 이 결제 옵션의 제호로 표시할 텍스트를 추가합니다. 옵션: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [결제 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions)지정한 결제 방법에 대한 {target=&quot;_blank&quot;} 입니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | 웹 사이트 | Adobe Commerce에서 체크아웃 추적 정보를 볼트와 공유할 수 있도록 허용하는지 정의합니다. 기본적으로 활성화되어 있습니다. 비활성화하면 보고에 영향을 줍니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | 웹 사이트 | 고객이 로그인한 후 탐색 흐름을 변경합니다. 옵션: [!UICONTROL Payment] / [!UICONTROL Shipping] |

{style=&quot;table-layout:auto&quot;}
