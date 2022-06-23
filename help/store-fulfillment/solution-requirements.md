---
title: 저장 이행 요구 사항
description: 프로비저닝 및 온보딩에 대한 요구 사항 [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 421c90f4c8bd687216cd48c72f30301a32115522
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 2%

---

# Adobe Commerce에 대한 주문 처리 요구 사항 저장

Adobe Commerce용 Store Fulfillment 솔루션을 설치하고 사용하려면 다음 기술 및 비즈니스 요구 사항을 충족해야 합니다.

## 플랫폼 및 소프트웨어 버전 요구 사항

다음 [!DNL Store Fulfillment] 솔루션은 다음 플랫폼에서 Adobe Commerce 고객이 사용할 수 있습니다.

- Adobe Commerce on cloud infrastructure(ECE)
- Adobe Commerce 온-프레미스(EE)

Store Fulfillment 솔루션은 다음 소프트웨어 버전과 호환됩니다.

**소프트웨어 호환성**

| **소프트웨어** | **최소 버전** | **최대 버전** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| 작성기 | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

자세한 요구 사항은 Adobe Commerce 를 검토하십시오 [시스템 요구 사항](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) 를 개발자 설명서에서 참조하십시오.

## 스토어 지원 앱 요구 사항

스토어 픽업 주문을 관리하는 종단 간 프로세스는 모바일 장치에 설치된 스토어 지원 앱을 통해 관리됩니다. 소매업체 또는 개인 스마트폰을 사용하는 매장 직원이 제공하는 이러한 장치는 다음 요구 사항을 충족해야 합니다.

**최소 운영 체제 요구 사항**

- Android 6
- iOS 12

**최소 하드웨어 요구 사항**

- 1GB RAM
- 600MB의 사용 가능한 디스크 공간

## 비즈니스 요구 사항

Store Fulfillment 솔루션을 구현하려면 다음과 같은 최소 기준을 충족해야 합니다.

- 미국 기반 기업만

- B2C 소매업자, D2C를 판매하는 CPG 제조업체 또는 D2C를 판매하거나 소기업에 판매하는 유통업체

- 하나 이상의 물리적 스토어 또는 창고

- Adobe Commerce용 Inventory management(MSI라고도 함)로 제품 인벤토리 관리

- 가맹점 인벤토리 신디케이션 기능

- Store Fulfillment 솔루션을 지원하는 모든 위치에 Wi-Fi 가용성을 저장합니다. 3Mbps 최소 인터넷 속도

- 스토어 및 창고 파트너는 개인 또는 상인이 제공하는 이동 중에 iOS 또는 Android 모바일 장치에 액세스할 수 있습니다

- Store Fulfillment 솔루션을 사용하여 관리하는 제품에는 SKU 또는 UPC 제품 코드를 포함하는 제품 속성이 있어야 합니다
