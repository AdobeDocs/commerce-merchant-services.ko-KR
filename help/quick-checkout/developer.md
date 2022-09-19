---
title: "[!DNL Quick Checkout] Adobe Commerce 개발자 정보용"
description: "[!DNL Quick Checkout] 개발자 정보."
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] 개발자 정보

이 주제에서는 Adobe Commerce과 긴밀하게 협력하는 개발자를 위한 정보를 제공합니다. [!DNL Magento Open Source] 코드를 작성하고 [!DNL Quick Checkout] 확장.

## 확장 지점

확장 포인트를 사용하여 사용자 지정 [!DNL Quick Checkout].

확장 지점을 사용하면 애플리케이션 코드에서 핵심 구성 요소를 실제로 변경하지 않고 사용자 지정을 수행할 수 있습니다.

## 배송 세부 정보 단계

확장 포인트는 [!DNL Bolt].

쇼핑객이 [!DNL Bolt]를 입력하면 모든 유효한 정보가 미리 입력되어 주문을 위한 결제 세부 사항 단계로 리디렉션됩니다. 자세한 내용은 [체크아웃 흐름](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) 주제 를 참조하십시오.

이 확장 지점을 사용하면 결제 단계로 이동하는 것을 방지할 수 있으며, 쇼핑객이 운송 단계에서 추가 작업을 수행해야 하는 확장이 있는 경우 유용할 수 있습니다. mixin에서 확장 포인트를 사용할 수 있는 방법에 대한 아래 예를 참조하십시오.

1. 에서 새 mixin 등록 `require-config.js` 에 있는 파일 `app/code/Vendor/ModuleName/view/frontend/`.

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

1. 에서 모델 확장 `can-navigate-to-payment.js` 에 있는 파일 `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

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
> 이는 독일(DE)에서 쇼핑하는 사람이 배송 세부 사항 단계를 계속 유지하려는 경우의 예입니다.

확인 [[!DNL Bolt] 개발자 도움말](https://help.bolt.com/developers/) 추가 정보 [!DNL Bolt] 개발자용.
