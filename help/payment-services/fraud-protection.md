---
title: 상당한 사기 방지
description: 자동화된 사기 행위 보호 활성화 [!DNL Payment Services] with Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
source-git-commit: 400d1f8a384fceebcd13e9496f8e218e694d2752
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---


# 상당한 사기 방지

다음에 대해 자동화된 사기 행위 보호를 활성화할 수 있습니다. [!DNL Payment Services] (으)로 [Signifyd 확장](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

Adobe Commerce은 Signifyd 버전 5.4.0 이상을 지원합니다. [!DNL Payment Services] 는 사전 인증 및 사후 인증 Signifyd 흐름을 지원합니다.

다음을 참조하십시오 [Signifyd 설명서](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) 확장 설치 및 구성에 대해 알아봅니다.

## 통합 제한 사항

현재 Signifyd와 의 통합에는 다음과 같은 제한이 적용됩니다 [!DNL Payment Services]:

* The Signifyd/[!DNL Payment Services] 통합은 [신용 카드 필드](../payment-services/payments-options.md#credit-card-fields) (PayPal 결제 단추 또는 Apple Pay는 아님). [!DNL Payment Services] payPal 결제 버튼 및 Apple Pay를 통해 받은 주문 데이터를 Signifyd로 전송하지만 통합은 신용 카드 필드를 통해 주문된 주문에 대한 세부 정보만 제공합니다.
* Signifyd는 쇼핑객에 대한 상인이 관리자에 주문한 주문을 지원하지 않습니다.
* Signifyd는 다음으로 주문된 주문을 지원하지 않습니다. [저장된 신용 카드](../payment-services/vaulting.md).

## 온보딩

에서 사용할 수 있도록 확장을 온보딩하려면 Signifyd와 직접 통신해야 합니다. [!DNL Payment Services]- 없음 [!DNL Payment Services] 구성이 필요합니다. 설치 후 관리자에서 Signifyd 확장을 구성할 수 있습니다. 이 확장과 관련된 모든 지원은 Signifyd에서 관리합니다.

Signifyd로 온보딩할 때 다음을 수행해야 합니다.

1. 새 계정을 설정하려면 Signifyd에 문의하십시오.
1. 기본적으로 Signifyd는 [허용 목록에추가된](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) Signifyd가 다른 결제 옵션에 대해 트리거되지 않도록 하기 위해 현재 지원되지 않습니다. 특정 지불 방법을 금지하려면 변경해야 합니다.
1. Paypal이 Paypal에서 승인할 수 있는 상인의 사기 방지 설정을 통해 Signifyd에 의해 주문을 거부하지 않을 것인지 확인하십시오.
1. Signifyd 확장이 호환되도록 활성화 [!DNL Payment Services]:
   * 사용 시 [!DNL Payment Services] 위치: _라이브_ 모드, Signifyd는 프로덕션 모드에 있어야 합니다.
   * 사용 시 [!DNL Payment Services] 위치: _샌드박스_ 모드, Signifyd는 테스트 모드여야 합니다.

## 구성

Signifyd는 주문에 대해 일부 조치를 취하므로 다음에 대해 설정한 결제 조치를 기반으로 적절히 동작하도록 확장을 구성해야 합니다 [!DNL Payment Services].

이러한 구성 옵션은 결제 서비스 및 Signifyd 통합과 호환되지 않습니다.

* 날짜 [!DNL Payment Services] 이(가) 다음으로 구성됩니다. `Authorize` 지불 조치 _및_ Signifyd이(가) 있습니다. `PostAuth` 를 사용하는 모드 _[!UICONTROL Decline Guarantees]_옵션이 로 설정됨&#x200B;**대변 메모 만들기**.

  이유: [!DNL Payment Services] 는 Signify가 환불을 시도하는 인증 거래를 생성합니다.


* [!DNL Payment Services] 이(가) 다음으로 구성됩니다. `Authorize and Capture` 지불 조치 _및_ Signifyd이(가) 있습니다. `PostAuth` 를 사용하는 모드 _[!UICONTROL Decline Guarantees]_옵션이 로 설정됨&#x200B;**주문 취소**.

  이유: [!DNL Payment Services] 는 Signifyd가 무효화하려고 시도하는 캡처 트랜잭션을 생성합니다.


자세한 내용은 Signifyd 설명서 를 참조하십시오 [확장 구성](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

다음으로 보내려면 Signifyd 설명서 를 참조하십시오. [주문 워크플로우에 대해 자세히 알아보기](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
