---
title: 온보드 [!DNL Payment Services]
description: 인스턴스 연결 [!DNL Payment Services] 몇 가지 온보딩 단계를 완료하여 기능을 사용할 수 있습니다.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# 온보드 [!DNL Payment Services]

를 사용하려면 [!DNL Payment Services] Adobe Commerce 및 Magento Open Source의 경우 인스턴스에 결제 기능을 연결하기 위해 몇 가지 온보딩 단계를 완료해야 합니다.

## 온보딩 흐름

![온보딩 흐름](assets/onboarding-diagram.svg)

이 온보딩 흐름 다이어그램은 온보딩에 대한 일반 프로세스를 보여줍니다 [!DNL Payment Services].

샌드박스 또는 라이브 지급에 대한 온보딩을 완료하면 Financial Reporting에서 액세스할 수 있습니다 [!DNL Payment Services] 관리자.

샌드박스와 Live Payments가 모두 온보딩되고 활성화되면 [!DNL Payment Services] 집.

## 전제 조건

를 사용하려면 [!DNL Payment Services]를 채울 때는 인스턴스에 다음 사항을 사용할 수 있어야 합니다.

* 서비스 커넥터 모듈
* 서비스 ID 모듈
* API 키

서비스 커넥터 및 서비스 ID 모듈은 [설치 [!DNL Payment Services]](install.md). 설치가 완료되면 구성 설정에서 새 섹션을 볼 수 있습니다(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)를 확장할 때&#x200B;**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

API 키를 만들거나 액세스하는 방법에 대해 알아보려면 [API 자격 증명](#obtain-api-credentials).

## 온보딩 단계

1. [설치 [!DNL Payment Services] 확장](install.md#get-payment-services).
1. [API 자격 증명 가져오기](connect.md#obtain-api-credentials).
1. [인스턴스 연결](connect.md#configure-commerce-services) Commerce Services로 이동합니다. 이 연결은 상거래 인스턴스당 한 번만 완료해야 합니다.
1. [샌드박스 서비스 설정](sandbox.md#enable-sandbox-testing) (또는, [라이브 지급 활성화](sandbox.md#enable-live-payments) 테스트 PayPal 결제 처리 계정으로 다른 환경에서 기능을 테스트한 경우
1. [설정 [!DNL Payment Services] 결제 방법으로](production.md#set-payment-services-as-payment-method)샌드박스 모드에서 테스트 지급 처리를 시작합니다.
1. [지급 권한 요청](production.md#request-payments-entitlement-from-adobe) 로 설정되어야 합니다.
1. [Complete Merchant 온보딩](production.md#complete-merchant-onboarding) 전자 상거래 웹 사이트에 대해 라이브 지급을 사용하도록 설정하려면 다음을 수행하십시오.
1. [다운로드 [!DNL Payment Services] Merchant ID](production.md#configure-pricing-tier) 올바른 가격 책정 계층을 구성하려면 Sales 로 전달하십시오.
1. [활성화 [!DNL Payment Services] 라이브 모드에서](production.md#enable-live-payments) Live Payments 처리를 시작합니다.
1. 지급 테스트, 두 가지 모두 [샌드박스](sandbox.md#test-in-sandbox-environment) 및 [production](production.md#test-in-production) 환경.

>[!NOTE]
>
>관리자(3단계)에서 상거래 서비스를 구성하지 않으면 샌드박스 또는 라이브 지급을 설정할 수 없습니다.

## 문제 해결

* [문제 해결 [!DNL Payment Services] 설치](https://support.magento.com/hc/en-us/articles/4406603542541)
* [PayPal 샌드박스 계정이 확인되지 않음](https://support.magento.com/hc/en-us/articles/4406954952461)
* [지연 [!DNL Payment Services] 보고서 데이터](https://support.magento.com/hc/en-us/articles/4406114741517)
