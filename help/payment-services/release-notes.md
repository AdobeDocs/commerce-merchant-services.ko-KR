---
title: '"[!DNL Payment Services] 릴리스 정보"'
description: 모든 정보에 대해서는 릴리스 노트 를 검토하십시오 [!DNL Payment Services] 릴리스.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 1%

---

# 릴리스 정보

이러한 릴리스 노트는 [!DNL Payment Services] 다음을 포함합니다.

![새로 만들기](../assets/new.svg) 새로운 기능
![해결된 문제](../assets/fix.svg) 수정 사항 및 향상된 기능
![알려진 문제](../assets/bug.svg) 알려진 문제

## v1.0.0

![새로 만들기](../assets/new.svg)<!-- Issue PAY-2127 --> 일반 공급 릴리스. [결제 서비스](https://marketplace.magento.com/magento-payment-services.html) 는 이제 Adobe Commerce 및 Magento Open Source 버전 2.4.0에서 2.4.3-p1과 호환됩니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-124 --> 다음 [!DNL Payment Services] Adobe Commerce 및 Magento Open Source용 확장은 [Adobe Commerce on cloud 인프라](install.md#magento-commerce-cloud) 또는 [온-프레미스](install.md#on-premises) 인스턴스. 이러한 메서드를 사용하려면 명령줄 인터페이스를 사용해야 합니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 은 [샌드박스 계정](onboard.md#enable-sandbox-testing) 판매자는 테스트 모드에서 확장을 평가할 수 있습니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-666 --> 상인은 다음을 수행할 수 있습니다 [결제 서비스 구성](configure-admin.md) 기본 결제 행동을 사용하는 확장(예: 인증 캡처와 함께 샌드박스 또는 프로덕션 환경 간 전환)을 참조하십시오.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-780 --> 쇼핑객은 다음 사항을 확인할 수 있습니다 [!DNL Payment Services] 아니면 전화로 주문을 받아 [전체 주문 만들기](create-order.md) 관리자 섹션에 있는 마지막 항목이 될 필요가 없습니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] 상점 주문과 지불을 명확하게 파악할 수 있도록 가맹점 포괄적인 보고를 제공합니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 은 모든 상인에 적용되는 TPV를 기반으로 계층화된 가격을 지원합니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-1443 --> PayPal 단추와 CC 필드의 모양 및 느낌을 사용자 지정할 수 있습니다. [결제 서비스](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) 확장.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2473 --> 사용 [잘못된 작성기 키](https://support.magento.com/hc/en-us/articles/4406603542541) 확장을 설치하는 동안 사용자는 [인증](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 정확하 `MAGEID`.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [보고서](https://support.magento.com/hc/en-us/articles/4406114741517) 지급 및 주문 지급 상태에 대해서는 즉시 동기화되지 않을 수 있습니다.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2475 --> [PayPal 샌드박스 계정](https://support.magento.com/hc/en-us/articles/4406954952461) 대상 [!DNL Payment Services] 확인할 수 없습니다.
