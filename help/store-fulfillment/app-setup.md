---
title: 앱 설정
description: 설정 [!DNL Store Assist] 온라인 구매를 위한 종단 간 저장소 이행 워크플로우 및 프로세스를 관리하는 앱으로, Store Orders에서 선택합니다.
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 421c90f4c8bd687216cd48c72f30301a32115522
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# 앱 설정

Store Assist 는 Walmart Commerce Technologies에서 제공하는 Faa(Fulfillment-as-a-service) 플랫폼 앱입니다. 이 앱에서는 처리할 매장 내 주문 처리 기능을 제공합니다 [!DNL buy online], [!DNL pick up in store] (BOPIS) 주문.  스토어 도우미에서, 스토어 동료는 고객이 주문한 품목을 확인하고, 올바른 품목을 더 빨리 선택하고, 매장 내 또는 현재 픽업 배송에 대한 이행 주문을 고객에게 설정할 수 있습니다.

스토어 지원 앱은 주문 세부 사항부터 시간을 선택하는 데 이르기까지 모든 주문 및 고객 정보를 수신하고, 모바일 장치를 통해 온라인으로 연결된 데이터를 저장할 수 있도록 합니다. 앱에는 다음이 포함됩니다 [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], 및 [!UICONTROL Orders] Store Associate에서 다음과 같은 이행 활동을 수행할 수 있도록 지원하는 모듈입니다.

- 주문 납품 일자 및 시간을 지정합니다.
- 고객이 주문 수집에 도착하면 고객으로부터 알림을 받습니다.
- 고객에게 전달을 위한 주문 단계.
- 지정된 저장소 위치의 모든 주문에 대한 주문 상태를 추적합니다.

>[!NOTE]
>
>자세한 내용은 [저장 지원 이행 워크플로우](store-assist-modules.md) 스토어 지원 앱에 대해 자세히 알아보십시오 .

## 스토어 지원 앱 구성

스토어 지원 앱에는 두 가지 유형의 구성이 필요합니다.

- Adobe Commerce 관리 구성 설정 대상 [Adobe Commerce Admin 시스템 설정에서 사용자 계정, 사용자 역할 및 리소스 권한 관리](user-setup.md).

- Store Assist 앱 인터페이스와 다음을 포함한 기타 설정을 사용자 지정하는 프런트 엔드 구성 설정:

   - **스토어 지원 앱 브랜딩**- 회사 로고와 색상을 사용하여 앱 사용자 인터페이스를 사용자 정의합니다.

   - **기본 지침 업데이트**- Pick, Stage, Handoff 및 Order 모듈의 Store Assist 인터페이스에 있는 지침을 사용자 정의하여 회사 정책 및 절차를 준수하고 이행 워크플로우의 각 단계를 통해 Store Associates에 대한 지침을 안내합니다.

   - **로컬라이제이션**- 앱에 사용할 수 있는 언어를 선택합니다. 날짜 및 시간 형식을 선택하고 기본 측정 단위 및 기본 통화를 선택합니다.

   - **비활성 시간**- 앱이 로그아웃하기 전에 비활성 상태여야 하는 시간을 지정합니다.

   - **상점의 취소**—저장소에서 주문을 취소할 수 있는지 여부와 취소 권한이 있는 역할을 지정합니다

   - **주문 정리 창**- 선택된 주문이 다시 복원되기 전에 스테이징에 남아 있는 스케줄링된 픽업 시간(예: 3일)을 경과하도록 지정합니다.

   - 앱 지침(선택, 스테이징, 핸드오프)에서 모든 것을 사용자 지정합니다.

   - **알림 선택**-고객이 주문을 한 후 피킹 프로세스를 시작하기 위해 푸시 알림을 전송할지 여부를 지정합니다.

   - **알림 확인**-고객 대기 시간이 지정된 기간을 초과한 후, 체크인 후 주문 픽업을 위한 체크인 프로세스 동안 푸시 알림을 전송할지 여부를 지정합니다. 또는 알림을 비활성화합니다.

   - **핸드오프 프로세스**- Store Associate에서 고객에게 주문을 전달할 때 선택적 프로세스를 활성화합니다. 예를 들어 고객 서명이 필요하거나, Associate에서 고객 ID를 확인하라는 메시지가 표시됩니다.

   - **핸드오프 시 항목 거부 활성화**-주문 핸드오프 중에 고객이 주문 품목을 반품하거나 취소할 수 있도록 허용합니다.
   Walmart Commerce Technologies 클라이언트 서비스 팀과 협력하여 스토어 지원 앱에 대한 프런트 엔드 구성을 완료합니다.

## 앱 다운로드 및 설치

스토어 지원 앱 구성이 완료되면 Store Associates는 모바일 장치에서 스토어 지원 앱을 다운로드하여 설치하고 로그인할 수 있습니다.

- 모바일 장치가 를 충족하는지 확인합니다 [하드웨어 및 소프트웨어 요구 사항](solution-requirements.md#store-assist-app-requirements) Store Fulfillment 솔루션에 대해 설명합니다.

- 에서 스토어 지원 앱을 다운로드합니다. [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390){target=&quot;_blank&quot;} 또는 [Google Play 스토어](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target=&quot;_blank&quot;}.

- Store Associates에서 로그인하려면 다음 정보가 필요합니다.

   - 스토어 지원 계정과 연결된 회사 이름

   - 계정 지원 계정 자격 증명(사용자 이름 및 해당 계정의 암호 자격 증명)을 저장합니다.
   Adobe Commerce 관리자는 사용자 계정을 만들고 저장소 지원 앱 사용자 계정에 대해 다음 권한을 가진 저장소 위치에 대한 권한을 설정할 수 있습니다 [매장 내 픽업](merchant-store-configuration.md#pickup-location-configuration) 관리자 저장소 설정에서 활성화했습니다.
