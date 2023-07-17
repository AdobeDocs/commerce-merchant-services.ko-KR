---
title: "온보드 [!DNL Quick Checkout] for Adobe Commerce extension"
description: "다음 방법 알아보기 [!DNL Quick Checkout] 는 Adobe Commerce 인스턴스와 확장을 성공적으로 온보딩하고 설정하는 방법에 도움이 될 수 있습니다."
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 0%

---

# [!DNL Quick Checkout] 온보딩

을(를) 사용하려면 [!DNL Quick Checkout] Adobe Commerce 확장의 경우 인스턴스를 체크아웃 기능과 연결하려면 몇 가지 온보딩 단계를 완료해야 합니다.

![빠른 체크아웃](assets/overview-admin-panel.png)

1. [확장 가져오기](#get-extension).
1. [다음을 사용하여 프로덕션 또는 샌드박스 판매자 계정 만들기 [!DNL Bolt]](#create-account-with-bolt). 신원을 확인하는 데 필요한 모든 정보를 제공하십시오.
1. [고유한 을 제공합니다. [!DNL API Key] 및 [!DNL Publishable Key]](#obtain-api-credentials) 생성 위치 [!DNL Bolt].
1. [에서 결제 공급자를 설정합니다. [!DNL Bolt] account](#configure-payment-providers).
1. [활성화 드롭다운을 예로 설정합니다.](#enable-extension) 확장을 활성화합니다.
1. [서비스 설정 정의](#complete-admin-configuration) 을(를) 구성하려면 [!DNL Quick Checkout] 확장명.
1. [Save Config 클릭](#enable-live-quick-checkout) 확장을 활성화하는 단추입니다.
1. 범위 다음으로 전환 **기본 웹 사이트** 및 [콜백 URL 구성 클릭](#check-shopper-valid-account) 단추를 클릭합니다.

Gainsight가 활성화되면 **둘러보기** 의 단추 [!DNL Quick Checkout] 관리 패널 정보 [!DNL Quick Checkout] Adobe Commerce용:

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > 고급:

   ![빠른 체크아웃](assets/gainsight-admin.png)

Gainsight가 활성화되지 않은 경우 온보딩 단계를 계속 진행하십시오.

다음을 참조하십시오. [[!DNL Quick Checkout] 관리 패널](../quick-checkout/admin-panel.md) 항목 을 참조하십시오.

>[!NOTE]
>
> 을(를) 구성하지 않으면 [!DNL Bolt] 계정 샌드박스 또는 프로덕션 환경을 설정할 수 없습니다.

## 전제 조건

를 사용하려면 [!DNL Quick Checkout], 다음 항목을 사용할 수 있어야 합니다. [!DNL Bolt]:

- 지원되는 결제 공급자
- 의 판매자 및 생산 계정 [!DNL Bolt]
- API 및 [!DNL Publishable key] 생성 위치 [!DNL Bolt]

다음을 참조하십시오. [전제 조건](../quick-checkout/prerequisites.md) 항목 을 참조하십시오.

다음을 참조하십시오 [API 자격 증명](#obtain-api-credentials) 을(를) 만들거나 액세스하는 방법에 대해 알아보려면 [!DNL API keys] 예:

## 확장 가져오기

다음을 참조하십시오. [설치](../quick-checkout/install.md) 항목(확장 기능 획득에 대한 자세한 정보).

## 다음 계정으로 계정 만들기 [!DNL Bolt]

을(를) 구성하기 전에 [!DNL Quick Checkout] Adobe Commerce 관리에서 [샌드박스](https://merchant-sandbox.bolt.com/register?platform=magento2){target="_blank"} and [production](https://merchant.bolt.com/register?platform=magento2){target="_blank"}  의 판매자 계정 [!DNL Bolt]. 에서 계정을 만드는 데 필요한 모든 세부 정보를 제공합니다. [!DNL Bolt].

다음을 참조하십시오. [테스트 및 유효성 검사](../quick-checkout/testing.md) 항목 을 참조하십시오.

## API 자격 증명 가져오기

을(를) 사용하려면 [!DNL Quick Checkout] 다음이 필요합니다. [!DNL Bolt] 고유 키 및 [!DNL signing secret]. 다음 항목 얻기 [!DNL API keys] 로 이동하여 **개발자** > **API** > **키** 다음에서 **Bolt Merchant 대시보드**.

- [!DNL API key]: 백엔드에서 상호 작용하는 데 사용하는 개인 키 [!DNL Bolt] API.
- [!DNL Publishable key]: 프론트엔드가 상호 작용하는 데 사용하는 키 [!DNL Bolt] API.
- [!DNL Signing secret]: 다음 위치에서 받은 요청에 대한 서명 확인에 사용됩니다. [!DNL Bolt].

  ![빠른 체크아웃](assets/account-credentials.png)

다음을 참조하십시오. [[!DNL Bolt] 환경 세부 정보](https://help.bolt.com/developers/references/environment-details/#about-keys){target="_blank"} 키 및 서명 암호에 대해 알아볼 수 있는 페이지 [!DNL Bolt] 대상: [!DNL Quick Checkout] 확장명.

>[!CAUTION]
>
> 다음을 만들어야 합니다. [!DNL API keys] 샌드박스 및 프로덕션 환경 모두에 해당합니다.

## 결제 공급자 구성

결제 서비스 공급업체에 연결하려면 다음에 설명된 단계를 따르십시오. [프로세서 설정](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/){target="_blank"} 개발자 [!DNL Bolt] 페이지를 가리키도록 업데이트하는 중입니다.

## 확장 사용

1. 다음에서 _관리자_ 사이드바, 이동 **스토어** > _설정_ > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **판매** 및 선택 **체크아웃**.
1. 다음에서 [!DNL Quick Checkout] 보기, 설정 **사용** 끝 `Yes`.

![빠른 체크아웃](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> 빠른 체크아웃 필드는 다음 경우에만 표시됩니다. **사용** 이(가) (으)로 설정됨 `Yes`.

1. 사용할 방법(샌드박스 또는 프로덕션)을 선택합니다.

   - 테스트 및 개발을 위한 샌드박스
   - 라이브 결제 프로세서에서 트랜잭션을 처리하는 프로덕션

1. 고유 API 및 를 제공한 후 자격 증명의 유효성 검사 [!DNL Publishable keys].

![빠른 체크아웃](assets/quick-checkout-main-view.png)

다음을 참조하십시오. [설정](../quick-checkout/settings-quick-checkout.md) 항목 을 참조하십시오. [!DNL Quick Checkout] Adobe Commerce 확장.

>[!CAUTION]
>
> 고유한 API를 제공하고 [!DNL Publishable] 확장 기능을 활성화하기 전에 키. 그렇지 않으면 고객이 결제 양식을 보고 주문할 수 없습니다.

## 관리자 구성 완료

1. 다음에서 _관리자_ 사이드바, 다음 위치로 이동 **스토어** > **구성** > **체크아웃** 일반 체크 아웃 관리자 구성 페이지에 액세스합니다.
1. 다음에서 _서비스 설정_ 섹션에서 확장을 활성화하는 데 필요한 모든 세부 정보를 제공합니다.
1. 설정 _결제 작업_ 두 옵션 중 하나를 선택합니다.

   - `Authorize`: 승인 시 트랜잭션을 자동으로 캡처하지 마십시오.
   - `Authorize and Capture`: 인증 시 자동으로 트랜잭션을 캡처합니다.

Adobe Commerce 표준 체크아웃 옵션에 대한 자세한 내용은 [체크아웃](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 주제.

## 실시간 빠른 체크아웃 활성화

활성화하려면 [!DNL Quick Checkout] Adobe Commerce 확장의 경우:

1. 다음을 확인하십시오. [!UICONTROL Enable] 드롭다운이 다음으로 설정됨 **예** 확장을 활성화합니다.
1. 클릭 **구성 저장**.

## 쇼핑객 유효 계정 확인

쇼핑객의 구매 여부 확인 [!DNL Bolt] 계정:

1. 범위를 다음으로 전환 **기본 웹 사이트**.
1. 다음을 클릭합니다. **콜백 URL 구성** 단추를 클릭합니다. 이를 통해 다음을 수행할 수 있습니다. [!DNL Bolt] 쇼핑객에게 계정이 있는지 확인합니다. 그러면 OTP 팝업이 나타납니다.

   >[!CAUTION]
   >
   > 범위를 로 전환 **기본 웹 사이트** 는 적절한 URL이 설정되었는지 확인합니다. 각 웹 사이트에는 여러 도메인이 있을 수 있습니다.

다음을 참조하십시오. [사이트, 스토어 및 보기 범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings){target="_blank"} topic(Adobe Commerce의 범위에 대한 자세한 정보).

## 서비스 설정 구성

![빠른 체크아웃](assets/service-settings.png)

1. 설정 **체크아웃 추적 활성화** 끝 `Yes`.

   >[!CAUTION]
   >
   > Adobe Commerce은 Bolt와 체크아웃 추적 정보를 공유할 수 없으므로 이 옵션을 비활성화하면 보고에 영향을 줍니다.

1. 다음 항목 선택 **로그인 후 다음 단계** 고객이 로그인한 후 탐색 흐름을 변경하는 옵션입니다. 기본적으로 로 설정됩니다 **결제** 페이지를 가리키도록 업데이트하는 중입니다.
1. 다음과 같은 경우 정의 [!DNL Quick Checkout] 을(를) 허용합니다 **자동 로그인** 체크아웃하는 동안. 기본적으로에 자동으로 로그인하도록 활성화되어 있습니다. [!DNL Bolt] 네트워크.

   >[!NOTE]
   >
   > 다음을 참조하십시오 [Bolt&#39;s Enable Automatic Login 설명서](https://help.bolt.com/products/embedded/direct-api/auto-login/) 추가 정보.

## 도움말 보기

온보딩 프로세스는 의 설정 및 활성화에 필요한 단계를 안내하도록 설계되었습니다. [!DNL Express Checkout] 기능.

다음을 통해 Adobe Commerce 지원 센터에 문의 [Adobe Commerce 도움말 센터](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) 도움이 필요하시면

다음을 참조하십시오. [테스트 및 유효성 검사](../quick-checkout/testing.md) 항목 을 참조하십시오.
