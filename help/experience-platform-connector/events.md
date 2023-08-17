---
title: 이벤트
description: 각 이벤트가 캡처하는 데이터를 알아봅니다.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '4779'
ht-degree: 0%

---

# Experience Platform 커넥터 이벤트

다음은 Experience Platform 커넥터 확장을 설치할 때 사용할 수 있는 상거래 이벤트 목록입니다. 이러한 이벤트가 수집하는 데이터는 Adobe Experience Platform Edge로 전송됩니다. 다음을 만들 수도 있습니다. [사용자 지정 이벤트](custom-events.md) 즉시 제공되지 않는 추가 데이터를 수집합니다.

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
| `productListAdds` | 장바구니에 제품이 추가되었는지 보여 줍니다. 값 `1` 제품이 추가되었음을 나타냅니다. |
| `productListItems` | 장바구니에 추가된 제품 배열 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `quantity` | 장바구니에 추가된 제품 단위 수 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID |

### openCart

| 설명 | XDM 이벤트 이름 |
|---|---|
| 새 장바구니가 생성될 때 트리거됩니다. 즉, 빈 장바구니에 제품이 추가될 때입니다. | `commerce.productListOpens` |

#### openCart에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `productListOpens` | 장바구니가 생성되었는지 보여 줍니다. 값 `1` 장바구니가 생성되었음을 나타냅니다. |
| `productListItems` | 장바구니에 추가된 제품 배열 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `quantity` | 장바구니에 추가된 제품 단위 수 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID |

### removeFromCart

| 설명 | XDM 이벤트 이름 |
|---|---|
| 제품이 제거되거나 장바구니에 있는 제품의 수량이 감소할 때마다 트리거됩니다. | `commerce.productListRemovals` |

#### removeFromCart에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `productListRemovals` | 장바구니에서 제품이 제거되었는지 보여 줍니다. 값 `1` 제품이 장바구니에서 제거되었음을 나타냅니다. |
| `productListItems` | 장바구니에서 제거된 제품 배열 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `quantity` | 장바구니에서 제거된 제품 단위 수 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID |

### shoppingCartView

| 설명 | XDM 이벤트 이름 |
|---|---|
| 장바구니 페이지가 로드될 때 트리거됩니다. | `commerce.productListViews` |

#### shoppingCartView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `productListViews` | 제품 목록을 보았는지 표시 |
| `productListItems` | 장바구니에 있는 제품 배열 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `quantity` | 장바구니에 있는 제품 단위의 수 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID |

### pageView

| 설명 | XDM 이벤트 이름 |
|---|---|
| 페이지가 로드될 때 트리거됩니다. | `web.webpagedetails.pageViews` |

#### pageView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `pageViews` | 페이지가 로드되었는지 보여 줍니다. A `value` / `1` 페이지가 로드되었음을 나타냅니다. |

### 제품 페이지 보기

| 설명 | XDM 이벤트 이름 |
|---|---|
| 제품 페이지가 로드되면 트리거됩니다. | `commerce.productViews` |

#### productPageView에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `productViews` | 제품을 보았는지 표시 |
| `productListItems` | 장바구니에 있는 제품 배열 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |

### startCheck

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 체크아웃 버튼을 클릭할 때 트리거됩니다. | `commerce.checkouts` |

#### startCheckout에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `checkouts` | 체크아웃 프로세스 중에 작업이 발생했는지 보여 줍니다. |
| `productListItems` | 장바구니에 있는 제품 배열 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `quantity` | 장바구니에 있는 제품 단위의 수 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 제품에 대한 통화 |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |
| `cartID` | 고객의 장바구니를 식별하는 고유 ID |

### completeCheckout

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 할 때 트리거됩니다. | `commerce.order` |

