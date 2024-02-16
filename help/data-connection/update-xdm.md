---
title: 상거래 데이터 수집을 위한 시계열 이벤트 스키마 업데이트
description: 스키마, 데이터 세트 및 데이터스트림을 만들어 상거래 데이터 수집을 위한 시계열 이벤트 데이터를 수집하고 전송하는 방법에 대해 알아봅니다.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# 상거래 데이터 수집을 위한 시계열 이벤트 스키마 업데이트

다음 중 하나 [온보딩 단계](overview.md#onboarding-steps) 사용 [!DNL Data Connection] 확장은 데이터 스트림 작업 영역에 액세스하고 [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) Adobe Commerce 전용입니다. 해당 데이터 스트림을 생성할 때 수집하려는 데이터를 설명하는 스키마도 선택해야 합니다. 해당 스키마에는 상업용 필드 그룹이 포함되어야 합니다.

이 문서에서는 Adobe Commerce 이벤트에서 제공한 다음 시계열 데이터를 성공적으로 수집하기 위해 스키마에 포함해야 하는 필드 그룹을 제공합니다.

- [동작](events.md) - 상점, 프로필, 검색 및 B2B 이벤트가 포함됩니다.
- [백오피스](events-backoffice.md) - 주문 상태 및 프로필 이벤트가 포함됩니다.

자세히 알아보기 [시계열 데이터](data-ingestion.md).

에 대해 자세히 알아보기 [스키마 컴포지션 기본 사항](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## 시계열 행동 및 백 오피스 이벤트 데이터로 스키마 업데이트

이 섹션에서는 기존 스키마를 업데이트하거나 행동 및 백 오피스 이벤트 데이터를 포함하는 스키마를 만드는 방법을 알아봅니다.

>[!NOTE]
>
>다음을 참조하십시오 [시계열 프로필 이벤트 데이터](#time-series-profile-event-data) 프로필별 필드를 추가하는 방법을 알아봅니다.

1. 스키마가 없는 경우 [만들기](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) (이)가 (으)로 설정된 클래스 **경험 이벤트**.

1. [추가](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 다음 상거래 관련 필드 그룹(또는 기존 스키마를 편집하고 이러한 필드 그룹 추가):

   - 사이트 검색
   - 웹 페이지 방문
   - 사용자 로그인 프로세스
   - 참조 키
   - 개인 연락처 세부 정보
   - 채널 세부 사항
   - 상거래 세부 정보
   - Adobe Analytics ExperienceEvent Commerce (Adobe Analytics에 데이터를 전송하려는 경우)

   >[!NOTE]
   >
   > 상거래 관련 필드 그룹을 다음으로 설정하지 마십시오. `Primary identity`. 이렇게 하면 필드가 필수 항목으로 식별되며 Experience Platform은 모든 이벤트에서 해당 필드를 예상합니다. 해당 필드가 없으면 데이터 수집이 실패합니다.

   이제 스키마에는 상거래 관련 필드 그룹이 포함되므로 Commerce에서 시계열 데이터를 수집할 수 있습니다 [동작](events.md) 및 [후선 근무](events-backoffice.md) 이벤트는 스키마에 표시됩니다.

1. [사용](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 프로필에 대한 스키마.

   프로필에 대해 스키마를 활성화하면 이 스키마에서 만든 모든 데이터 세트가 Real-Time CDP에 참여하며, 이 데이터 세트는 개별 소스의 데이터를 병합하여 각 고객에 대한 전체 보기를 구성합니다.

1. [데이터 세트 만들기](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 생성 또는 업데이트한 스키마를 기반으로 합니다.

   데이터 집합은 데이터 수집을 위한 저장 및 관리 구성으로서, 일반적으로 스키마(열) 및 필드(행)를 포함하는 테이블입니다. 데이터 세트에는 저장하는 데이터의 다양한 측면을 설명하는 메타데이터도 포함됩니다.

1. [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 및 상거래 관련 필드 그룹과 해당 데이터 세트를 포함하는 스키마를 선택합니다.

   데이터스트림은 수집된 데이터를 데이터 세트로 전달합니다. 데이터는 선택한 스키마를 기반으로 데이터 세트에 표시됩니다.

1. **베타** (선택 사항) Commerce 인스턴스에서 Experience Platform으로 사용자 지정 백 오피스 이벤트 데이터를 전달하려는 경우 사용자 지정 특성을 사용할 수 있습니다. 이 기능은 Beta 버전입니다. Beta 프로그램에 참여하려면 다음 대상에게 요청을 전송하십시오. [dataconnection@adobe.com](mailto:dataconnection@adobe.com). 요청에 다음 내용을 포함하십시오.

   - 사용자 [Adobe 조직 ID](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). 예 `organization_id@AdobeOrg`.
   - 주문 수준 사용자 지정 특성 목록입니다.
   - 주문 품목 레벨 속성 목록입니다.

   Adobe Commerce 팀이 자세한 정보와 다음 단계에 대해 연락을 드릴 것입니다.

동작 및 백 오피스 데이터에 대해 구성된 스키마, 데이터 세트 및 데이터 스트림을 사용하여 다음을 수행할 수 있습니다. [구성](connect-data.md#data-collection) 상거래 인스턴스에서 해당 데이터를 수집하여 Experience Platform으로 보냅니다.

쇼핑객의 프로필 정보를 포함하려면 다음 섹션을 참조하십시오.

## 시계열 프로필 이벤트 데이터

>[!NOTE]
>
>이 기능은 Beta 버전입니다. Beta 프로그램에 참여하려면 다음 대상에게 요청을 전송하십시오. [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

시계열 프로필 이벤트 데이터는 다음 이벤트에서 생성됩니다.

- [&#39;accountCreated&#39;](events-backoffice.md#accountcreated)
- [&#39;accountUpdated&#39;](events-backoffice.md#accountupdated)
- [&#39;accountDeleted&#39;](events-backoffice.md#accountdeleted)

고객의 프로필 이벤트 데이터를 Experience Platform에 수집하려는 경우 기존 상거래 스키마를 업데이트하고 이미 구성된 동일한 데이터스트림을 사용하거나 프로필별 데이터스트림 및 스키마를 만들 수 있습니다. 이러한 결정은 회사의 데이터 거버넌스를 기반으로 합니다. 다음 두 섹션에서는 두 경우 중 하나를 설명합니다.

### 기존 데이터 스트림을 사용하여 시계열 프로필 이벤트 데이터를 Experience Platform에 보내기

시계열을 추가하려면 [서버측 프로필 이벤트 데이터](events-backoffice.md#customer-profile-events-server-side) 기존 상거래 데이터스트림에 를 추가합니다. `Demographic Details` 스키마에 대한 필드 그룹입니다. 이제 스키마에 다음과 같은 상거래 관련 필드 그룹이 포함됩니다.

- 사이트 검색
- 웹 페이지 방문
- 사용자 로그인 프로세스
- 참조 키
- 개인 연락처 세부 정보
- 채널 세부 사항
- 상거래 세부 정보
- Adobe Analytics ExperienceEvent Commerce (Adobe Analytics에 데이터를 전송하려는 경우)
- 신규: **인구 통계 세부 정보**

를 추가하여 `Demographic Details` 기존 상거래 스키마의 필드 그룹, 상거래 스키마와 이미 연결된 데이터 세트 및 데이터 스트림이 이 시계열 프로필 데이터에 사용됩니다.

### 시계열 프로필 이벤트 데이터를 별도의 데이터 스트림에 있는 Experience Platform으로 보내기

을(를) 추가하려면 [서버측 프로필 이벤트 데이터](events-backoffice.md#customer-profile-events-server-side) 새 프로필별 데이터 스트림 및 스키마에 대해 다음 단계를 완료합니다.

1. [만들기](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 스키마 및 클래스를 로 설정 **경험 이벤트**.

1. [추가](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 다음 프로필별 필드 그룹:

   - 인구 통계 세부 정보
   - 개인 연락처 세부 정보
   - 채널 세부 사항
   - 상거래 세부 정보

1. [사용](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 프로필에 대한 스키마.

   프로필에 대해 스키마를 활성화하면 이 스키마에서 만든 모든 데이터 세트가 Real-Time CDP에 참여하며, 이 데이터 세트는 개별 소스의 데이터를 병합하여 각 고객에 대한 전체 보기를 구성합니다.

1. [데이터 세트 만들기](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 만든 스키마를 기반으로 합니다.

   데이터 집합은 데이터 수집을 위한 저장 및 관리 구성으로서, 일반적으로 스키마(열) 및 필드(행)를 포함하는 테이블입니다. 데이터 세트에는 저장하는 데이터의 다양한 측면을 설명하는 메타데이터도 포함됩니다.

1. [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 상거래 관련 필드 그룹과 해당 데이터 세트를 포함하는 XDM 스키마를 선택합니다.

   데이터스트림은 수집된 데이터를 데이터 세트로 전달합니다. 데이터는 선택한 스키마를 기반으로 데이터 세트에 표시됩니다.

고객 프로필 데이터에 대해 구성된 스키마, 데이터 세트 및 데이터 스트림을 사용하여 다음을 수행할 수 있습니다 [구성](connect-data.md#data-collection) 상거래 인스턴스를 사용하여 해당 데이터를 수집하여 Experience Platform으로 보냅니다.

프로필 레코드 데이터에 대한 스키마, 데이터 세트 및 데이터 스트림을 생성하려면 다음을 참조하십시오. [Experience Platform에게 프로필 레코드 데이터 보내기](profile-data.md).
