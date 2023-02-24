---
title: 사용자 세션 라이프타임
description: 관리자는 [!DNL Quick Checkout] 확장.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# 사용자 세션 라이프타임

쇼퍼 세션의 수명은 Adobe Commerce 관리자에서 구성할 수 있는 몇 가지 요인에 의해 결정됩니다. 자세한 내용은 [쿠키 라이프타임 구성](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} 추가 정보.

구성된 쿠키 라이프타임은 [!DNL Quick Checkout] if:

1. 비활성 상태로 인해 쇼핑객이 Adobe Commerce에서 로그아웃됩니다.
1. 다음 [!DNL Bolt] 세션이 만료됩니다.

쇼핑객이 주문을 하면 [!DNL Bolt] 세션이 만료되면 주문이 성공적으로 실행되지만 사용자가 두 네트워크에서 로그아웃됩니다.

체크아웃에 성공한 후에도 사용자가 여전히 활성 상태인 경우, Adobe Commerce과 [!DNL Bolt].
