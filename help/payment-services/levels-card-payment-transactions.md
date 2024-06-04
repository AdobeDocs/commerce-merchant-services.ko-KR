---
title: 레벨 2 및 레벨 3 처리
description: 다음 범위 내의 카드 결제 처리 수준 [!DNL Payment Services] 트랜잭션.
role: Admin
feature: Payments
source-git-commit: d1379bb108f2259051641a7bf77cd8b459fd9cbf
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# 레벨 2 및 레벨 3 처리

다음을 통해 사용할 수 있는 세 가지 수준의 카드 처리 [!DNL Payment Services]:

* 레벨 1이 가장 일반적이고, 필요한 정보가 적기 때문에 일반적으로 기업 및 구매 신용카드와 관련된 레벨 2 또는 레벨 3 데이터로 처리된 거래에 비해 높은 교환 수수료가 발생합니다.

* 레벨 2 및 레벨 3의 경우, [!DNL Payment Services] 구매 카드나 법인 카드 거래를 많이 수락하는 IC++(interchange plus) 가격 책정 고객은 다음을 허용하여 더 낮은 처리 속도를 받을 수 있습니다. [!DNL Payment Services] 트랜잭션에 대한 자세한 정보를 보냅니다. 거래가 유효하다면, 카드 네트워크 요건에 따라, 판매자는 특정 거래에 대해 더 낮은 처리율을 받을 수 있다.

>[!NOTE]
>
>레벨 2 및 레벨 3 가격은 비자 및 마스터 카드 거래에 대해서만 적용됩니다. American Express는 레벨 2 가격만 제공합니다. Discover는 레벨 2와 레벨 3 가격을 제공하지 않습니다. 다음을 참조하십시오 [결제 처리](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} 자세한 내용은 PayPal 개발자 설명서 를 참조하십시오.

다음을 참조하십시오 [IC란 무엇입니까++?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} 자세한 내용은 PayPal 개발자 설명서 를 참조하십시오.

레벨 2 및 레벨 3 처리 데이터를 사용하면 프로세서 위험을 줄이고 유용한 측면을 제공하는 구매에 대한 추가 세부 정보를 제공하는 경우 판매자가 IC++ 가격을 낮출 수 있습니다.

* 대규모 고객은 이 처리 데이터를 제공하여 비용을 줄일 수 있습니다.

* 주문 정보가 많을수록 고객이 사기 상황에 처할 가능성이 적다.

그러나 Visa 및 Mastercard와 같은 카드 네트워크는 최종적으로 트랜잭션이 레벨 2 또는 레벨 3 처리에 적합한지 여부를 결정합니다.

* 레벨 2 데이터에는 주문에 대한 세액이나 고객 코드 또는 PO 번호와 같은 추가 정보가 포함됩니다.

* 레벨 3 데이터는 판매에 대한 보다 자세한 정보이므로 레벨 2에 비해 훨씬 낮은 교환 비율에 대한 자격을 얻습니다. 레벨 3 데이터에는 구매 품목, 구매 단위 수량, 주문 품목에 대한 UOM 및 기타 특정 상세내역에 대한 설명과 같은 정보가 포함됩니다.

[!DNL Payment Services] 는 이 데이터를 수집하고 결제 거래에 대한 자세한 보고를 제공합니다.

## 의 레벨 2 및 레벨 3 카드 결제 거래 [!DNL Payment Services]

레벨 2 또는 레벨 3 처리의 자격을 얻으려면 상인은 이전 정보를 전송해야 하지만, 카드 네트워크가 거래를 처리할 때 최종적으로 어느 레벨에 자격이 있는지를 결정합니다.

다음을 참조하십시오. [결제 처리 FAQ](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} 자세한 내용은 PayPal 개발자 설명서 를 참조하십시오.

레벨 2 및 레벨 3 처리는 기본적으로 [!DNL Payment Services] 상점 수준의 상인.

이미 IC++ 가격을 사용하고 있다면 레벨 2 및 레벨 3 처리를 사용할 수 있습니다. 이 기능을 활성화하려면 다음을 통해 이 작업을 수행합니다. [명령줄 인터페이스(CLI)](configure-cli.md).

>[!IMPORTANT]
>
>질문이 있는 경우 다음으로 문의하십시오. [!DNL Payment Services] 계정 관리자.
