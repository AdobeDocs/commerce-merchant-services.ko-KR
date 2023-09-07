---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] 릴리스 정보'
description: "릴리스 정보에서 모든 항목에 대한 정보를 검토하십시오. [!DNL Store Fulfillment by Walmart Commerce Technologies] 릴리스."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# 릴리스 정보

이 릴리스 노트는 의 초기 릴리스에 대해 설명합니다. [!DNL Store Fulfillment Services by Walmart Commerce Technologies] 및 포함:

![신규](../assets/new.svg) 새로운 기능
![해결된 문제](../assets/fix.svg) 수정 사항 및 향상된 기능
![알려진 문제](../assets/bug.svg) 알려진 문제

다음을 참조하십시오 [예정된 릴리스](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) 릴리스 일정 및 지원에 대해 알아봅니다.

다음을 참조하십시오 [제품 가용성](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) 이 확장을 지원하는 Adobe Commerce 버전을 알아봅니다.

## v1.5.0

*2023년 8월 3일*

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}[Adobe Commerce 2.4.4~2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), 2.4.6-p1, 2.4.5-p3 및 2.4.4-p4 보안 패치 릴리스 포함

이번 릴리스에는 다음 업데이트가 포함됩니다.

![신규](../assets/fix.svg) 지원할 확장이 업데이트됨 [Adobe Commerce 보안 패치 릴리스](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 및 2.4.4-p4.

![신규](../assets/new.svg)<!-- WMTP-918 --> 에 대한 지원이 추가되었습니다. [비동기 전송](sales-emails.md) 판매 이메일에 대한 구성 옵션. 버전 1.5.0으로 업그레이드하는 판매자는 즉시(기본값) 또는 비동기적으로 이메일을 보낼 수 있습니다.

![신규](../assets/new.svg)<!-- WMTP-916--> 을(를) 업데이트함 [소스 구성](merchant-store-configuration.md) 국제 전화 번호 포맷을 지원합니다.

![신규](../assets/new.svg) 환불 금액이 남은 금액이나 송장 발행 금액을 초과하지 않도록 하는 논리를 추가했습니다.

![신규](../assets/new.svg)<!-- WMTP-882 --> 대체됨 `google.map.LatLng` 이전 버전의 과의 호환성을 지원하기 위해 JSON 리터럴이 포함된 개체 [!DNL Google Maps].

![해결된 문제](../assets/fix.svg)<!-- WMTP- --> 을(를) 만드는 스크립트가 업데이트되었습니다. `[!DNL Available for Store Pickup]` 및 `[!DNL Available for Home Delivery]` 제품 속성을 사용하십시오.

![해결된 문제](../assets/fix.svg)<!-- WMTP-915 --> 일부 엔티티를 로드하고 저장할 때 무한 루프가 발생하는 호환성 문제를 해결했습니다.

![해결된 문제](../assets/fix.svg)<!-- WMTP-921 --> 이(가) 다음을 방지할 수 있는 문제를 해결했습니다. [!DNL Ship to Store] 항목이 제품 세부 사항 페이지(PDP)에서 장바구니에 추가될 때 트리거되는 견적 유효성 검사.

![해결된 문제](../assets/fix.svg)<!-- WMTP- 932 --> 고객이 홈 게재에 적합하지 않은 항목에 대한 홈 게재 방법을 선택할 수 있는 체크아웃 문제를 해결했습니다.

![해결된 문제](../assets/fix.svg) 설치 업데이트:

- <!-- WMTP-880--> 를 설치할 때 잘못된 웹 사이트 코드가 반환되는 문제를 해결했습니다. [!DNL Store Fulfillment] 확장명.

- <!-- WMTP-878--> 설치 중에 데이터 유형을 문자열 유형으로 변환해야 하는 SKU 정수 문제를 해결했습니다.

![해결된 문제](../assets/fix.svg)<!-- WMTP-915--> 체크인 오류 코드 누락으로 인한 오류를 수정했습니다.

![해결된 문제](../assets/fix.svg)<!-- WMTP-932 --> 분배 작업 중 부분 거부와 관련된 버그가 수정되었습니다.

![신규](../assets/new.svg)<!-- WMTP-953 --> 상태 매개 변수를 선택적 개체로 사용하도록 Cancel API 끝점이 업데이트되었습니다.

![신규](../assets/new.svg)<!-- WMTP-960 --> 분배 API 끝점에 대한 로깅 세부 사항이 개선되었습니다.

## v1.4.0

*2023년 4월 13일*

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

![신규](../assets/fix.svg) [!DNL Store Fulfillment] 현재 [호환 가능 [!DNL Adobe Commerce] 2.4.4~2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*2023년 2월 27일*

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

이번 릴리스에는 다음 업데이트가 포함됩니다.

![신규](../assets/fix.svg)<!-- WMTP-795 --> 웹 사이트에서 전역 웹 사이트로 시스템 구성 설정의 기본 범위를 변경하여 특정 사이트에 대한 스토어 이행 솔루션을 비활성화하는 기능이 추가되었습니다.

## v1.2.0

*2022년 9월 27일*

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

이번 릴리스에는 다음 업데이트가 포함됩니다.

![신규](../assets/fix.svg) [!DNL Store Fulfillment] 현재 [호환 가능 [!DNL Adobe Commerce] 2.4.4~2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*2022년 7월 15일*

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

안정성: 일반 가용성

![신규](../assets/fix.svg)<!-- WMTP-731 --> 를 간소화했습니다. [체크인 경험 구성](check-in-experience-setup.md) 기본 자동차 제조 및 모델 선택을 추가하여 Store Assist 앱의 경우 이전 버전에서는 자동차 제조와 모델 선택을 가맹점이 수동으로 구성해야 했다.

## v1.0.0

*2022년 3월 4일*

[!BADGE 지원됨]{type=Informative tooltip="지원됨"}

안정성: 일반 가용성

## 스토어 지원 앱

Store Assist 앱의 새 릴리스에 대한 자세한 내용은 [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
