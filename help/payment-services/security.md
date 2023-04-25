---
title: 보안 및 규정 준수
description: 사이트에 대한 보안 및 규정 준수 요구 사항을 검토합니다.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: bfce1cb702d634647022a92669d704dd82fe41e6
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---

# 보안 및 규정 준수

보안은 [!DNL Payment Services] 그리고 PCI(Private 또는 Payment Card Industry) 규정 정보가 사용자의 [!DNL Payment Services].

## 상거래 보안

[!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 여러 보안 기능에 대한 지원을 포함합니다.

자세한 내용은 [보안](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} 핵심 사용 안내서에서 보안 모범 사례를 검토하고, 관리 세션 및 자격 증명을 관리하고, CAPTCHA를 구현하고, 웹 사이트 제한 사항을 관리하는 방법을 알아봅니다.

## PCI 규정 준수

PCI(Payment Card Industry)는 인터넷을 통해 신용카드로 결제를 받는 기업에 대한 일련의 요구 사항을 제정했다. 안전한 환경을 유지하는 것 외에도, 고객 카드 정보를 처리하는 상인들은 몇 가지 표준 지침을 따라야 합니다.

자세한 내용은 [PCI 규정 준수 지침](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} 추가 정보.

상인은 다음을 완료할 수 있습니다. [자체 평가 질문(SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}: 카드 소유자 데이터의 보안을 평가하기 위한 자체 유효성 검사 도구입니다.

### 신용 카드 필드

신용 카드 필드를 사용하면 PCI 규정 데이터가 서비스 전체에 전달되지 않습니다. 데이터를 저장하거나 유지 관리할 필요가 없으므로 PCI 규정 준수 문제를 크게 줄일 수 있습니다.

### 3DS

PCI 3D Secure(3DS)는 온라인 신용 카드 구매 시 신용 카드 발급자와 구매자 인증을 사용할 수 있도록 합니다. 이러한 추가 보안 계층은 온라인 사기를 방지하는 데 도움이 되며, EU(유럽 연합) 규정 준수 규정의 일부로 필요합니다.

[!UICONTROL Payment Services] 에서는 상인이 EU 규정을 준수하고, 고객과 상인이 자신의 스토어에서 사기 행위를 하지 못하도록 할 수 있는 3DS 기능을 제공합니다.

3DS 규정 준수를 요구하는 EU 또는 영국 내 판매자인 경우 3DS를 수동으로 설정해야 합니다. `Off` 기본적으로 [설정](settings.md#credit-card-fields).

>[!NOTE]
>
>3DS 요구 사항은 비즈니스 및 카드 소지자의 은행이 있는 [유럽 경제 지역](https://www.efta.int/eea) (EEA) 및 영국. 미국 상인들은 3DS를 필요로 하지 않지만, 원하는 경우 거래를 가능하게 할 수 있습니다.

상거래/매장 직원이 구매자에 대해 수행한 주문은 3DS 규정 준수 조치로 구성되지 않습니다.

자세한 내용은 [설정의 3DS](settings.md#3ds) 추가 정보.

### 카드 소산

쇼핑객 [자격 증명 카드 정보 — 또는 &quot;저장&quot;](vaulting.md) 상점에서 향후 구매의 경우, 최소 신용 카드 정보는 구매자와 공유됩니다(최근 4자리, 카드 만료 날짜 및 카드 브랜드). 신용 카드 정보는 결제 공급자와 함께 저장됩니다. 카드가 만료되거나 더 이상 정보를 저장할 필요가 없는 경우, 결제 공급자가 정보를 더 이상 저장하지 않도록 해당 토큰을 삭제할 수 있습니다.

자세한 내용은 [신용 카드 저장](vaulting.md) 추가 정보.

### PayPal 스마트 단추

PayPal 스마트 버튼을 사용하면 서비스 전반에 PCI 규정 데이터가 전달되지 않습니다. 데이터를 저장하거나 유지 관리할 필요가 없으므로 PCI 규정 준수 문제를 크게 줄일 수 있습니다.

보안상의 이유로 PayPal은 체크아웃 중에 청구 주소를 전달하지 않습니다. 국가, 이메일 및 이름은 사용되는 유일한 청구 정보입니다. PayPal에 연락하고 검증 프로세스를 완료하여 사이트의 PayPal 체크아웃을 사용하여 전체 청구 주소를 반환할 수 있습니다(선택적).

또한 PayPal은 사기 행위를 방지하기 위해 기계 학습을 사용하는 통합된 사기 보호 기능도 제공합니다. PayPal을 참조하십시오 [판매자 보호 설명서](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 추가 정보.
