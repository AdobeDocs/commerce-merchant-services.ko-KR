---
title: Inventory management 소스 전송
description: '"에 대한 주식 구성 [!DNL Store Fulfillment solution] Adobe Commerce Inventory management 사용. Store Fulfillment 솔루션에서 필요한 Store Pickup 기능을 사용하도록 구성된 출처에 할당할 수 있도록 새 재고를 설정하고 기본 재고로부터 재고를 이전합니다."'
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Inventory management 소스 전송

다음 [!DNL Store Fulfillment] 솔루션은 기본 Adobe Commerce Inventory management을 사용합니다. 기본적으로 [!DNL Commerce] 구성은 모든 웹 인벤토리를 기본 스톡에 할당하며, 추가 소스는 할당할 수 없습니다. 웹 사이트에는 단일 스톡 하나만 지정할 수 있으므로, 머천트는 새 스톡 구성 및 선택적으로 기본 소스 인벤토리를 적절한 범위에 지정된 출처로 전송해야 합니다. 그런 다음 소스를 새 주식에 지정할 수 있습니다.

이러한 구성 변경 사항은 다음 세 가지 사항을 수행하는 데 도움이 됩니다.

1. [출처로 재고 이전](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) 기본 재고/출처의 재고를 새 재고/출처로 이동하려면

1. [소스를 일괄 지정](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) 를 추가하여 모든 제품에 대한 새 소스를 추가합니다.

1. [제품 속성에 대한 전체 벌크 업데이트](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) 를 추가하려면 `Allow Store Pickup` 및 `Allow Home Delivery` 기존 제품에 대한 속성입니다. 솔루션이 설치되면 속성에 최적화가 사용됩니다 *기본* 값. 그러나 벌크 업데이트 프로세스를 완료할 때까지 이러한 속성은 기존 제품에 적용되지 않습니다.

선택한 출처(소매점 위치 또는 전자 상거래 창고)에서 재고가 공제됩니다. 전자 상거래 웨어하우스로 사용되는 소스는 상점 픽업 위치와 동일한 주식에 할당하고 소매 위치 이전에 우선 순위를 지정해야 합니다. 자세한 내용은 [스톡 소스 우선 순위 지정](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

인벤토리, 주식 및 소스 관리에 대한 자세한 내용은 Adobe Commerce 사용 설명서를 참조하십시오.

- [인벤토리 관리](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [재고 수량 관리](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [재고 관리](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [소스 관리](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [스톡 소스 우선 순위 지정](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [제품 속성에 대한 벌크 업데이트](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>재고 및 재고 소스에 대한 구성을 변경하면 통합 시스템에 다운스트림으로 영향을 줄 수도 있습니다. 재고 구성 변경 사항이 이러한 시스템에 미치는 영향을 이해하는지 확인합니다.
