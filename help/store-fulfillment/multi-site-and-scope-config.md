---
title: 여러 웹 사이트 및 범위 구성
description: 여러 웹 사이트 및 저장소 범위에 대한 주식 및 전달 방법을 구성합니다.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# 여러 웹 사이트 및 범위 구성

을(를) 설정할 수 있습니다 [범위](https://docs.magento.com/user-guide/configuration/scope.html) 여러 웹 사이트, 저장소 및 저장소 보기를 수용하는 몇 가지 요소의 경우:

- [재고 관리](https://docs.magento.com/user-guide/catalog/inventory-stock.html) 범위 단위

- 관리 [!DNL Delivery Methods] 범위 단위

웹 사이트나 스토어 범위에 스톡을 할당할 수 있습니다. 그런 다음 저장소 소스를 업데이트하여 사용 가능한 배달 방법(집 배달, 스토어 픽업)을 설정합니다.

구성을 성공적으로 업데이트한 후 저장소 업로드를 허용하는 스톡 소스에서 사용할 수 있는 제품에 대해서만 Adobe Commerce 스토어의 제품 세부 정보 페이지(PDP)에 있는 스토어 픽업옵션을 선택할 수 있습니다.

## 매장 내 픽업 설정 관리

을(를) 활성화 또는 비활성화합니다 [!UICONTROL In-Store Pickup] 각 웹 사이트 또는 저장소 범위에 대한 옵션 [배달 방법 구성](enable-general.md#delivery-methods) 관리자.

1. 다음으로 이동 **[!UICONTROL Stores > Configuration]**.

1. 구성할 범위(저장할 웹 사이트)를 선택합니다.

1. 범위를 선택한 상태에서 다음 위치로 이동합니다. **[!UICONTROL Sales > Delivery Methods]**.

1. 를 비활성화하거나 활성화합니다 **[!UICONTROL In-Store Pickup]** 배달 방법입니다.

또한 이 섹션에서 전체적으로 조정 또는 매장 내 픽업 기능을 사용할 수 있는지 여부를 관리할 수도 있습니다.

관리 [!UICONTROL In-Store Pickup] 및 [!UICONTROL Delivery Method] 스톡 소스당 설정. 구현에 비해 유연하기 위해 다른 다양한 구성이 있습니다.
