---
title: 저장소 이행 구성 개요
description: Store Fulfillment 솔루션에서 제공하는 확장 이행 기능을 사용자 지정하는 데 사용할 수 있는 관리 구성 설정 유형에 대해 알아보고 구성을 완료하기 위한 지침에 연결합니다.
role: User, Admin
level: Intermediate
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# 저장소 이행 구성 개요

Adobe Commerce 관리에서 Walmart Commerce Technologies의 Store Fulfillment Services 구성 설정은 유형별로 분류됩니다.

**유형별 이행 구성 설정 저장**

| **유형** | **설명** | **API 구성 가능** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [일반 구성](enable-general.md) | Store Fulfillment 솔루션, 활성 기능 및 자격 증명에 대해 설정된 일반 통합으로 이행 서비스에 연결할 수 있습니다. | 아니요 |
| [영업 전자 메일 구성](sales-emails.md) | 체크인 프로세스 중에 전송된 고객 알림에 대해 추가 전자 메일 템플릿을 설정합니다. | 아니요 |
| [Merchant Store 구성](merchant-store-configuration.md) | Merchant Store로 향상된 Inventory management 소스를 설정합니다. | 예 |
| [제품 스톡 관리](product-stock.md) | 고객에게 제공되는 머천트 스톡 메시지 및 기능을 구성합니다. | 예 |
| [Inventory management 소스 전송](inventory-stock-transfer.md) | 새 재고를 설정하고, 기본 재고에서 재고를 이전합니다. | 예 |
| [다중 웹 사이트/범위 구성](multi-site-and-scope-config.md) | 여러 웹 사이트/스토어 범위에 대한 주식 및 전달 방법을 구성합니다. | 아니요 |
| [백그라운드 프로세스 시스템 구성](background-processes.md) | 데이터를 이행 서비스와 동기화하는 데 사용되는 백그라운드 프로세스에 대한 일정을 구성합니다. | 아니요 |
| [저장소 위치 및 매핑 설정](store-location-map-provider-setup.md) | 거리 공급자를 사용하여 소매점을 검색하고 이 정보를 SLS 맵에 표시할 수 있습니다 | 예 |
| [체크인 Experience Setup](check-in-experience-setup.md) | 체크 인 프로세스 중에 사용할 수 있는 자동차 색상 및 자동차 제조 옵션을 구성합니다 | 예 |
| [사용자 설정](user-setup.md) | Store Assist 앱을 사용하는 Store Associate의 사용자 계정, 역할 및 권한을 관리합니다. 범위. | 예 |
| [앱 설정](app-setup.md) | 온보딩 프로세스를 완료하는 데 필요한 스토어 지원 앱에 사용 가능한 구성을 검토합니다. Adobe Commerce 관리에서 이러한 설정을 구성할 수 없습니다. | 예 |

## 구성 참조 사용

에서 유형 이름을 선택하여 각 설정 유형에 대한 구성 참조를 확인합니다. _유형별 이행 구성 설정 저장_ 테이블.

각 유형에 대한 구성 참조에서 구성 세부 사항은 다음 열 헤더가 있는 테이블에 표시됩니다.

- **필드** 는 구성할 필드의 이름을 나타냅니다

- **설명** 에서는 필드의 목적 및 동작에 대한 중요한 세부 사항을 제공합니다

- **범위** 설정에 대한 Adobe Commerce 구성 범위(전역, 웹 사이트, 스토어)를 나타냅니다.

- **필수 여부** 값은 필드에 값을 설정해야 하는지 여부를 나타냅니다.

기술 참조의 경우 각 필드에 대한 내부 구성 경로를 찾을 수도 있습니다.
