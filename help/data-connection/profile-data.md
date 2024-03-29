---
title: 상거래 데이터 수집을 위한 프로필 레코드 스키마 업데이트
description: Experience Platform, 데이터 세트 및 데이터 스트림을 만들어 Commerce 프로필 레코드 데이터를 수집하고 프로필로 전송하는 방법을 알아봅니다.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# 상거래 데이터 수집을 위한 프로필 레코드 스키마 업데이트

쇼핑객이 상거래 사이트에서 프로필을 만들면 프로필 레코드가 생성되고 데이터가 캡처됩니다. 해당 프로필 데이터를 Experience Platform에 스트리밍하려면 먼저 해당 프로필 레코드와 관련된 스키마 및 데이터 세트를 만들어야 합니다.

1. [만들기](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) 스키마 및 클래스를 로 설정 **개인 프로필**.

1. [추가](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) 다음 프로필별 필드 그룹:

   - identityMap
   - 인구 통계 세부 정보
   - 개인 연락처 세부 정보
   - 사용자 계정 세부 정보

1. [사용](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) 프로필에 대한 스키마.

   프로필에 대해 스키마를 활성화하면 이 스키마에서 만든 모든 데이터 세트가 Real-Time CDP에 참여하며, 이 데이터 세트는 개별 소스의 데이터를 병합하여 각 고객에 대한 전체 보기를 구성합니다.

1. [데이터 세트 만들기](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 생성 또는 업데이트한 스키마를 기반으로 합니다.

   데이터 집합은 데이터 수집을 위한 저장 및 관리 구성으로서, 일반적으로 스키마(열) 및 필드(행)를 포함하는 테이블입니다. 데이터 세트에는 저장하는 데이터의 다양한 측면을 설명하는 메타데이터도 포함됩니다.

고객 프로필 레코드 데이터에 대해 구성된 스키마 및 데이터 세트를 사용하여 다음과 같은 작업을 수행할 수 있습니다 [구성](connect-data.md#data-collection) 상거래 인스턴스를 사용하여 해당 데이터를 수집하여 Experience Platform으로 보냅니다.

동작 및 백 오피스 이벤트 데이터에 대한 스키마, 데이터 세트 및 데이터 스트림을 생성하려면 다음을 참조하십시오. [상거래 데이터 수집을 위한 시계열 이벤트 스키마 업데이트](update-xdm.md).
