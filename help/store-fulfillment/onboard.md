---
title: 스토어 이행 서비스에 대한 온보딩 개요
description: '[!DNL Live Search] 온보딩 플로우, 시스템 요구 사항, 경계 및 제한 사항'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# 스토어 이행 온보딩 개요

시작 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 다음 구성 요소를 설정, 구성 및 활성화합니다.

- **스토어 이행 확장**-Adobe Commerce 인스턴스에 이 타사 확장을 설치하고 구성합니다. 설치 후 관리자로부터 저장소 이행 솔루션을 구성하고 관리하여 지원할 수 있습니다. [!DNL buys online, pickup in store] (BOPIS) Commerce 상점 첫 화면의 시나리오.

   ![[!DNL Store Fulfillment Service] 관리자 보기의 구성](assets/store-fulfillment-admin-home.png)

- **주문 처리 계정 저장**-활성화 프로세스 중에 계정 관리자는 스토어 이행 계정을 만들고 계정 정보와 자격 증명을 제공합니다. Adobe Commerce과 스토어 이행 솔루션 간 연결을 활성화하려면 이러한 자격 증명이 필요합니다.

- **스토어 지원 앱**—스토어 관련 서비스를 전체 스토어 이행 워크플로우와 함께 제공하여 모바일 디바이스에서 BOPI 주문을 관리합니다. Store Associates는 Walmart를 다운로드하여 설치할 수 있습니다. [!DNL Store Assist] iOS 및 Android™ 디바이스용. 앱 온보딩 프로세스는 Walmart Commerce Technologies 클라이언트 센터에서 별도의 프로세스로 관리합니다. 그러나 [일부 앱 구성 설정](user-setup.md) Adobe Commerce 관리에서 작성합니다.

   | 스토어 지원 앱 - 시작 보기 | 스토어 지원 앱 - 모듈 보기 |
   |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
   | ![[!DNL Store Assist App Getting Started] 모바일 장치에서 보기](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] 모바일 장치에서](assets/store-assist-orders-small.png) |

## 프로비저닝 단계

- **다음에 등록[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]**-에서 등록 양식 작성 [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)또는 Adobe Commerce 계정 관리자에게 문의하십시오.

- **스토어 이행 프로비저닝을 위한 요청 시작**- 계정 관리자가 제공한 접수 양식을 완료하여 프로비저닝 프로세스를 시작하는 데 필요한 정보를 제공합니다.

- **스토어 이행 계정 자격 증명 가져오기**- 스토어 이행 계정이 생성되면 스토어 이행 솔루션을 Adobe Commerce과 통합하는 데 필요한 자격 증명을 받게 됩니다.

- **[소스 코드를 다운로드하여 다음을 설치하십시오. [!DNL Store Fulfillment] 확장](install.md)**

## 온보딩 단계

1. [Adobe Commerce용 스토어 이행 확장 설치](install.md).

1. 관리자로부터 [솔루션 활성화](enable-general.md).

1. [Adobe Commerce 관리자에서 스토어 이행 확장 구성](service-config-settings-overview.md).

1. [연결 [!DNL Store Fulfillment] 제공된 스토어 이행 자격 증명을 사용하는 서비스](connect-set-up-service.md).

1. [스토어 지원 앱에 대한 사용자 및 역할 만들기](user-setup.md).

1. [Walmart&#39;s 다운로드 [!DNL Store Assist] 앱을 원하는 장치에 추가합니다. 이 앱은 Apple 앱(iOS)과 Google Play(Android™) 모두에서 사용할 수 있습니다](app-setup.md) 상점.

을(를) 성공적으로 설치, 구성 및 온보딩을 완료하고에 액세스하면 [!DNL Store Assist] 앱, 다음 작업을 수행할 수 있습니다. [주문 및 테스트 생성 시작](test-and-deploy.md).
