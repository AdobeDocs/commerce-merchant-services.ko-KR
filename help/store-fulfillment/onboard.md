---
title: Store Fulfillment 서비스에 대한 온보딩 개요
description: '`[!DNL Live Search] 온보딩 흐름, 시스템 요구 사항, 경계 및 제한 사항'''
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 1fb22b4644d41ea5c60aead3fe2c455dfa3382f8
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# 스토어 이행에 대한 온보딩 개요

시작하기 [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] 다음 구성 요소를 설정, 구성 및 활성화하여 다음을 수행합니다.

- **저장 이행 확장**-Adobe Commerce 인스턴스에 이 타사 확장을 설치하고 구성합니다. 설치 후 관리자가 제공하는 Store Fulfillment 솔루션을 구성하고 관리할 수 있습니다 [!DNL buys online, pickup in store] (BOPIS) 시나리오와 동일합니다.

   ![[!DNL Store Fulfillment Service] 관리자 보기의 구성](assets/store-fulfillment-admin-home.png)

- **주문 처리 계정 저장**-사용 프로세스 중에 계정 관리자가 저장소 이행 계정을 만들고 계정 정보 및 자격 증명을 제공합니다. 이러한 자격 증명은 Adobe Commerce과 Store Fulfillment 솔루션 간에 연결을 활성화하는 데 필요합니다.

- **스토어 지원 앱**- 모바일 장치에서 BOPIS 주문을 관리하기 위해 Store Associate와 End-to-End Store 이행 워크플로우를 제공합니다. Store Associates에서 Walmart&#39;s를 다운로드하여 설치할 수 있습니다 [!DNL Store Assist] iOS 및 Android™ 장치용. 앱 온보딩 프로세스는 Walmart Commerce Technologies Client Center에서 별도의 프로세스로 관리됩니다. 하지만, [일부 앱 구성 설정](user-setup.md) Adobe Commerce 관리자에서 이 완료되었습니다.

   | 스토어 지원 앱 - 시작 보기 | 스토어 지원 앱 — 모듈 보기 |
   |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
   | ![[!DNL Store Assist App Getting Started] 모바일 장치에서 보기](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] 모바일 장치](assets/store-assist-orders-small.png) |

## 프로비저닝 단계

- **등록[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]**-등록 양식 완료 [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)도움이 필요하면 Adobe Commerce 계정 관리자에게 문의하십시오.

- **저장소 이행 프로비전 요청 시작**-프로비저닝 프로세스를 시작하는 데 필요한 정보를 제공하기 위해 계정 관리자가 제공하는 intructure 양식을 작성합니다.

- **저장소 이행 계정 자격 증명 가져오기**-Store Fulfillment 계정이 생성되면 Store Fulfillment 솔루션을 Adobe Commerce과 통합하는 데 필요한 자격 증명을 받게 됩니다.

- **[소스 코드를 다운로드하여 [!DNL Store Fulfillment] 확장](install.md)**

## 온보딩 단계

1. [Adobe Commerce용 Store Fulfillment 확장 설치](install.md).

1. 관리자에서 [솔루션 활성화](enable-general.md).

1. [Adobe Commerce 관리에서 저장소 이행 확장 구성](service-config-settings-overview.md).

1. [연결 [!DNL Store Fulfillment] 사용자에게 제공된 저장소 이행 자격 증명을 사용한 서비스](connect-set-up-service.md).

1. [스토어 지원 앱의 사용자 및 역할 만들기](user-setup.md).

1. [월마트 다운로드 [!DNL Store Assist] 앱을 원하는 장치에 추가합니다. 이 앱은 Apple 앱(iOS)과 Google Play(Android™) 모두에서 사용할 수 있습니다](app-setup.md) 상점들.

설치, 구성, 온보딩을 완료하고 를 액세스할 수 있게 되면 [!DNL Store Assist] 앱, [주문 및 테스트 만들기](test-and-deploy.md).
