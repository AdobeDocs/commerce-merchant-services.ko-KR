---
title: Voids
description: 사용자는 구매 금액의 인가에 의해 차단되거나 보류된 신용 또는 직불 카드 계정의 자금을 인출할 수 있습니다.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Voids

사용 [!DNL Payment Services]기존 상거래 기능을 사용하여 거래를 무효화할 수 있습니다. 사용자는 구매 금액의 인가에 의해 차단되거나 보류된 신용 또는 직불 카드 계정의 자금을 인출할 수 있습니다.

>[!NOTE]
>
>지급이 아직 캡처되지 않은 경우에만 거래를 무효화할 수 있습니다.

스토어가 [구성](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions)판매 시점에 (캡처되지 않음) 자금만 승인하도록 하기 위해 {target=&quot;_blank&quot;}, 저장소에서 구매하면 `Processing` Magento 관리자의 상태입니다.

다음을 수행할 수도 있습니다 [주문 취소](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order)송장이 발행되지 않은 {target=&quot;_blank&quot;}. 캡처되지 않은 권한 부여도 취소 프로세스의 일부로 취소됩니다.

>[!NOTE]
>
>주문을 취소하면 무효가 되지만 주문을 취소하면 취소가 트리거되지 않습니다.

주문이 수행하는 기본 단계에 대한 자세한 내용은 [주문 워크플로우](https://docs.magento.com/user-guide/sales/order-workflow.html)핵심 사용 안내서의 {target=&quot;_blank&quot;} 주제입니다.

void 기능 및 주문 거래를 무효화하는 방법에 대해 알아보려면 [주문 처리](https://docs.magento.com/user-guide/sales/order-processing.html)핵심 사용 안내서의 {target=&quot;_blank&quot;}.
