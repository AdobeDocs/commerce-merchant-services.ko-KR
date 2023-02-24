---
title: 저장소 위치 및 매핑 시스템 구성
description: 상점 UI에서 저장소 위치 매핑을 지원하도록 거리 공급자를 구성합니다. Store Fulfillment 솔루션에서는 소매점 검색 및 종단간 이행 워크플로우에 대한 기타 매핑 및 스케줄링 기능을 사용하기 위해 거리 공급자가 필요합니다.
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 저장소 위치 및 매핑 설정

다음을 구성하여 Store Fulfillment에 대한 저장소 위치 및 매핑 기능을 활성화합니다 [거리 공급자](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) 를 입력하여 소매점 위치를 검색합니다.

**요구 사항**

구성 프로세스 중에 Google 맵 플랫폼에 대한 Google API 키를 제공합니다. 없는 경우 [Google 맵 플랫폼에서 하나를 생성합니다.](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

거리 공급자를 구성하려면 다음을 수행합니다.

1. 에서 **[!UICONTROL Stores > General]** 구성을 관리자에서, 맵 콘텐츠 유형에 대한 Google 맵 통합을 추가합니다.

   - 이동 **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - 에 Google API 키 추가 **[!UICONTROL Google Maps API Key]** 필드.

1. 에서 **[!UICONTROL Stores > Inventory]** 구성에서 Store Fulfillment의 거리 공급자를 선택합니다.

   - 이동 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - 를 확장합니다. **[!UICONTROL Distance Provider for Distance Based SSA]** 섹션을 참조하십시오.

   - 설정 **공급자** to **Google 맵**.

1. 에 대한 설정 구성 **[!UICONTROL Google Distance Provider]**.

   - 추가 **Google API 키**.

   - 설정 **[!UICONTROL Computation Mode]** to `Driving` 및 **[!UICONTROL Value]** to `Distance`
