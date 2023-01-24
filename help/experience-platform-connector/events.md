---
title: 이벤트
description: 각 이벤트가 캡처하는 데이터를 알아봅니다.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 18edfec6dbc66ef0e94e9f54ca1061386104d90c
workflow-type: tm+mt
source-wordcount: '3141'
ht-degree: 0%

---

# Experience Platform 커넥터 이벤트

다음은 Experience Platform 커넥터 확장을 설치할 때 사용할 수 있는 상거래 이벤트 목록입니다. 이러한 이벤트가 수집하는 데이터는 Adobe Experience Platform Edge로 전송됩니다. 만들 수도 있습니다 [사용자 지정 이벤트](custom-events.md) 기본적으로 제공되지 않은 추가 데이터를 수집하기 위해

다음 이벤트가 수집하는 데이터 외에도 [기타 데이터](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK에서 제공합니다.

## Storefront 이벤트

상점 이벤트는 고객이 사이트를 탐색할 때 익명으로 처리된 행동 데이터를 수집합니다. 이러한 이벤트가 수집하는 데이터를 특정 구매자 집합을 대상으로 하는 프로모션 및 캠페인을 만드는 데 사용할 수 있습니다.

>[!NOTE]
>
>모든 상점 이벤트에는 `identityMap` 필드의 고유 식별자입니다.

### addToCart

| 설명 | XDM 이벤트 이름 |
|---|---|
| 장바구니에 제품을 추가하거나 장바구니의 제품 수량이 증가될 때 트리거됩니다. | `commerce.productListAdds` |

#### addToCart에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `productListAdds` | 제품이 장바구니에 추가되었는지 여부를 나타냅니다. 값 `1` 제품이 추가되었음을 나타냅니다. |
| `productListItems` | 장바구니에 추가된 일련의 제품 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `quantity` | 장바구니에 추가된 제품 단위 수입니다 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID입니다 |

### openCart

| 설명 | XDM 이벤트 이름 |
|---|---|
| 새 장바구니가 생성될 때, 즉 제품을 빈 장바구니에 추가할 때 트리거됩니다. | `commerce.productListOpens` |

#### openCart에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `productListOpens` | 장바구니가 만들어졌는지 여부를 나타냅니다. 값 `1` 장바구니가 만들어졌음을 나타냅니다. |
| `productListItems` | 장바구니에 추가된 일련의 제품 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `quantity` | 장바구니에 추가된 제품 단위 수입니다 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID입니다 |

### removeFromCart

| 설명 | XDM 이벤트 이름 |
|---|---|
| 제품이 제거되거나 장바구니의 제품 수량이 감소될 때마다 트리거됩니다. | `commerce.productListRemovals` |

#### removeFromCart에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `productListRemovals` | 장바구니에서 제품이 제거되었는지 여부를 나타냅니다. 값 `1` 장바구니에서 제품이 제거되었음을 나타냅니다. |
| `productListItems` | 장바구니에서 제거된 제품 배열입니다 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `quantity` | 장바구니에서 제거된 제품 단위 수입니다 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID입니다 |

### shoppingCartView

| 설명 | XDM 이벤트 이름 |
|---|---|
| 장바구니 페이지가 로드될 때 트리거됩니다. | `commerce.productListViews` |

#### shoppingCartView에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `productListViews` | 제품 목록을 보았는지 여부를 나타냅니다 |
| `productListItems` | 장바구니에 있는 일련의 제품 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `quantity` | 장바구니에 있는 제품 단위 수입니다 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID입니다 |

### pageView

| 설명 | XDM 이벤트 이름 |
|---|---|
| 페이지가 로드될 때 트리거됩니다. | `web.webpagedetails.pageViews` |

#### pageView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `pageViews` | 페이지가 로드되었는지 여부를 나타냅니다. A `value` 의 `1` 페이지가 로드되었음을 나타냅니다. |

### productPageView

| 설명 | XDM 이벤트 이름 |
|---|---|
| 제품 페이지가 로드될 때 트리거됩니다. | `commerce.productViews` |

#### productPageView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `productViews` | 제품을 보았는지 여부를 나타냅니다 |
| `productListItems` | 장바구니에 있는 일련의 제품 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |

### startCheckout

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 체크아웃 단추를 클릭할 때 트리거됩니다. | `commerce.checkouts` |

#### startCheckout에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `checkouts` | 체크아웃 프로세스 중에 작업이 발생했는지 여부를 나타냅니다 |
| `productListItems` | 장바구니에 있는 일련의 제품 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `quantity` | 장바구니에 있는 제품 단위 수입니다 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID입니다 |

### completeCheckout

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 할 때 트리거됩니다. | `commerce.order` |

#### completeCheckout에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `purchases` | 주문이 수락되었는지 여부를 나타냅니다. |
| `order` | 하나 이상의 제품에 대한 주문 내용에 대한 정보가 들어 있습니다 |
| `purchaseID` | 이 구매 또는 계약에 대해 판매자가 지정한 고유 식별자입니다. ID가 고유하다는 보장이 없습니다. |
| `orderType` | 체크아웃이나 인스턴트 구매와 같이 주문된 주문 유형을 나타냅니다 |
| `payments` | 이 주문에 대한 지급 목록 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 지급 항목에 사용되는 통화 코드. 예, `USD` 또는 `EUR`. |
| `paymentAmount` | 지급 값 |
| `paymentType` | 이 주문에 대한 결제 방법입니다. 옵션은 다음과 같습니다. `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | 이 지급 품목에 대한 고유 거래 식별자 |
| `shipping` | 하나 이상의 제품에 대한 배송 세부 사항입니다. |
| `shippingMethod` | 표준 배송, 신속 배송, 매장 선별 등과 같이 고객이 선택한 배송 방법 |
| `shippingAmount` | 장바구니에 있는 항목의 총 배송 비용 |
| `promotionID` | 프로모션의 고유 식별자(있는 경우) |
| `personalEmail` | 개인 전자 메일 주소를 지정합니다 |
| `address` | 기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다. |
| `productListItems` | 장바구니에 있는 일련의 제품 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `quantity` | 장바구니에 있는 제품 단위 수입니다 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 주문 합계에 사용되는 통화 코드. |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |


## 프로필 이벤트

프로필 이벤트에는 다음과 같은 계정 정보가 포함됩니다. `signIn`, `signOut`, `createAccount`, 및 `editAccount`. 이 데이터는 New York에 거주하는 구매자를 타겟팅하려는 경우와 같이 세그먼트를 더 잘 정의하거나 마케팅 캠페인을 실행하는 데 필요한 주요 고객 세부 사항을 채우는 데 사용됩니다.

### signIn

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 로그인하려고 할 때 트리거됩니다. | `userAccount.login` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

#### SignIn에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `eventType` | 다음과 같은 이 시계열 레코드의 기본 이벤트 유형: `userAccount.login` |
| `person` | 개별 배우, 연락처 또는 소유자 |
| `accountID` | 사용자 계정 ID 캡처 |
| `personalEmailID` | 개인 전자 메일의 고유 식별자를 지정합니다 |
| `address` | 기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다. |
| `userAccount` | 충성도 세부 사항, 환경 설정, 로그인 프로세스 및 기타 계정 기본 설정을 나타냅니다 |
| `login` | 방문자가 로그인하려고 했는지 여부를 나타냅니다 |

### signOut

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 로그아웃하려 할 때 트리거됩니다. | `userAccount.logout` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

#### 로그아웃에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `eventType` | 다음과 같은 이 시계열 레코드의 기본 이벤트 유형: `userAccount.logout` |
| `userAccount` | 충성도 세부 사항, 환경 설정, 로그인 프로세스 및 기타 계정 기본 설정을 나타냅니다 |
| `logout` | 방문자가 로그아웃하려고 했는지 여부를 나타냅니다 |

### createAccount

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 계정을 만들려고 할 때 트리거됩니다. | `userAccount.createProfile` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

#### createAccount에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `eventType` | 다음과 같은 이 시계열 레코드의 기본 이벤트 유형: `account.createProfile` |
| `person` | 개별 배우, 연락처 또는 소유자 |
| `accountID` | 사용자 계정 ID 캡처 |
| `accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당되는 경우 |
| `personalEmailID` | 개인 전자 메일의 고유 식별자를 지정합니다 |
| `address` | 기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다. |
| `userAccount` | 충성도 세부 사항, 환경 설정, 로그인 프로세스 및 기타 계정 기본 설정을 나타냅니다 |
| `createProfile` | 사용자가 계정 프로필을 만들었는지 여부를 나타냅니다 |

### editAccount

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 계정을 편집하려고 할 때 트리거됩니다. | `userAccount.updateProfile` |

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

#### editAccount에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `eventType` | 다음과 같은 이 시계열 레코드의 기본 이벤트 유형: `account.updateProfile` |
| `person` | 개별 배우, 연락처 또는 소유자 |
| `accountID` | 사용자 계정 ID 캡처 |
| `accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당되는 경우 |
| `personalEmailID` | 개인 전자 메일의 고유 식별자를 지정합니다 |
| `personalEmail` | 개인 전자 메일 주소를 지정합니다 |
| `address` | 기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다. |
| `userAccount` | 충성도 세부 사항, 환경 설정, 로그인 프로세스 및 기타 계정 기본 설정을 나타냅니다 |
| `updateProfile` | 사용자가 계정 프로필을 업데이트했는지 여부를 나타냅니다 |

## 이벤트 검색

검색 이벤트는 구매자의 의도와 관련된 데이터를 제공합니다. 쇼핑객의 의도에 대한 통찰력은 쇼핑객이 어떻게 항목을 검색하고, 무엇을 클릭하며, 궁극적으로 구매하거나 포기하는 지를 상인이 확인하는 데 도움이 됩니다. 이 데이터를 사용하는 방법의 예는 최상위 제품을 검색하지만 제품을 구매하지 않는 기존 구매자를 타겟팅하려는 경우입니다.

### searchRequestSent

| 설명 | XDM 이벤트 이름 |
|---|---|
| &quot;입력할 때 검색&quot; 팝오버에서 다음 이벤트에 의해 트리거됩니다.<br><br>Enter 키를 누른 다음 클릭 _모두 보기_<br><br>&#x200B;검색 결과 페이지에서 다음 이벤트에 의해 트리거됩니다.<br><br>필터를 선택하고 정렬 순서 변경(_정렬 기준_), 정렬 방향 변경(오름차순 또는 내림차순), 페이지당 결과 수 변경(_페이지당 # 표시_). 다음 페이지로 이동하고, 이전 페이지로 이동한 다음 다른 페이지로 이동합니다 | `searchRequest` |

>[!NOTE]
>
>검색 이벤트는 B2B 모듈이 설치된 Adobe Commerce Enterprise Edition에서 지원되지 않습니다.

#### searchRequestSent에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `searchRequest` | 검색 요청이 전송되었는지 여부를 나타냅니다 |
| `filter` | 검색 결과를 제한하는 필터가 적용되었는지 여부를 나타냅니다 |
| `attribute` (필터) | 검색 결과에 항목을 포함할지 여부를 결정하는 데 사용되는 항목의 패싯 |
| `value` | 검색 결과에 포함할 항목을 결정하는 데 사용되는 속성 값 |
| `isRange` | true일 경우 값은 허용 가능한 값 범위의 끝점을 나타냅니다 |
| `sort` | 검색 결과를 정렬하는 방법을 나타냅니다 |
| `attribute` (sort) | 검색 결과의 항목을 정렬하는 데 사용되는 속성입니다 |
| `order` | 검색 결과를 반환하는 순서 |
| `query` | 검색어 |

### searchResponseReceived

| 설명 | XDM 이벤트 이름 |
|---|---|
| Live Search가 &quot;입력한 대로 검색&quot; 팝업 또는 검색 결과 페이지에 대한 결과를 반환하는 경우 트리거됩니다. | `searchResponse` |

>[!NOTE]
>
>검색 이벤트는 B2B 모듈이 설치된 Adobe Commerce Enterprise Edition에서 지원되지 않습니다.

#### searchResponseReceived에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `searchResponse` | 검색 응답이 수신되었는지 여부를 나타냅니다. |
| `suggestions` | 검색 쿼리와 유사한 카탈로그에 있는 제품 및 카테고리의 이름을 포함하는 문자열 배열입니다 |
| `numberOfResults` | 반환된 제품 수 |
| `productListItems` | 장바구니에 있는 일련의 제품입니다. |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `productImageUrl` | 제품의 기본 이미지 URL |

## (베타) 백오피스 이벤트

>[!NOTE]
>
>이미 백오피스 베타 프로그램에 등록한 상인의 경우 백오피스 이벤트에 액세스할 수 있습니다. 백오피스 베타 프로그램에 참여하시려면 [drios@adobe.com](mailto:drios@adobe.com).

백 오피스 이벤트에는 주문, 취소, 환불 또는 배송과 같은 주문 상태에 대한 정보가 포함되어 있습니다. 이러한 서버측 이벤트가 수집하는 데이터는 쇼퍼 순서에 대한 360 보기를 표시합니다. 이를 통해 마케터는 마케팅 캠페인을 개발할 때 전체 주문 상태를 더 잘 타깃팅하거나 분석할 수 있습니다. 예를 들어, 한 해의 다른 시간대에 잘 수행하는 특정 제품 카테고리의 트렌드를 파악할 수 있습니다. 추운 달 동안 더 잘 팔리는 겨울 옷이나 몇 년 동안 쇼핑하는 사람들이 관심이 있는 특정한 상품색들 같은 것입니다. 또한 주문 상태 데이터는 이전 주문을 기반으로 전환하려는 구매자의 성향을 파악하여 라이프타임 고객 값을 계산하는 데 도움이 될 수 있습니다.

### orderPlaced

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 할 때 트리거됩니다. | `commerce.orderPlaced` |

#### orderPlaced에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `identityMap` | 고객을 식별하는 이메일 주소를 포함합니다 |
| `address` | 기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다. |
| `eventType` | `commerce.orderPlaced` |
| `productListItems` | 순서의 제품 배열입니다 |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `quantity` | 장바구니에 있는 제품 단위 수입니다 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `order` | 주문에 대한 정보를 포함합니다 |
| `purchaseID` | 이 구매 또는 계약에 대해 판매자가 지정한 고유 식별자입니다. ID가 고유하다는 보장이 없습니다 |
| `purchaseOrderNumber` | 이 구매 또는 계약에 대해 구매자가 할당한 고유 식별자입니다 |
| `payments` | 이 주문에 대한 지급 목록 |
| `paymentType` | 이 주문에 대한 결제 방법입니다. 열거된 사용자 지정 값이 허용됩니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 지급 항목에 사용된 통화 코드 |
| `paymentAmount` | 지급 값 |
| `shipping` | 하나 이상의 제품에 대한 배송 세부 사항 |
| `shippingMethod` | 표준 배송, 신속 배송, 매장 선별 등과 같이 고객이 선택한 배송 방법 |
| `shippingAddress` | 실제 배송 주소 |
| `street1` | 1차 거리 레벨 정보, 아파트 번호, 거리 번호 및 거리 이름 |
| `shippingAmount` | 고객이 배송비를 지불해야만 했던 금액입니다. |
| `billingAddress` | 청구 우편 주소 |
| `street1` | 1차 거리 레벨 정보, 아파트 번호, 거리 번호 및 거리 이름 |
| `street2` | 거리 수준 정보에 대한 추가 필드 |
| `city` | 시의 이름 |
| `state` | 상태의 이름입니다. 자유형이에요. |
| `postalCode` | 위치의 우편 번호입니다. 모든 국가에서는 우편 번호를 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만을 포함합니다. |
| `country` | 정부 관리 지역의 명칭. 기타 `xdm:countryCode`, 모든 언어로 국가 이름을 가질 수 있는 자유 형식 필드입니다. |

### orderShipped

| 설명 | XDM 이벤트 이름 |
|---|---|
| 주문이 출하될 때 트리거됩니다. | `commerce.orderLineItemShipped` |

#### orderShipped에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.
|필드|설명| |—|—| |`identityMap`|고객을 식별하는 전자 메일 주소를 포함합니다.| |`address`|기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다.| |`eventType`|`commerce.orderLineItemShipped`| |`productListItems`|순서대로 제품 배열| |`name`|제품의 표시 이름 또는 사람이 읽을 수 있는 이름| |`SKU`|재고 유지 단위. 제품의 고유 식별자입니다.| |`quantity`|장바구니에 있는 제품 단위 수| |`priceTotal`|제품 라인 항목의 총 가격| |`discountAmount`|적용된 할인 금액을 나타냅니다.| |`order`|주문에 대한 정보를 포함합니다.| |`purchaseID`|이 구매 또는 계약에 대해 판매자가 지정한 고유 식별자입니다. ID가 고유하다는 보장이 없습니다.| |`purchaseOrderNumber`|이 구매 또는 계약에 대해 구매자가 지정한 고유 식별자| |`payments`|이 주문에 대한 결제 목록| |`paymentType`|이 주문에 대한 결제 방법입니다. 열거된 사용자 지정 값이 허용됩니다.| |`currencyCode`|다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 결제 항목에 사용된 통화 코드| |`paymentAmount`|결제 값| |`shipping`|하나 이상의 제품에 대한 배송 세부 정보| |`shippingMethod`|표준 배송, 신속 배송, 매장 픽업 등과 같이 고객이 선택한 배송 방법| |`shippingAddress`|실제 배송 주소| |`street1`|기본 거리 수준 정보, 아파트 번호, 거리 번호 및 거리 이름| |`shippingAmount`|고객이 배송비를 지불해야 하는 금액입니다.| |`billingAddress`|청구 우편 주소| |`street1`|기본 거리 수준 정보, 아파트 번호, 거리 번호 및 거리 이름| |`street2`|거리 수준 정보를 위한 추가 필드| |`city`|도시 이름| |`state`|상태 이름입니다. 자유형이에요.| |`postalCode`|위치의 우편 번호입니다. 모든 국가에서는 우편 번호를 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만을 포함합니다.| |`country`|정부 관리 구역의 이름입니다. 기타 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식 필드입니다.|

### orderCanceled

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 취소할 때 트리거됩니다. | `commerce.orderCancelled` |

#### orderCanceled에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.
|필드|설명| |—|—| |`identityMap`|고객을 식별하는 전자 메일 주소를 포함합니다.| |`address`|기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다.| |`eventType`|`commerce.orderCancelled`| |`productListItems`|순서대로 제품 배열| |`name`|제품의 표시 이름 또는 사람이 읽을 수 있는 이름| |`SKU`|재고 유지 단위. 제품의 고유 식별자입니다.| |`quantity`|장바구니에 있는 제품 단위 수| |`priceTotal`|제품 라인 항목의 총 가격| |`discountAmount`|적용된 할인 금액을 나타냅니다.| |`order`|주문에 대한 정보를 포함합니다.| |`purchaseID`|이 구매 또는 계약에 대해 판매자가 지정한 고유 식별자입니다. ID가 고유하다는 보장이 없습니다.| |`purchaseOrderNumber`|이 구매 또는 계약에 대해 구매자가 지정한 고유 식별자|

### orderRevoked

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 항목을 순서대로 반환할 때 트리거됩니다. | `commerce.creditMemoIssued` |

#### orderRevoed에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.
|필드|설명| |—|—| |`identityMap`|고객을 식별하는 전자 메일 주소를 포함합니다.| |`address`|기술 주소(예: `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의된 바와 같습니다.| |`eventType`|`commerce.creditMemoIssued`| |`productListItems`|순서대로 제품 배열| |`order`|주문에 대한 정보를 포함합니다.| |`purchaseID`|이 구매 또는 계약에 대해 판매자가 지정한 고유 식별자입니다. ID가 고유하다는 보장이 없습니다.| |`purchaseOrderNumber`|이 구매 또는 계약에 대해 구매자가 지정한 고유 식별자|
