---
title: 사용자 지정 이벤트 만들기
description: 사용자 지정 이벤트를 만들어 Adobe Commerce 데이터를 다른 Adobe DX 제품에 연결하는 방법에 대해 알아봅니다.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
source-git-commit: 2e1a0b2a79449562a2716929084f12eeee55a159
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 사용자 지정 이벤트 만들기

다음을 확장할 수 있습니다. [이벤트 플랫폼](events.md) 고유한 데이터를 수집하기 위한 자체 상점 이벤트를 생성하여. 사용자 지정 이벤트를 만들고 구성하면 [Adobe Commerce 이벤트 수집기](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## 사용자 지정 이벤트 처리

사용자 지정 이벤트는 Adobe Experience Platform에 대해서만 지원됩니다. 사용자 지정 데이터는 Adobe Commerce 대시보드 및 지표 추적기로 전달되지 않습니다.

모든 항목 `custom` 이벤트를 감지하면 컬렉터가 `personId` (`ecid`) 받는 사람 `customContext` 다음을 래핑 `xdm` 에지로 전달하기 전에 주위에 개체를 추가합니다.

예:

Adobe Commerce 이벤트 SDK를 통해 게시된 사용자 지정 이벤트:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

Experience Platform 에지에서:

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

## 이벤트 재정의 처리(사용자 지정 속성)

표준 Experience Platform에 대한 속성 재정의는 이벤트에만 지원됩니다. 사용자 지정 데이터는 상거래 대시보드 및 지표 추적기로 전달되지 않습니다.

세트가 있는 모든 이벤트 `customContext`, 수집기는 재정의됩니다 `personId` 및 Adobe Analytics 카운터가 있으며, 의 다른 모든 특성을 전달합니다. `customContext`.

예:

Adobe Commerce Events SDK를 통해 게시된 재정의를 사용하는 제품 보기:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

Experience Platform 에지에서:

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

Adobe Commerce Events SDK를 통해 게시된 Adobe Commerce 재정의를 사용하는 제품 보기:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

Experience Platform 에지에서:

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
> 사용자 지정 속성으로 이벤트를 재정의하는 경우 기본 Adobe Analytics 보고서에 영향을 줄 수 있습니다.
