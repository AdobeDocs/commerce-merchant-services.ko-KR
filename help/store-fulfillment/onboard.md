---
title: 온보딩 개요
description: '"연결 [!DNL Commerce] 에 인스턴스 [!DNL Store Fulfillment Manager] 몇 가지 온보딩 단계를 완료하여 서비스를 제공합니다."'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 1%

---

# 온보딩 개요

Onboard Store Fulfillment에서 상거래 인스턴스에 확장을 설치하고 API 연결을 구성하여 제공합니다. 이러한 연결을 통해 상거래 인스턴스, 인벤토리 관리를 위한 타사 시스템 및 스토어 지원 앱 간에 통신과 데이터 동기화를 수행할 수 있습니다.

온보딩을 완료하면 상거래 관리자에서 솔루션을 구성하고 관리합니다

![[!DNL Store Fulfillment Service] 관리자 보기의 구성](assets/store-fulfillment-admin-home.png)

## 온보딩 개요

1. Adobe Commerce용 Store Fulfillment by Walmart Technologies 확장을 설치합니다.

1. 관리자에서 솔루션을 활성화하고 통합, 활성 기능을 위한 전체 일반 구성을 완료한 다음 온보딩 수집 양식을 작성하여 이행 서비스에 연결합니다.

1. 게재 방법을 구성합니다.

1. 소스를 물리적 저장소로 설정하고 카탈로그에 제품을 구성합니다.

1. 전자 메일 템플릿을 선택하고 구성하여 고객 커뮤니케이션을 관리하여 온라인 구입, 매장 내(BOPIS) 트랜잭션을 관리할 수 있습니다.

1. 스토어 지원 앱의 사용자 및 역할을 만듭니다.

1. 데이터를 이행 서비스에 동기화하도록 백그라운드 프로세스에 대한 일정을 구성합니다.

## 요구 사항

솔루션을 설치, 배포 및 사용하려면 다음 요구 사항을 충족해야 합니다.

* **상거래 계정 정보**-설치 중 [!DNL Channel Manager] 를 사용하려면 [상거래 계정](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. 에 대한 소유자 또는 관리자 액세스 권한이 있는 계정 ID 및 자격 증명이 필요합니다 [!DNL Adobe Commerce] 인스턴스.

* 대상 [!DNL Adobe Commerce] 클라우드 인프라 프로젝트에서 소프트웨어 설치 관리자는 클라우드 프로젝트에 대한 관리자 액세스 권한이 있어야 합니다. 자세한 내용은 [사용자 액세스 관리](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Store Fulfillment by Walmart Technologies 소프트웨어 아카이브(.zip 파일)에 액세스하여 Store Fulfillment 솔루션을 설치합니다**-온보딩 및 지원 프로세스 중에 고객 계정 담당자가 설치 파일에 대한 다운로드 액세스 권한을 제공합니다.

* **작성기 및 를 사용한 경험[!DNL Commerce CLI]**- 자세한 내용은 [일반 CLI 설치](https://devdocs.magento.com/extensions/install/)다음 도구를 사용하여 확장을 설치 및 관리하는 방법에 대한 자세한 내용은 target=&quot;_blank&quot;} 를 참조하십시오. [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 플랫폼.

* [!DNL Inventory Management] Adobe Commerce 및 Magento Open Source 확장

   Adobe Commerce 및 Magento Open Source 인스턴스에 Inventory management 확장이 설치 및 활성화되어 있어야 합니다. 일반적으로 이 확장은 Adobe Commerce 2.3.x 이상에서 기본적으로 설치 및 활성화됩니다. 자세한 내용은 [Inventory management 설치](https://devdocs.magento.com/extensions/inventory-management/) ( Adobe Commerce 개발자 설명서).

## 플랫폼 및 버전 요구 사항

다음 [!DNL Store Fulfillment] 솔루션은 다음 플랫폼에서 Adobe Commerce 고객이 사용할 수 있습니다.

* Adobe Commerce on cloud infrastructure(ECE)
* Adobe Commerce 온-프레미스(EE)

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

### 비즈니스 요구 사항

Store Fulfillment 솔루션을 구현하려면 다음과 같은 최소 기준을 충족해야 합니다.

* 미국 기반 기업만

* B2C 소매업자, D2C를 판매하는 CPG 제조업체 또는 D2C를 판매하는 유통업체 또는 소규모 기업에 판매하기

* 하나 이상의 물리적 스토어 또는 창고

* Adobe Commerce용 Inventory management(MSI)를 사용하여 제품 인벤토리 관리

* 가맹점 인벤토리 신디케이션 기능

* Store Fulfillment 솔루션을 지원하는 모든 위치에 Wi-Fi 가용성을 저장합니다.

* 스토어 및 창고 파트너는 개인 또는 상인이 제공하는 이동 중에 iOS 또는 Android 모바일 장치에 액세스할 수 있습니다

* Store Fulfillment 솔루션을 사용하여 관리하는 제품에는 SKU 또는 UPC 제품 코드를 포함하는 제품 속성이 있어야 합니다
