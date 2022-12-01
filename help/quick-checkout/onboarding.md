---
title: '"온보드 [!DNL Quick Checkout] Adobe Commerce 확장 프로그램'
description: "자세한 내용은 [!DNL Quick Checkout] Adobe Commerce 인스턴스 및 확장을 성공적으로 온보드 및 설정하는 방법을 활용할 수 있습니다."
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: 1f2305df7566cd77a6be161cc9d1265c0291171c
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 0%

---

# [!DNL Quick Checkout] 온보딩

를 사용하여 시작하려면 [!DNL Quick Checkout] Adobe Commerce 확장의 경우 인스턴스를 체크아웃 기능과 연결하려면 몇 가지 온보딩 단계를 완료해야 합니다.

![빠른 체크아웃](assets/overview-admin-panel.png)

1. [확장 가져오기](#get-extension).
1. [을 사용하여 프로덕션 또는 샌드박스 머천트 계정 만들기 [!DNL Bolt]](#create-account-with-bolt). ID를 확인하는 데 필요한 모든 정보를 제공합니다.
1. [고유 값을 제공합니다 [!DNL API Key] 및 [!DNL Publishable Key]](#obtain-api-credentials) 생성된 [!DNL Bolt].
1. [에서 결제 공급자를 설정합니다. [!DNL Bolt] account](#configure-payment-providers).
1. [활성화 드롭다운을 예로 설정](#enable-extension) 확장을 활성화하려면
1. [서비스 설정 정의](#complete-admin-configuration) 를 [!DNL Quick Checkout] 확장.
1. [Save Config 를 클릭합니다.](#enable-live-quick-checkout) 확장을 활성화하는 단추.
1. 범위를 다음으로 전환 **기본 웹 사이트** 및 [콜백 URL 구성 을 클릭합니다.](#check-shopper-valid-account) 버튼을 클릭합니다.

Gainsight가 활성화된 경우 **관광을 하세요** 버튼 [!DNL Quick Checkout] 관리 패널 정보 [!DNL Quick Checkout] Adobe Commerce용:

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > 고급:

   ![빠른 체크아웃](assets/gainsight-admin.png)

Gainsight가 활성화되지 않은 경우 온보딩 단계를 계속 진행합니다.

자세한 내용은 [[!DNL Quick Checkout] 관리 패널](../quick-checkout/admin-panel.md) 주제 를 참조하십시오.

>[!NOTE]
>
> 을 구성하지 않으면 [!DNL Bolt] 샌드박스 또는 프로덕션 환경을 설정할 수 없는 계정입니다.

## 전제 조건

를 사용하려면 [!DNL Quick Checkout]에 사용할 수 있는 다음 항목이 있어야 합니다. [!DNL Bolt]:

- 지원되는 결제 공급자
- 의 Merchant 및 Production 계정 [!DNL Bolt]
- API 및 [!DNL Publishable key] 생성된 [!DNL Bolt]

자세한 내용은 [전제 조건](../quick-checkout/prerequisites.md) 주제 를 참조하십시오.

자세한 내용은 [API 자격 증명](#obtain-api-credentials) 을(를) 만들거나 액세스하는 방법을 알아봅니다. [!DNL API keys] 참조하십시오.

## 확장 가져오기

자세한 내용은 [설치](../quick-checkout/install.md) 확장을 가져오는 방법에 대한 자세한 내용은 항목을 참조하십시오.

## 계정 만들기 [!DNL Bolt]

구성하기 전에 [!DNL Quick Checkout] Adobe Commerce 관리자에서 다음을 만들어야 합니다. [샌드박스](https://merchant-sandbox.bolt.com/register?platform=magento2){target=&quot;_blank&quot;} 및 [production](https://merchant.bolt.com/register?platform=magento2){target=&quot;_blank&quot;} 머천트 계정 [!DNL Bolt]. 에서 계정을 만드는 데 필요한 모든 세부 정보를 제공합니다. [!DNL Bolt].

자세한 내용은 [테스트 및 유효성 검사](../quick-checkout/testing.md) 주제 를 참조하십시오.

## API 자격 증명 가져오기

를 사용하려면 [!DNL Quick Checkout] 필요한 경우 [!DNL Bolt] 고유 키 및 [!DNL signing secret]. 다음을 얻습니다 [!DNL API keys] 으로 이동 **개발자** > **API** > **키** 에서 **볼트 머천트 대시보드**.

- [!DNL API key]: 백 엔드가 상호 작용하는 데 사용하는 개인 키 [!DNL Bolt] API.
- [!DNL Publishable key]: 선단이 상호 작용하는 데 사용하는 키 [!DNL Bolt] API.
- [!DNL Signing secret]: 에서 받은 요청에 대한 서명 확인에 사용됩니다. [!DNL Bolt].

   ![빠른 체크아웃](assets/account-credentials.png)

자세한 내용은 [[!DNL Bolt] 환경 세부 사항](https://help.bolt.com/developers/references/environment-details/#about-keys)다음 페이지에서 키 및 서명 비밀에 대해 알아보려면 {target=&quot;_blank&quot;} 페이지를 참조하십시오. [!DNL Bolt] 대상 [!DNL Quick Checkout] 확장.

>[!CAUTION]
>
> 만들어야 합니다 [!DNL API keys] 을 사용할 수 있습니다.

## 결제 공급자 구성

결제 서비스 공급자를 연결하려면 [프로세서 설정](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target=&quot;_blank&quot;} 개발자 [!DNL Bolt] 페이지.

## 확장 활성화

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **스토어** > _설정_ > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **영업** 을(를) 선택합니다. **체크아웃**.
1. 에서 [!DNL Quick Checkout] 보기, 설정 **활성화** to `Yes`.

![빠른 체크아웃](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> 빠른 체크아웃 필드는 **활성화** 가 로 설정되어 있습니다. `Yes`.

1. 사용할 방법(샌드박스 또는 프로덕션)을 선택하십시오.

   - 테스트 및 개발을 위한 샌드박스
   - Production to process 트랜잭션을 Live Payment 처리로 처리

1. 고유 API를 제공한 후 자격 증명을 확인하고 [!DNL Publishable keys].

![빠른 체크아웃](assets/quick-checkout-main-view-react.png)

자세한 내용은 [설정](../quick-checkout/settings-quick-checkout.md) 구성 옵션에 대한 자세한 내용은 를 참조하십시오. [!DNL Quick Checkout] Adobe Commerce 확장

>[!CAUTION]
>
> 고유한 API를 제공하고 [!DNL Publishable] 확장을 활성화하기 전에 키가 있으면 고객이 결제 양식을 볼 수 있고 주문을 할 수 없습니다.

## 관리 구성 완료

1. 설정 _관리_ 사이드바, 탐색 **스토어** > **구성** > **체크아웃** 를 눌러 일반 체크아웃 관리 구성 페이지에 액세스합니다.
1. 에서 _서비스 설정_ 섹션에서 확장을 활성화하는 데 필요한 모든 세부 사항을 제공합니다.
1. 설정 _결제 조치_ 다음 중 하나를 선택합니다.

   - `Authorize`: 승인 시 트랜잭션을 자동으로 캡처하지 마십시오.
   - `Authorize and Capture`: 승인 시 트랜잭션을 자동으로 캡처합니다.

Adobe Commerce 표준 체크아웃 옵션에 대한 자세한 내용은 [체크아웃](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 주제.

## 라이브 빠른 체크아웃 활성화

를 사용하려면 [!DNL Quick Checkout] Adobe Commerce 확장:

1. 다음을 확인하십시오. [!UICONTROL Enable] 드롭다운이 **예** 확장을 활성화하려면
1. 클릭 **구성 저장**.

## 구매자의 유효한 계정 확인

쇼핑객에게 [!DNL Bolt] 계정:

1. 범위를 다음으로 전환 **기본 웹 사이트**.
1. 을(를) 클릭합니다. **콜백 URL 구성** 버튼을 클릭합니다. 이렇게 하면 [!DNL Bolt] 에 계정이 있는지 확인합니다. 그러면 OTP 팝업이 나타납니다.

   >[!CAUTION]
   >
   > 범위를 로 전환 **기본 웹 사이트** 는 적절한 URL이 설정되었는지 확인합니다. 각 웹 사이트에는 여러 도메인이 있을 수 있습니다.

자세한 내용은 [사이트, 저장 및 보기 범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)Adobe Commerce의 범위에 대한 자세한 내용은 {target=&quot;_blank&quot;} 항목을 참조하십시오.

## 서비스 설정 구성

![빠른 체크아웃](assets/service-settings.png)

1. 설정 **체크아웃 추적 활성화** to `Yes`.

   >[!CAUTION]
   >
   > Adobe Commerce은 볼트와 체크아웃 추적 정보를 공유할 수 없으므로 이 옵션을 비활성화하면 보고에 영향을 줍니다.

1. 을(를) 선택합니다 **로그인 후 다음 단계** 고객이 로그인한 후 탐색 흐름을 변경하는 옵션입니다. 기본적으로 **결제** 페이지.

## 지원 요청

온보딩 프로세스는 을 설정하고 구현하는 데 필요한 단계를 안내하도록 설계되었습니다 [!DNL Express Checkout] 기능을 사용할 수 있습니다.

다음을 통해 Adobe Commerce 지원 센터에 문의하십시오 [Adobe Commerce 도움말 센터](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=en) 도움이 필요하십니까?

자세한 내용은 [테스트 및 유효성 검사](../quick-checkout/testing.md) 주제 를 참조하십시오.
