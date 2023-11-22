---
title: 사용 [!DNL Payment Services] 프로덕션용
description: 을(를) 활성화하여 온보딩 프로세스를 완료합니다. [!DNL Payment Services] 프로덕션용
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '731'
ht-degree: 0%

---

# 사용 [!DNL Payment Services] 프로덕션용

서비스를 프로덕션에 넣고 다음을 완료할 수 있습니다. [온보딩 프로세스](onboard.md), 이 항목의 단계에 따라 다음 작업을 수행하십시오.

* [설치](install.md) 결제 서비스 확장
* [구성 및 연결](connect.md) 내 인스턴스
* [설정](sandbox.md) 및 [테스트](test-validate.md) 내 샌드박스

## 설정 [!DNL Payment Services] 결제 방법으로

이후 [상거래 서비스 구성](connect.md#configure-commerce-services) 다음 중 하나를 활성화합니다. [샌드박스 테스트](sandbox.md#enable-sandbox-testing) 또는 [라이브 결제](#enable-live-payments), 다음을 설정해야 합니다. [!DNL Payment Services] 결제 방법을 사용하겠습니다.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 클릭 **[!UICONTROL Enable Payment Services]**.

   이 옵션은 아직 구성하지 않은 경우 표시됩니다 [!DNL Payment Services] 하나 이상의 웹 사이트에 대한 결제 방법으로 사용됩니다.

   관련 옵션이 확장된 상태로 홈 보기의 설정 영역으로 이동합니다(**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_)를 클릭하여 제품에서 [!DNL Payment Services] 옵션 을 참조하십시오. [결제 방법](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. 위치 _[!UICONTROL General Configuration]_, 설정됨&#x200B;**[!UICONTROL Enable]**끝 `Yes`.
1. 설정 **[!UICONTROL Payment Action]**, 두 가지 모두에 대해 _[!UICONTROL Credit Card Fields]_및_[!UICONTROL PayPal Smart Buttons]_&#x200B;을 클릭하여 다음 중 하나로 만듭니다.

   | 설정 | 설명 |
   |---|---|
   | `Authorize` | 구매를 승인하고 자금을 보류합니다. 상인에게 &#39;포착&#39;되기 전까지는 그 금액이 인출되지 않는다. |
   | `Authorize and Capture` | 구매를 승인하고 판매자가 자금을 &quot;캡처&quot;합니다. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] 는 부분 캡처를 지원합니다. 판매자는 주문의 일부를 부분적으로 수집(송장)할 수 있습니다. 예를 들어 각 항목을 개별적으로 캡처하거나 지금 항목 하나와 나중에 항목 하나를 캡처할 수 있습니다.

1. 클릭 **[!UICONTROL Save]**.
1. 클릭 **[!UICONTROL Go to Payment Services]** 로 돌아가려면 [!DNL Payment Services] 집.
1. [캐시 지우기](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   모든 구성 변경 후 지우기를 수행해야 합니다.

다음을 참조하십시오 [결제 서비스 구성](settings.md) 신용 카드 필드 및 PayPal 스마트 단추 구성에 대한 자세한 내용을 보려면.

## 완전한 판매자 온보딩

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 클릭 **[!UICONTROL Live onboarding]**.

   다음에 대한 라이브 온보딩을 아직 완료하지 않은 경우 이 옵션이 표시됩니다 [!DNL Payment Services].

   PayPal 창이 나타납니다.

1. PayPal 계정 자격 증명(샌드박스 계정 자격 증명이 아님)을 사용하여 PayPal 흐름을 계속 진행하거나 새 PayPal 계정에 등록합니다.
1. 관리 사이드바에서 다음 위치로 이동하십시오. **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   다음 _[!UICONTROL Live onboarding]_버튼이 더 이상 표시되지 않고 &quot;[!UICONTROL Live payments pending]&quot; 텍스트 상자입니다.

   이 텍스트 상자에는 온보딩을 완료하기 위해 PayPal을 사용하여 이메일 주소를 확인하라는 메시지가 표시될 수도 있습니다.

1. 이메일 주소를 확인하라는 메시지가 표시되면 PayPal에서 보낸 확인 메시지에 대해 이메일을 확인하고 을 클릭하여 이메일 주소를 확인합니다.
1. 관리 사이드바에서 다음 위치로 이동하십시오. **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 브라우저 창을 새로 고칩니다.

   PayPal 판매자 온보딩이 승인되면 결제 시스템이 샌드박스 모드이고 라이브 결제를 처리하지 않는다는 알림이 표시됩니다.

   >[!IMPORTANT]
   >
   >에 대한 동의를 취소하는 경우 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 결제를 처리하기 위해(PayPal 계정 설정에서) 스토어의 주문은 [!DNL Payment Services]. 결제 서비스 홈에서 해지된 동의에 대한 경고가 나타납니다.

## Adobe에서 결제 권한 요청

라이브 온보딩을 활성화하려면 Adobe에서 지급 자격을 요청해야 합니다.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 클릭 **[!UICONTROL Get Live Payments]** (으)로 [!DNL Payment Services] 집.

   ![권한 요청](assets/request-entitlements.png){width="500" zoomable="yes"}

1. 양식을 작성합니다.
1. 영업팀 직원이 연락을 드릴 것입니다.

또는 다음 Adobe에서 결제 권한을 요청할 수 있습니다. [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**라이브 온보딩** 지급 권한이 승인될 때까지 액세스할 수 없습니다.

## 가격 책정 계층 구성

을(를) 가져오려면 [!DNL Payment Services] _판매자 ID_:


1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 홈 보기에서 **[!UICONTROL Settings]**. 다음을 참조하십시오 [홈](payments-home.md) 추가 정보.
1. 필요한 항목 선택 _판매자 ID_ 영업 담당자에게 제출하면 영업 담당자가 정확한 가격 책정 계층을 구성하게 됩니다.

## 라이브 결제 활성화

A _프로덕션 판매자 ID_ 는에서 자동 생성되고 채워집니다. [구성](configure-admin.md). 이 ID를 변경하거나 변경하지 마십시오.

라이브 지급을 사용하려면

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 홈에서 **[!UICONTROL Settings]** 페이지 오른쪽 상단에 있습니다. 다음을 참조하십시오 [홈](payments-home.md) 추가 정보.
1. 다음에서 _[!UICONTROL General Configuration]_섹션 세트&#x200B;**[!UICONTROL Payment mode]**끝 `Production`.
1. 클릭 **[!UICONTROL Save]**.
1. [캐시 지우기](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >캐시를 지우지 않으면 고객이 체크아웃 중에 PayPal 결제 옵션을 볼 수 없습니다.

다음으로 돌아가는 경우 [!DNL Payment Services] 홈에서 이제 라이브 결제를 처리 중이므로 샌드박스 결제 모드 메시지가 더 이상 표시되지 않습니다.

다음을 참조하십시오 [관리에서 구성](configure-admin.md) 레거시 구성 옵션의 경우

>[!IMPORTANT]
>
>에 대한 동의를 취소하는 경우 [!DNL Payment Services] 결제를 처리하기 위해(PayPal 계정 설정에서) 스토어의 주문은 [!DNL Payment Services]. 결제 처리를 다시 활성화하려면 온보딩을 다시 완료해야 합니다. 결제 서비스 홈에서 해지된 동의에 대한 경고가 나타납니다.

## 프로덕션에서 테스트

이 기능을 쇼핑객에게 노출하기 전에 실제 신용 카드 및 은행으로 생산 시 결제를 테스트하는 것이 좋습니다.

다음을 참조하십시오 [테스트 및 유효성 검사](test-validate.md) 추가 정보.
