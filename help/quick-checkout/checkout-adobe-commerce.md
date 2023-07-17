---
title: "Adobe Commerce 사용자에 대한 체크아웃 흐름"
description: "개요 [!DNL Quick Checkout] Adobe Commerce 사용자용 흐름입니다."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 기존 Adobe Commerce 사용자: 작동 방식

기존 Adobe Commerce 사용자는 주문 시 저장된 배송 및 결제 세부 사항을 선택할 수 있습니다. [!DNL Quick Checkout] 더 빠른 체크아웃 경험을 위해.

구매자가 체크아웃 시 이메일 주소를 입력하면 [!DNL Quick Checkout] 유효성을 검사하고 기존 을(를) 찾습니다 [!DNL Bolt] 계정입니다.

## Adobe Commerce 및 의 등록된 사용자 [!DNL Bolt]

쇼핑객이 Adobe Commerce 및 모두에서 등록된 사용자인 경우 [!DNL Bolt] 네트워크, 두 네트워크 모두 저장된 배송 및 결제 세부 정보가 제공됩니다.

다음과 같은 경우 [!DNL Bolt] 체크아웃하는 동안 계정이 검색되며, 쇼핑객은 계속 [!DNL Quick Checkout] 원활한 체크아웃 환경:

1. 전송된 OTP(일회용 암호)를 입력하십시오. [!DNL Bolt] 다음에 따라 계정의 이메일 주소 또는 모바일 [에서 사용자 환경 설정 [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP 팝업](assets/new-logo-otp-email.png)

1. (으)로 로그인한 후 [!DNL Bolt] 계정, 세부 사항이 자동으로 추가됩니다.

   - 배송 정보
   - 결제 방법

1. 주문하십시오.

>[!NOTE]
>
> Bolt OTP 팝업은 구매자가 체크아웃 페이지에 있을 때만 나타납니다. 쇼핑객은 그 팝업 창을 닫음으로써 볼트에 로그인하는 것을 거부할 수 있습니다.

구매자가 체크아웃 전에 Adobe Commerce에 로그인한 경우 [!DNL Bolt] 체크아웃 중에는 OTP 팝업이 나타나지 않지만, 구매자가 볼트 지갑에 액세스하기 위해 로그인해야 한다는 메시지가 나타납니다.

기존 Adobe Commerce 사용자로 주문할 때 문제가 발생하는 경우 다음을 참조하십시오. [빠른 체크아웃 문제 해결](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Adobe Commerce 도움말 센터의 문서입니다.

## 자동 로그인

자동 로그인 구성 요소는 구매자가 활성 Bolt 세션을 가지고 있는 시기를 감지하고 구매자를 자동으로 로그인시킵니다. 쇼핑객이 이전 세션에서 계정 검색 및 OTP(일회성 암호) 단계를 완료했으므로 건너뜁니다.

에 대해 자동 로그인을 구성할 수 있습니다. [!DNL Quick Checkout] 사용자. 체크 아웃 중에 사용자가 자동으로 로그인하도록 구성할 수 있습니다.

1. 다음에서 _관리자_ 사이드바, 다음 위치로 이동 **스토어** > **구성** > **체크아웃** 일반 체크 아웃 관리자 구성 페이지에 액세스합니다.
1. 다음에서 _서비스 설정_ 섹션 [!DNL Quick Checkout], 자동 로그인을 설정하는 데 필요한 모든 세부 정보를 제공합니다.

다음을 참조하십시오 [[!DNL Quick Checkout] 서비스 설정 구성](../quick-checkout/onboarding.md#configure-service-settings) 항목 을 참조하십시오.

>[!NOTE]
>
> 다음과 같은 경우 처음 로그인 **자동 로그인** 이 활성화되려면 팝업 창을 수락하여 권한을 부여하는 데 사용자의 동의가 필요합니다.

## 신규 [!DNL Bolt] account

없는 경우 [!DNL Bolt] 계정이 검색되면 구매자는 기본 Adobe Commerce 체크아웃을 계속 진행하며 구매자는 저장된 정보에서 필요한 모든 세부 정보를 선택하여 주문합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토
- 에 등록하는 옵션 [!DNL Bolt] 주문 전에 더 빠른 체크아웃 기능이 표시됩니다. 구매자는 구매자를 만들기 위한 약관에 동의할 수 있습니다. [!DNL Bolt] 계정입니다.

  ![기억 [!DNL Bolt]](assets/checkbox-remember-bolt.png)
