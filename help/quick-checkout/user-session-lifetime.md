---
title: 사용자 세션 라이프타임
description: 관리자는 [!DNL Quick Checkout] 확장.
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# 사용자 세션 라이프타임

쇼퍼 세션의 수명은 Adobe Commerce 관리자에서 구성할 수 있는 몇 가지 요인에 의해 결정됩니다. 자세한 내용은 [쿠키 라이프타임 구성](https://docs.magento.com/user-guide/customers/customer-online-options.html)자세한 내용은 {target=_blank}.

구성된 쿠키 라이프타임은 [!DNL Quick Checkout] if:

1. 비활성 상태로 인해 쇼핑객이 Adobe Commerce에서 로그아웃됩니다.
1. 다음 [!DNL Bolt] 세션이 만료됩니다.

쇼핑객이 주문을 하면 [!DNL Bolt] 세션이 만료되면 주문이 성공적으로 실행되지만 사용자가 두 네트워크에서 로그아웃됩니다.

체크아웃에 성공한 후에도 사용자가 여전히 활성 상태인 경우, Adobe Commerce과 [!DNL Bolt].
