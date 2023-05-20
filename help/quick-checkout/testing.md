---
title: "테스트 [!DNL Quick Checkout] for Adobe Commerce extension"
description: "테스트 및 유효성 검사를 통해 [!DNL Quick Checkout] 확장은 예상대로 작동합니다."
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# 테스트 [!DNL Quick Checkout] 확장

노출하기 전에 [!DNL Quick Checkout] 쇼핑객을 위한 Adobe Commerce 확장의 경우 샌드박스 환경 및 프로덕션 환경에서 테스트하는 것이 좋습니다. 테스트 및 유효성 검사는 다음을 수행하는 데 도움이 됩니다. [!DNL Quick Checkout] 는 예상대로 작동하며 상점 및 고객에게 원활한 체크아웃 경험을 제공합니다.

을(를) 구성하기 전에 [!DNL Quick Checkout] Adobe Commerce 관리에서 다음을 생성해야 합니다.  [production](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} 의 판매자 계정 [!DNL Bolt].

## 샌드박스에서 테스트

테스트 [!DNL Quick Checkout] 샌드박스 환경에서는 에만 연결되는 시뮬레이션된 환경이지만 매우 중요한 유효성 검사 단계입니다. [!DNL Bolt] 샌드박스 계정입니다. 실제 은행이나 가맹점은 해당되지 않습니다.

### 샌드박스 계정 사용

샌드박스를 테스트하고 유효성을 검사할 때 가짜 신용 카드 번호와 [샌드박스](https://merchant-sandbox.bolt.com/register){target="_blank"} 의 판매자 계정 [!DNL Bolt]기존 신용카드 계정에 실제 요금을 부과하지 않도록 할 수 있습니다.

## 프로덕션에서 테스트

>[!NOTE]
>
> 다음을 테스트하는 것이 좋습니다. [!DNL Quick Checkout] 실제 신용 카드와 은행이 있는 프로덕션 환경에서 확장을 쇼핑객에게 노출하기 전에. 샌드박스에서 테스트하는 것은 중요하지만 프로덕션에서 테스트하는 것은 예상대로 작동하는지 확인하기 위한 가장 어리석은 방법입니다.

다음 두 가지 권장 방법 중 하나로 프로덕션 환경을 테스트합니다.

- 구매자가 주문을 하지 않을 때를 선택합니다.
- 일시적으로 쇼핑객에게 액세스할 수 없지만 테스트를 위해 액세스할 수 있는 웹 스토어를 사용하십시오.

실제 신용 카드 및 [!DNL Bolt] 프로덕션 계정, 체크아웃 전체 라이프사이클 테스트. 테스트 중에 전체 체크아웃 플로우를 완료하면 라이브 쇼핑객이 기능을 사용할 때 기능이 어떻게 작동하는지 명확하게 파악할 수 있습니다.

또한 생산 테스트에 사용하는 결제 방법에 대한 은행 거래 명세서에 표시되는 정보가 정확하고 예상되는지 확인해야 합니다(비즈니스 설명 포함).

## 테스트 방법 [!DNL Quick Checkout] 확장

스토어에서 성공적으로 체크아웃을 완료합니다.

1. 상점으로 이동하여 원하는 항목을 장바구니에 담으십시오.
1. 체크아웃을 진행합니다.
1. 과(와) 연결된 이메일 주소를 입력하십시오. [!DNL Bolt] 메시지가 표시되면 계정을 만듭니다.
1. 계정의 이메일 주소로 전송되는 일회용 암호(OTP)를 입력합니다.
1. 환경 대시보드를 선택합니다.

   - 샌드박스
   - 프로덕션

1. 주문하십시오.

주문이 이루어지면 다음에서 주문 세부 사항을 볼 수 있습니다. _주문 그리드_ 보기:

1. 다음으로 이동 _판매_ > _주문 수_.
1. 모든 주문 목록을 참조하십시오.

다음을 참조하십시오. [주문 수](https://docs.magento.com/user-guide/sales/orders.html) 항목 을 참조하십시오. _주문 그리드_ 보기.
