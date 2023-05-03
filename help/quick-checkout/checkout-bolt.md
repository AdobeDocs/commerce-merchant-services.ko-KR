---
title: "Adobe Commerce에서 볼트 사용자의 체크아웃 흐름"
description: 개요 [!DNL Quick Checkout] Adobe Commerce에서 볼트 사용자에 대한 흐름.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# 게스트 사용자

게스트 체크아웃 경험은 Adobe 사용자 경험과 다릅니다. 쇼핑객이 체크아웃에 이메일 주소를 입력하면 [!DNL Quick Checkout] 검증 후 기존 [!DNL Bolt] 계정이 필요합니다.

>[!WARNING]
>
> 다음 [!DNL In-Store Pickup] (ISPU) 기능은 [!DNL Quick Checkout] 이 활성화되어 있습니다.

## 등록 [!DNL Bolt] account

다음과 같은 경우 [!DNL Bolt] 계정이 발견되면 구매자는 계속해서 [!DNL Quick Checkout] 원활한 체크아웃 경험:

1. 보낸 OTP(일회용 암호)를 입력합니다 [!DNL Bolt] 계정에 따라 이메일 주소 또는 모바일 [사용자 환경 설정 [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP 팝업](assets/new-logo-otp-email.png)

1. 을 사용하여 로그인하면 [!DNL Bolt] account에 세부 정보가 자동으로 추가됩니다.

   - 배송 정보
   - 결제 방법

1. 주문하십시오.

>[!TIP]
>
> 게스트 사용자가 주문을 배치하여 Adobe Commerce에 선택적으로 등록할 수 있습니다.

## 새로 만들기 [!DNL Bolt] account

없는 경우 [!DNL Bolt] 계정이 발견되면 구매자는 기본 기본 제공 Adobe Commerce 체크아웃을 계속 수행하고 구매자는 주문 처리에 필요한 모든 세부 정보를 제공합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토
- 로그인하는 확인란이 표시됩니다 [!DNL Bolt] 주문하기 전에 더 빠른 체크아웃 쇼핑객은 약관을 준수하여 고객을 만들 수 있습니다 [!DNL Bolt] 계정이 필요합니다.
- 게스트 사용자가 주문을 배치하여 Adobe Commerce에 선택적으로 등록할 수 있습니다.
