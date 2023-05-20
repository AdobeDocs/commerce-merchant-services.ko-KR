---
title: "[!DNL Quick Checkout] Adobe Commerce 개발자 정보용"
description: "[!DNL Quick Checkout] developer information."
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] 개발자 정보

이 항목에는 Adobe Commerce 및 [!DNL Magento Open Source] 코드 및 을(를) 사용하여 [!DNL Quick Checkout] 확장명.

## 확장 지점

확장 지점을 사용하여 [!DNL Quick Checkout].

확장 지점을 사용하면 애플리케이션 코드의 핵심 구성 요소를 실제로 변경하지 않고 사용자 지정할 수 있습니다.

## 배송 세부 사항 단계

확장 지점을 사용하여 로 로그인한 후 자동화된 단계 탐색을 사용자 정의할 수 있습니다. [!DNL Bolt].

쇼핑객이 다음으로 로그인하면 [!DNL Bolt]를 클릭하면 유효한 모든 정보가 미리 채워지고 결제 세부 사항 단계로 리디렉션되어 주문됩니다. 다음을 참조하십시오. [체크아웃 흐름](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) 항목 을 참조하십시오.

이 확장 포인트를 사용하면 결제 단계로 이동할 수 없으며, 구매 고객이 배송 단계에서 추가 작업을 수행해야 하는 확장이 있는 경우 유용할 수 있습니다. mixin에서 확장 포인트를 사용하는 방법에 대해서는 아래 예를 참조하십시오.

1. 에서 새 mixin 등록 `require-config.js` 파일 위치: `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. 에서 모델 확장 `can-navigate-to-payment.js` 파일 위치: `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> 배송 세부 사항 단계에 머무르고자 하는 독일(DE)의 쇼핑객에 대한 예입니다.

확인 [[!DNL Bolt] 개발자 도움말](https://help.bolt.com/developers/) 에 대한 추가 정보를 위해 [!DNL Bolt] 개발자용.
