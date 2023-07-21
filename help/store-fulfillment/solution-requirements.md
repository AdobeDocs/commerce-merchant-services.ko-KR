---
title: 저장소 이행 요구 사항
description: 프로비저닝 및 온보딩 요구 사항 [!DNL Store Fulfillment solution].
role: Leader, Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Adobe Commerce에 대한 스토어 이행 요구 사항

다음 섹션에서는 Adobe Commerce용 스토어 이행 솔루션 설치 및 활성화를 위한 기술 및 비즈니스 요구 사항에 대해 자세히 설명합니다.

## 플랫폼 및 소프트웨어 버전 요구 사항

다음 [!DNL Store Fulfillment] 솔루션은 다음 플랫폼에서 Adobe Commerce 고객에게 제공됩니다.

- ECE(클라우드 인프라)의 Adobe Commerce
- Adobe Commerce 온-프레미스 (EE)

Store Fulfillment 솔루션은 *소프트웨어 호환성* 테이블.

**소프트웨어 호환성**

| **소프트웨어** | **최소 버전** | **최대 버전** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| 작성기 | 1.x | 2.x |
| 마리아DB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

자세한 요구 사항은 Adobe Commerce 를 검토하십시오 [시스템 요구 사항](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) 다음에서 *Adobe Commerce 설치 안내서*.

## 스토어 지원 앱 요구 사항

스토어 픽업 주문을 관리하는 엔드 투 엔드 프로세스는 모바일 장치에 설치된 스토어 지원 앱을 통해 관리됩니다. 소매점이나 매장 직원이 개인 스마트폰을 사용하여 제공하는 이러한 기기는 다음 요구 사항을 충족해야 합니다.

**최소 운영 체제 요구 사항**

- Android 6
- iOS 12

**최소 하드웨어 요구 사항**

- 1GB RAM
- 사용 가능한 디스크 공간 600MB

## 비즈니스 요구 사항

스토어 이행 솔루션을 구현하려면 기업이 다음 최소 기준을 충족해야 합니다.

- 미국 기업 전용

- B2C(Business to Consumer) 판매업체, D2C(Consumer Packaged Goods) 제조업체 또는 소비자 또는 소기업에 직접 판매하는 유통업체

- 하나 이상의 실제 저장소 또는 웨어하우스

- Adobe Commerce용 Inventory management(MSI)를 사용하여 제품 인벤토리 관리

- 판매자 인벤토리를 신디케이트하는 기능

- Store Fulfillment 솔루션을 지원하는 모든 위치에 Wi-Fi 가용성 저장: 최소 3Mbps 인터넷 속도

- 상점 및 웨어하우스 제휴자는 교대 기간 동안 개인 또는 판매자가 제공하는 iOS 또는 Android 모바일 장치에 액세스할 수 있습니다

- 스토어 이행 솔루션을 사용하여 관리되는 제품에는 SKU 또는 UPC 제품 코드를 포함하는 제품 속성이 있어야 합니다
