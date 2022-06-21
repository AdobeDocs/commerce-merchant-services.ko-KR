---
title: '"온보드 [!DNL Quick Checkout] Adobe Commerce 확장 프로그램'
description: '"자세한 내용은 [!DNL Quick Checkout] Adobe Commerce 인스턴스 및 확장을 성공적으로 온보드 및 설정하는 방법을 활용할 수 있습니다."'
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: a62c38adeb41812e91089716eb36c375b09595f4
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# [!DNL Quick Checkout] 온보딩

를 사용하여 시작하려면 [!DNL Quick Checkout] Adobe Commerce 확장의 경우 인스턴스를 체크아웃 기능과 연결하려면 몇 가지 온보딩 단계를 완료해야 합니다.

1. [확장 가져오기](#get-extension).
1. [을 사용하여 프로덕션 또는 샌드박스 머천트 계정 만들기 [!DNL Bolt]](#create-account-with-bolt). ID를 확인하는 데 필요한 모든 정보를 제공합니다.
1. [고유 값을 제공합니다 [!DNL API Key] 및 [!DNL Publishable Key] 생성된 [!DNL Bolt]](#obtain-api-credentials).
1. [에서 결제 공급자를 설정합니다. [!DNL Bolt] account](#configure-payment-providers).
1. [활성화 드롭다운을 예로 설정](#enable-extension) 확장을 활성화하려면
1. [서비스 설정 정의](#complete-admin-configuration) 를 [!DNL Quick Checkout] 확장.
1. [Save Config 단추를 클릭합니다.](#enable-live-quick-checkout) 확장을 활성화하려면

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

구성하기 전에 [!DNL Quick Checkout] Adobe Commerce 관리자에서 다음을 만들어야 합니다. [샌드박스](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} 및 [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} 머천트 계정 [!DNL Bolt]. 에서 계정을 만드는 데 필요한 모든 세부 정보를 제공합니다. [!DNL Bolt].

자세한 내용은 [테스트 및 유효성 검사](../quick-checkout/testing.md) 주제 를 참조하십시오.

## API 자격 증명 가져오기

를 사용하려면 [!DNL Quick Checkout] 필요한 경우 [!DNL Bolt] 고유 키. 다음을 얻습니다 [!DNL API keys] 으로 이동 **개발자** > **API** > **키** 에서 **볼트 머천트 대시보드**.

- [!DNL API key]: 백 엔드가 상호 작용하는 데 사용하는 개인 키 [!DNL Bolt] API.
- [!DNL Publishable key]: 선단이 상호 작용하는 데 사용하는 키 [!DNL Bolt] API.

자세한 내용은 [[!DNL Bolt] 환경 세부 사항](https://help.bolt.com/developers/references/environment-details/#about-keys)API에 대해 알아보려면 {target=&quot;_blank&quot;} 페이지 [!DNL Publishable keys] 대상 [!DNL Quick Checkout] 확장.

>[!CAUTION]
>
> 만들어야 합니다 [!DNL API keys] 을 사용할 수 있습니다.

## 결제 공급자 구성

결제 서비스 공급자를 연결하려면 [프로세서 설정](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;} 개발자 [!DNL Bolt] 페이지.

## 확장 활성화

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **스토어** > _설정_ > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **영업** 을(를) 선택합니다. **체크아웃**.

   ![빠른 체크아웃](assets/admin-view.png)

1. 에서 [!DNL Quick Checkout] 보기, 설정 **활성화** to `Yes`.
1. 사용할 방법(샌드박스 또는 프로덕션)을 선택하십시오.

   - 테스트 및 개발을 위한 샌드박스
   - Production to process 트랜잭션을 Live Payment 처리로 처리

1. 고유 API를 제공한 후 자격 증명을 확인하고 [!DNL Publishable keys].

>[!CAUTION]
>
> 고유한 API를 제공하고 [!DNL Publishable keys] 확장을 활성화하기 전에는 고객이 결제 양식을 볼 수 있으며 주문을 할 수 없습니다.

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

## 지원 요청

온보딩 프로세스는 을 설정하고 구현하는 데 필요한 단계를 안내하도록 설계되었습니다 [!DNL Express Checkout] 기능을 사용할 수 있습니다. 지정된 Slack을 통해 Adobe Commerce 엔지니어링 팀에 문의하십시오 [Adobe 베타 프로그램 채널](http://adobe-beta-programs.slack.com/) 채널 을 참조하십시오.

자세한 내용은 [테스트 및 유효성 검사](../quick-checkout/testing.md) 주제 를 참조하십시오.