#### completeCheckout에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `purchases` | 주문이 수락되었는지 보여 줍니다. |
| `order` | 하나 이상의 제품에 대한 주문 정보가 포함되어 있습니다. |
| `purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다. |
| `orderType` | 체크아웃 또는 즉시 구매와 같이 주문된 주문 유형을 나타냅니다. |
| `payments` | 이 주문에 대한 결제 목록 |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 결제 항목에 사용된 통화 코드. 예를 들어, `USD` 또는 `EUR`. |
| `paymentAmount` | 결제 값 |
| `paymentType` | 해당 주문에 대한 결제 방법. 옵션은 다음과 같습니다. `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | 해당 결제 항목에 대한 고유 거래 식별자 |
| `shipping` | 하나 이상의 제품에 대한 배송 세부 정보. |
| `shippingMethod` | 표준 배송, 신속 배송, 매장 픽업 등 고객이 선택한 배송 방법 |
| `shippingAmount` | 장바구니에 있는 항목의 총 배송 비용 |
| `promotionID` | 프로모션에 대한 고유 식별자(있는 경우) |
| `personalEmail` | 개인 이메일 주소를 지정합니다. |
| `address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `productListItems` | 장바구니에 있는 제품 배열 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `quantity` | 장바구니에 있는 제품 단위의 수 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 주문 합계에 사용되는 통화 코드입니다. |
| `productImageUrl` | 제품의 기본 이미지 URL |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |

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
| `person` | 개인 작업자, 연락처 또는 소유자 |
| `accountID` | 사용자 계정 ID 캡처 |
| `accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당되는 경우 |
| `personalEmailID` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `personalEmail` | 연락처 세부 정보 - 이메일 및 관련 정보 캡처 |
| `address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `login` | 방문자가 로그인을 시도했는지 여부를 나타냅니다. |

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
| `logout` | 방문자가 로그아웃을 시도했는지 여부를 나타냅니다. |

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
| `person` | 개인 작업자, 연락처 또는 소유자 |
| `accountID` | 사용자 계정 ID 캡처 |
| `accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당되는 경우 |
| `personalEmailID` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `personalEmail` | 연락처 세부 정보 - 이메일 및 관련 정보 캡처 |
| `address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `createProfile` | 사용자가 계정 프로필을 만들었는지 여부를 나타냅니다. |

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
| `person` | 개인 작업자, 연락처 또는 소유자 |
| `accountID` | 사용자 계정 ID 캡처 |
| `accountType` | 다음과 같은 사용자 계정 유형을 캡처합니다. `Personal` 또는 `Company`, 해당되는 경우 |
| `personalEmailID` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `personalEmail` | 연락처 세부 정보 - 이메일 및 관련 정보 캡처 |
| `address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `updateProfile` | 사용자가 계정 프로필을 업데이트했는지 보여 줍니다. |

## 이벤트 검색

검색 이벤트는 구매자의 의도와 관련된 데이터를 제공합니다. 쇼핑객의 의도에 대한 통찰력은 쇼핑객이 품목을 검색하는 방법, 고객이 클릭하는 항목, 궁극적으로 구매 또는 포기를 수행하는 방법을 가맹점이 확인하는 데 도움이 됩니다. 이 데이터를 사용하는 방법의 예로는 상위 제품을 검색하지만 제품을 구매하지 않는 기존 구매자를 타겟팅하려는 경우입니다.

사용 `uniqueIdentifier` 필드 둘 다에 있음 `searchRequestSent` 및 `searchResponseReceived` 검색 요청을 해당 검색 응답과 상호 참조할 이벤트.

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
| `id` | 이 특정 검색 요청에 대한 고유 ID |
| `filter` | 검색 결과 제한에 필터가 적용되었는지 보여 줍니다. |
| `attribute` (필터) | 항목을 검색 결과에 포함할지 여부를 결정하는 데 사용되는 항목의 패싯 |
| `value` | 검색 결과에 포함된 항목을 결정하는 데 사용되는 속성 값 |
| `isRange` | true인 경우 값은 허용되는 값 범위의 끝점을 나타냅니다 |
| `sort` | 검색 결과를 정렬하는 방법을 나타냅니다. |
| `attribute` (정렬) | 검색 결과에서 항목을 정렬하는 데 사용되는 속성 |
| `order` | 검색 결과를 반환하는 순서 |
| `query` | 검색어 |

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
| `searchResponse` | 검색 응답이 수신되었는지 보여 줍니다. |
| `id` | 이 특정 검색 응답에 대한 고유 ID |
| `suggestions` | 카탈로그에 있는 검색 쿼리와 유사한 제품 및 범주를 포함하는 문자열 배열 |
| `numberOfResults` | 반환된 제품 수 |
| `productListItems` | 장바구니에 있는 제품 배열. |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `productImageUrl` | 제품의 기본 이미지 URL |

