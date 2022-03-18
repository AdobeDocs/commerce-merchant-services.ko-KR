---
title: 보안 및 규정 준수
description: 사이트에 대한 보안 및 규정 준수 요구 사항을 검토합니다.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# 보안 및 규정 준수

보안은 [!DNL Payment Services] 그리고 PCI(Private 또는 Payment Card Industry) 규정 정보가 사용자의 [!DNL Payment Services].

## 상거래 보안

Adobe Commerce 및 Magento Open Source에는 몇 가지 보안 기능이 지원됩니다.

자세한 내용은 [보안](https://docs.magento.com/user-guide/stores/security.html)핵심 사용 안내서의 {target=&quot;_blank&quot;} 를 사용하여 보안 모범 사례를 검토하고, 관리 세션 및 자격 증명을 관리하고, CAPTCHA를 구현하고, 웹 사이트 제한을 관리하는 방법을 알아봅니다.

## PCI 규정 준수

PCI(Payment Card Industry)는 인터넷을 통해 신용카드로 결제를 받는 기업에 대한 일련의 요구 사항을 제정했다. 안전한 환경을 유지하는 것 외에도, 고객 카드 정보를 처리하는 상인들은 몇 가지 표준 지침을 따라야 합니다.

자세한 내용은 [PCI 규정 준수 지침](https://docs.magento.com/user-guide/stores/compliance-pci.html)자세한 내용은 {target=&quot;_blank&quot;} 를 참조하십시오.

상인은 다음을 완료할 수 있습니다. [자체 평가 질문(SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment)카드홀더 데이터의 보안을 평가하는 자체 유효성 검사 도구인 {target=&quot;_blank&quot;}.

### 신용 카드 필드

신용 카드 필드를 사용하면 PCI 규정 데이터가 서비스 전체에 전달되지 않습니다. 데이터를 저장하거나 유지 관리할 필요가 없으므로 PCI 규정 준수 문제를 크게 줄일 수 있습니다.

### PayPal 스마트 단추

PayPal 스마트 버튼을 사용하면 서비스 전반에 PCI 규정 데이터가 전달되지 않습니다. 데이터를 저장하거나 유지 관리할 필요가 없으므로 PCI 규정 준수 문제를 크게 줄일 수 있습니다.

보안상의 이유로 PayPal은 체크아웃 중에 청구 주소를 전달하지 않습니다. 국가, 이메일 및 이름은 사용되는 유일한 청구 정보입니다. PayPal에 연락하고 검증 프로세스를 완료하여 사이트의 PayPal 체크아웃을 사용하여 전체 청구 주소를 반환할 수 있습니다(선택적).

또한 PayPal은 사기 행위를 방지하기 위해 기계 학습을 사용하는 통합된 사기 보호 기능도 제공합니다. PayPal을 참조하십시오 [판매자 보호 설명서](https://www.paypal.com/us/webapps/mpp/security/seller-protection) 추가 정보.
