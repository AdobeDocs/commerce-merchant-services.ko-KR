---
title: 온보드 [!DNL Express Checkout] Adobe Commerce 확장 프로그램
description: 방법 알아보기 [!DNL Express Checkout] Adobe Commerce 인스턴스 및 확장을 성공적으로 온보드 및 설정하는 방법을 활용할 수 있습니다.
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# [!DNL Express Checkout] 온보딩

>[!IMPORTANT]
>
> 이 기능은 EAP(Early Adopter Program) 사용자만 사용할 수 있으며 모든 고객이 아직 액세스할 수 없습니다. 현재 미국 고객에게만 제공됩니다. 도움이 필요한 경우 Adobe Commerce 지원 센터에 문의하십시오.

를 사용하여 시작하려면 [!DNL Express Checkout] Adobe Commerce 확장의 경우 인스턴스를 체크아웃 기능과 연결하려면 몇 가지 온보딩 단계를 완료해야 합니다.

1. [확장 가져오기](#get-extension).
1. [Bolt를 사용하여 프로덕션 또는 샌드박스 머천트 계정을 만듭니다](#create-account-with-bolt). ID를 확인하는 데 필요한 모든 정보를 제공합니다.
1. [볼트에서 생성된 고유한 API 키 및 게시 가능한 키를 제공합니다](#obtain-api-credentials).
1. [볼트(Bolt) 계정에서 결제 공급자를 설정합니다](#configure-payment-providers).
1. [활성화 드롭다운을 예로 설정](#enable-extension) 확장을 활성화하려면
1. [서비스 설정 정의](#complete-admin-configuration) 를 [!DNL Express Checkout] 확장.
1. [Save Config 단추를 클릭합니다.](#enable-live-express-checkout) 확장을 활성화하려면

>[!NOTE]
>
> 볼트 계정(위의 2단계)을 구성하지 않으면 샌드박스 또는 프로덕션 환경을 설정할 수 없습니다.

## 전제 조건

를 사용하려면 [!DNL Express Checkout]를 채울 수 있는 볼트가 있어야 합니다.

- 지원되는 결제 공급자
- 볼트의 머천트 및 프로덕션 계정
- 볼트에서 생성된 API 및 게시 가능한 키

자세한 내용은 [전제 조건](../express-checkout/prerequisites.md) 주제 를 참조하십시오.

자세한 내용은 [API 자격 증명](#obtain-api-credentials) 인스턴스에 대한 API 키를 만들거나 액세스하는 방법을 배웁니다.

## 확장 가져오기

자세한 내용은 [설치](../express-checkout/install.md) 확장을 가져오는 방법에 대한 자세한 내용은 항목을 참조하십시오.

## 볼트로 계정 만들기

구성하기 전에 [!DNL Express Checkout] Adobe Commerce 관리자에서 다음을 만들어야 합니다. [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} 및 [샌드박스](https://merchant-sandbox.bolt.com/register)볼트의 {target=&quot;_blank&quot;} 머천트 계정입니다. 볼트에서 계정을 만드는 데 필요한 세부 정보를 모두 입력합니다.

자세한 내용은 [테스트 및 유효성 검사](../express-checkout/testing.md) 주제 를 참조하십시오.

## API 자격 증명 가져오기

를 사용하려면 [!DNL Express Checkout] 볼트 고유 키가 필요합니다. 로 이동하여 다음 API 키를 얻습니다. **개발자** > **API** > **키** 에서 **볼트 머천트 대시보드**.

- API 키: 백 엔드가 볼트 API와 상호 작용하는 데 사용하는 개인 키입니다.
- 게시 가능한 키: 프런트 엔드가 볼트 API와 상호 작용하는 데 사용하는 키입니다.

자세한 내용은 [볼트 환경 세부 사항](https://help.bolt.com/developers/references/environment-details/#about-keys){target=&quot;_blank&quot;} 페이지에 대한 API 및 게시 가능한 키에 대해 알아보기 [!DNL Express Checkout] 확장.

>[!CAUTION]
>
> 샌드박스 및 프로덕션 환경에 대한 API 키를 만들어야 합니다.

## 결제 공급자 구성

결제 서비스 공급자를 연결하려면 [프로세서 설정](https://help.bolt.com/integrations/adobe-express-checkout/set-up/){target=&quot;_blank&quot;} 개발자 볼트 페이지입니다.

## 확장 활성화

1. 설정 _관리_ 사이드바, 탐색 **스토어** > **구성** > **체크아웃** 을 눌러 체크아웃 관리 구성 페이지에 액세스합니다.

![빠른 체크아웃](../assets/admin-view.png)

1. 에서 [!DNL Express Checkout] 보기, 설정 **활성화** to `Yes`.
1. 사용할 방법(프로덕션 또는 샌드박스)을 선택하십시오.
1. 고유 API 및 게시 가능한 키를 제공한 후 자격 증명을 확인합니다.

>[!CAUTION]
>
> 확장을 활성화하기 전에 고유한 API 및 게시 가능 키를 제공해야 합니다. 그렇지 않으면 고객이 결제 양식을 볼 수 있고 주문을 할 수 없습니다.

## 관리 구성 완료

1. 설정 _관리_ 사이드바, 탐색 **스토어** > **구성** > **체크아웃** 를 눌러 일반 체크아웃 관리 구성 페이지에 액세스합니다.
1. 에서 _서비스 설정_ 섹션에서 확장을 활성화하는 데 필요한 모든 세부 사항을 제공합니다.
1. 설정 _결제 조치_ 로서의:

   - 권한 부여: 승인 시 트랜잭션을 자동으로 캡처하지 마십시오.
   - 인증 및 캡처: 승인 시 트랜잭션을 자동으로 캡처합니다.

Adobe Commerce 표준 체크아웃 옵션에 대한 자세한 내용은 [체크아웃](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 주제.

## Live Express 체크아웃 활성화

를 사용하려면 [!DNL Express Checkout] Adobe Commerce 확장:

1. 클릭 **구성 저장**.

## 지원 요청

온보딩 프로세스는 모든 것을 설정하고 구현하는 데 필요한 단계를 안내하도록 설계되었습니다 [!DNL Express Checkout] 기능을 사용할 수 있습니다. 도움이 필요한 경우 Adobe Commerce 지원 센터에 문의하십시오.

자세한 내용은 [테스트 및 유효성 검사](../express-checkout/testing.md) 주제 를 참조하십시오.
