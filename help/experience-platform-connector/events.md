---
title: 이벤트
description: 각 이벤트가 캡처하는 데이터를 알아봅니다.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: aaaab3d11c15a69856711a41e889a5d0208aedd2
workflow-type: tm+mt
source-wordcount: '1977'
ht-degree: 0%

---

# Experience Platform 커넥터 이벤트

다음은 Experience Platform 커넥터 확장을 설치할 때 사용할 수 있는 상거래 이벤트 목록입니다. 이러한 이벤트가 수집하는 데이터는 Adobe Experience Platform Edge로 전송됩니다. 만들 수도 있습니다 [사용자 지정 이벤트](custom-events.md) 기본적으로 제공되지 않은 추가 데이터를 수집하기 위해

다음 이벤트가 수집하는 데이터 외에도 [기타 데이터](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) Adobe Experience Platform Web SDK에서 제공합니다.

>[!NOTE]
>
>모든 상점 이벤트에는 `personID` 필드의 고유 식별자입니다.

## addToCart

장바구니에 제품을 추가하거나 장바구니의 제품 수량이 증가될 때 트리거됩니다.

### XDM 이벤트 이름

`commerce.productListAdds`

### 유형

상점

### 수집한 데이터

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

## openCart

새 장바구니가 생성될 때, 즉 제품을 빈 장바구니에 추가할 때 트리거됩니다.

### XDM 이벤트 이름

`commerce.productListOpens`

### 유형

상점

### 수집한 데이터

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

## removeFromCart

제품이 제거되거나 장바구니의 제품 수량이 감소될 때마다 트리거됩니다.

### XDM 이벤트 이름

`commerce.productListRemovals`

### 유형

상점

### 수집한 데이터

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

## shoppingCartView

장바구니 페이지가 로드될 때 트리거됩니다.

### XDM 이벤트 이름

`commerce.productListViews`

### 유형

상점

### 수집한 데이터

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

## pageView

페이지가 로드될 때 트리거됩니다.

### XDM 이벤트 이름

`web.webpagedetails.pageViews`

### 유형

상점

### 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `pageViews` | 페이지가 로드되었는지 여부를 나타냅니다. A `value` 의 `1` 페이지가 로드되었음을 나타냅니다. |

## productPageView

제품 페이지가 로드될 때 트리거됩니다.

### XDM 이벤트 이름

`commerce.productViews`

### 유형

상점

### 수집한 데이터

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

## startCheckout

쇼핑객이 체크아웃 단추를 클릭할 때 트리거됩니다.

### XDM 이벤트 이름

`commerce.checkouts`

### 유형

상점

### 수집한 데이터

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

## completeCheckout

쇼핑객이 주문을 할 때 트리거됩니다.

### XDM 이벤트 이름

`commerce.order`

### 유형

상점

### 수집한 데이터

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
| `productListItems` | 장바구니에 있는 일련의 제품 |
| `SKU` | 주식 보유 단위입니다. 제품의 고유 식별자입니다. |
| `name` | 제품의 표시 이름 또는 사람이 읽을 수 있는 이름 |
| `priceTotal` | 제품 라인 항목의 총 가격 |
| `quantity` | 장바구니에 있는 제품 단위 수입니다 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 주문 합계에 사용되는 통화 코드. |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드입니다. `attribute` 는 다음과 같이 구성 가능한 제품의 속성을 식별합니다 `size` 또는 `color` 및 `value` 와 같은 속성의 값을 식별합니다. `small` 또는 `black`. |

## signIn

쇼핑객이 로그인하려고 할 때 트리거됩니다.

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

### XDM 이벤트 이름

`userAccount.login`

### 유형

프로필

### 수집한 데이터

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

## signOut

쇼핑객이 로그아웃하려 할 때 트리거됩니다.

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

### XDM 이벤트 이름

`userAccount.logout`

### 유형

프로필

### 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `eventType` | 다음과 같은 이 시계열 레코드의 기본 이벤트 유형: `userAccount.logout` |
| `userAccount` | 충성도 세부 사항, 환경 설정, 로그인 프로세스 및 기타 계정 기본 설정을 나타냅니다 |
| `logout` | 방문자가 로그아웃하려고 했는지 여부를 나타냅니다 |

## createAccount

쇼핑객이 계정을 만들려고 할 때 트리거됩니다.

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

### XDM 이벤트 이름

`userAccount.createProfile`

### 유형

프로필

### 수집한 데이터

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

## editAccount

쇼핑객이 계정을 편집하려고 할 때 트리거됩니다.

>[!NOTE]
>
> 이 이벤트는 특정 작업이 시도될 때 트리거됩니다. 작업이 성공했음을 나타내지 않습니다.

### XDM 이벤트 이름

`userAccount.updateProfile`

### 유형

프로필

### 수집한 데이터

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

## searchRequestSent

&quot;입력할 때 검색&quot; 팝오버에서 다음 이벤트에 의해 트리거됩니다.

- Enter 키를 누릅니다.
- 클릭 _모두 보기_

검색 결과 페이지에서 다음 이벤트에 의해 트리거됩니다.

- 필터 선택
- 정렬 순서 변경(_정렬 기준_)
- 정렬 방향 변경(오름차순 또는 내림차순)
- 페이지당 결과 수 변경(_페이지당 # 표시_)
- 다음 페이지로 이동합니다
- 이전 페이지로 이동합니다
- 다른 페이지로 이동

>[!NOTE]
>
>검색 이벤트는 B2B 모듈이 설치된 Adobe Commerce Enterprise Edition에서 지원되지 않습니다.

### XDM 이벤트 이름

`searchRequest`

### 유형

검색

### 수집한 데이터

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

## searchResponseReceived

Live Search가 &quot;입력한 대로 검색&quot; 팝업 또는 검색 결과 페이지에 대한 결과를 반환하는 경우 트리거됩니다.

>[!NOTE]
>
>검색 이벤트는 B2B 모듈이 설치된 Adobe Commerce Enterprise Edition에서 지원되지 않습니다.

### XDM 이벤트 이름

`searchResponse`

### 유형

검색

### 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터를 설명합니다.

| 필드 | 설명 |
|---|---|
| `searchResponse` | 검색 응답이 수신되었는지 여부를 나타냅니다. |
| `suggestions` | 검색 쿼리와 유사한 카탈로그에 있는 제품 및 카테고리의 이름을 포함하는 문자열 배열입니다 |
| `numberOfResults` | 반환된 제품 수 |
| `productListItems` | 장바구니에 있는 일련의 제품입니다. 다음을 포함합니다 `SKU`(주식 보유 단위) 및 `name` 제품(표시 이름 또는 사람이 읽을 수 있는 이름) |
