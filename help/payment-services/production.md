---
title: 활성화 [!DNL Payment Services] 프로덕션
description: 을(를) 활성화하여 온보딩 프로세스를 완료합니다 [!DNL Payment Services] 제작 관련
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 활성화 [!DNL Payment Services] 프로덕션

Payments Services 확장이 [설치](install.md)이면 인스턴스가 [구성 및 연결](connect.md), 그리고 [샌드박스 설정](sandbox.md) 테스트한 후 서비스를 프로덕션에 넣고 [온보딩 프로세스](onboard.md).

## 설정 [!DNL Payment Services] 결제 방법

다음에 [commerce Services 구성](connect.md#configure-commerce-services) 다음 중 하나를 활성화합니다. [샌드박스 테스트](sandbox.md#enable-sandbox-testing) 또는 [지불](#enable-live-payments), 설정해야 합니다. [!DNL Payment Services] 을 결제 방법으로 사용할 수 있습니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 클릭 **[!UICONTROL Enable Payment Services]**.

   이 옵션은 아직 구성되지 않은 경우 표시됩니다 [!DNL Payment Services] 하나 이상의 Magento 웹 사이트에 대한 결제 방법입니다.

   관련 옵션이 확장되어 홈 보기에서 설정 영역으로 이동됩니다(**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_) 여기에서 [!DNL Payment Services] 옵션 [결제 방법](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target=&quot;_blank&quot;}.

1. in _[!UICONTROL General Configuration]_, 설정&#x200B;**[!UICONTROL Enable]**to `Yes`.
1. 설정 **[!UICONTROL Payment Action]**, 두 가지 모두에 대해 _[!UICONTROL Credit Card Fields]_및_[!UICONTROL PayPal Smart Buttons]_&#x200B;를 다음 중 한 곳에 추가합니다.

   | 설정 | 설명 |
   |---|---|
   | `Authorize` | 구매승인을 하고 자금을 보류한다. 그 금액은 상인이 포획할 때까지 인출되지 않는다. |
   | `Authorize and Capture` | 상인은 구매를 승인하고 자금을 &quot;회수&quot;한다. |

1. 클릭 **[!UICONTROL Save]**.
1. 클릭 **[!UICONTROL Go to Payment Services]** 다시 [!DNL Payment Services] 집에
1. [캐시 지우기](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}.

   구성 변경이 있을 때마다 선택을 취소해야 합니다.

자세한 내용은 [결제 서비스 구성](settings.md) 신용 카드 필드 및 PayPal 스마트 단추 구성에 대한 자세한 내용을 참조하십시오.

## Complete Merchant 온보딩

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 클릭 **[!UICONTROL Live onboarding]**.

   에 대한 라이브 온보딩을 아직 완료하지 않은 경우 이 옵션이 표시됩니다 [!DNL Payment Services].

   PayPal 창이 표시됩니다.

1. PayPal 계정 자격 증명(샌드박스 계정 자격 증명이 아님)을 사용하여 PayPal 흐름을 계속 진행하거나 새 PayPal 계정에 등록하십시오.
1. 관리 사이드바에서 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   다음 _[!UICONTROL Live onboarding]_단추가 더 이상 보이지 않고 &quot;[!UICONTROL Live payments pending]&quot; 텍스트 상자.

   해당 텍스트 상자에서 PayPal로 이메일 주소를 확인하여 온보딩을 완료하라는 메시지가 표시될 수도 있습니다.

1. 이메일 주소를 확인하라는 메시지가 표시되면 PayPal에서 보낸 확인 메시지를 이메일로 확인하고 을 클릭하여 이메일 주소를 확인합니다.
1. 관리 사이드바에서 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 브라우저 창을 새로 고칩니다.

   PayPal 머천트 온보딩이 승인되면, 결제 시스템이 샌드박스 모드이며 라이브 결제를 처리하지 않는다는 내용의 알림이 표시됩니다.

   >[!IMPORTANT]
   >
   >동의를 취소하는 경우 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 결제 처리를 위해(PayPal 계정 설정에서) 스토어의 주문은 [!DNL Payment Services].

## Adobe에서 지급 자격 요청

Live Onboarding을 사용하려면 Adobe에서 지급을 요청해야 합니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 클릭 **[!UICONTROL Get Live Payments]** 다음 위치에서 [!DNL Payment Services] 집에

   ![권한 요청](assets/request-entitlements.png)

1. 양식을 작성합니다.
1. 영업팀 직원이 연락드리겠습니다.

또는 Adobe에서 지급 자격을 요청할 수 있습니다 [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**라이브 온보딩** 지급 자격이 승인될 때까지 액세스할 수 없습니다.

## 가격 책정 계층 구성

원하는 [!DNL Payment Services] _Merchant ID_:


1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 홈 보기에서 **[!UICONTROL Settings]**. 자세한 내용은 [홈](payments-home.md) 추가 정보.
1. 필요한 을(를) 선택합니다 _Merchant ID_ 영업 담당자에게 제출하면 올바른 가격 책정 계층을 구성할 수 있습니다.

## 라이브 지급 활성화

A _프로덕션 머천트 ID_ 는 자동으로 생성되어 [구성](configure-admin.md). 이 ID를 변경하거나 변경하지 마십시오.

Live Payments를 사용하려면

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 홈에서 **[!UICONTROL Settings]** 을 클릭합니다. 자세한 내용은 [홈](payments-home.md) 추가 정보.
1. 에서 _[!UICONTROL General Configuration]_섹션 세트&#x200B;**[!UICONTROL Payment mode]**to `Production`.
1. 클릭 **[!UICONTROL Save]**.
1. [캐시 지우기](https://docs.magento.com/user-guide/system/cache-management.html){target=&quot;_blank&quot;}.

   >[!IMPORTANT]
   >
   >캐시를 지우지 않으면 체크아웃 중에 PayPal 결제 옵션이 표시되지 않습니다.

로 돌아가는 경우 [!DNL Payment Services] 홈에서 이제 Live Payments를 처리하고 있으므로 Sandbox 결제 모드 메시지가 더 이상 표시되지 않습니다.

자세한 내용은 [관리자에서 구성](configure-admin.md) 을 참조하십시오.

>[!IMPORTANT]
>
>동의를 취소하는 경우 [!DNL Payment Services] 결제 처리를 위해(PayPal 계정 설정에서) 스토어의 주문은 [!DNL Payment Services]. 결제 처리를 다시 활성화하려면 온보딩을 다시 완료해야 합니다.

## 프로덕션 테스트

구매자에게 이 기능을 노출하기 전에 실제 신용카드와 은행과 함께 프로덕션에서 결제를 테스트하는 것이 좋습니다.

자세한 내용은 [테스트 및 유효성 검사](test-validate.md) 추가 정보.
