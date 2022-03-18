---
title: 환불
description: 환불 만들기 [!DNL Payment Services] 대변 메모 프로세스의 일부로 관리자에서 주문.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 환불

환불 [!DNL Payment Services] 주문은 대변 메모 프로세스의 일부로 관리에서 생성됩니다. 대변 메모는 고객에게 적용되거나 고객에게 직접 환급할 수 있는 전체 또는 일부 환불을 위해 고객에게 만기된 금액을 보여 주는 문서입니다. 대변 메모는 해당 주문에 대해서만 발행할 수 있습니다 [송장](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}.

자세한 내용은 [대변 메모](https://docs.magento.com/user-guide/sales/credit-memos.html)자세한 내용을 확인하고 신용 메모 발행 및 인쇄 방법을 알아보려면 핵심 사용 안내서의 {target=&quot;_blank&quot;} 를 참조하십시오.

PayPal 또는 신용 카드로 처리된 주문의 경우 다음 작업을 수행할 수 있습니다.

* 주문 전체 금액 환급
* 주문 부분 금액(또는 복수 부분 금액)을 환불
* 특정 주문 품목 값보다 작은 금액을 환불

자세한 내용은 [대변 메모 발행](https://docs.magento.com/user-guide/sales/credit-memo-create.html)자세한 내용은 핵심 사용 안내서의 {target=&quot;_blank&quot;} 를 참조하십시오.

>[!NOTE]
>
>나머지 주문 금액(원래 금액에서 기존 환불 총액을 뺀 금액)보다 많은 주문에 대해 일부 환불을 시도하거나 전체 주문 금액보다 큰 금액에 대해 환불을 발행하는 경우 PayPal 또는 신용 카드 처리 주문에 오류가 발생합니다.

다음 [!UICONTROL Payment Action] 에서 설정 [!UICONTROL Payment Settings] 구성 - 다음 중 하나 `Authorize` 또는 `Authorize and Capture`- 결정 [기본 환불 워크플로우](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow)주문에 대해 {target=&quot;_blank&quot;}.

자세한 내용은 [결제 작업 설정 섹션](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target=&quot;_blank&quot;}/ _대변 메모 발행_ 추가 정보.
