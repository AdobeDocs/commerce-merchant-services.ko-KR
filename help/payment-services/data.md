---
title: 사용 가능한 데이터
description: Financial Reporting 데이터를 사용하여 비상거래 시스템과 보고를 조정합니다.
role: User
level: Intermediate
source-git-commit: ed471f363546f1d337e85568dc5079cae4507840
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 사용 가능한 데이터

일부 주문 및 페이아웃 데이터를 사용할 수 있으므로 외부 시스템 전반에서 Adobe Commerce 재무 보고를 조정할 수 있습니다.

## ERP 시스템과 조정

특정 주문과 연관된 증분 ID를 사용하여 Adobe이 아닌 ERP(Enterprise Resource Planning) 시스템과 Adobe Commerce Financial Reporting을 조정할 수 있습니다.

Payment Services가 PayPal에 상거래 주문을 전송하는 경우, 증분 ID는 `custom_id` _및_ 에서 `invoice_id` (또한 다음 항목 뒤에 임의의 문자열을 포함합니다. `increment_id`).

이 ID는 PayPal 웹 후크에서 지급과 관련하여 머천트 활동 세부 사항 모두에서 쉽게 액세스할 수 있습니다.

다음 `invoice_id` 및 `custom_id` 지급금에 대한 머천트 활동 세부 정보 하단 근처에 표시됩니다.

![`custom_id` 머천트 활동 세부 사항](assets/merchant-activity-ids.png)

`custom_id` 및 `invoice_id` payPal 웹 후크에 있는 세부 사항:

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

자세한 내용은 PayPal의 REST API 설명서 를 참조하십시오.

* [`purchase_unit`: `custom_id` 및 `invoice_id` 상주해](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit,-축소)
* [주문 세부 사항 표시](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
