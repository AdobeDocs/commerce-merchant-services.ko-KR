---
title: 릴리스 정보
description: 에 대한 최신 릴리스 정보 [!DNL Data Connection] Adobe Commerce에서 확장되었습니다.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: a2d5e695b3f6491d051da77bfc0fb596f5411c92
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---

# 릴리스 정보

>[!IMPORTANT]
>
>Experience Platform 커넥터의 이름이 (으)로 변경되었습니다. [!DNL Data Connection].

이러한 릴리스 노트에는 [!DNL Data Connection] 확장 및 포함 사항:

![신규](../assets/new.svg) - 새로운 기능
![수정](../assets/fix.svg) - 수정 사항 및 향상된 기능
![버그](../assets/bug.svg) - 알려진 문제

에서 사용하는 확장과 관련된 기능 변경 및 수정 사항 [!DNL Data Connection] 확장, 참조 **지원되는 서비스 업데이트**.

다음을 참조하십시오 [예정된 릴리스](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 릴리스 일정 및 지원에 대해 알아봅니다.

개발자 설명서 를 참조하여 다음을 수행합니다 [이 모듈을 지원하는 Commerce 버전 알아보기](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## 지원되는 서비스 업데이트

이러한 릴리스 노트는 에서 사용하는 확장과 관련된 기능 변경 사항 및 수정 사항에 대해 설명합니다. [!DNL Data Connection] 확장명.

+++지원되는 서비스 업데이트

_2024년 1월 24일_

![신규](../assets/new.svg) - 을(를) 업데이트함 `data-services-b2b` 새 구매요청 이벤트를 포함하는 확장명 [deleteRequisitionList](events.md#deleterequisitionlist) B2B 판매자용.

_2023년 11월 16일_

![수정](../assets/fix.svg) - 여러 배송 주소가 있는 주문을 했을 때 오류 메시지가 잘못 표시되는 문제를 해결했습니다.
![수정](../assets/fix.svg) - 의 문제가 해결되었습니다. [제품 페이지 보기](events.md#productpageview) 이벤트 위치 `productListItems.priceTotal` 스토어 보기에서 통화를 전환한 후 이벤트 필드에서 가격이 전환되지 않았습니다.
![수정](../assets/fix.svg) - 의 문제가 해결되었습니다. `productListItems` 판매자가 스토어 보기를 전환할 때 통화 코드가 업데이트되지 않은 이벤트 필드.

_2023년 10월 10일_

![신규](../assets/new.svg) - 새 주문 상태 이벤트가 추가되었습니다. [인보이스 발행 주문](events-backoffice.md#orderinvoiced), [주문 품목 반품 시작됨](events-backoffice.md#orderitemsreturninitiated), 및 [주문 품목 반품 완료](events-backoffice.md#orderitemreturncompleted).
![수정](../assets/fix.svg) - 캐시를 새로 고친 후 통화 구성 변경 사항이 이벤트에 반영되지 않던 문제를 수정했습니다.
![수정](../assets/fix.svg) - 비동기 주문 배치가 활성화된 경우 주문 확인 메시지가 표시되지 않는 경우 오류를 수정했습니다.
![신규](../assets/new.svg) - 데이터를에 추가했습니다. [addToRequisitionList](events.md#addtorequisitionlist) 카테고리 보기 페이지의 단순 제품에 대한 이벤트입니다.
![수정](../assets/fix.svg) - 의 문제가 해결되었습니다. `selectedOptions` 의 데이터 [addToRequisitionList](events.md#addtorequisitionlist) 이벤트 : 주문 확인 페이지에서 제품이 추가될 때.
![신규](../assets/new.svg) - 제품 데이터를에 추가했습니다. [addToRequisitionList](events.md#addtorequisitionlist) 이벤트: 범주 보기 페이지에서 구매요청 목록에 제품이 추가될 때.
![신규](../assets/new.svg) - 추가됨 [addToRequisitionList](events.md#addtorequisitionlist) 이벤트: 구성 가능한 제품이 제품 보기 페이지의 구매요청 목록에 추가될 때.
![신규](../assets/new.svg) - 추가됨 [addToRequisitionList](events.md#addtorequisitionlist) 및 [removeFromRequisitionList](events.md#removefromrequisitionlist) 구매요청 목록에서 제품 수량이 증가 및/또는 감소하는 경우 이벤트.

_2023년 6월 10일_

![수정](../assets/fix.svg) - 다음과 같은 경우 문제가 해결되었습니다. `orderId` Commerce 주문 식별자의 접두사로 인해 를 컨텍스트에 전달하지 않았습니다.
![수정](../assets/fix.svg) - 콘텐츠 보안 정책 구성을 업데이트했습니다.

_2023년 3월 30일_

![신규](../assets/new.svg) - (이)라는 확장이 추가되었습니다. `data-services-b2b` 다음을 포함 [구매요청 목록 이벤트](events.md#b2b-events) B2B 판매자용.
![신규](../assets/new.svg) - 이(가) 을(를) 추가함 `uniqueIdentifier` 필드 대상 [검색](events.md#search-events) 이벤트. 이 새 필드를 사용하면 판매자가 검색 요청과 검색 응답을 상호 참조할 수 있습니다.

_2022년 10월 12일_

![신규](../assets/new.svg) - 2개 추가됨 [storefront 이벤트](events.md), `openCart` 및 `removeFromCart`: Adobe Commerce Storefront 이벤트 SDK 및 수집기에 연결합니다.
![신규](../assets/new.svg) - 다음에 대한 지원이 추가됨 [AEM 상점 첫 화면](overview.md#aem-support).

+++

## 3.1.2

[!BADGE 호환성]{type=Informative tooltip="호환성"}

_2024년 6월 5일_

![수정](../assets/new.svg) - 을(를) 시작할 때 잘못된 날짜 형식이 사용되는 문제가 해결되었습니다. [이전 동기화](connect-data.md#specify-order-history-date-range).
![수정](../assets/new.svg) - 다음과 같은 문제가 해결되었습니다. [startCheck](events.md#startcheckout) 이벤트가 Adobe Commerce 2.4.7에서 전송되지 않았습니다.

## 3.1.1

[!BADGE 호환성]{type=Informative tooltip="호환성"}

_2024년 4월 4일_

![신규](../assets/new.svg) - 모든 PHP 8.3에 대한 지원을 추가했습니다. [!DNL Data Connection] 확장.
![신규](../assets/new.svg) - 다음 방법에 대한 문서 추가 [통합](mobile-sdk-epc.md) Adobe Experience Platform Mobile SDK와 Commerce.

## 3.2.0-베타2

_2024년 3월 4일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![신규](../assets/new.svg) - Beta에 참여하는 경우 `composer.json` 파일의 루트 레벨은 다음과 같습니다. ` "minimum-stability": "beta"`. 또한, 추가 `composer require "magento/customers-connector: ^1.2.0"` Commerce 인스턴스에서 SaaS로 고객 프로필을 보냅니다.
![신규](../assets/new.svg) - 에 추가된 기능 [사용자 지정 속성 추가](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![신규](../assets/new.svg) - 에 추가된 기능 [프로필 레코드 수집 및 보내기](connect-data.md#send-customer-profile-data) 및 데이터를 Experience Platform에 추가합니다.

## 3.1.0

_2023년 11월 16일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

![신규](../assets/new.svg) - Experience Platform 커넥터의 이름이 (으)로 변경되었습니다. [!DNL Data Connection].
![수정](../assets/new.svg) - Adobe IMS에서 액세스 토큰을 생성할 수 없는 경우 오류 응답을 기록하는 기능이 추가되었습니다.
![수정](../assets/new.svg) - 이전 주문을 동기화하려고 시도했지만 계정 자격 증명을 지정하지 않은 경우 알림 메시지가 추가되었습니다.

## 3.0.0

_2023년 10월 10일_

[!BADGE 호환성]{type=Informative tooltip="호환성"}

주요 버전 릴리스입니다. [편집](install.md#update-the-data-connection) 프로젝트의 루트 composer.json 파일.

![신규](../assets/new.svg) - 다음에 대한 일반 가용성 [이전 주문 보내기](connect-data.md#send-historical-order-data) Experience Platform에 대한 데이터 및 상태.
![신규](../assets/new.svg) - 다음을 수행하는 경우 OAuth 2.0에 대한 지원이 추가됨: [구성](connect-data.md#connect-commerce-data-to-adobe-experience-platform) 다음 [!DNL Data Connection] 확장명.
![신규](../assets/new.svg) - Adobe Commerce 2.4.3에 대한 지원이 종료되었습니다.

## 2.3.0

_2023년 6월 27일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) - 에 추가된 기능 [상점 이벤트 보내기 끄기](connect-data.md#data-collection) Experience Platform.
![수정](../assets/fix.svg) - 콘텐츠 보안 정책 구성을 업데이트했습니다.
![수정](../assets/fix.svg) - Commerce 2.4.7 버전의 백오피스 이벤트에 대한 지원이 수정되었습니다.
![신규](../assets/new.svg) - 변경 사항을 저장할 때 캐시 무효화에 대한 알림 메시지가 추가되었습니다. [!DNL Data Connection] 확장 양식.


## 3.0.0-beta1(내부용)

_2023년 6월 13일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) - (Beta) 다음에 대한 기능 추가됨 [이전 주문 보내기](connect-data.md#beta-send-historical-order-data) Experience Platform에 대한 데이터 및 상태.

## 2.2.0

_2023년 3월 30일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) - 번들 `commerce-data-export` 및 `saas-export` 과의 종속성 `experience-platform-connector` 확장명. 이전에는 이러한 종속성을 별도로 설치해야 했습니다. 이러한 종속성은 판매자 구성과 함께 서버 측 처리를 가능하게 합니다. [백오피스 이벤트](events-backoffice.md).
![신규](../assets/new.svg) - (이)라는 새로운 백오피스 이벤트가 추가되었습니다. [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_2023년 2월 28일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) - 모든 PHP 8.2에 대한 지원을 추가했습니다. [!DNL Data Connection] 확장.

## 2.1.0

_2023년 1월 17일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) - 을(를) 업데이트함 [[!DNL Data Connection] 확장 관리자](connect-data.md) 따라서 고유한 AEP 웹 SDK(alloy)를 지정할 수 있습니다.
![수정](../assets/fix.svg) 을(를) 사용하기로 변경함 `identityMap` 대신 `personID` 에지에 푸시된 데이터에 대한 기본 id 설정 시.

## 2.0.1

_2022년 11월 10일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![수정](../assets/fix.svg) - 이제 Adobe Experience Platform 컨텍스트는 Storefront 이벤트 수집기 및 Storefront 이벤트 SDK가 성공적으로 로드된 후에만 설정됩니다.

## 2.0.0

_2022년 10월 12일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) - 다음과 같은 경우 자체 AEP 웹 SDK를 지정할 수 있는 기능이 추가되었습니다. [연결 중](connect-data.md) Adobe Commerce 인스턴스를 Experience Platform에 추가합니다.
![수정](../assets/fix.svg) - 데이터스트림 ID의 범위가 storeview가 아닌 웹 사이트로 지정되도록 데이터스트림 범위 요구 사항이 업데이트되었습니다.

## 1.0.0

_2022년 8월 9일_

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/new.svg) - 일반 공급 릴리스.
