---
title: 사용 가능한 데이터
description: Financial Reporting 데이터를 사용하여 비상거래 시스템과 보고를 조정합니다.
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# 사용 가능한 데이터

일부 주문 및 페이아웃 데이터를 사용할 수 있으므로 외부 시스템 전반에서 Adobe Commerce 재무 보고를 조정할 수 있습니다.

## ERP 시스템과 조정

특정 주문과 연관된 증분 ID를 사용하여 Adobe이 아닌 ERP(Enterprise Resource Planning) 시스템과 Adobe Commerce Financial Reporting을 조정할 수 있습니다.

Payment Services가 PayPal에 상거래 주문을 전송하는 경우, 증분 ID는 `custom_id`. 다음 `custom_id` 지급금에 대한 머천트 활동 세부 정보 및 PayPal 웹 후크에 표시됩니다.

`custom_id` 상거래 활동 아래쪽에서 지급금 세부 정보:

![`custom_id` 머천트 활동 세부 사항](assets/merchant-activity.png)

`custom_id` payPal 웹 후크에 있는 세부 사항:

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

자세한 내용은 PayPal의 REST API 설명서 를 참조하십시오.

* [`purchase_unit` 여기서 `custom_id` 저장](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-축소)
* [주문 세부 사항 표시](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
