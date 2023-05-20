---
title: 여러 웹 사이트 및 범위 구성
description: 여러 웹 사이트 및 스토어 범위에 대한 재고 및 게재 방법을 구성합니다.
role: User, Admin
level: Intermediate
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 여러 웹 사이트 및 범위 구성

다음을 설정할 수 있습니다. [범위](https://docs.magento.com/user-guide/configuration/scope.html) 여러 웹 사이트, 스토어 및 스토어 보기를 수용할 수 있는 몇 가지 요소의 경우:

- [재고 관리](https://docs.magento.com/user-guide/catalog/inventory-stock.html) 범위당

- 관리 [!DNL Delivery Methods] 범위당

웹 사이트 또는 스토어 범위에 재고를 할당할 수 있습니다. 그런 다음 저장소 소스를 업데이트하여 사용 가능한 게재 방법(홈 게재, 저장소 픽업)을 설정합니다.

구성을 정상적으로 업데이트하면 Adobe Commerce 상점 첫 화면의 PDP(제품 세부 사항 페이지)에 있는 상점 픽업 옵션은 상점 선택을 허용하는 재고 소스에서 사용 가능한 제품에 대해서만 선택할 수 있습니다.

## 매장 내 픽업 설정 관리

활성화 또는 비활성화 [!UICONTROL In-Store Pickup] 에서 각 웹 사이트 또는 스토어 범위에 대한 옵션 [게재 방법 구성](enable-general.md#delivery-methods) 관리에서.

1. 다음으로 이동 **[!UICONTROL Stores > Configuration]**.

1. 구성할 범위(저장할 웹 사이트)를 선택합니다.

1. 범위를 선택한 상태에서 다음으로 이동 **[!UICONTROL Sales > Delivery Methods]**.

1. 비활성화 또는 활성화 **[!UICONTROL In-Store Pickup]** 게재 방법.

또한 이 섹션에서 전체적으로 커브사이드 또는 매장 내 픽업을 사용할 수 있는지 여부를 관리할 수도 있습니다.

관리 [!UICONTROL In-Store Pickup] 및 [!UICONTROL Delivery Method] 스톡 소스당 설정. 구현에 비해 완벽한 유연성을 제공하기 위해 다양한 다른 구성이 존재합니다.
