---
title: XDM 스키마에 필드 그룹 추가
description: XDM 스키마에 Adobe Commerce 관련 필드 그룹을 추가하는 방법을 알아봅니다.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: 90356cc593653cf4583da86bc29d69112fc948ba
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# XDM 스키마에 필드 그룹 추가

다음 중 하나 [온보딩 단계](overview.md#onboarding-steps) Experience Platform 커넥터를 사용하는 방법은 데이터 스트림 작업 공간에 액세스하고 [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) Adobe Commerce에만 해당됩니다. 해당 데이터 스트림을 만들 때 수집할 데이터를 나타내는 XDM 스키마도 선택해야 합니다. 이 항목에서는 Adobe Commerce storefront에서 제공한 데이터를 성공적으로 수집하기 위해 XDM 스키마에 포함해야 하는 필드 그룹을 제공합니다 [events](events.md).

1. XDM 스키마가 없는 경우 [만들기](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 하나 그렇지 않으면, [편집](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) Adobe Experience Platform UI에서 기존 XDM 스키마.

1. [추가](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 다음 상거래 특정 필드 그룹:

   - 사이트 검색
   - 웹 페이지 방문
   - 사용자 로그인 프로세스
   - 참조 키
   - 개인 연락처 세부 정보
   - 상거래 세부 사항
   - Adobe Analytics ExperienceEvent Commerce (Adobe Analytics에 데이터를 전송하려는 경우)
   - ID 맵

   >[!NOTE]
   >
   > 상거래 관련 필드 그룹을 `Primary identity`. 필드를 필수 필드로 식별하므로 Experience Platform은 모든 이벤트에 해당 필드를 예상합니다. 해당 필드가 없으면 데이터 수집이 실패합니다.

   이제 XDM 스키마에 Commerce Storefront에서 수집된 데이터가 상거래 관련 필드 그룹이 포함됩니다 [events](events.md) 는 XDM에서 표시됩니다.

1. [데이터 집합 만들기](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 만들거나 업데이트한 스키마를 기반으로 합니다.

   데이터 집합은 스키마(열) 및 필드(행)를 포함하는 데이터 수집을 위한 저장소 및 관리 구성입니다. 데이터 세트에는 저장하는 데이터의 다양한 측면을 설명하는 메타데이터도 포함되어 있습니다.

1. [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) 및 전자 상거래 관련 필드 그룹과 해당 데이터 세트를 포함하는 XDM 스키마를 선택합니다.

   데이터 스트림은 수집된 데이터를 데이터 세트에 전달합니다. 데이터는 선택한 스키마를 기반으로 하여 데이터 집합에 표시됩니다.
