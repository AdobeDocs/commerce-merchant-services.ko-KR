---
title: 릴리스 정보
description: Adobe Commerce의 Adobe Experience Platform 커넥터에 대한 최신 릴리스 정보입니다.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 22823b662eefa953fcca6ae78f6c37ee8abff3d1
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 1%

---

# 릴리스 정보

이러한 릴리스 노트에는 Experience Platform 커넥터에 대한 업데이트가 포함되어 있으며 다음과 같은 내용이 포함됩니다.

* ![신규](../assets/new.svg) - 새로운 기능
* ![수정](../assets/fix.svg) - 수정 사항 및 향상된 기능
* ![버그](../assets/bug.svg) - 알려진 문제

Experience Platform 커넥터에서 사용하는 확장과 관련된 기능 변경 및 수정 사항에 대해서는 를 참조하십시오. **지원되는 서비스 업데이트**.

다음을 참조하십시오 [예정된 릴리스](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 릴리스 일정 및 지원에 대해 알아봅니다.

개발자 설명서 를 참조하여 다음을 수행합니다 [제품 호환성에 대해 알아보기](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 지원되는 서비스 업데이트

이러한 릴리스 노트는 Experience Platform 커넥터에서 사용하는 확장과 관련된 기능 변경 사항 및 수정 사항에 대해 설명합니다.

+++지원되는 서비스 업데이트

_2023년 3월 30일_

* ![신규](../assets/new.svg) - 라는 새 확장이 추가되었습니다. `data-services-b2b` 다음을 포함 [구매요청 목록 이벤트](events.md#b2b-events) B2B 판매자용
* ![신규](../assets/new.svg) - 이(가) 을(를) 추가함 `uniqueIdentifier` 필드 대상 [검색](events.md#search-events) 이벤트. 이 새 필드를 사용하면 판매자는 검색 응답에 해당하는 검색 요청을 상호 참조할 수 있습니다.

_2022년 10월 12일_

* ![신규](../assets/new.svg) - 2개 추가됨 [storefront 이벤트](events.md): `openCart` 및 `removeFromCart` Adobe Commerce Storefront 이벤트 SDK 및 컬렉터에 연결
* ![신규](../assets/new.svg) - 다음에 대한 지원이 추가됨 [AEM 상점 첫 화면](overview.md#aem-support)

+++

## 2.2.0

_2023년 3월 30일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

* ![신규](../assets/new.svg) - 번들 `commerce-data-export` 및 `saas-export` 과의 종속성 `experience-platform-connector` 확장명. 이전에는 이러한 종속성을 별도로 설치해야 했습니다. 이러한 종속성은 판매자 구성과 함께 서버 측 처리를 가능하게 합니다. [백오피스 이벤트](events.md#back-office-events).
* ![신규](../assets/new.svg) - (이)라는 새로운 백오피스 이벤트가 추가되었습니다. [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_2023년 2월 28일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

* ![신규](../assets/new.svg) - 모든 Experience Platform 커넥터 모듈에 대해 PHP 8.2에 대한 지원을 추가했습니다.

## 2.1.0

_2023년 1월 17일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

* ![신규](../assets/new.svg) - 을(를) 업데이트함 [Experience Platform 커넥터 관리](connect-data.md) 따라서 고유한 AEP 웹 SDK(alloy)를 지정할 수 있습니다.
* ![수정](../assets/fix.svg) 을(를) 사용하기로 변경함 `identityMap` 대신 `personID` 에지에 푸시된 데이터에 대한 기본 id 설정 시.

## 2.0.1

_2022년 11월 10일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

* ![해결된 문제](../assets/fix.svg) - 이제 Adobe Experience Platform 컨텍스트는 Storefront 이벤트 수집기 및 Storefront 이벤트 SDK가 성공적으로 로드된 후에만 설정됩니다.

## 2.0.0

_2022년 10월 12일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

* ![신규](../assets/new.svg) - 다음과 같은 경우 자체 AEP 웹 SDK를 지정할 수 있는 기능이 추가되었습니다. [연결 중](connect-data.md) Experience Platform에 대한 Adobe Commerce 인스턴스
* ![수정](../assets/fix.svg) - 데이터 스트림 ID의 범위가 storeview가 아닌 웹 사이트로 지정되도록 데이터 스트림 범위 요구 사항이 업데이트되었습니다.

## 1.0.0

_2022년 8월 9일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

* ![신규](../assets/new.svg) - 일반 가용성 릴리스