## B2B 이벤트

![Adobe Commerce용 B2B](../assets/b2b.svg) B2B 판매자의 경우 다음을 수행해야 합니다 [설치](install.md#install-the-b2b-extension) 다음 `experience-platform-connector-b2b` 확장을 사용하여 이러한 이벤트를 활성화합니다.

B2B 이벤트에는 [징발 목록](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) 구매요청 목록이 생성되었는지, 추가되었는지, 삭제되었는지를 나타내는 정보. 구매요청 목록과 관련된 이벤트를 추적하여 고객이 자주 구매하는 제품을 확인하고 해당 데이터를 기반으로 캠페인을 생성할 수 있습니다.

### createRequisitionList

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 새 구매 요청 목록을 만들 때 트리거됩니다. | `commerce.requisitionListOpens` |

#### createRequisitionList에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `requisitionList` | 고객이 생성한 구매요청 목록의 속성 |
| `ID` | 구매요청 목록의 고유 식별자 |
| `name` | 고객이 지정한 구매요청 목록의 이름 |
| `description` | 고객이 지정한 구매요청 목록에 대한 설명 |

### addToRequisitionList

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 기존 요청 목록에 제품을 추가하거나 새 목록을 만들 때 트리거됩니다. | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` 카테고리 보기 페이지 또는 구성 가능한 제품에 대해서는 가 지원되지 않습니다. 제품 보기 페이지 및 간단한 제품에 대해 지원됩니다.

#### addToRequisitionList에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `requisitionList` | 고객이 생성한 구매요청 목록의 속성 |
| `ID` | 구매요청 목록의 고유 식별자 |
| `name` | 고객이 지정한 구매요청 목록의 이름 |
| `description` | 고객이 지정한 구매요청 목록에 대한 설명 |
| `productListItems` | 구매요청 목록에 추가된 제품 배열 |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `quantity` | 추가된 제품 단위 수 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 결제 항목에 사용된 통화 코드 |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |

### removeFromRequisitionList

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 구매요청 목록에서 제품을 제거할 때 트리거됩니다. | `commerce.requisitionListRemovals` |

#### removeFromRequisitionList에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `requisitionList` | 고객이 생성한 구매요청 목록의 속성 |
| `ID` | 구매요청 목록의 고유 식별자 |
| `name` | 고객이 지정한 구매요청 목록의 이름 |
| `description` | 고객이 지정한 구매요청 목록에 대한 설명 |
| `productListItems` | 구매요청 목록에 추가된 제품 배열 |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `quantity` | 추가된 제품 단위 수 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 결제 항목에 사용된 통화 코드 |
| `selectedOptions` | 구성 가능한 제품에 사용되는 필드. `attribute` 는 구성 가능한 제품의 속성을 식별합니다. 예: `size` 또는 `color` 및 `value` 는 다음과 같은 속성 값을 식별합니다. `small` 또는 `black`. |

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
| `address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에서 일반적으로 정의됨 |
| `productListItems` | 순서대로 정렬된 제품 배열 |
| `id` | 해당 제품 항목에 대한 라인 항목 식별자. 제품 자체는 를 통해 식별됩니다. `product` 필드. |
| `name` | 제품의 표시 이름 또는 사람이 인식할 수 있는 이름 |
| `SKU` | 재고 관리 장치. 제품에 대한 고유 식별자. |
| `quantity` | 장바구니에 있는 제품 단위의 수 |
| `priceTotal` | 제품 라인 항목에 대한 총 가격 |
| `discountAmount` | 적용된 할인 금액을 나타냅니다. |
| `commerceScope` | 이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다. |
| `environmentID` | 환경 ID. 하이픈으로 구분된 32자리 영숫자 ID. |
| `storeCode` | 고유한 스토어 코드. 웹사이트당 많은 매장이 있을 수 있습니다. |
| `storeViewCode` | 고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다. |
| `websiteCode` | 고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다. |
| `order` | 주문에 대한 정보 포함 |
| `purchaseID` | 판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다고 보장할 수는 없습니다 |
| `priceTotal` | 할인과 세금이 모두 적용된 후 이 주문의 총 가격 |
| `currencyCode` | 주문 합계에 사용되는 ISO 4217 통화 코드 |
| `purchaseOrderNumber` | 구매자가 해당 구매 또는 계약에 할당한 고유 식별자 |
| `payments` | 이 주문에 대한 결제 목록 |
| `paymentType` | 해당 주문에 대한 결제 방법. 열거됨, 사용자 정의 값이 허용됨. |
| `currencyCode` | 다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 결제 항목에 사용된 통화 코드 |
| `paymentAmount` | 결제 값 |
| `taxAmount` | 최종 지급의 일부로 구매자가 지불한 세액 |
| `createdDate` | 상거래 시스템에서 새 주문이 생성된 시간 및 날짜. For example, `2022-10-15T20:20:39+00:00` |
| `shipping` | 하나 이상의 제품에 대한 배송 세부 정보 |
| `shippingMethod` | 표준 배송, 신속 배송, 매장 픽업 등 고객이 선택한 배송 방법 |
| `shippingAmount` | 고객이 배송비로 지불해야 했던 금액. |
| `address` | 실제 배송 주소 |
| `street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명 |
| `street2` | 거리 수준 정보를 위한 추가 필드 |
| `city` | 도시 이름 |
| `state` | 상태 이름. 자유 형식의 필드입니다. |
| `postalCode` | 위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다. |
| `country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `billingAddress` | 청구 우편 주소 |
| `street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명 |
| `street2` | 거리 수준 정보를 위한 추가 필드 |
| `city` | 도시 이름 |
| `state` | 상태 이름. 자유 형식의 필드입니다. |
| `postalCode` | 위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다. |
| `country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `personalEmail` | 개인 이메일 주소 |
| `address` | RFC2822 및 이후 표준에서 일반적으로 정의하는 기술 주소(예: &#39;name@domain.com&#39;) |

### orderItemsShipped

| 설명 | XDM 이벤트 이름 |
|---|---|
| 주문이 배송될 때 트리거됩니다. | `commerce.backofficeOrderItemsShipped` |

#### orderItemsShipped에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.
|필드|설명| |—|—| |`address`|기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에 정의된 대로| |`productListItems`|순서대로 제품 배열| |`id`|이 제품 항목에 대한 라인 항목 식별자. 제품 자체는 를 통해 식별됩니다. `product` 필드.| |`name`|제품의 표시 이름 또는 사람이 인식할 수 있는 이름| |`SKU`|재고 유지 단위. 제품에 대한 고유 식별자.| |`quantity`|장바구니에 있는 제품 수| |`priceTotal`|제품 라인 항목의 총 가격| |`discountAmount`|적용되는 할인 금액을 나타냅니다| |`commerceScope`|이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다.| |`environmentID`|환경 ID. 하이픈으로 구분된 32자리 영숫자 ID.| |`storeCode`|고유한 스토어 코드입니다. 웹사이트당 많은 매장이 있을 수 있습니다.| |`storeViewCode`|고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다.| |`websiteCode`|고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다.| |`order`|주문에 대한 정보 포함| |`purchaseID`|판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다는 보장은 없습니다| |`priceTotal`|모든 할인 및 세금이 적용된 후 이 주문의 총 가격| |`currencyCode`|주문 합계에 사용되는 ISO 4217 통화 코드| |`purchaseOrderNumber`|구매자가 해당 구매 또는 계약에 할당한 고유 식별자| |`payments`|이 주문에 대한 결제 목록| |`paymentType`|이 주문에 대한 결제 방법입니다. 열거됨, 사용자 정의 값이 허용됨.| |`currencyCode`|다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 결제 항목에 사용된 통화 코드| |`paymentAmount`|결제 값| |`lastUpdatedDate`|특정 주문 레코드가 상거래 시스템에서 마지막으로 업데이트된 시간| |`shipping`|하나 이상의 제품에 대한 배송 세부 정보| |`shippingMethod`|표준 배송, 신속 배송, 매장 픽업 등 고객이 선택한 배송 방법| |`trackingNumber`|주문 항목 배송에 대해 배송 회사가 제공한 추적 번호| |`trackingURL`|주문 항목의 배송 상태를 추적할 URL| |`shipDate`|주문에서 하나 이상의 품목이 배송된 날짜| |`address`|실제 배송 주소| |`street1`|기본 거리 수준 정보, 아파트 번호, 거리 번호 및 거리 이름| |`street2`|거리 수준 정보를 위한 추가 필드| |`city`|도시 이름| |`state`|상태 이름. 자유 형식의 필드입니다.| |`postalCode`|위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다.| |`country`|정부에서 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다.| |`shippingAmount`|고객이 배송비로 지불해야 했던 금액입니다.| |`billingAddress`|청구 우편 주소| |`street1`|기본 거리 수준 정보, 아파트 번호, 거리 번호 및 거리 이름| |`street2`|거리 수준 정보를 위한 추가 필드| |`city`|도시 이름| |`state`|상태 이름. 자유 형식의 필드입니다.| |`postalCode`|위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다.| |`country`|정부에서 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다.| |`personalEmail`|개인 이메일 주소| |`address`|기술 주소(예: RFC2822 및 후속 표준에 정의된 &#39;name@domain.com&#39;)|

### orderCanceled

| 설명 | XDM 이벤트 이름 |
|---|---|
| 쇼핑객이 주문을 취소할 때 트리거됩니다. | `commerce.backofficeOrderCancelled` |

#### orderCanceled에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.
|필드|설명| |—|—| |`address`|기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에 정의된 대로| |`productListItems`|순서대로 제품 배열| |`id`|이 제품 항목에 대한 라인 항목 식별자. 제품 자체는 를 통해 식별됩니다. `product` 필드.| |`name`|제품의 표시 이름 또는 사람이 인식할 수 있는 이름| |`SKU`|재고 유지 단위. 제품에 대한 고유 식별자.| |`quantity`|장바구니에 있는 제품 수| |`priceTotal`|제품 라인 항목의 총 가격| |`discountAmount`|적용되는 할인 금액을 나타냅니다| |`commerceScope`|이벤트가 발생한 위치(스토어 보기, 스토어, 웹 사이트 등)를 나타냅니다.| |`environmentID`|환경 ID. 하이픈으로 구분된 32자리 영숫자 ID.| |`storeCode`|고유한 스토어 코드입니다. 웹사이트당 많은 매장이 있을 수 있습니다.| |`storeViewCode`|고유한 스토어 보기 코드입니다. 매장당 여러 개의 매장을 볼 수 있습니다.| |`websiteCode`|고유 웹 사이트 코드. 하나의 환경에 여러 개의 웹 사이트가 있을 수 있습니다.| |`order`|주문에 대한 정보 포함| |`purchaseID`|판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다는 보장은 없습니다| |`purchaseOrderNumber`|구매자가 해당 구매 또는 계약에 할당한 고유 식별자| |`cancelDate`|구매자가 주문을 취소한 날짜 및 시간| |`lastUpdatedDate`|특정 주문 레코드가 상거래 시스템에서 마지막으로 업데이트된 시간| |`personalEmail`|개인 이메일 주소| |`address`|기술 주소(예: RFC2822 및 후속 표준에 정의된 &#39;name@domain.com&#39;)|

### 대변 메모 발행됨

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 주문에서 항목을 반환할 때 트리거됩니다. | `commerce.backofficeCreditMemoIssued` |

#### creditMemoIssued에서 수집된 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.
|필드|설명| |—|—| |`address`|기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에 정의된 대로| |`productListItems`|순서대로 제품 배열| |`id`|이 제품 항목에 대한 라인 항목 식별자. 제품 자체는 를 통해 식별됩니다. `product` 필드.| |`name`|제품의 표시 이름 또는 사람이 인식할 수 있는 이름| |`SKU`|재고 유지 단위. 제품에 대한 고유 식별자.| |`quantity`|장바구니에 있는 제품 수| |`priceTotal`|제품 라인 항목의 총 가격| |`discountAmount`|적용되는 할인 금액을 나타냅니다| |`order`|주문에 대한 정보 포함| |`purchaseID`|판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다는 보장은 없습니다| |`purchaseOrderNumber`|구매자가 해당 구매 또는 계약에 할당한 고유 식별자| |`lastUpdatedDate`|특정 주문 레코드가 상거래 시스템에서 마지막으로 업데이트된 시간| |`personalEmail`|개인 이메일 주소| |`address`|기술 주소(예: RFC2822 및 후속 표준에 정의된 &#39;name@domain.com&#39;)|

### orderShipmentCompleted

| 설명 | XDM 이벤트 이름 |
|---|---|
| 구매자가 주문에서 항목을 반환할 때 트리거됩니다. | `commerce.backofficeOrderShipmentCompleted` |

#### orderShipmentCompleted에서 수집한 데이터

다음 표에서는 이 이벤트에 대해 수집된 데이터에 대해 설명합니다.
|필드|설명| |—|—| |`address`|기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에 정의된 대로| |`productListItems`|순서대로 제품 배열| |`id`|이 제품 항목에 대한 라인 항목 식별자. 제품 자체는 를 통해 식별됩니다. `product` 필드.| |`name`|제품의 표시 이름 또는 사람이 인식할 수 있는 이름| |`SKU`|재고 유지 단위. 제품에 대한 고유 식별자.| |`quantity`|장바구니에 있는 제품 수| |`priceTotal`|제품 라인 항목의 총 가격| |`discountAmount`|적용되는 할인 금액을 나타냅니다| |`order`|주문에 대한 정보 포함| |`purchaseID`|판매자가 해당 구매 또는 계약에 할당한 고유 식별자. ID가 고유하다는 보장은 없습니다| |`priceTotal`|모든 할인 및 세금이 적용된 후 이 주문의 총 가격| |`currencyCode`|주문 합계에 사용되는 ISO 4217 통화 코드| |`purchaseOrderNumber`|구매자가 해당 구매 또는 계약에 할당한 고유 식별자| |`taxAmount`|최종 지급의 일부로 구매자가 지불한 세액| |`createdDate`|상거래 시스템에서 새 주문이 생성된 시간과 날짜입니다. 예를 들어, `2022-10-15T20:20:39+00:00`| |`payments`|이 주문에 대한 결제 목록| |`paymentType`|이 주문에 대한 결제 방법입니다. 열거됨, 사용자 정의 값이 허용됨.| |`currencyCode`|다음 [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) 이 결제 항목에 사용된 통화 코드| |`paymentAmount`|결제 값| |`shipping`|하나 이상의 제품에 대한 배송 세부 정보| |`shippingMethod`|표준 배송, 신속 배송, 매장 픽업 등 고객이 선택한 배송 방법| |`address`|실제 배송 주소| |`street1`|기본 거리 수준 정보, 아파트 번호, 거리 번호 및 거리 이름| |`street2`|거리 수준 정보를 위한 추가 필드| |`city`|도시 이름| |`state`|상태 이름. 자유 형식의 필드입니다.| |`postalCode`|위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 우편 번호의 일부만 포함됩니다.| |`country`|정부에서 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다.| |`shippingAmount`|고객이 배송비로 지불해야 했던 금액입니다.| |`address`|기술 주소(예: ) `name@domain.com` RFC2822 및 후속 표준에 정의된 대로| |`billingAddress`|청구 우편 주소| |`street1`|기본 거리 수준 정보, 아파트 번호, 거리 번호 및 거리 이름| |`street2`|거리 수준 정보를 위한 추가 필드| |`city`|도시 이름| |`state`|상태 이름. 자유 형식의 필드입니다.| |`postalCode`|위치의 우편 번호입니다. 우편 번호는 모든 국가에서 사용할 수 없습니다. 일부 국가에서는 이 데이터에 우편 번호 일부만 포함되어 있습니다.| |`country`|정부에서 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다.| |`personalEmail`|개인 이메일 주소| |`address`|기술 주소(예: RFC2822 및 후속 표준에 정의된 &#39;name@domain.com&#39;)|
