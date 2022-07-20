---
title: 체크아웃 흐름
description: 개요 [!DNL Quick Checkout] Adobe Commerce 사용자의 흐름.
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# 기존 Adobe Commerce 사용자: 작동 방법

기존 Adobe Commerce 사용자는 [!DNL Quick Checkout] 를 참조하십시오.

쇼핑객이 체크아웃 시 이메일 주소를 입력하면 [!DNL Quick Checkout] 검증 후 기존 [!DNL Bolt] 계정이 필요합니다.

## Adobe Commerce 및 [!DNL Bolt]

쇼핑객이 Adobe Commerce 및 [!DNL Bolt] 네트워크, 두 네트워크 모두 저장된 배송 및 결제 세부 정보가 제공됩니다.

다음과 같은 경우 [!DNL Bolt] 체크아웃 중에 계정이 발견되면 구매자는 계속 작업할 수 있습니다 [!DNL Quick Checkout] 원활한 체크아웃 경험:

1. 보낸 OTP(일회용 암호)를 입력합니다 [!DNL Bolt] 계정에 따라 이메일 주소 또는 모바일 [사용자 환경 설정 [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![OTP 팝업](assets/pop-up.png)

1. 을 사용하여 로그인하면 [!DNL Bolt] account에 세부 정보가 자동으로 추가됩니다.

   - 배송 정보
   - 결제 방법

1. 주문하십시오.

>[!NOTE]
>
> Bolt OTP 팝업은 쇼핑객이 체크아웃 페이지에 있을 때만 나타납니다. 쇼핑객은 해당 팝업 창을 닫아서 Bolt에 로그인하는 것을 옵트아웃할 수 있습니다.

체크아웃하기 전에 쇼핑객이 Adobe Commerce에 로그인한 경우에는 [!DNL Bolt] 체크 아웃 중에는 OTP 팝업이 표시되지 않습니다.

기존 Adobe Commerce 사용자로 주문할 때 문제가 발생하는 경우 [빠른 체크아웃 문제 해결](https://support.magento.com/hc/en-us/articles/6909450342541) Adobe Commerce 도움말 센터의 문서.

## 새로 만들기 [!DNL Bolt] account

없는 경우 [!DNL Bolt] 계정이 발견되면 구매자는 기본 기본 제공 Adobe Commerce 체크아웃을 계속 수행하고 구매자는 저장된 정보에서 필요한 모든 세부 정보를 선택하여 주문을 수행합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토
- 등록할 옵션 [!DNL Bolt] 를 선택하면 주문이 나타납니다. 쇼핑객은 약관을 준수하여 고객을 만들 수 있습니다 [!DNL Bolt] 계정이 필요합니다.

   ![기억 [!DNL Bolt]](assets/checkbox-remember-bolt.png)
