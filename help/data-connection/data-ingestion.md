---
title: 상거래 데이터 유형
description: 수집하여 Experience Platform으로 보낼 수 있는 데이터 유형을 알아봅니다.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# 상거래 데이터 유형

다음 [데이터 연결 확장](overview.md) 상거래 데이터를 Experience Platform에 연결합니다. Experience Platform에서 사용하려는 데이터는 다음 두 가지 동작 유형으로 그룹화됩니다. 시계열 데이터는 **경험 이벤트** 클래스 및 레코드 데이터가 포함된 **개인 프로필** 클래스.

자세히 알아보기 [데이터 동작](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) 및 [클래스](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) Experience Platform.

## 시계열 데이터

시계열 데이터는 레코드 주체가 직접 또는 간접적으로 작업을 수행한 시간에 시스템의 스냅샷을 제공합니다. 예를 들어, 쇼핑객이 사이트에서 제품을 탐색할 때 장바구니에 제품을 추가하고, 주문하는 등의 작업을 수행합니다. 시계열 데이터는 클래스가 설정된 스키마를 사용하여 Experience Platform에 수집됩니다 **경험 이벤트**.

### 캡처된 시계열 데이터

다음을 참조하십시오 [동작 이벤트](events.md) 및 [백오피스 이벤트](events-backoffice.md) 시계열 이벤트가 생성될 때 캡처된 데이터를 학습합니다.

### 시계열 이벤트 데이터를 수집하는 데 필요한 스키마

방법 알아보기 [스키마 만들기](update-xdm.md) 행동 및 백 오피스 시계열 이벤트 데이터를 수집할 수 있습니다.

## 레코드 데이터

레코드 데이터는 주체의 속성에 대한 정보를 제공합니다. 주제는 조직 또는 개인일 수 있습니다. 예를 들어 사이트의 쇼핑객이 계정을 만들고 이 계정은 레코드 데이터를 생성합니다. 이 데이터는 클래스가 설정된 스키마를 사용하여 Experience Platform에 수집됩니다. **개인 프로필**. 해당 레코드 데이터를 Adobe의 프로필 관리 및 세분화 서비스로 보낼 수 있습니다. [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=ko-KR).

### 캡처된 프로필 레코드 데이터

다음을 참조하십시오 [고객 프로필 레코드 데이터](events-profilerecord.md) 프로필 레코드가 생성될 때 캡처되는 데이터를 알아봅니다.

### 프로필 레코드 데이터를 수집하는 데 필요한 스키마

방법 알아보기 [스키마 만들기](profile-data.md) 프로필 레코드 데이터를 수집할 수 있습니다.
