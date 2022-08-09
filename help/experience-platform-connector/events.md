---
title: 이벤트
description: 데이터를 캡처하는 이벤트를 알아보고 전체 스키마 정의를 확인합니다.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Experience Platform 커넥터 이벤트

다음은 Experience Platform 커넥터 확장을 설치할 때 사용할 수 있는 상거래 이벤트 목록입니다. 이러한 이벤트가 수집하는 데이터는 Adobe Experience Platform Edge로 전송됩니다. 만들 수도 있습니다 [사용자 지정 이벤트](custom-events.md) 기본적으로 제공되지 않은 추가 데이터를 수집하기 위해

전체 스키마 정의를 보려면 이벤트 이름을 클릭합니다.

| Event | 유형 |
|---|---|
| [장바구니에 추가](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | 상점 |
| [장바구니 보기](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | 상점 |
| [페이지 보기](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | 상점 |
| [제품 보기](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | 상점 |
| [체크아웃 시작](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | 상점 |
| [체크아웃 완료](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | 상점 |
| [로그인](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | 프로필 |
| [로그아웃](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | 프로필 |
| [계정 만들기](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | 프로필 |
| [계정 편집](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | 프로필 |
| [검색 요청이 전송됨](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts) | 검색 |
| [검색 응답 수신](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts) | 검색 |

>[!NOTE]
>
> 다음 `Sign In`, `Sign Out`, `Create Account`, 및 `Update Account` 특정 작업이 시도되면 이벤트가 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.
