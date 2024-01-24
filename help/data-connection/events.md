---
title: 이벤트
description: 각 이벤트가 캡처하는 데이터를 알아봅니다.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 136cd11e65674ec6e797aeaabd80750a50324566
workflow-type: tm+mt
source-wordcount: '6957'
ht-degree: 0%

---

# [!DNL Data Connection] 이벤트

다음은 를 설치할 때 사용할 수 있는 상거래 이벤트 목록입니다. [!DNL Data Connection] 확장명. 이러한 이벤트가 수집하는 데이터는 Adobe Experience Platform Edge로 전송됩니다. 다음을 만들 수도 있습니다. [사용자 지정 이벤트](custom-events.md) 즉시 제공되지 않는 추가 데이터를 수집합니다.

다음 이벤트가 수집하는 데이터 외에도 [기타 데이터](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK에서 제공합니다.

## Storefront 이벤트

상점 이벤트는 사이트를 탐색할 때 쇼핑객으로부터 익명으로 처리된 행동 데이터를 수집합니다. 이러한 이벤트가 수집하는 데이터를 사용하여 특정 쇼핑객 집합을 대상으로 하는 프로모션 및 캠페인을 만들 수 있습니다. Storefront 이벤트 데이터에는 간단하고 구성 가능한 제품만 포함됩니다.

>[!NOTE]
>
>모든 상점 이벤트에는 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 구매 가능한 경우 구매자의 이메일 주소 및 ECID가 포함된 필드. 각 이벤트에 이 프로필 데이터를 포함하면 Adobe Commerce에서 별도의 사용자 계정을 가져올 필요가 없습니다.

### 추가 장바구니

| 설명 | XDM 이벤트 이름 |
|---|---|
| 제품이 장바구니에 추가되거나 장바구니에 있는 제품의 수량이 증가하면 트리거됩니다. | `commerce.productListAdds` |

#### addToCart에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.productListAdds` | 장바구니에 제품이 추가되었는지 보여 줍니다. 값 `1` 제품이 추가되었음을 나타냅니다. |
| `commerce.cart.cartID` | 고객의 장바구니를 식별하는 고유 ID입니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### openCart

| 설명 | XDM 이벤트 이름 |
|---|---|
| 새 장바구니가 생성될 때 트리거됩니다. 즉, 빈 장바구니에 제품이 추가될 때입니다. | `commerce.productListOpens` |

#### openCart에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.productListOpens` | 장바구니가 생성되었는지 보여 줍니다. 값 `1` 장바구니가 생성되었음을 나타냅니다. |
| `commerce.cart.cartID` | 고객의 장바구니를 식별하는 고유 ID입니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### removeFromCart

| 설명 | XDM 이벤트 이름 |
|---|---|
| 제품이 제거되거나 장바구니에 있는 제품의 수량이 감소할 때마다 트리거됩니다. | `commerce.productListRemovals` |

#### removeFromCart에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.productListRemovals` | 장바구니에서 제품이 제거되었는지 보여 줍니다. 값 `1` 제품이 장바구니에서 제거되었음을 나타냅니다. |
| `commerce.cart.cartID` | 고객의 장바구니를 식별하는 고유 ID입니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### shoppingCartView

| 설명 | XDM 이벤트 이름 |
|---|---|
| 장바구니 페이지가 로드될 때 트리거됩니다. | `commerce.productListViews` |

#### shoppingCartView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.productListViews` | 제품 목록을 보았는지 여부를 나타냅니다. |
| `commerce.cart.cartID` | 고객의 장바구니를 식별하는 고유 ID입니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### pageView

| 설명 | XDM 이벤트 이름 |
|---|---|
| 페이지가 로드될 때 트리거됩니다. | `web.webpagedetails.pageViews` |

#### pageView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `web.webPageDetails.pageViews` | 페이지가 로드되었는지 보여 줍니다. A `value` / `1` 페이지가 로드되었음을 나타냅니다. |
| `web.webPageDetails.URL` | 웹 페이지의 표준 또는 일반 URL. 를 사용하여 기록되는 페이지에 도달하기 위해 사용되는 실제 URL일 수 있습니다. `Web Link`. |
| `web.webPageDetails.name` | 웹 페이지의 표준 이름. 이 이름은 반드시 페이지 제목이 아니거나 페이지 콘텐츠와 직접 연결되는 것은 아니지만 분류 목적으로 사이트의 페이지를 구성하는 데 사용됩니다. |
| `web.webReferrer.URL` | 사이트 링크를 클릭하기 전에 쇼핑객이 방문한 웹 페이지의 URL입니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

### 제품 페이지 보기

| 설명 | XDM 이벤트 이름 |
|---|---|
| 제품 페이지가 로드되면 트리거됩니다. | `commerce.productViews` |

#### productPageView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.productViews` | 제품을 보았는지 보여 줍니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### startCheck

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 체크아웃 버튼을 클릭할 때 트리거됩니다. | `commerce.checkouts` |

#### startCheckout에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.checkouts` | 체크아웃 프로세스 중에 작업이 발생했는지 보여 줍니다. |
| `commerce.cart.cartID` | 고객의 장바구니를 식별하는 고유 ID입니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### completeCheckout

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 할 때 트리거됩니다. | `commerce.purchases` |

#### completeCheckout에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.purchases` | 주문이 수락되었는지 여부를 나타냅니다. |
| `commerce.order` | 하나 이상의 제품에 대한 주문 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.payments` | 해당 주문에 대한 결제 목록. |
| `commerce.order.payments.paymentTransactionID` | 해당 결제 거래에 대한 고유 식별자. |
| `commerce.order.payments.paymentAmount` | 결제 값. |
| `commerce.order.payments.paymentType` | 해당 주문에 대한 결제 방법. 옵션은 다음과 같습니다. `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.order.taxAmount` | 최종 지급의 일부로 구매자가 지불한 세액. |
| `commerce.order.discountAmount` | 전체 주문에 적용되는 할인 금액을 나타냅니다. |
| `commerce.order.createdDate` | 상거래 시스템에서 새 주문이 생성된 시간 및 날짜. 예를 들어, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 하나 이상의 제품에 대한 배송 세부 정보. |
| `commerce.shipping.shippingMethod` | 일반배송, 퀵배송, 매장픽업 등 고객이 선택한 배송 방법 |
| `commerce.shipping.shippingAmount` | 고객이 배송비로 지불해야 했던 금액. |  | `shipping` | 하나 이상의 제품에 대한 배송 세부 정보. |
| `commerce.shipping.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

## 프로필 이벤트

프로필 이벤트에는 다음과 같은 계정 정보가 포함됩니다. `signIn`, `signOut`, `createAccount`, 및 `editAccount`. 이 데이터는 뉴욕에 거주하는 쇼핑객을 타겟팅하려는 경우와 같이, 세그먼트를 더 잘 정의하거나 마케팅 캠페인을 실행하는 데 필요한 주요 고객 세부 정보를 채우는 데 사용됩니다.

### 로그인

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 로그인을 시도할 때 트리거됩니다. | `userAccount.login` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지는 않습니다.

#### 로그인에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `person` | 개인 작업자, 연락처 또는 소유자입니다. |
| `person.accountID` | 사용자 계정 ID 캡처 |
| `person.accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당하는 경우. |
| `person.personalEmailID` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `personalEmail` | 연락처 세부 정보(이메일 및 관련 정보)를 캡처합니다. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `userAccount.login` | 방문자가 로그인을 시도했는지 여부를 나타냅니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

### 로그아웃

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 로그아웃하려고 할 때 트리거됩니다. | `userAccount.logout` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지는 않습니다.

#### SignOut에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `userAccount.logout` | 방문자가 로그아웃을 시도했는지 여부를 나타냅니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

### createAccount

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 계정을 만들려고 할 때 트리거됩니다. | `userAccount.createProfile` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지는 않습니다.

#### createAccount에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `person` | 개인 작업자, 연락처 또는 소유자입니다. |
| `person.accountID` | 사용자 계정 ID 캡처 |
| `person.accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당하는 경우. |
| `person.personalEmailID` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `personalEmail` | 연락처 세부 정보(이메일 및 관련 정보)를 캡처합니다. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `userAccount.updateProfile` | 사용자가 계정 프로필을 업데이트했는지 보여 줍니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

### editAccount

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 계정을 편집하려고 할 때 트리거됩니다. | `userAccount.updateProfile` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지는 않습니다.

#### editAccount에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `person` | 개인 작업자, 연락처 또는 소유자입니다. |
| `person.accountID` | 사용자 계정 ID 캡처 |
| `person.accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당하는 경우. |
| `person.personalEmailID` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `personalEmail` | 연락처 세부 정보(이메일 및 관련 정보)를 캡처합니다. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `userAccount.updateProfile` | 사용자가 계정 프로필을 업데이트했는지 보여 줍니다. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

## 이벤트 검색

검색 이벤트는 구매자의 의도와 관련된 데이터를 제공합니다. 쇼핑객의 의도에 대한 통찰력은 쇼핑객이 품목을 검색하는 방법, 고객이 클릭하는 방법, 궁극적으로 구매 또는 포기를 수행하는 방법을 가맹점이 확인하는 데 도움이 됩니다. 이 데이터를 사용하는 방법의 예로는 상위 제품을 검색하지만 제품을 구매하지 않는 기존 구매자를 타겟팅하려는 경우입니다.

사용 `searchRequest.id` 및 `searchResponse.id` 두 필드 모두에서 찾을 수 있음 `searchRequestSent` 및 `searchResponseReceived` 검색 요청을 해당 검색 응답과 상호 참조하는 이벤트입니다.

### searchRequestSent

| 설명 | XDM 이벤트 이름 |
|---|---|
| &quot;입력할 때 검색&quot; 팝오버의 다음 이벤트에 의해 트리거됩니다.<br><br>Enter 키를 누르고 _모두 보기_<br><br>&#x200B;검색 결과 페이지에서 다음 이벤트에 의해 트리거됨:<br><br>필터 선택, 정렬 순서 변경(_정렬 기준:_), 정렬 방향 변경(오름차순 또는 내림차순), 페이지당 결과 수 변경(_페이지당 # 표시_), 다음 페이지로 이동, 이전 페이지로 이동, 다른 페이지로 이동 | `searchRequest` |

>[!NOTE]
>
>B2B 확장이 설치된 Adobe Commerce Enterprise Edition에서는 검색 이벤트가 지원되지 않습니다.

#### searchRequestSent에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `searchRequest` | 검색 요청이 전송되었는지 보여 줍니다. |
| `searchRequest.id` | 해당 특정 검색 요청에 대한 고유 ID. |
| `searchRequest.value` | 요청의 수량 값. |
| `siteSearch` | 검색에 대한 정보를 포함합니다. |
| `siteSearch.filter` | 검색 결과를 제한하기 위해 필터가 적용되었는지 보여 줍니다. |
| `siteSearch.filter.attribute` (필터) | 항목을 검색 결과에 포함할지 여부를 결정하는 데 사용되는 항목의 패싯. |
| `siteSearch.filter.isRange` | true인 경우 값은 허용되는 값 범위의 끝점을 나타냅니다. |
| `siteSearch.filter.value` | 검색 결과에 포함된 항목을 결정하는 데 사용되는 속성 값입니다. |
| `siteSearch.sort` | 검색 결과를 정렬하는 방법을 나타냅니다. |
| `siteSearch.sort.attribute` (정렬) | 검색 결과에서 항목을 정렬하는 데 사용되는 속성입니다. |
| `siteSearch.sort.order` | 검색 결과를 반환하는 순서. |
| `siteSearch.query` | 검색어. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

### searchResponseReceived

| 설명 | XDM 이벤트 이름 |
|---|---|
| 라이브 검색에서 &quot;입력 시 검색&quot; 팝오버 또는 검색 결과 페이지에 대한 결과를 반환할 때 트리거됩니다. | `searchResponse` |

>[!NOTE]
>
>B2B 확장이 설치된 Adobe Commerce Enterprise Edition에서는 검색 이벤트가 지원되지 않습니다.

#### searchResponseReceived에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `searchResponse` | 검색 응답이 수신되었는지 여부를 나타냅니다. |
| `searchResponse.id` | 해당 특정 검색 응답에 대한 고유 ID. |
| `searchResponse.value` | 응답의 수량 값. |
| `siteSearch.numberOfResults` | 반환된 제품의 수입니다. |
| `siteSearch.suggestions` | 카탈로그에 존재하는 제품 및 범주의 이름을 포함하는 문자열 배열로서 검색 쿼리와 유사합니다. |
| `productListItems` | 장바구니에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

## B2B 이벤트

![Adobe Commerce용 B2B](../assets/b2b.svg) B2B 판매자의 경우 다음을 수행해야 합니다 [설치](install.md#install-the-b2b-extension) 다음 `experience-platform-connector-b2b` 확장을 사용하여 이러한 이벤트를 활성화합니다.

B2B 이벤트에는 [징발 목록](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 구매요청 목록이 생성되었는지, 추가되었는지, 삭제되었는지를 나타내는 정보. 구매요청 목록과 관련된 이벤트를 추적하여 고객이 자주 구매하는 제품을 확인하고 해당 데이터를 기반으로 캠페인을 생성할 수 있습니다.

### createRequisitionList

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 구매 요청 목록을 만들 때 트리거됩니다. | `commerce.requisitionListOpens` |

#### createRequisitionList에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.requisitionListOpens` | 새 구매요청 목록의 초기화를 나타냅니다. |
| `commerce.requisitionList` | 고객이 생성한 구매요청 목록의 속성. |
| `commerce.requisitionList.ID` | 구매요청 목록에 대한 고유 식별자. |
| `commerce.requisitionList.name` | 고객이 지정한 구매요청 목록의 이름. |
| `commerce.requisitionList.description` | 고객이 지정한 구매요청 목록에 대한 설명. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

### addToRequisitionList

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 기존 구매요청 목록에 제품을 추가하거나 목록을 생성하는 동안 트리거됩니다. | `commerce.requisitionListAdds` |

#### addToRequisitionList에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.requisitionListAdds` | 구매요청 목록에 하나 이상의 제품을 추가함을 나타냅니다. |
| `commerce.requisitionList` | 고객이 생성한 구매요청 목록의 속성. |
| `commerce.requisitionList.ID` | 구매요청 목록에 대한 고유 식별자. |
| `commerce.requisitionList.name` | 고객이 지정한 구매요청 목록의 이름. |
| `commerce.requisitionList.description` | 고객이 지정한 구매요청 목록에 대한 설명. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 구매요청 목록에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### removeFromRequisitionList

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 구매요청 목록에서 제품을 제거할 때 트리거됩니다. | `commerce.requisitionListRemovals` |

#### removeFromRequisitionList에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.requsitionListRemovals` | 구매요청 목록에서 하나 이상의 제품이 제거되었음을 나타냅니다. |
| `commerce.requisitionList` | 고객이 생성한 구매요청 목록의 속성. |
| `commerce.requisitionList.ID` | 구매요청 목록에 대한 고유 식별자. |
| `commerce.requisitionList.name` | 고객이 지정한 구매요청 목록의 이름. |
| `commerce.requisitionList.description` | 고객이 지정한 구매요청 목록에 대한 설명. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `productListItems` | 구매요청 목록에 추가된 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |

### deleteRequisitionList

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 구매 요청 목록을 삭제할 때 트리거됩니다. | `commerce.requisitionListDeletes` |

#### deleteRequisitionList에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.requisitionListDeletes` | 구매요청 목록이 삭제되었음을 나타냅니다. |
| `commerce.requisitionList` | 고객이 생성한 구매요청 목록의 속성. |
| `commerce.requisitionList.ID` | 구매요청 목록에 대한 고유 식별자. |
| `commerce.requisitionList.name` | 고객이 지정한 구매요청 목록의 이름. |
| `commerce.requisitionList.description` | 고객이 지정한 구매요청 목록에 대한 설명. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |

## 백오피스 이벤트

백오피스 이벤트에는 주문이 접수, 취소, 환불, 배송 또는 완료된 경우와 같은 주문 상태에 대한 정보가 포함됩니다. 이러한 서버측 이벤트가 수집하는 데이터는 쇼핑객 주문에 대한 360 뷰를 보여줍니다. 이 보기는 마케팅 캠페인을 개발할 때 판매자가 전체 주문 상태를 더 잘 타겟팅하거나 분석하는 데 도움이 됩니다. 예를 들어 연중 다양한 시기에 탁월한 성능을 발휘하는 특정 제품 범주의 트렌드를 확인할 수 있습니다. 예를 들어, 추운 달에 더 잘 팔리는 겨울 옷이나 몇 년 동안 쇼핑객들이 관심을 갖는 특정 제품 색깔. 또한 주문 상태 데이터를 사용하면 이전 주문을 기반으로 전환하는 쇼핑객의 성향을 파악하여 라이프타임 고객 가치를 계산하는 데 도움이 될 수 있습니다.

>[!NOTE]
>
>모든 백오피스 이벤트에는 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 쇼핑객의 이메일 주소를 제공하는 필드. 각 이벤트에 이 프로필 데이터를 포함하면 Adobe Commerce에서 별도의 사용자 계정을 가져올 필요가 없습니다.

### 주문

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 할 때 트리거됩니다. | `commerce.backofficeOrderPlaced` |

#### orderPlaced에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.payments` | 해당 주문에 대한 결제 목록. |
| `commerce.order.payments.paymentTransactionID` | 해당 결제 거래에 대한 고유 식별자. |
| `commerce.order.payments.paymentAmount` | 결제 값. |
| `commerce.order.payments.paymentType` | 해당 주문에 대한 결제 방법. 계산, 사용자 지정 값이 허용됩니다. |
| `commerce.order.payments.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.order.taxAmount` | 최종 지급의 일부로 구매자가 지불한 세액. |
| `commerce.order.discountAmount` | 전체 주문에 적용되는 할인 금액을 나타냅니다. |
| `commerce.order.createdDate` | 상거래 시스템에서 새 주문이 생성된 시간 및 날짜. 예를 들어, `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | 주문 합계에 사용되는 ISO 4217 통화 코드. |
| `commerce.shipping` | 하나 이상의 제품에 대한 배송 세부 정보. |
| `commerce.shipping.shippingMethod` | 일반배송, 퀵배송, 매장픽업 등 고객이 선택한 배송 방법 |
| `commerce.shipping.shippingAmount` | 고객이 배송비로 지불해야 했던 금액. |
| `commerce.shipping.currencyCode` | 총 배송에 사용되는 ISO 4217 통화 코드. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `commerce.billing.address` | 청구 우편 주소. |
| `commerce.billing.address.street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명 |
| `commerce.billing.address.street2` | 상세 정보 필드를 위한 추가 필드입니다. |
| `commerce.billing.address.city` | 도시 이름. |
| `commerce.billing.address.state` | 상태 이름. 자유 형식의 필드입니다. |
| `commerce.billing.address.postalCode` | 위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다. |
| `commerce.billing.address.country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 순서대로 제품 배열. |
| `productListItems.id` | 해당 제품 항목에 대한 라인 항목 식별자. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |
| `productListItems.categories` | 제품 범주에 대한 정보를 포함합니다. |
| `productListItems.categories.id` | 카테고리에 대한 고유 식별자. |
| `productListItems.categories.name` | 범주의 이름입니다. |
| `productListItems.categories.path` | 카테고리에 대한 경로입니다. |
| `productListItems.productImageUrl` | 제품의 기본 이미지 URL. |

### 인보이스 발행 주문

| 설명 | XDM 이벤트 이름 |
|---|---|
| 상인이 지급을 요청하기 위해 송장을 제출할 때 트리거됩니다. | `commerce.backofficeOrderInvoiced` |

#### orderInvoiced에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.priceTotal` | 할인 및 세금이 모두 적용된 후 이 주문의 총 가격. |
| `commerce.order.currencyCode` | 주문 합계에 사용되는 ISO 4217 통화 코드. |
| `commerce.order.purchaseOrderNumber` | 구매자가 해당 구매 또는 계약에 할당한 고유 식별자. |
| `commerce.order.payments` | 해당 주문에 대한 결제 목록. |
| `commerce.order.payments.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.order.payments.paymentType` | 해당 주문에 대한 결제 방법. 계산, 사용자 지정 값이 허용됩니다. |
| `commerce.order.payments.paymentAmount` | 결제 값. |
| `commerce.shipping` | 하나 이상의 제품에 대한 배송 세부 정보. |
| `commerce.shipping.shippingMethod` | 일반배송, 퀵배송, 매장픽업 등 고객이 선택한 배송 방법 |
| `commerce.shipping.shippingAmount` | 고객이 배송비로 지불해야 했던 금액. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 순서대로 제품 배열. |
| `productListItems.id` | 해당 제품 항목에 대한 라인 항목 식별자. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.categories` | 제품 범주에 대한 정보를 포함합니다. |
| `productListItems.categories.id` | 카테고리에 대한 고유 식별자. |
| `productListItems.categories.name` | 범주의 이름입니다. |
| `productListItems.categories.path` | 카테고리에 대한 경로입니다. |

### orderItemsShipped

| 설명 | XDM 이벤트 이름 |
|---|---|
| 주문이 배송될 때 트리거됩니다. | `commerce.backofficeOrderItemsShipped` |

#### orderItemsShipped에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.payments` | 해당 주문에 대한 결제 목록. |
| `commerce.order.payments.paymentTransactionID` | 해당 결제 거래에 대한 고유 식별자. |
| `commerce.order.payments.paymentAmount` | 결제 값. |
| `commerce.order.payments.paymentType` | 해당 주문에 대한 결제 방법. 계산, 사용자 지정 값이 허용됩니다. |
| `commerce.order.payments.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.order.priceTotal` | 할인 및 세금이 모두 적용된 후 이 주문의 총 가격. |
| `commerce.order.purchaseOrderNumber` | 구매자가 해당 구매 또는 계약에 할당한 고유 식별자. |
| `commerce.order.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.order.lastUpdatedDate` | 상거래 시스템에서 특정 주문 레코드가 마지막으로 업데이트되는 시간. |
| `commerce.shipping` | 하나 이상의 제품에 대한 배송 세부 정보. |
| `commerce.shipping.shippingMethod` | 일반배송, 퀵배송, 매장픽업 등 고객이 선택한 배송 방법 |
| `commerce.shipping.shippingAmount` | 고객이 배송비로 지불해야 했던 금액. |
| `commerce.shipping.address` | 실제 배송 주소. |
| `commerce.shipping.address.street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명. |
| `commerce.shipping.address.street2` | 2차선 도로 정보(선택 사항). |
| `commerce.shipping.address.city` | 도시 이름. |
| `commerce.shipping.address.state` | 주 이름입니다. 자유 형식의 필드입니다. |
| `commerce.shipping.address.postalCode` | 위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다. |
| `commerce.shipping.address.country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `commerce.shipping.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.shipping.trackingNumber` | 주문 품목 선적에 대해 운송 회사가 제공하는 추적 번호. |
| `commerce.shipping.trackingURL` | 주문 항목의 배송 상태를 추적할 URL입니다. |
| `commerce.shipping.shipDate` | 주문에서 하나 이상의 품목이 배송된 날짜. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `commerce.billing.address` | 청구 우편 주소. |
| `commerce.billing.address.street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명 |
| `commerce.billing.address.street2` | 상세 정보 필드를 위한 추가 필드입니다. |
| `commerce.billing.address.city` | 도시 이름. |
| `commerce.billing.address.state` | 상태 이름. 자유 형식의 필드입니다. |
| `commerce.billing.address.postalCode` | 위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다. |
| `commerce.billing.address.country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 순서대로 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |
| `productListItems.categories` | 제품 범주에 대한 정보를 포함합니다. |
| `productListItems.categories.id` | 카테고리에 대한 고유 식별자. |
| `productListItems.categories.name` | 범주의 이름입니다. |
| `productListItems.categories.path` | 카테고리에 대한 경로입니다. |

### orderCanceled

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 취소할 때 트리거됩니다. | `commerce.backofficeOrderCancelled` |

#### orderCanceled에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.purchaseOrderNumber` | 구매자가 해당 구매 또는 계약에 할당한 고유 식별자. |
| `commerce.order.cancelDate` | 쇼핑객이 주문을 취소하는 날짜 및 시간입니다. |
| `commerce.order.lastUpdatedDate` | 상거래 시스템에서 특정 주문 레코드가 마지막으로 업데이트되는 시간. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |

### orderLineItemReturned

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 반품된 항목을 환불받을 때 트리거됩니다. | `commerce.backofficeCreditMemoIssued` |

#### orderLineItemRefferenced에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.lastUpdatedDate` | 상거래 시스템에서 특정 주문 레코드가 마지막으로 업데이트되는 시간. |
| `commerce.order.purchaseOrderNumber` | 구매자가 해당 구매 또는 계약에 할당한 고유 식별자. |
| `commerce.refunds` | 해당 주문에 대한 환불 목록. |
| `commerce.refunds.transactionID` | 해당 환불에 대한 고유 식별자. |
| `commerce.refunds.refundAmount` | 환불 금액. |
| `commerce.refunds.refundPaymentType` | 해당 주문에 대한 결제 방법. 계산, 사용자 지정 값이 허용됩니다. |
| `commerce.refunds.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 순서대로 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |
| `productListItems.categories` | 제품 범주에 대한 정보를 포함합니다. |
| `productListItems.categories.id` | 카테고리에 대한 고유 식별자. |
| `productListItems.categories.name` | 범주의 이름입니다. |
| `productListItems.categories.path` | 카테고리에 대한 경로입니다. |

### orderItemsReturnInitiated

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 항목 반환을 요청할 때 트리거됩니다. | `commerce.backofficeOrderItemsReturnInitiated` |

#### orderItemsReturnInitiated에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.returns` | 이 주문에 대한 RMA(반품 상품 승인) 정보. |
| `commerce.order.returns.returnID` | 해당 RMA(Return Merchandises Authorization)의 고유 식별자. |
| `commerce.order.returns.returnStatus` | 보류 중, 마감됨 등과 같은 RMA(Return Merchandise Authorization)의 상태. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 순서대로 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |
| `productListItems.categories` | 제품 범주에 대한 정보를 포함합니다. |
| `productListItems.categories.id` | 카테고리에 대한 고유 식별자. |
| `productListItems.categories.name` | 범주의 이름입니다. |
| `productListItems.categories.path` | 카테고리에 대한 경로입니다. |
| `productListItems.returnItem` | 이 품목에 대한 RMA(반품 상품 승인) 정보. |
| `productListItems.returnItem.returnStatus` | 보류 중, 승인됨 등 반환된 항목의 상태입니다. |
| `productListItems.returnItem.returnReason` | 이 항목에 대한 반환이 요청되는 이유입니다. |
| `productListItems.returnItem.returnItemCondition` | 반환이 요청되는 항목의 상태입니다. |
| `productListItems.returnItem.returnResolution` | 환불, 교환 등과 같이 반환되는 항목의 요청된 해결 방법. |
| `productListItems.returnItem.returnQuantityRequested` | 구매자가 반품을 요청한 이 항목의 번호입니다. |
| `productListItems.returnItem.returnQuantityAuthorized` | 반환할 수 있는 이 항목의 번호입니다. |
| `productListItems.returnItem.eturnQuantityReceived` | 받은 반환된 항목 수입니다. |
| `productListItems.returnItem.returnQuantityApproved` | 반품이 완전히 완료되고 승인된 이 항목의 수입니다. |

### orderItemReturnCompleted

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 반환을 요청한 항목이 완료되면 트리거됩니다. | `commerce.backofficeOrderItemsReturnCompleted` |

#### orderItemReturnCompleted에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.returns` | 이 주문에 대한 RMA(반품 상품 승인) 정보. |
| `commerce.order.returns.returnID` | 해당 RMA(Return Merchandises Authorization)의 고유 식별자. |
| `commerce.order.returns.returnStatus` | 보류 중, 마감됨 등과 같은 RMA(Return Merchandise Authorization)의 상태. |
| `commerce.commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `commerce.commerceScope.environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `commerce.commerceScope.storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `commerce.commerceScope.storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `commerce.commerceScope.websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 순서대로 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |
| `productListItems.categories` | 제품 범주에 대한 정보를 포함합니다. |
| `productListItems.categories.id` | 카테고리에 대한 고유 식별자. |
| `productListItems.categories.name` | 범주의 이름입니다. |
| `productListItems.categories.path` | 카테고리에 대한 경로입니다. |
| `productListItems.returnItem` | 이 품목에 대한 RMA(반품 상품 승인) 정보. |
| `productListItems.returnItem.returnStatus` | 보류 중, 승인됨 등 반환된 항목의 상태입니다. |
| `productListItems.returnItem.returnReason` | 이 항목에 대한 반환이 요청되는 이유입니다. |
| `productListItems.returnItem.returnItemCondition` | 반환이 요청되는 항목의 상태입니다. |
| `productListItems.returnItem.returnResolution` | 환불, 교환 등과 같이 반환되는 항목의 요청된 해결 방법. |
| `productListItems.returnItem.returnQuantityRequested` | 구매자가 반품을 요청한 이 항목의 번호입니다. |
| `productListItems.returnItem.returnQuantityAuthorized` | 반환할 수 있는 이 항목의 번호입니다. |
| `productListItems.returnItem.eturnQuantityReceived` | 받은 반환된 항목 수입니다. |
| `productListItems.returnItem.returnQuantityApproved` | 반품이 완전히 완료되고 승인된 이 항목의 수입니다. |

### orderShipmentCompleted

| 설명 | XDM 이벤트 이름 |
|---|---|
| 선적이 완료되면 트리거됩니다. | `commerce.backofficeOrderShipmentCompleted` |

#### orderShipmentCompleted에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `commerce.order` | 주문에 대한 정보가 포함되어 있습니다. |
| `commerce.order.purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `commerce.order.payments` | 해당 주문에 대한 결제 목록. |
| `commerce.order.payments.paymentTransactionID` | 해당 결제 거래에 대한 고유 식별자. |
| `commerce.order.payments.paymentAmount` | 결제 값. |
| `commerce.order.payments.paymentType` | 해당 주문에 대한 결제 방법. 계산, 사용자 지정 값이 허용됩니다. |
| `commerce.order.payments.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `commerce.order.taxAmount` | 최종 지급의 일부로 구매자가 지불한 세액. |
| `commerce.order.createdDate` | 상거래 시스템에서 새 주문이 생성된 시간 및 날짜. 예를 들어, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | 하나 이상의 제품에 대한 배송 세부 정보. |
| `commerce.shipping.shippingMethod` | 일반배송, 퀵배송, 매장픽업 등 고객이 선택한 배송 방법 |
| `commerce.shipping.shippingAmount` | 고객이 배송비로 지불해야 했던 금액. |
| `commerce.shipping.shipDate` | 주문에서 하나 이상의 품목이 배송된 날짜. |
| `commerce.shipping.address` | 실제 배송 주소. |
| `commerce.shipping.address.street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명. |
| `commerce.shipping.address.street2` | 2차선 도로 정보(선택 사항). |
| `commerce.shipping.address.city` | 도시 이름. |
| `commerce.shipping.address.state` | 주 이름입니다. 자유 형식의 필드입니다. |
| `commerce.shipping.address.postalCode` | 위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다. |
| `commerce.shipping.address.country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `commerce.billing.address` | 청구 우편 주소. |
| `commerce.billing.address.street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명 |
| `commerce.billing.address.street2` | 상세 정보 필드를 위한 추가 필드입니다. |
| `commerce.billing.address.city` | 도시 이름. |
| `commerce.billing.address.state` | 상태 이름. 자유 형식의 필드입니다. |
| `commerce.billing.address.postalCode` | 위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다. |
| `commerce.billing.address.country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `productListItems` | 순서대로 제품 배열. |
| `productListItems.SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `productListItems.name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름. |
| `productListItems.priceTotal` | 제품 라인 항목에 대한 총 가격. |
| `productListItems.quantity` | 장바구니에 있는 제품 단위의 수입니다. |
| `productListItems.discountAmount` | 적용되는 할인 금액을 나타냅니다. |
| `productListItems.currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 사용된 통화 코드, 예: `USD` 또는 `EUR`. |
| `productListItems.selectedOptions` | 구성 가능한 제품에 사용되는 필드. |
| `productListItems.selectedOptions.attribute` | 구성 가능한 제품의 속성(예: ) 식별 `size` 또는 `color`. |
| `productListItems.selectedOptions.value` | 속성 값(예: ) 식별 `small` 또는 `black`. |
| `productListItems.categories` | 제품 범주에 대한 정보를 포함합니다. |
| `productListItems.categories.id` | 카테고리에 대한 고유 식별자. |
| `productListItems.categories.name` | 범주의 이름입니다. |
| `productListItems.categories.path` | 카테고리에 대한 경로입니다. |
