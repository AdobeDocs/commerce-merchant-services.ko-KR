---
title: 릴리스 노트
description: Adobe Commerce의 Adobe Experience Platform 커넥터에 대한 최신 릴리스 정보입니다.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 57d0d0604e871a0d8a76bfd2c006250b55f0eeb1
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 1%

---

# 릴리스 노트

이러한 릴리스 노트에는 Experience Platform 커넥터에 대한 업데이트가 포함되어 있으며 다음을 포함합니다.

* ![새로 만들기](../assets/new.svg) - 새로운 기능
* ![수정](../assets/fix.svg) - 수정 사항 및 향상된 기능
* ![버그](../assets/bug.svg) - 알려진 문제

Experience Platform 커넥터에서 사용하는 확장과 관련된 기능 변경 사항 및 수정 사항에 대해서는 다음을 참조하십시오 **지원되는 서비스 업데이트**.

자세한 내용은 [예정된 릴리스](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) 릴리스 일정 및 지원에 대해 알아보십시오.

자세한 내용은 [사용 가능](https://experienceleague.adobe.com/docs/commerce-operations/release/availability.html) 제품 호환성에 대해 자세히 알아보십시오.

## 지원되는 서비스 업데이트

이러한 릴리스 노트에서는 Experience Platform 커넥터에서 사용하는 확장과 관련된 기능 변경 사항 및 수정 사항을 설명합니다.

+++지원되는 서비스 업데이트

_2022년 10월 12일_

* ![새로 만들기](../assets/new.svg) - 2개 추가됨 [storefront 이벤트](events.md): `openCart` 및 `removeFromCart` Adobe Commerce Storefront Events SDK 및 Collector로 업그레이드
* ![새로 만들기](../assets/new.svg) - 에 대한 지원을 추가했습니다. [AEM storfront](overview.md#aem-support)

+++

## 2.1.1

_2023년 2월 28일_

* ![새로 만들기](../assets/new.svg) - 모든 Experience Platform 커넥터 모듈에 대한 PHP 8.2에 대한 지원이 추가되었습니다.

## 2.1.0

_2023년 1월 17일_

* ![새로 만들기](../assets/new.svg) - 업데이트 날짜: [Experience Platform 커넥터 관리](connect-data.md) 고유한 AEP 웹 SDK(alloy)를 지정할 수 있습니다. 또한, 백오피스 베타 프로그램에 등록한 상인들을 위한 전송 옵션을 추가했습니다 [office 이벤트 데이터](connect-data.md#data-collection) 끝. 이러한 이벤트는 다음과 같습니다 [주문 상태 정보](events.md#beta-order-status-events) 주문, 취소, 환불 또는 출하가 이루어진 경우와 같은 주문 정보. 백오피스 베타 프로그램에 참여하시려면 [drios@adobe.com](mailto:drios@adobe.com).
* ![수정](../assets/fix.svg) 을 사용 `identityMap` 대신 `personID` 에지에 푸시된 데이터의 기본 ID를 설정할 때.

## 2.0.1

_2022년 11월 10일_

* ![해결된 문제](../assets/fix.svg) - 이제 Storefront Event Collector 및 Storefront Event SDK가 성공적으로 로드된 후에만 Adobe Experience Platform 컨텍스트이 설정됩니다.

## 2.0.0

_2022년 10월 12일_

* ![새로 만들기](../assets/new.svg) - 다음과 같은 경우 고유한 AEP 웹 SDK를 지정하는 기능이 추가되었습니다. [연결](connect-data.md) Experience Platform에 대한 Adobe Commerce 인스턴스
* ![수정](../assets/fix.svg) - 데이터 스트림 ID를 storeview가 아닌 웹 사이트로 범위를 지정하도록 데이터 스트림 범위 요구 사항을 업데이트했습니다

## 1.0.0

_2022년 8월 9일_

* ![새로 만들기](../assets/new.svg) - 일반 출시 릴리스

## 설명서

자세한 내용:

* [Adobe Commerce 개발자 설명서](https://devdocs.magento.com/)
* [Adobe Commerce 사용 안내서](https://docs.magento.com/user-guide/)
