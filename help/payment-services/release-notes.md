---
title: '"[!DNL Payment Services] 릴리스 정보"'
description: 모든 정보에 대해서는 릴리스 노트 를 검토하십시오 [!DNL Payment Services] 릴리스.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 1%

---

# 릴리스 정보

이러한 릴리스 노트는 [!DNL Payment Services] 다음을 포함합니다.

![새로 만들기](../assets/new.svg) 새로운 기능
![해결된 문제](../assets/fix.svg) 수정 사항 및 향상된 기능
![알려진 문제](../assets/bug.svg) 알려진 문제

자세한 내용은 [예정된 릴리스](https://devdocs.magento.com/release/) 릴리스 일정 및 지원에 대해 알아보십시오.

자세한 내용은 [사용 가능](https://devdocs.magento.com/release/availability.html) 개발자 설명서에서 제품 호환성에 대해 알아봅니다.

## v1.1.0

![새로 만들기](../assets/new.svg)<!-- Issue PAY-2127 --> 일반 공급 릴리스—[!DNL Payment Services] is now [호환 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 버전 2.4.0~2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![새로 만들기](../assets/new.svg)<!-- Issue PAY-2682 --> 다음 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 현재 캐나다 상인들이 이용할 수 있습니다. 상인은 다음 중 하나에서 결제 구성을 볼 수 있습니다 [프랑스어](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) 또는 [영어](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![새로 만들기](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] 지원 [캐나다 달러(CAD)](overview.md#accepted-credit-cards-and-currencies) 신용 카드 및 PayPal 거래의 경우

![새로 만들기](../assets/new.svg)<!-- Issue PAY-2680 --> 상인은 다음을 수행할 수 있습니다 [온보드 [!DNL Payment Services]](onboard.md) 확장 프로그램(영어 또는 프랑스어)을 사용할 수 있습니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-2678 --> 상인들은 이제 두 가지 모두 재무 보고서를 볼 수 있습니다 [주문 결제 상태](order-payment-status.md) 및 [페이아웃 보고서](payouts.md): 캐나다 달러(CAD)입니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] 는 이제 와 호환됩니다. [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-3017 --> 여러 스토어가 있는 적절한 경고를 표시하도록 샌드박스 모드 경고를 개선했습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2742 --> 이제 저장소 보기 수준에서 벤 등의 사용 가능한 결제 방법을 활성화하고 비활성화할 수 있습니다. 이전에는 웹 사이트당 결제 방법을 구성할 수만 있었습니다.

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2277 --> 이제 선택적으로 사용할 수 있습니다 [개별 PayPal 스마트 단추 활성화 또는 비활성화](settings.md#paypal-smart-buttons).

![해결된 문제](../assets/fix.svg)<!-- Issue PAY-2561 --> 이전에 제거한 제품이 _검토 순서_ 페이지.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2842 --> 신용 카드 거래 테스트 [PayPal에서 실패할 수 있음](https://support.magento.com/hc/en-us/articles/5201041963917) 샌드박스 환경에서 지급을 처리할 때.

## v1.0.0

![새로 만들기](../assets/new.svg)<!-- Issue PAY-2127 --> 일반 공급 릴리스—[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) 는 이제 와 호환됩니다. [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 버전 2.4.0에서 2.4.3-p1

![새로 만들기](../assets/new.svg)<!-- Issue PAY-124 --> 다음 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 다음 중 한 방법으로 설치할 수 있습니다. [[!DNL Adobe Commerce] 클라우드 인프라](install.md#adobe-commerce-on-cloud-infrastructure) 또는 [온-프레미스](install.md#on-premises) 인스턴스. 이러한 메서드를 사용하려면 명령줄 인터페이스를 사용해야 합니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] 은 [샌드박스 계정](sandbox.md) 판매자는 테스트 모드에서 확장을 평가할 수 있습니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-666 --> 상인은 다음을 수행할 수 있습니다 [결제 서비스 구성](settings.md) 활용 등과 같은 기본 지급 동작으로 확장 [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) 샌드박스 또는 프로덕션 환경 간 전환.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-780 --> 쇼핑하시는 분들께서 체크아웃하실 수 있습니다 [!DNL Payment Services] 또는 [수동 주문 생성](create-order.md).

![새로 만들기](../assets/new.svg)<!-- Issue PAY-1856 --> 을 통해 포괄적인 보고 [주문 결제 상태](order-payment-status.md) 및 [페이아웃 보고서](payouts.md)에 대해 를 사용할 수 있습니다. [!DNL Payment Services] 가게 주문과 관련된 지불을 명확하게 보기 위해.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] 모든 매상에 맞게 총 처리 볼륨을 기반으로 유연한 계층형 가격을 지원합니다.

![새로 만들기](../assets/new.svg)<!-- Issue PAY-1443 --> 쉽게 할 수 있습니다 [모양 및 느낌 사용자 지정](payments-options.md) 결제 서비스 확장을 위한 PayPal 스마트 버튼 및 신용 카드 필드

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2473 --> 사용 [잘못된 작성기 키](https://support.magento.com/hc/en-us/articles/4406603542541) 확장을 설치하는 동안 사용자가 [인증](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 올바른 `MAGEID`.

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] 보고서 [즉시 동기화되지 않음](https://support.magento.com/hc/en-us/articles/4406114741517).

![알려진 문제](../assets/bug.svg)<!-- Issue PAY-2475 --> 사용자 [PayPal 샌드박스 계정](https://support.magento.com/hc/en-us/articles/4406954952461) 대상 [!DNL Payment Services] 온보딩 중에 해당 계정을 만든 경우에는 을 확인할 수 없습니다.
