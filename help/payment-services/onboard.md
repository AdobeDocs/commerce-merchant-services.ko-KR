---
title: 온보드 [!DNL Payment Services]
description: 인스턴스 연결 [!DNL Payment Services] 몇 가지 온보딩 단계를 완료하여 기능을 제공합니다.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# 온보드 [!DNL Payment Services]

을(를) 시작하려면 [!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source], 인스턴스를 결제 기능과 연결하기 위한 몇 가지 온보딩 단계를 완료해야 합니다.

## 온보딩 플로우

![온보딩 플로우](assets/onboarding-diagram.svg)

이 온보딩 흐름 다이어그램은 온보딩에 대한 일반적인 프로세스를 보여 줍니다 [!DNL Payment Services].

샌드박스 또는 라이브 결제에 대한 온보딩을 완료한 후에서 재무 보고에 액세스할 수 있습니다. [!DNL Payment Services] 관리에서.

샌드박스와 라이브 결제가 모두 온보딩되고 활성화된 경우 [!DNL Payment Services] 집.

## 전제 조건

를 사용하려면 [!DNL Payment Services]를 사용하려면 인스턴스에 사용할 수 있는 다음 항목이 있어야 합니다.

* 서비스 커넥터 모듈
* 서비스 ID 모듈
* API 키

Services Connector 및 Services ID 모듈은 [설치 [!DNL Payment Services]](install.md). 설치가 완료되면 구성 설정에 새 섹션이 표시됩니다(**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**)을 클릭하여 페이지를 확장합니다.**[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

API 키를 만들거나 액세스하는 방법에 대한 자세한 내용은 [API 자격 증명](#obtain-api-credentials).

## 온보딩 단계

1. [설치 [!DNL Payment Services] 확장](install.md#get-payment-services).
1. [API 자격 증명 가져오기](connect.md#obtain-api-credentials).
1. [인스턴스 연결](connect.md#configure-commerce-services) 상거래 서비스로 이동합니다. 이 연결은 상거래 인스턴스당 한 번만 완료되어야 합니다.
1. [샌드박스 서비스 설정](sandbox.md#enable-sandbox-testing) (또는, 다음으로 진행) [라이브 결제 활성화](sandbox.md#enable-live-payments) 다른 환경에서 PayPal 결제 처리 계정을 사용하여 기능을 테스트한 경우.
1. [설정 [!DNL Payment Services] 결제 수단으로 사용](production.md#set-payment-services-as-payment-method), 샌드박스 모드에서 테스트 결제 처리를 시작합니다.
1. [지급 권한 요청](production.md#request-payments-entitlement-from-adobe) 라이브 온보딩을 활성화하십시오.
1. [완전한 판매자 온보딩](production.md#complete-merchant-onboarding) 상거래 웹 사이트에 대해 실시간 결제를 활성화하려면.
1. [가져오기 [!DNL Payment Services] 판매자 ID](production.md#configure-pricing-tier) 올바른 가격 책정 계층을 구성하려면 Sales에 전달하십시오.
1. [사용 [!DNL Payment Services] 라이브 모드에서](production.md#enable-live-payments) 을 눌러 라이브 결제 처리를 시작합니다.
1. 지급 테스트(두 가지 모두) [샌드박스](sandbox.md#test-in-sandbox-environment) 및 [production](production.md#test-in-production) 환경.

>[!NOTE]
>
>관리자(3단계)에서 상거래 서비스를 구성하지 않으면 샌드박스 또는 라이브 결제를 설정할 수 없습니다.

## 문제 해결

* [문제 해결 [!DNL Payment Services] 설치](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [PayPal 샌드박스 계정이 확인되지 않음](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [지연됨 [!DNL Payment Services] 보고서 데이터](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [샌드박스 환경에서 결제를 처리할 때 PayPal로 신용 카드 테스트 실패](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
