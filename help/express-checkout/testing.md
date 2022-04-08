---
title: 테스트 [!DNL Express Checkout] Adobe Commerce 확장 프로그램
description: 테스트 및 유효성 검사 를 통해 [!DNL Express Checkout] 확장은 예상대로 작동합니다.
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 테스트 [!DNL Express Checkout] Adobe Commerce 확장 프로그램

>[!IMPORTANT]
>
> 이 기능은 EAP(Early Adopter Program) 사용자만 사용할 수 있으며 모든 고객이 아직 액세스할 수 없습니다. 현재 미국 고객에게만 제공됩니다. 도움이 필요한 경우 Adobe Commerce 지원 센터에 문의하십시오.

Adobe Analytics Mobile Apps 또는 Analytics Premium이 [!DNL Express Checkout] Adobe Commerce 확장을 구매자에게 사용하려면 샌드박스 환경 및 프로덕션 환경에서 테스트하는 것이 좋습니다. 테스트 및 유효성 검사는 [!DNL Express Checkout] 는 예상대로 작동하며 저장소 및 고객을 위한 매끄러운 체크아웃 환경을 제공합니다.

구성하기 전에 [!DNL Express Checkout] Adobe Commerce 관리자에서 다음을 만들어야 합니다. [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} 및 [샌드박스](https://merchant-sandbox.bolt.com/register)볼트의 {target=&quot;_blank&quot;} 머천트 계정입니다.

## 샌드박스에서 테스트

테스트 [!DNL Express Checkout] 샌드박스 환경에서는 실제 은행이나 상인이 아닌 Bolt 샌드박스 계정에만 연결된 시뮬레이션 환경이지만 매우 중요한 유효성 검사 단계입니다.

### 샌드박스 계정 사용

샌드박스를 테스트하고 유효성을 확인할 때 가짜 신용 카드 번호와 [샌드박스](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} 머천트 계정 [!DNL Bolt]기존 신용 카드 계정에 실제 비용을 생성하지 않도록 하는 등

## 프로덕션 테스트

>[!NOTE]
>
> 을 테스트하는 것이 좋습니다 [!DNL Express Checkout] 실제 신용카드와 은행이 있는 생산 환경에서 구매를 하는 사람들에게 이 확장을 노출하기 전. 샌드박스에서 테스트하는 것이 중요하긴 하지만, 프로덕션 테스트는 이것이 예상대로 작동하는지 입증하는 가장 어리석은 방법입니다.

다음 두 가지 방법 중 하나로 프로덕션에서 테스트하는 것이 좋습니다.

- 쇼핑하는 사람이 주문을 하지 않을 때를 선택하세요.
- 일시적으로 구매자가 액세스할 수 없지만 테스트를 위해 액세스할 수 있는 웹 스토어를 사용합니다.

실제 신용 카드와 볼트 프로덕션 계정으로 프로덕션 테스트를 완료하고 체크아웃의 전체 라이프사이클을 테스트합니다. 테스트 중에 전체 체크아웃 플로우를 완료하면 라이브 쇼핑객이 이 플러그인을 사용할 때 기능이 어떻게 작동하는지 명확하게 파악할 수 있습니다.

또한 생산 테스트에 사용하는 지급 방법에 대한 은행 명세서에 표시되는 정보가 올바르고 예상된(업무 내용 포함)인지 확인해야 합니다.

## 테스트 방법 [!DNL Express Checkout] 확장

다음 단계에 따라 저장소에서 성공적으로 체크아웃을 완료합니다.

1. 스토어프런트로 이동하여 원하는 항목을 카트에 넣습니다.
1. 체크아웃을 진행합니다.
1. 와 연결된 이메일 주소를 입력합니다 [!DNL Bolt] 메시지가 표시되면 계정이 설정됩니다.
1. 계정의 전자 메일 주소로 보낸 OTP(일회성 암호)를 입력합니다.
1. 환경 대시보드를 선택합니다.

   - 샌드박스
   - 프로덕션

1. 주문.

주문이 제출되면, _주문 그리드_ 보기:

1. 다음으로 이동 _영업_ > _주문_.
1. 모든 주문 목록을 참조하십시오.

자세한 내용은 [주문](https://docs.magento.com/user-guide/sales/orders.html) 항목 을 참조하십시오 _주문 그리드_ 보기.
