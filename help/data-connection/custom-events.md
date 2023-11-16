---
title: 사용자 지정 이벤트 만들기
description: 사용자 지정 이벤트를 만들어 Adobe Commerce 데이터를 다른 Adobe DX 제품에 연결하는 방법에 대해 알아봅니다.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# 사용자 지정 이벤트 만들기

다음을 확장할 수 있습니다. [이벤트 플랫폼](events.md) 고유한 데이터를 수집하기 위한 자체 상점 이벤트를 생성하여. 사용자 지정 이벤트를 만들고 구성하면 [Adobe Commerce 이벤트 수집기](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-collector).

## 사용자 지정 이벤트 처리

사용자 지정 이벤트는 Adobe Experience Platform에 대해서만 지원됩니다. 사용자 지정 데이터는 Adobe Commerce 대시보드 및 지표 추적기로 전달되지 않습니다.

모든 항목 `custom` 이벤트, 수집기:

- 추가 `identityMap` 포함 `ECID` 기본 ID로
- 포함 `email` 위치: `identityMap` 보조 ID로 _if_ `personalEmail.address` 이벤트에 설정됩니다.
- 전체 이벤트를 `xdm` Edge로 전달하기 전의 개체

예:

Adobe Commerce 이벤트 SDK를 통해 게시된 사용자 지정 이벤트:

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

Experience Platform 에지에서:

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> 사용자 지정 이벤트를 사용하면 기본 Adobe Analytics 보고서에 영향을 줄 수 있습니다.

## 이벤트 재정의 처리(사용자 지정 속성)

표준 Experience Platform에 대한 속성 재정의는 이벤트에만 지원됩니다. 사용자 지정 데이터는 상거래 대시보드 및 지표 추적기로 전달되지 않습니다.

가 있는 모든 이벤트의 경우 `customContext`, 컬렉터는 관련 컨텍스트에 설정된 필드를 의 필드와 조인합니다. `customContext`. 재정의에 대한 사용 사례는 개발자가 이미 지원되는 이벤트에서 페이지의 다른 부분에 의해 설정된 컨텍스트를 재사용하고 확장하려는 경우입니다.

>[!NOTE]
>
>사용자 지정 이벤트를 재정의할 때 이벤트 유형이 중복되지 않도록 해당 Experience Platform 유형에 대해 이벤트로의 전달을 꺼야 합니다.

예시:

Adobe Commerce Events SDK를 통해 게시된 재정의를 사용하는 제품 보기:

```javascript
mse.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

Experience Platform 에지에서:

```javascript
{
  xdm: {
    eventType: 'commerce.productViews',
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true,
        }
      ]
    },
    commerce: {
      productViews: {
        value : 1,
      }
    },
    productListItems: [{
        SKU: "1234",
        name: "leora summer pants",
        productCategories: [{
            categoryID: "cat_15",
            categoryName: "summer pants",
            categoryPath: "pants/mens/summer",
        }],
    }],
  }
}
```

>[!NOTE]
>
> 사용자 지정 속성으로 이벤트를 재정의하는 경우 기본 Adobe Analytics 보고서에 영향을 줄 수 있습니다.
