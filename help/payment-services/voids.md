---
title: 빈 공간
description: Void를 사용하면 구매 금액에 대한 승인이 차단되거나 보류된 신용 카드 또는 직불 카드 계정의 자금을 확보할 수 있습니다.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# 빈 공간

포함 [!DNL Payment Services], 거래 무효화에 기존 상거래 기능을 사용할 수 있습니다. Void를 사용하면 구매 금액에 대한 승인이 차단되거나 보류된 신용 카드 또는 직불 카드 계정의 자금을 확보할 수 있습니다.

>[!NOTE]
>
>지급이 아직 수집되지 않은 경우에만 거래를 무효화할 수 있습니다.

스토어가 [구성됨](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} 판매 시점에서 자금만 승인(캡처하지 않음)하려면 스토어에서 구매하면 `Processing` 상거래 관리자의 상태입니다.

다음을 수행할 수도 있습니다. [주문 취소](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} 송장이 발행되지 않았습니다. 해당 취소 프로세스의 일부로 캡처되지 않은 승인도 무효화됩니다.

>[!NOTE]
>
>주문을 취소하면 공백도 생성되지만, 주문을 취소하면 취소가 트리거되지 않습니다.

주문이 거치는 기본 단계에 대한 자세한 내용은 [주문 워크플로우](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} 핵심 사용 안내서의 항목입니다.

무효 기능과 주문 거래를 무효화하는 방법에 대해 알려면 다음을 참조하십시오. [주문 처리](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} ( 핵심 사용 안내서)를 참조하십시오.
