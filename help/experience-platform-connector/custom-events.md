---
title: 사용자 지정 이벤트 만들기
description: Adobe Commerce 데이터를 다른 Adobe DX 제품에 연결하는 사용자 지정 이벤트를 만드는 방법을 알아봅니다.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# 사용자 지정 이벤트 만들기

을(를) 확장할 수 있습니다 [이벤트 플랫폼](events.md) 고유한 데이터를 수집하기 위해 고유한 storefront 이벤트를 만듭니다. 사용자 지정 이벤트를 만들고 구성하면 [Adobe Commerce 이벤트 수집기](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## 사용자 지정 이벤트 처리

사용자 지정 이벤트는 Adobe Experience Platform에서만 지원됩니다. 사용자 지정 데이터는 Adobe Commerce 대시보드 및 지표 추적기에 전달되지 않습니다.

기타 `custom` 이벤트가 발생하면 컬렉터가 `personId` (`ecid`) `customContext` 그리고 `xdm` Edge로 전달하기 전에 개체 주위에 있는 개체.

예:

Adobe Commerce 이벤트 SDK를 통해 게시된 사용자 지정 이벤트:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

Experience Platform 모서리에서:

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> 사용자 지정 이벤트를 사용하면 기본 Adobe Analytics 보고서에 영향을 줄 수 있습니다.

## 이벤트 무시 처리(사용자 지정 속성)

표준 이벤트에 대한 속성 재정의는 Experience Platform에 대해서만 지원됩니다. 사용자 지정 데이터가 상거래 대시보드 및 지표 추적기에 전달되지 않습니다.

세트가 있는 모든 이벤트에 대해 `customContext`로 설정되면 컬렉터가 재정의됩니다 `personId` 및 Adobe Analytics 카운터와 는 에 설정된 다른 모든 속성을 전달합니다. `customContext`.

예:

Adobe Commerce 이벤트 SDK를 통해 게시된 재정의가 있는 제품 보기:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

Experience Platform 모서리에서:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

Adobe Commerce이 있는 제품 보기는 Adobe Commerce Events SDK를 통해 게시되었습니다.

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

Experience Platform 모서리에서:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> 사용자 지정 속성으로 이벤트를 재정의하는 것은 기본 Adobe Analytics 보고서에 영향을 줄 수 있습니다.
