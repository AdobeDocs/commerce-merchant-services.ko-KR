---
title: 테스트 샌드박스 설정
description: PayPal 샌드박스 계정을 사용하여 [!DNL Payment Services] 테스트 모드.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: 5aba246ce2a7802954a90c08c7dac2247a71ff6d
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# 테스트 샌드박스 설정

샌드박스 온보딩을 시작하기 전에 무료 PayPal 개발자 계정에 등록하고 머천트(온보딩에 사용)와 쇼퍼 계정(체크아웃을 테스트하는 데 사용)을 모두 만들어야 합니다. 원하는 경우 여러 개발자 계정을 만들 수 있습니다.

PayPal 샌드박스 계정을 사용하면 [!DNL Payment Services] 테스트 모드. PayPal을 사용하려면 PayPal Developer Portal에서 생성한 비즈니스 샌드박스 테스트 계정, 이메일 및 암호를 샌드박스 온보딩에 사용해야 합니다. *샌드박스 온보딩 프로세스 중에 다른 계정을 만들지 마십시오.*

## 샌드박스 온보딩

샌드박스 온보딩을 완료하려면

1. 로 이동합니다 [PayPal 개발자 계정 페이지](https://developer.paypal.com/developer/accounts/).
1. 클릭 **[!UICONTROL Log in to Dashboard]** 기존 PayPal Developer Portal 생성 비즈니스 샌드박스 테스트 계정으로 로그인하거나 **등록** 계정을 만들려면
1. PayPal 샌드박스 계정을 만듭니다.
   1. 이동 _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. 클릭 **[!UICONTROL Create account]**.

      샌드박스 PayPal 온보딩 프로세스 중에 PayPal 샌드박스 계정을 만든 경우 다음을 수행해야 합니다 [온보딩 샌드박스 재설정](#reset-your-sandbox-account) 또는 이메일을 확인할 수 없기 때문입니다.

   1. 선택 **[!UICONTROL Business]** 을(를) 계정 유형으로 사용하고 **[!UICONTROL Create]**.
   1. 에서 _[!UICONTROL Sandbox Accounts]_섹션에서_[!UICONTROL Manage accounts]_ 만든 샌드박스 계정에 대한 열입니다.
   1. 클릭 **[!UICONTROL View/edit account]**.

      ![PayPal - 샌드박스 계정 보기/편집](assets/onboarding-viewedit-sandbox.png)

   1. 나중에 사용할 수 있도록 이메일 ID 및 시스템 생성 암호를 복사하여 저장합니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. 클릭 **[!UICONTROL Sandbox onboarding]**.

   이 옵션은 용 샌드박스 온보딩을 아직 완료하지 않은 경우 표시됩니다 [!DNL Payment Services].

   샌드박스 머천 ID가 자동으로 생성되어 [설정](settings.md). 이 ID를 변경하거나 변경하지 마십시오.

   지급 수락을 시작하기 위해 PayPal 계정을 연결하는 PayPal 창이 표시됩니다.

1. 3단계에서 생성한 PayPal 샌드박스 계정의 전자 메일 및 암호를 입력하고(PayPal 비즈니스 계정 정보가 아님) 해당 국가 또는 지역을 입력합니다.
1. 클릭 **[!UICONTROL Next]**.

   ![PayPal - 지급 PayPal 계정 연결](assets/paypal-connectacct.png)

1. 이전에 저장한 샌드박스 계정 자격 증명을 사용하여 PayPal 흐름을 계속 따릅니다.
1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   다음 **[!UICONTROL Sandbox onboarding]** 단추가 더 이상 표시되지 않고 &quot;샌드박스 지급 보류 중&quot; 텍스트가 표시됩니다.

PayPal 샌드박스 온보딩이 승인되면, 결제 시스템이 현재 샌드박스 모드이며 라이브 지불을 처리하고 있지 않다는 알림이 표시됩니다.

>[!IMPORTANT]
>
>동의를 취소하는 경우 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 결제 처리를 위해(PayPal 계정 설정에서) 스토어의 주문은 [!DNL Payment Services]. 결제 서비스 홈에 해지된 동의에 대한 경고가 표시됩니다. 경고를 취소하려면 **[!UICONTROL Do not show again]**.

### 샌드박스 계정 재설정

샌드박스 PayPal 온보딩 프로세스 중에 PayPal 샌드박스 계정을 만든 경우, 또는 이메일을 확인할 수 없으므로 온보딩 샌드박스를 재설정해야 합니다.

샌드박스 계정을 재설정하려면 다음을 수행하십시오.

1. 클릭 **[!UICONTROL Reset sandbox]**. [PayPal 비즈니스 샌드박스 계정 만들기](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. 클릭 **[!UICONTROL Sandbox onboarding]** 다음 단계 세트를 완료합니다.

## 연락처 전화 번호 사용

연락처 전화 번호를 사용하면 PayPal이 고객으로부터 수집하는 연락처를 얻을 수 있습니다. PayPal은 항상 PayPal 계정 보유자로부터 연락처 전화 번호를 수집하여 자신의 ID를 확인하고 해당 고객과의 문제를 해결하거나 이행 프로세스를 완료할 수 있도록 합니다. 그러나 PayPal은 판매량에 부정적인 영향을 줄 수 있으므로 판매점에서 직접 연락처를 사용하는 것을 막고 있습니다. 자세한 내용은 [PayPal 전화 번호 받기](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) 설명서 를 참조하십시오.

이 기능은 다음과 같습니다 `off` 기본적으로 제공됩니다. 이 기능을 활성화하면 고객이 체크아웃 페이지 외부에서 Brand Checkout 흐름을 완료하면 저장소 관리자가 전화 번호를 볼 수 있습니다.

>[!IMPORTANT]
>
>이 설정은 다른 체크아웃 플로우에는 적용되지 않습니다.

## 샌드박스 환경에서 테스트

자세한 내용은 [테스트 및 유효성 검사](test-validate.md) 추가 정보.
