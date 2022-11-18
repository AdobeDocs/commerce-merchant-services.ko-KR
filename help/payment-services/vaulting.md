---
title: 신용 카드 저장
description: 구매자는 향후 구매에 대한 신용 카드 세부 사항을 저장(저장)할 수 있습니다.
source-git-commit: c993a2afe5b4da478ab57cbb391bb524d83c3d1a
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 0%

---

# 신용 카드 저장

일회성 고객을 신용 카드 볼팅(vaulting)을 통해 단골 고객으로 전환하십시오. 구매자는 체크아웃 중에 신용 카드 자격 증명을 저장하여 동일 머천트 계정에 나중에 구매하거나 다른 계정에 저장할 수 있습니다.

![나중에 사용할 수 있도록 신용 카드 저장](assets/save-card-for-later.png)

구매자는 저장된 토큰을 사용하여 저장된 신용 카드 정보로 향후 체크아웃을 완료합니다.

![나중에 구매할 때 저장된 자격 증명 사용](assets/use-stored-card.png)

저장된 신용카드를 쉽게 삭제할 수도 있습니다 [저장된 결제 방법](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) 내 계정에 있을 때

![내 계정에 저장된 결제 방법](assets/stored-payment-methods.png)

## 저장 활성화

결제 서비스에서 귀하의 스토어에 대해 신용 카드 소산을 활성화할 수 있습니다 [설정](settings.md#card-vaulting).

## 보안

최소한의 신용 카드 정보는 쇼핑객과 공유됩니다. 저장된 신용 카드의 마지막 4자리, 만료 날짜 및 브랜드만 표시됩니다. 신용 카드 정보는 결제 제공자와 함께 저장되어 만족할 수 있습니다 [PCI](security.md#PCI-compliance) 규정 준수 표준.
