---
title: 저장 위치 및 매핑 시스템 구성
description: 상점 UI에서 저장소 위치 매핑을 지원하도록 거리 공급자를 구성합니다. 스토어 이행 솔루션은 소매 스토어 검색 및 전체 이행 워크플로우를 위한 기타 매핑 및 스케줄링 기능을 사용할 수 있도록 거리 공급 업체를 필요로 합니다.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# 저장소 위치 및 매핑 설정

다음을 구성하여 저장소 이행 기능용 저장소 위치 및 매핑 기능 활성화 [거리 제공자](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) 소매점 위치를 검색합니다.

**요구 사항**

구성 프로세스 중에 Google 맵 플랫폼에 Google API 키를 제공합니다. 없으시면, [Google 맵 플랫폼에서 하나를 생성합니다.](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

거리 공급자를 구성하려면:

1. 다음에서 **[!UICONTROL Stores > General]** 구성에서 맵 콘텐츠 유형에 대한 Google 맵 통합을 추가합니다.

   - 다음으로 이동 **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Google API 키 추가 **[!UICONTROL Google Maps API Key]** 필드.

1. 다음에서 **[!UICONTROL Stores > Inventory]** 구성에서 스토어 이행 거리 공급자를 선택합니다.

   - 다음으로 이동 **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - 확장 **[!UICONTROL Distance Provider for Distance Based SSA]** 섹션.

   - 설정 **공급자** 끝 **Google 맵**.

1. 다음에 대한 설정 구성 **[!UICONTROL Google Distance Provider]**.

   - 사용자 추가 **Google API 키**.

   - 설정 **[!UICONTROL Computation Mode]** 끝 `Driving` 및 **[!UICONTROL Value]** 끝 `Distance`
