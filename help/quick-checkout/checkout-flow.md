---
title: '"체크아웃 흐름"'
description: '"개요 [!DNL Quick Checkout] Adobe Commerce의 흐름"'
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# [!DNL Quick Checkout] 흐름

이 섹션에서는 [!DNL Quick Checkout] Adobe Commerce 확장

성공 [!DNL Quick Checkout] 흐름은 다음 단계로 구성됩니다.

1. 스토어를 열고 장바구니에 항목을 추가합니다.
1. 체크아웃을 진행합니다.

![체크아웃](assets/proceed-checkout.png)

1. 메시지가 표시되면 연결된 이메일 주소를 입력합니다 [!DNL Bolt] 계정이 필요합니다.
1. 보낸 OTP(일회용 암호)를 입력합니다 [!DNL Bolt] 계정의 이메일 주소 또는 전화 번호입니다.
1. 을 사용하여 로그인하면 [!DNL Bolt] 계정, 체크아웃 세부 사항이 자동으로 입력됩니다.

   - 배송 정보
   - 결제 방법

   >[!NOTE]
   >
   > 체크 아웃 세부 사항이 자동으로 입력되더라도 기존 전자 지갑 정보(주소 또는 신용 카드 정보)를 사용할 수 있습니다.

1. 주문.

다음 [!DNL Quick Checkout] 는 다음과 같은 표준 추가 Adobe Commerce 체크아웃 옵션과 호환됩니다. [선물 카드](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 또는 [할인 코드](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] 사용 사례

다음 [!DNL Quick Checkout] 에서는 체크아웃 흐름 중에 여러 사용 사례를 사용할 수 있습니다.

- 등록된 게스트 사용자 [!DNL Bolt] 계정이 필요합니다.
- 새 기능이 있는 게스트 사용자 [!DNL Bolt] 계정이 필요합니다.
- 등록된 사용자/없는 기존 Adobe Commerce 사용자 [!DNL Bolt] 계정이 필요합니다.

## 게스트 사용자 체크아웃: 작동 방법

게스트 체크아웃 경험은 로그인한 경험과 다릅니다. 쇼핑객이 체크아웃에 이메일 주소를 입력하면 [!DNL Quick Checkout] 유효성을 검사하여 기존 [!DNL Bolt] 계정이 필요합니다.

### 등록 [!DNL Bolt] account

다음과 같은 경우 [!DNL Bolt] 계정이 발견되면 구매자는 계속해서 [!DNL Quick Checkout] 원활한 체크아웃 경험:

1. 보낸 OTP(일회용 암호)를 입력합니다 [!DNL Bolt] 계정의 이메일 주소 또는 모바일 [!DNL Bolt] 계정이 필요합니다.
1. 을 사용하여 로그인하면 [!DNL Bolt] 계정을 사용하면 자동으로 체크아웃 세부 사항을 채웁니다.

   - 배송 정보
   - 결제 방법

1. 주문.

>[!TIP]
>
> 게스트 사용자는 순서를 지정하며 Adobe Commerce에 등록할 수 있습니다.

### 새로 만들기 [!DNL Bolt] account

없는 경우 [!DNL Bolt] 계정이 발견되면 구매자는 기본 기본 Adobe Commerce 체크아웃을 계속 수행하고 구매자는 주문 처리에 필요한 모든 세부 정보를 제공합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토
- 로그인하는 확인란이 표시됩니다 [!DNL Bolt] 주문하기 전에 더 빠른 체크아웃 이러한 사용자는 이용 약관에 동의하여 사용 약관을 만들 수 있습니다 [!DNL Bolt] 계정이 필요합니다.

   ![기억 [!DNL Bolt]](assets/checked-bolt.png)

- 게스트 사용자는 순서를 지정하며 Adobe Commerce에 등록할 수 있습니다.

## 기존 Adobe Commerce 사용자: 작동 방법

기존 사용자는 사용자가 [!DNL Quick Checkout] 를 참조하십시오.

쇼핑객이 체크아웃에 이메일 주소를 입력하면 [!DNL Quick Checkout] 유효성을 검사하여 기존 [!DNL Bolt] 계정이 필요합니다.

### 등록 [!DNL Bolt] Adobe Commerce 사용자가 있는 계정

다음과 같은 경우 [!DNL Bolt] 계정이 발견되면 구매자는 기본 기본 제공 Adobe Commerce 체크아웃을 계속 수행하고 구매자는 필요한 모든 세부 사항을 제공하고 다음 주문을 배치합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토

자세한 내용은 [문제 해결](../quick-checkout/troubleshooting.md) 기존 Adobe Commerce 사용자로 주문할 때 문제가 발생하는 경우 항목을 더 확인하십시오.

>[!NOTE]
>
> 사용자에게 [!DNL Bolt] 계정 및 이메일이 Adobe Commerce에 등록된 것으로 표시되지 않으므로 OTP(일회성 암호) 로그인을 트리거합니다. 자세한 내용은 [등록 [!DNL Bolt] account](#registered-bolt-account) 흐름.

### 새로 만들기 [!DNL Bolt] account

없는 경우 [!DNL Bolt] 계정이 발견되면 구매자는 기본 Adobe Commerce 체크아웃을 계속 수행하고 구매자는 저장된 정보에서 필요한 모든 세부 정보를 선택하여 주문을 수행합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토
- 로그인하는 확인란이 표시됩니다 [!DNL Bolt] 주문하기 전에 더 빠른 체크아웃 이러한 사용자는 이용 약관에 동의하여 사용 약관을 만들 수 있습니다 [!DNL Bolt] 계정이 필요합니다.

   ![기억 [!DNL Bolt]](assets/checked-bolt.png)

## 지원 요청

연락처 [Adobe Commerce 지원](mailto:quick-checkout-support@adobe.com) 도움이 필요하십니까?
