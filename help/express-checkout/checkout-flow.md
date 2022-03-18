---
title: 체크아웃 흐름
description: 개요 [!DNL Express Checkout] Adobe Commerce의 흐름.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---

# [!DNL Express Checkout] 흐름

>[!IMPORTANT]
>
> 이 기능은 EAP(Early Adopter Program) 사용자만 사용할 수 있으며 모든 고객이 아직 액세스할 수 없습니다. 현재 미국 고객에게만 제공됩니다. 도움이 필요한 경우 Adobe Commerce 지원 센터에 문의하십시오.

이 섹션에서는 [!DNL Express Checkout] Adobe Commerce 확장

성공 [!DNL Express Checkout] 흐름은 다음 단계로 구성됩니다.

1. 스토어를 열고 장바구니에 항목을 추가합니다.
1. 체크아웃을 진행합니다.

![체크아웃](../assets/proceed-checkout.png)

1. 메시지가 표시되면 볼트 계정과 연결된 이메일 주소를 입력합니다.
1. 해당 볼트 계정의 전자 메일 주소나 전화 번호로 보낸 OTP(일회성 암호)를 입력합니다.
1. 볼트 계정으로 로그인하면 체크아웃 세부 사항이 자동으로 입력됩니다.

   - 배송 정보
   - 결제 방법

   >[!NOTE]
   >
   > 체크 아웃 세부 사항이 자동으로 입력되더라도 기존 전자 지갑 정보(주소 또는 신용 카드 정보)를 사용할 수 있습니다.

1. 주문.

다음 [!DNL Express Checkout] 는 다음과 같은 표준 추가 Adobe Commerce 체크아웃 옵션과 호환됩니다. [선물 카드](https://docs.magento.com/user-guide/catalog/product-gift-card.html) 또는 [할인 코드](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] 사용 사례

다음 [!DNL Express Checkout] 에서는 체크아웃 흐름 중에 여러 사용 사례를 사용할 수 있습니다.

- 등록된 볼트 계정이 있는 게스트 사용자.
- 새 볼트 계정이 있는 게스트 사용자.
- 등록된 볼트 계정이 있는/없는 기존 Adobe Commerce 사용자.

## 게스트 사용자 체크아웃: 작동 방법

게스트 체크아웃 경험은 로그인한 경험과 다릅니다. 쇼핑객이 체크아웃에 이메일 주소를 입력하면 [!DNL Express Checkout] 이를 확인하여 기존 볼트 계정을 찾습니다.

### 등록된 볼트 계정

볼트 계정이 발견되면 쇼핑객들은 계속 이 계정을 사용합니다 [!DNL Express Checkout] 원활한 체크아웃 경험:

1. 볼트(Bolt) 계정에서 사용자의 선호도에 따라 해당 볼트 계정의 이메일 주소나 모바일로 보낸 일회용 암호(OTP)를 입력합니다.
1. 볼트 계정으로 로그인하면 체크아웃 세부 사항이 자동으로 채워집니다.

   - 배송 정보
   - 결제 방법

1. 주문.

>[!TIP]
>
> 게스트 사용자는 순서를 지정하며 Adobe Commerce에 등록할 수 있습니다.

### 새 볼트 계정

볼트(Bolt) 계정이 없는 경우, 쇼핑객들은 기본 기본 제공 Adobe Commerce 체크아웃을 계속 진행하여 주문 시 필요한 모든 세부 정보를 제공합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토
- 순서를 지정하기 전에 더 빠른 체크아웃을 위해 볼트에 등록되는 확인란이 표시됩니다. 고객은 볼트(Bolt) 계정을 만들기 위해 사용 약관에 동의할 수 있습니다.

   ![볼트 기억](../assets/checked-bolt.png)

- 게스트 사용자는 순서를 지정하며 Adobe Commerce에 등록할 수 있습니다.

## 기존 Adobe Commerce 사용자: 작동 방법

기존 사용자는 사용자가 [!DNL Express Checkout] 를 참조하십시오.

쇼핑객이 체크아웃에 이메일 주소를 입력하면 [!DNL Express Checkout] 이를 확인하여 기존 볼트 계정을 찾습니다.

### Adobe Commerce 사용자가 등록된 볼트 계정

볼트 계정이 발견되면 구매자는 기본 기본 제공 Adobe Commerce 체크아웃을 계속 수행하고 구매자는 필요한 모든 세부 사항을 제공한 다음 순서를 지정합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토

자세한 내용은 [문제 해결](../express-checkout/troubleshooting.md) 기존 Adobe Commerce 사용자로 주문할 때 문제가 발생하는 경우 항목을 더 확인하십시오.

>[!NOTE]
>
> 사용자에게 볼트 계정이 있고 이메일이 Adobe Commerce에 등록된 것으로 표시되지 않으면 OTP(일회용 암호) 로그인을 트리거합니다. 자세한 내용은 [등록된 볼트 계정](#registered-bolt-account) 흐름.

### 새 볼트 계정

볼트 계정이 없으면 쇼핑객은 기본 Adobe Commerce 체크아웃을 계속 수행하고 구매자는 저장된 정보에서 필요한 모든 세부 정보를 선택하여 순서를 지정합니다.

- 배송 및 청구 정보
- 배송 방법
- 결제 방법 검토
- 순서를 지정하기 전에 더 빠른 체크아웃을 위해 볼트에 등록되는 확인란이 표시됩니다. 고객은 볼트(Bolt) 계정을 만들기 위해 사용 약관에 동의할 수 있습니다.

   ![볼트 기억](../assets/checked-bolt.png)

## 지원 요청

도움이 필요한 경우 Adobe Commerce 지원 센터에 문의하십시오.
