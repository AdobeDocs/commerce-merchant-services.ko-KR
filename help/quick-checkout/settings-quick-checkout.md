---
title: 구성 [!DNL Quick Checkout] Adobe Commerce 확장
description: 에 대한 구성 옵션 알아보기 [!DNL Quick Checkout] 확장을 성공적으로 온보딩하고 설정하는 방법.
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# [!DNL Quick Checkout] 설정

[!DNL Quick Checkout] Adobe Commerce 및 Magento Open Source용 에서는 확장을 설정하는 데 필요한 모든 정보가 포함된 구성 보기를 제공합니다.

이러한 구성 설정에 액세스하려면:

1. 다음에서 _관리자_ 사이드바, 이동 **스토어** > _설정_ > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **판매** 및 선택 **체크아웃**.

   ![빠른 체크아웃](assets/config-new-logo-view.png)

다음을 참조하십시오. [온보딩](../quick-checkout/onboarding.md) 항목 을 참조하십시오. [!DNL Quick Checkout] Adobe Commerce용

## 확장 사용

![빠른 체크아웃](assets/enable-method.png)

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Enable] | 웹 사이트 | 활성화 또는 비활성화 [!DNL Quick Checkout] 웹 사이트용. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | 웹 사이트 | 에 대한 메서드 또는 환경을 설정합니다. [!DNL Quick Checkout]. 옵션: [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## 계정 자격 증명

![빠른 체크아웃](assets/account-creds.png)

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL API key] | 웹 사이트 | 백엔드에서 상호 작용하는 데 사용하는 개인 키 [!DNL Bolt] API. |
| [!UICONTROL Publishable key] | 웹 사이트 | 프론트엔드에서 상호 작용하는 데 사용하는 키 [!DNL Bolt] API. |
| [!UICONTROL Signing secret] | 웹 사이트 | 에서 받은 요청에 대한 서명 확인에 사용됩니다. [!DNL Bolt]. |

{style="table-layout:auto"}

## 서비스 설정

![빠른 체크아웃](assets/service-settings.png)

| 필드 | 범위 | 설명 |
|---|---|---|
| [!UICONTROL Title] | 스토어 뷰 | 체크아웃 중에 결제 방법 보기에서 이 결제 방법의 제목으로 표시할 텍스트를 추가합니다. 옵션: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | 웹 사이트 | 다음 [지불 조치](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 지정된 결제 방법에 대해 참조할 수 있습니다. 옵션: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | 웹 사이트 | 디버그 모드를 활성화하거나 비활성화합니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | 웹 사이트 | Adobe Commerce에서 체크아웃 추적 정보를 Bolt와 공유할 수 있는지 여부를 정의합니다. 기본적으로 활성화되어 있습니다. 비활성화하면 보고에 영향을 줍니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | 웹 사이트 | 고객이 로그인한 후 탐색 흐름을 변경합니다. 옵션: [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | 웹 사이트 | 다음과 같은 경우 정의 [!DNL Quick Checkout] 체크아웃 중에 자동 로그인을 허용합니다. 기본적으로 활성화되어 있습니다. 옵션: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | 웹 사이트 | 고객이 자동으로 로그인하는 네트워크를 선택합니다. 기본적으로 볼트(Bolt)가 활성화되었습니다. 옵션: [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
