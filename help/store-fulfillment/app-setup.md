---
title: 앱 설정
description: 다음을 설정합니다. [!DNL Store Assist] 앱에서 온라인 구매, 스토어 주문 픽업을 위한 전체 스토어 이행 워크플로우 및 프로세스를 관리합니다.
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '625'
ht-degree: 0%

---

# 앱 설정

Store Assist는 Walmart Commerce Technologies에서 제공하는 서비스별 주문 처리(Fulfillment-as-a-Service) 플랫폼 앱입니다. 이 앱은 처리할 매장 주문 처리 기능을 제공합니다 [!DNL buy online, pick up in store] (BOPIS) 주문. 스토어 어시스트를 통해 스토어 제휴자는 고객이 주문한 품목을 확인하고, 정확한 품목을 더 빨리 선택하며, 고객에게 매장 내 또는 커브사이드 픽업 배송에 대한 이행된 주문을 설정할 수 있습니다.

Store Assist 앱은 주문 세부 사항에서 시간을 선택하는 데 이르기까지 모든 주문 및 고객 정보를 수신하고 데이터를 모바일 장치를 통해 온라인으로 협력사에 저장할 수 있도록 합니다. 앱에는 다음이 포함됩니다 [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], 및 [!UICONTROL Orders] 스토어 연합을 다음과 같은 이행 활동과 돕는 모듈입니다.

- 주문 납품 일자 및 시간을 지정합니다.
- 주문 픽업을 위해 고객이 도착하면 알림을 받습니다.
- 고객에게 전달할 스테이지 주문.
- 할당된 저장소 위치의 모든 주문에 대한 주문 상태를 추적합니다.

>[!NOTE]
>
>다음을 검토하여 Store Assist 앱에 대해 자세히 알아보세요. [지원 이행 워크플로우 저장](store-assist-modules.md) 주제.

## 스토어 지원 앱 구성

스토어 지원 앱에는 두 가지 유형의 구성이 필요합니다.

- Adobe Commerce 관리 시스템 설정 대상 [사용자 계정, 사용자 역할, 리소스 권한 관리](user-setup.md), 및 [체크인 프로세스 중에 고객이 자동차 제조 및 모델 선택 가능](check-in-experience-setup.md).

- Store Assist 앱 인터페이스를 사용자 지정하는 프론트엔드 구성 설정 및 다음을 포함한 기타 설정:

   - **스토어 지원 앱 브랜딩**—회사 로고 및 색상으로 앱 사용자 인터페이스를 사용자 지정합니다.

   - **기본 지침 업데이트**—Store Assist Pick, Stage, Handoff 및 Order 모듈의 지침을 사용자 정의하여 Store Associates가 회사의 이행 워크플로우의 각 단계를 수행하도록 안내합니다.

   - **로컬라이제이션**- 앱에 사용할 수 있는 언어를 선택합니다. 날짜 및 시간 형식을 선택하고 기본 측정 단위 및 기본 통화를 선택합니다.

   - **비활성 시간**- 로그아웃하기 전에 앱이 비활성 상태여야 하는 시간을 지정합니다.

   - **스토어에서 취소**- 저장소에서 주문을 취소할 수 있는지 여부와 취소 권한이 있는 역할을 지정합니다

   - **주문 정리 창**- 다음 기간 경과 시간을 지정합니다. [예상 픽업 리드 타임](enable-general.md#delivery-method-title-configuration) 예를 들어 피킹 주문이 재입고되기 전에 스테이징에 남아 있습니다. 기본값은 7일입니다. 이 구성이 켜져 있으면 이 시간이 만료되면 주문이 자동으로 취소됩니다. 품목은 재입고되고 판매자는 취소 이메일을 받습니다.

   - 앱 지침(선택, 스테이징, 전달)에서 모든 항목을 사용자 지정합니다.

   - **출하 통지**- 고객이 주문한 후 피킹 프로세스를 시작하기 위해 푸시 알림을 전송할지 여부를 지정합니다.

   - **알림 체크인**—주문 픽업을 위한 체크인 프로세스 중에 푸시 알림을 보낼지 여부를 지정합니다. 체크인 후 고객 대기 시간이 지정된 기간을 초과한 후에 알림을 보냅니다. 또는 알림을 비활성화합니다.

   - **핸드 오프 프로세스**—Store Associate에서 고객에게 주문을 전달할 때 선택적 프로세스를 사용할 수 있습니다. 예를 들어 고객 서명이 필요하거나 담당자에게 고객 ID를 확인하라는 메시지가 표시됩니다.

   - **제출 시 항목 거부 활성화**- 주문 전달 중에 고객이 주문 항목을 반환하거나 취소할 수 있습니다.

  Walmart Commerce Technologies Client Services 팀과 함께 스토어 지원 앱에 대한 프론트엔드 구성을 완료합니다.

## 앱 다운로드 및 설치

Store Assist 앱을 설정하고 구성한 후 Store Associates는 모바일 장치에서 Store Assist 앱을 다운로드하여 설치하고 로그인할 수 있습니다.

- 모바일 장치가 [하드웨어 및 소프트웨어 요구 사항](solution-requirements.md#store-assist-app-requirements) Store Fulfillment 솔루션용

- 에서 Store Assist 앱을 다운로드합니다. [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- Store Associates에서 로그인하려면 다음 정보가 필요합니다.

   - **[!UICONTROL Company name]** 스토어 지원 계정과 연결됨

   - **지원 계정 자격 증명 저장**—해당 계정의 사용자 이름 및 암호 자격 증명.

  Adobe Commerce 관리자는 을 만들고 관리할 수 있습니다 [!DNL Store Assist app] 다음을 보유한 모든 스토어 위치에 대한 사용자 계정 [매장 픽업](merchant-store-configuration.md#pickup-location-configuration) 관리자 저장소 설정에서 활성화됩니다.
