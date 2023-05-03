---
title: "Adobe Commerce의 체크아웃 흐름"
description: "개요 [!DNL Quick Checkout] Adobe Commerce의 흐름"
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] 흐름

이 섹션에서는 [!DNL Quick Checkout] Adobe Commerce 확장

성공 [!DNL Quick Checkout] 흐름은 다음 단계로 구성됩니다.

1. 스토어를 열고 장바구니에 항목을 추가합니다.
1. 체크아웃을 진행합니다.

![체크아웃](assets/proceed-checkout.png)

>[!NOTE]
>
> 상인에 대해 자동 로그인을 활성화할 수 있습니다. 자세한 내용은 [볼트의 자동 로그인 활성화 항목](https://help.bolt.com/products/embedded/direct-api/auto-login/) 추가 정보.

1. 메시지가 표시되면 연결된 이메일 주소를 입력합니다 [!DNL Bolt] 계정이 필요합니다.
1. 보낸 OTP(일회용 암호)를 입력합니다 [!DNL Bolt] 계정의 이메일 주소 또는 전화 번호입니다.

![OTP 팝업](assets/new-logo-otp-email.png)

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

- [게스트 사용자](../quick-checkout/checkout-bolt.md) 등록 또는 신규 [!DNL Bolt] 계정이 필요합니다.
- 기존 [Adobe Commerce 사용자](../quick-checkout/checkout-adobe-commerce.md) 등록 여부에 상관없이 [!DNL Bolt] 계정이 필요합니다.

## 지원 요청

다음을 통해 Adobe Commerce 지원 센터에 문의하십시오 [Adobe Commerce 도움말 센터](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) 도움이 필요하십니까?
