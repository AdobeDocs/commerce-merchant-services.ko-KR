---
title: '"테스트 [!DNL Quick Checkout] Adobe Commerce 확장 프로그램'
description: '"테스트 및 유효성 검사를 통해 [!DNL Quick Checkout] 확장은 예상대로 작동합니다."'
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# 테스트 [!DNL Quick Checkout] 확장

Adobe Analytics Mobile Apps 또는 Analytics Premium이 [!DNL Quick Checkout] Adobe Commerce 확장을 구매자에게 사용하려면 샌드박스 환경 및 프로덕션 환경에서 테스트하는 것이 좋습니다. 테스트 및 유효성 검사는 [!DNL Quick Checkout] 는 예상대로 작동하며 저장소 및 고객을 위한 매끄러운 체크아웃 환경을 제공합니다.

구성하기 전에 [!DNL Quick Checkout] Adobe Commerce 관리자에서 다음을 만들어야 합니다.  [production](https://merchant.bolt.com/register){target=&quot;_blank&quot;} 및 [샌드박스](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} 머천트 계정 [!DNL Bolt].

## 샌드박스에서 테스트

테스트 [!DNL Quick Checkout] 샌드박스 환경에서는 시뮬레이션된 환경이지만 매우 중요한 유효성 검사 단계입니다 [!DNL Bolt] 실제 은행이나 상인이 아닌 샌드박스 계정

### 샌드박스 계정 사용

샌드박스를 테스트하고 유효성을 확인할 때 가짜 신용 카드 번호와 [샌드박스](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} 머천트 계정 [!DNL Bolt]기존 신용 카드 계정에 실제 비용을 생성하지 않도록 하는 등

## 프로덕션 테스트

>[!NOTE]
>
> 을 테스트하는 것이 좋습니다 [!DNL Quick Checkout] 실제 신용카드와 은행이 있는 생산 환경에서 구매를 하는 사람들에게 이 확장을 노출하기 전. 샌드박스에서 테스트하는 것이 중요하긴 하지만, 프로덕션 테스트는 이것이 예상대로 작동하는지 입증하는 가장 어리석은 방법입니다.

다음 두 가지 권장 방법 중 하나로 프로덕션 환경을 테스트합니다.

- 쇼핑하는 사람이 주문을 하지 않을 때를 선택하세요.
- 일시적으로 구매자가 액세스할 수 없지만 테스트를 위해 액세스할 수 있는 웹 스토어를 사용합니다.

실제 신용 카드 및 [!DNL Bolt] 프로덕션 계정을 사용하여 체크아웃의 전체 라이프사이클을 테스트합니다. 테스트 중에 전체 체크아웃 플로우를 완료하면 라이브 구매자가 이 플러그인을 사용할 때 기능이 어떻게 작동하는지 명확하게 파악할 수 있습니다.

또한 생산 테스트에 사용하는 지급 방법에 대한 은행 명세서에 표시되는 정보가 올바르고 예상된(업무 내용 포함)인지 확인해야 합니다.

## 테스트 방법 [!DNL Quick Checkout] 확장

저장소에서 성공적으로 체크아웃을 완료합니다.

1. 스토어프런트로 이동하여 원하는 항목을 카트에 넣습니다.
2. 체크아웃을 진행합니다.
3. 와 연결된 이메일 주소를 입력합니다 [!DNL Bolt] 메시지가 표시되면 계정이 제대로 작동하지 않습니다.
4. 계정의 전자 메일 주소로 전송된 일회성 암호(OTP)를 입력합니다.
5. 환경 대시보드를 선택합니다.

   - 샌드박스
   - 프로덕션

6. 주문하세요.

주문이 제출되면, _주문 그리드_ 보기:

1. 다음으로 이동 _영업_ > _주문_.
1. 모든 주문 목록을 참조하십시오.

자세한 내용은 [주문](https://docs.magento.com/user-guide/sales/orders.html) 항목 을 참조하십시오 _주문 그리드_ 보기.
