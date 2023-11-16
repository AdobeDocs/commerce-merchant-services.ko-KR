---
title: Adobe Experience Platform 태그를 사용하여 상거래 데이터 수집
description: Adobe Experience Platform 태그를 사용하여 상거래 데이터를 수집하는 방법에 대해 알아봅니다.
exl-id: 852fc7d2-5a5f-4b09-8949-e9607a928b44
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 71e73b900db024eee6e7e11cbddbabf332acf70a
workflow-type: tm+mt
source-wordcount: '2635'
ht-degree: 0%

---

# Adobe Experience Platform 태그를 사용하여 상거래 데이터 수집

사용할 수 있는 동안 [!DNL Data Connection] storefront 이벤트를 게시하고 구독하기 위한 확장으로, 일부 판매자는 이미 다음과 같은 데이터 수집 솔루션을 사용하고 있을 수 있습니다. [Adobe Experience Platform 태그](https://experienceleague.adobe.com/docs/platform-learn/data-collection/tags/create-a-property.html). 이러한 판매자의 경우 Adobe Commerce에서 게시 전용 옵션을 제공합니다. [!DNL Data Connection] Adobe Commerce 이벤트 SDK를 사용하는 확장입니다.

![[!DNL Data Connection] 확장 데이터 흐름](assets/tags-data-flow.png)
_[!DNL Data Connection]태그를 사용한 확장 데이터 흐름_

이 항목에서는 다음에서 제공하는 상점 이벤트 값을 매핑하는 방법을 알아봅니다. [!DNL Data Connection] 이미 사용 중인 Adobe Experience Platform 태그 솔루션에 대한 확장입니다.

## Adobe Commerce에서 이벤트 데이터 수집

상거래 이벤트 데이터를 수집하려면:

- 설치 [Adobe Commerce 이벤트 SDK](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-sdk). PHP 상점 앞면은 [설치](install.md) 주제. PWA Studio 상점 앞면에 대해서는 [PWA Studio 안내서](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/).

  >[!NOTE]
  >
  > 실행 **아님** [구성](connect-data.md) 조직 ID 및 데이터 스트림 ID입니다.

## Commerce 상점 데이터를 Adobe Experience Platform에 매핑

Commerce 상점 데이터를 Adobe Experience Platform에 매핑하려면 Adobe Experience Platform 태그 내에서 다음을 구성 및 설치합니다.

1. [태그 속성 설정](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/create-a-property.html) Adobe Experience Platform 데이터 수집에서.

1. 아래 **작성**, 선택 **확장** 및 다음 확장을 설치하고 구성합니다.

   - [Adobe 클라이언트 데이터 레이어](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html)

   - [Adobe Experience Platform 웹 SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/installing-the-sdk.html)

1. [태그 게시](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html) 를 개발 환경에 배포합니다.

1. 다음 **이벤트 매핑** 특정 이벤트에 대한 데이터 요소 및 규칙을 구성하려면 아래 단계를 따르십시오.

### 이벤트 매핑

태그를 사용한 데이터 수집은 Adobe Commerce 이벤트 SDK를 사용하는 것과 다르므로 두 프레임워크에 사용된 것과 동일한 용어를 이해하는 것이 중요합니다.

| Adobe Experience Platform 태그 용어 | Adobe Commerce 이벤트 SDK 용어 |
|---|---|
| _데이터 요소_ | 컨텍스트 |
| _규칙_ | 이벤트 |
|  | _규칙 조건_ - 이벤트 리스너(ACDL에서)<br><br>_규칙 작업_ - 이벤트 핸들러(Adobe Experience Platform으로 전송) |

Adobe Experience Platform 태그의 데이터 요소와 규칙을 Adobe Commerce 관련 이벤트 데이터로 업데이트할 때 수행해야 하는 몇 가지 일반적인 단계가 있습니다.

예를 들어 Adobe Commerce을 추가하겠습니다 `signOut` 이벤트 를 Adobe Experience Platform 태그에 추가합니다. 설정한 특정 값을 제외하고 아래에 설명된 단계에서 추가 방법을 설명합니다. [데이터 요소](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#data-element) 및 [규칙](https://experienceleague.adobe.com/docs/experience-platform/collection/e2e.html#create-a-rule): 태그에 추가하는 모든 Adobe Commerce 이벤트에 적용됩니다.

1. 데이터 요소 만들기:

   ![새 데이터 요소 만들기](assets/create-new-data-elements.png)
   _새 데이터 요소 만들기_

1. 설정 **이름** 끝 `sign out`.

1. 설정 **확장** 끝 `Adobe Experience Platform Web SDK`.

1. 설정 **데이터 요소 유형** 끝 `XDM object`.

1. 다음 항목 선택 **샌드박스** 및 **스키마** 을 참조하십시오.

1. 아래 **userAccount** > **로그아웃**, 를 설정합니다. **값** 위치: **방문자 로그아웃** 끝 `1`.

   ![로그아웃 값 업데이트](assets/signout-value.png)
   _로그아웃 값 업데이트_

1. 선택 **저장**.

1. 규칙 만들기:

   ![새 규칙 만들기](assets/create-new-rule.png)
   _새 규칙 만들기_

1. 선택 **추가** 아래에 **이벤트**.

1. 설정 **확장** 끝 `Adobe Client Data Layer`.

1. 설정 **이벤트 유형** 끝 `Data Pushed`.

1. 선택 **특정 이벤트** 및 설정 **등록할 이벤트/키** 끝 `sign-out`.

1. 선택 **변경 내용 유지** 새 규칙을 저장합니다.

1. 작업을 추가합니다.

1. 설정 **확장** 끝 `Adobe Experience Platform Web SDK`.

1. 설정 **작업 유형** 끝 `Send Event`.

1. 설정 **인스턴스** 끝 `Alloy`.

1. 설정 **유형** 끝 `userAccount.logout`.

1. 설정 **XDM 데이터** 끝 `%sign out%`.

1. 클릭 **저장**.

   스키마에서 다음에 대한 데이터 요소를 만들었습니다. `signOut` Adobe Commerce의 이벤트입니다. 또한 Adobe Commerce 상점 첫 화면에서 해당 이벤트가 실행될 때 발생해야 하는 특정 작업을 사용하여 규칙을 만들었습니다.

아래 설명된 각 Adobe Commerce 이벤트에 대해 태그에 위의 단계를 반복합니다.

## 사용 가능한 이벤트

다음 각 이벤트에 대해 위의 단계에 따라 Adobe Commerce 이벤트를 XDM에 매핑합니다.

- [&#39;로그아웃&#39;](#signout)
- [&#39;로그인&#39;](#signin)
- [`createAccount`](#createaccount)
- [`editAccount`](#editaccount)
- [&#39;pageView&#39;](#pageview)
- [&#39;productView&#39;](#productview)
- [`searchRequestSent`](#searchrequestsent)
- [`searchResponseReceived`](#searchresponsereceived)
- [`addToCart`](#addtocart)
- [&#39;openCart&#39;](#opencart)
- [`viewCart`](#viewcart)
- [`removeFromCart`](#removefromcart)
- [`initiateCheckout`](#initiatecheckout)
- [&#39;placeOrder&#39;](#placeorder)

### 로그아웃

쇼핑객이 로그아웃하려고 할 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 로그아웃:

   - **이름**: `Sign out`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `userAccount` > `logout`
   - **방문자 로그아웃**: **값** = `1`

#### 규칙 

- **이름**: `Sign out`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `sign-out`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `userAccount.logout`
- **XDM 데이터**: `%sign-out%`

### 로그인

쇼핑객이 로그인을 시도할 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 계정 이메일:

   - **이름**: `account email`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.emailAddress`

1. 계정 유형:

   - **이름**: `account type`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.accountType`

1. 계정 ID:

   - **이름**: `account id`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로***: `accountContext.accountId`

1. 로그인:

   - **이름**: `sign in`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `person` > `accountID`
   - **계정 ID**: **값** = `%account id%`
   - **필드 그룹**: `person` > `accountType`
   - **계정 유형**: **값** = `%account type%`
   - **필드 그룹**: `person` > `personalEmailID`
   - **개인 이메일 주소**: **값** = `%account email%`
   - **필드 그룹**: `personalEmail` > `address`
   - **주소**: **값** = `%account email%`
   - **필드 그룹**: `userAccount` > `login`
   - **방문자 로그인**: **값** = `1`

#### 규칙 

- **이름**: `sign in`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `sign-in`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `userAccount.login`
- **XDM 데이터**: `%sign in%`

### createAccount

쇼핑객이 계정을 만들려고 할 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 계정 이메일:

   - **이름**: `account email`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.emailAddress`

1. 계정 유형:

   - **이름**: `account type`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.accountType`

1. 계정 ID:

   - **이름**: `account id`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.accountId`

1. 계정 만들기:

   - **이름**: `Create account`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `person` > `accountID`
   - **계정 ID**: **값** = `%account id%`
   - **필드 그룹**: `person` > `accountType`
   - **계정 유형**: **값** = `%account type%`
   - **필드 그룹**: `person` > `personalEmailID`
   - **개인 이메일 주소**: **값** = `%account email%`
   - **필드 그룹**: `personalEmail` > `address`
   - **주소**: **값** = `%account email%`
   - **필드 그룹**: `userAccount` > `createProfile`
   - **계정 프로필 만들기**: **값** = `1`

#### 규칙 

- **이름**: `Create account`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `create-account`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `userAccount.createProfile`
- **XDM 데이터**: `%create account%`

### editAccount

쇼핑객이 계정을 편집하려고 할 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 계정 이메일:

   - **이름**: `account email`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.emailAddress`

1. 계정 유형:

   - **이름**: `account type`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.accountType`

1. 계정 ID:

   - **이름**: `account id`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.accountId`

1. 계정 편집:

   - **이름**: `Edit account`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `person` > `accountID`
   - **계정 ID**: **값** = `%account id%`
   - **필드 그룹**: `person` > `accountType`
   - **계정 유형**: **값** = `%account type%`
   - **필드 그룹**: `person` > `personalEmailID`
   - **개인 이메일 주소**: **값** = `%account email%`
   - **필드 그룹**: `personalEmail` > `address`
   - **주소**: **값** = `%account email%`
   - **필드 그룹**: `userAccount` > `updateProfile`
   - **계정 프로필 만들기**: **값** = `1`

#### 규칙

- **이름**: `Edit account`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `edit-account`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `userAccount.updateProfile`
- **XDM 데이터**: `%edit account%`

### pageView

페이지가 로드될 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 페이지 이름:

   - **이름**: `page name`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `pageContext.pageName`

#### 규칙 

- **이름**: `page view`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `page-view`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `web.webPageDetails.pageViews`
- **XDM 데이터**: `%page view%`

### productView

제품 페이지가 로드되면 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 제품 이름:

   - **이름**: `product name`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.name`

1. 제품 SKU:

   - **이름**: `product sku`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.sku`

1. 제품 이미지 URL:

   - **이름**: `product image`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.mainImageUrl`

1. 제품 통화:

   - **이름**: `product currency`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.currencyCode`

1. 통화 코드:

   - **이름**: `currency code`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('product currency') || _satellite.getVar('storefront').storeViewCurrencyCode
   ```

1. 특별 가격:

   - **이름**: `special price`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.specialPrice`

1. 정규 가격:

   - **이름**: `regular price`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.regularPrice`

1. 제품 가격:

   - **이름**: `product price`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price')
   ```

1. 제품 보기:

   - **이름**: `product view`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `productListItems`. 선택 **개별 항목 제공** 을(를) 클릭하고 **항목 추가** 단추를 클릭합니다. 이 보기는 PDP용이므로 단일 항목으로 채울 수 있습니다.
   - **필드 그룹**: `productListItems` > `name`
   - **이름**: **값** = `%product name%`
   - **필드 그룹**: `productListItems` > `SKU`
   - **SKU**: **값** = `%product sku%`
   - **필드 그룹**: `productListItems` > `priceTotal`
   - **가격 합계**: **값** = `%product price%`
   - **필드 그룹**: `productListItems` > `currencyCode`
   - **통화 코드**: **값** = `%currency code%`
   - **필드 그룹**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **값** = `%product image%`
   - **필드 그룹**: `commerce` > `productViews` > `value`
   - **값**: **값** = `1`

#### 규칙 

- **이름**: `product view`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `product-page-view`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `commerce.productViews`
- **XDM 데이터**: `%product view%`

### searchRequestSent

입력할 때 검색 팝오버의 이벤트 및 검색 결과 페이지의 이벤트에 의해 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 검색 입력

   - **이름**: `search input`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `searchInputContext.units[0]`

1. 입력 구문 검색

   - **이름**: `search input phrase`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('search input').phrase;
   ```

1. 검색 입력 정렬

   - **이름**: `search input sort`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const sortFromInput = searchInput ? searchInput.sort : [];
   const sort = sortFromInput.map((searchSort) => {
       return {
           attribute: searchSort.attribute,
           order: searchSort.direction,
       };
   });
   return sort;
   ```

1. 입력 필터 검색

   - **이름**: `search input filters`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const searchInput = _satellite.getVar('search input');
   const filtersFromInput = searchInput ? searchInput.filter : [];
   const filters = filtersFromInput.map(
       (searchFilter) => {
           let value = [];
           let isRange = false;
           if (searchFilter.eq) {
               value.push(searchFilter.eq);
           } else if (searchFilter.in) {
               value = searchFilter.in;
           } else if (searchFilter.range) {
               isRange = true;
               value.push(String(searchFilter.range.from));
               value.push(String(searchFilter.range.to));
           }
           return {
               attribute: searchFilter.attribute,
               value,
               isRange,
           };
       }
   );
   
   return filters;
   ```

1. 검색 요청:

   - **이름**: `search request`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `siteSearch` > `phrase`
   - **값**: 아직 사용할 수 없음
   - **필드 그룹**: `siteSearch` > `sort`. 선택 **전체 개체 제공**.
   - **필드 그룹**: `siteSearch` > `filter`. 선택 **전체 개체 제공**.
   - **필드 그룹**: `searchRequest` > `id`
   - **고유 식별자**: **값** = `%search request ID%`
   - **필드 그룹**: `searchRequest` > `value`
   - **값**: **값** = `1`

#### 규칙 

- **이름**: `search request sent`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `search-request-sent`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `searchRequest`
- **XDM 데이터**: `%search request%`

### searchResponseReceived

라이브 검색에서 &quot;입력 시 검색&quot; 팝오버 또는 검색 결과 페이지에 대한 결과를 반환할 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 검색 결과:

   - **이름**: `search results`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `searchResultsContext.units[0]`

1. 제품 검색 결과 번호:

   - **이름**: `search result number of products`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('search result').products.length;
   ```

1. 검색 결과 제품:

   - **이름**: `search result products`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const productsFromResult = searchResult.products ? searchResult.products : [];
   const products = productsFromResult.map(
       (product) => {
           return { SKU: product.sku, name: product.name };
       }
   );
   return products;
   ```

1. 검색 결과 제안 사항:

   - **이름**: `search result products`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const searchResult = _satellite.getVar('search result');
   const suggestionsFromResult = searchResult.suggestions ? searchResult.suggestions : [];
   const suggestions = suggestionsFromResult.map((suggestion) => suggestion.suggestion);
   return suggestions;
   ```

1. 제품 이미지 URL:

   - **이름**: `product image`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.mainImageUrl`

1. 검색 응답:

   - **이름**: `search response`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `siteSearch` > `suggestions`. 선택 **전체 개체 제공**.
   - **데이터 요소**: `%search result suggestions%`
   - **필드 그룹**: `siteSearch` > `numberOfResults`
   - **값**: `%search result number of products%`
   - **필드 그룹**: `productListItems`. 선택 **전체 개체 제공**.
   - **필드 그룹**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **값** = `%product image%`
   - **데이터 요소**: `%search result products%`
   - **필드 그룹**: `searchResponse` > `id`
   - **고유 식별자**: **값** = `%search response ID%`
   - **필드 그룹**: `searchResponse` > `value`
   - **값**: **값** = `1`

#### 규칙 

- **이름**: `search response received`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `search-response-received`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `searchResponse`
- **XDM 데이터**: `%search response%`

### 추가 장바구니

제품이 장바구니에 추가될 때 또는 장바구니에 있는 제품의 수량이 증가할 때마다 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 제품 이름:

   - **이름**: `product name`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.name`

1. 제품 sku:

   - **이름**: `product sku`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.sku`

1. 통화 코드:

   - **이름**: `currency code`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.currencyCode`

1. 제품 특별 가격:

   - **이름**: `product special price`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.specialPrice`

1. 제품 이미지 URL:

   - **이름**: `product image`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.mainImageUrl`

1. 제품 일반 가격:

   - **이름**: `product regular price`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.regularPrice`

1. 제품 가격:

   - **이름**: `product price`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. 카트:

   - **이름**: `cart`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `shoppingCartContext`

1. 장바구니 ID:

   - **이름**: `cart id`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 장바구니에 추가:

   - **이름**: `add to cart`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `productListItems`. 선택 **개별 항목 제공** 을(를) 클릭하고 **항목 추가** 단추를 클릭합니다. 이 보기는 PDP용이므로 단일 항목으로 채울 수 있습니다.
   - **필드 그룹**: `productListItems` > `name`
   - **이름**: **값** = `%product name%`
   - **필드 그룹**: `productListItems` > `SKU`
   - **SKU**: **값** = `%product sku%`
   - **필드 그룹**: `productListItems` > `priceTotal`
   - **가격 합계**: **값** = `%product price%`
   - **필드 그룹**: `productListItems` > `currencyCode`
   - **필드 그룹**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **값** = `%product image%`
   - **통화 코드**: **값** = `%currency code%`
   - **필드 그룹**: `commerce` > `cart` > `cartID`
   - **장바구니 ID**: **값** = `%cart id%`
   - **필드 그룹**: `commerce` > `productListAdds` > `value`
   - **값**: **값** = `1`

#### 규칙 

- **이름**: `add to cart`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `add-to-cart`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `commerce.productListAdds`
- **XDM 데이터**: `%add to cart%`

### openCart

새 장바구니가 생성될 때 트리거되며, 빈 장바구니에 제품을 추가할 때 발생합니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 카트 열기:

   - **이름**: `open cart`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `commerce` > `productListOpens` > `value`
   - **값**: **값** = `1`
   - **필드 그룹**: `commerce` > `cart` > `cartID`
   - **장바구니 ID**: **값** = `%cart id%`
   - **필드 그룹**: `productListItems`. 대상 `productListItems`, 여러 항목을 미리 계산할 수 있습니다. 선택 **productListItem** > **전체 스토리지 제공**.

#### 규칙 

- **이름**: `open cart`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `open-cart`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `commerce.productListOpens`
- **XDM 데이터**: `%open cart%`

### viewCart

장바구니 페이지가 로드될 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 상점 첫 화면:

   - **이름**: `storefront`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `storefrontInstanceContext`

1. 제품 이미지 URL:

   - **이름**: `product image`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.mainImageUrl`

   1. 카트:

   - **이름**: `cart`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `shoppingCartContext`

1. 장바구니 ID:

   - **이름**: `cart id`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 제품 목록 항목:

   - **이름**: `product list items:`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. 장바구니 보기:

   - **이름**: `view cart`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `productListItems`. 대상 `productListItems`, 미리 계산된 항목이 여러 개 있을 수 있습니다. 선택 **productListItem** > **전체 배열 채우기**.
   - **데이터 요소**: `%product list items%`
   - **필드 그룹**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **값** = `%product image%`
   - **필드 그룹**: `commerce` > `cart` > `cartID`
   - **장바구니 ID**: **값** = `%cart id%`
   - **필드 그룹**: `commerce` > `productListViews` > `value`
   - **값**: **값** = `1`

#### 규칙

- **이름**: `view cart`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `shopping-cart-view`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `commerce.productListViews`
- **XDM 데이터**: `%view cart%`

### removeFromCart

장바구니에서 제품이 제거될 때 또는 장바구니에 있는 제품의 수량이 줄어들 때마다 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 제품 이름:

   - **이름**: `product name`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.name`

1. 제품 sku:

   - **이름**: `product sku`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.sku`

1. 통화 코드:

   - **이름**: `currency code`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.currencyCode`

1. 제품 특별 가격:

   - **이름**: `product special price`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.specialPrice`

1. 제품 일반 가격:

   - **이름**: `product regular price`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.pricing.regularPrice`

1. 제품 가격:

   - **이름**: `product price`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('product regular price') || _satellite.getVar('product special price') 
   ```

1. 카트:

   - **이름**: `cart`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `shoppingCartContext`

1. 장바구니 ID:

   - **이름**: `cart id`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 장바구니에서 제거:

   - **이름**: `remove from cart`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `productListItems`. 선택 **개별 항목 제공** 을(를) 클릭하고 **항목 추가** 단추를 클릭합니다. 이 보기는 PDP용이므로 단일 항목으로 채울 수 있습니다.
   - **필드 그룹**: `productListItems` > `name`
   - **이름**: **값** = `%product name%`
   - **필드 그룹**: `productListItems` > `SKU`
   - **SKU**: **값** = `%product sku%`
   - **필드 그룹**: `productListItems` > `priceTotal`
   - **가격 합계**: **값** = `%product price%`
   - **필드 그룹**: `productListItems` > `currencyCode`
   - **통화 코드**: **값** = `%currency code%`
   - **필드 그룹**: `commerce` > `cart` > `cartID`
   - **장바구니 ID**: **값** = `%cart id%`
   - **필드 그룹**: `commerce` > `productListRemovals` > `value`
   - **값**: **값** = `1`

#### 규칙 

- **이름**: `remove from cart`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `remove-from-cart`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `commerce.productListRemovals`
- **XDM 데이터**: `%remove from cart%`

### initiateCheckout

쇼핑객이 체크아웃 버튼을 클릭할 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 상점 첫 화면:

   - **이름**: `storefront`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `storefrontInstanceContext`

1. 제품 이미지 URL:

   - **이름**: `product image`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.mainImageUrl`

1. 카트:

   - **이름**: `cart`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `shoppingCartContext`

1. 장바구니 ID:

   - **이름**: `cart id`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 제품 목록 항목:

   - **이름**: `product list items`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. 체크아웃 시작:

   - **이름**: `initiate checkout`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `productListItems`. 대상 `productListItems`, 미리 계산된 항목이 여러 개 있을 수 있습니다. 선택 **productListItem** > **전체 배열 채우기**.
   - **데이터 요소**: `%product list items%`
   - **필드 그룹**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **값** = `%product image%`
   - **필드 그룹**: `commerce` > `cart` > `cartID`
   - **장바구니 ID**: **값** = `%cart id%`
   - **필드 그룹**: `commerce` > `checkouts` > `value`
   - **값**: **값** = `1`

#### 규칙 

- **이름**: `initiate checkout`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `initiate-checkout`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `commerce.checkouts`
- **XDM 데이터**: `%initiate checkout%`

### 주문

쇼핑객이 주문을 할 때 트리거됩니다.

#### 데이터 요소

다음 데이터 요소를 만듭니다.

1. 계정 이메일:

   - **이름**: `account email`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `accountContext.emailAddress`

1. 상점 첫 화면:

   - **이름**: `storefront`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `storefrontInstanceContext`

1. 제품 이미지 URL:

   - **이름**: `product image`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `productContext.mainImageUrl`

1. 카트:

   - **이름**: `cart`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `shoppingCartContext`

1. 장바구니 ID:

   - **이름**: `cart id`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('cart').id
   ```

1. 순서:

   - **이름**: `order`
   - **확장**: `Adobe Client Data Layer`
   - **데이터 요소 유형**: `Data Layer Computed State`
   - **[선택 사항] 경로**: `orderContext`

1. 상거래 주문:

   - **이름**: `commerce order`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const order = _satellite.getVar('order');
   const storefront = _satellite.getVar('storefront');
   
   if (order.payments && order.payments.length) {
       payments = order.payments.map(payment => {
           return {
               paymentAmount: payment.total,
               paymentType: payment.paymentMethodCode,
               transactionID: order.orderId.toString(),
           };
       });
   } else {
       payments = [
           {
               paymentAmount: order.grandTotal,
               paymentType: order.paymentMethodCode,
               transactionID: order.orderId.toString(),
           },
       ];
   }
   
   return {
       purchaseID: order.orderId.toString(),
       currencyCode: storefront.storeViewCurrencyCode,
       payments,
   };
   ```

1. 주문 배송:

   - **이름**: `order shipping`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const order = _satellite.getVar('order');
   return {
       shippingMethod: order.shipping.shippingMethod,
       shippingAmount: order.shipping.shippingAmount || 0,
   }
   ```

1. 프로모션 ID:

   - **이름**: `promotion id`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   return _satellite.getVar('order').appliedCouponCode
   ```

1. 제품 목록 항목:

   - **이름**: `product list items`
   - **확장**: `Core`
   - **데이터 요소 유형**: `Custom Code`
   - **편집기 열기**:

   ```bash
   const storefrontContext = _satellite.getVar('storefront');
   const cart = _satellite.getVar('cart');
   
   const returnList = [];
   cart.items.forEach(item => {
       const selectedOptions = [];
       item.configurableOptions?.forEach(option => {
           selectedOptions.push({
               attribute: option.optionLabel,
               value: option.valueLabel,
           });
       });
   
       const productListItem = {
           SKU: item.product.sku,
           name: item.product.name,
           quantity: item.quantity,
           priceTotal: item.prices.price.value * item.quantity,
           currencyCode: item.prices.price.currency ? item.prices.price.currency : storefrontContext.storeViewCurrencyCode,
           selectedOptions: selectedOptions,
       };
   
       returnList.push(productListItem);
   });
   return returnList;
   ```

1. 주문:

   - **이름**: `place order`
   - **확장**: `Adobe Experience Platform Web SDK`
   - **데이터 요소 유형**: `XDM object`
   - **필드 그룹**: `productListItems`. 대상 `productListItems`, 미리 계산된 항목이 여러 개 있을 수 있습니다. 선택 **productListItem** > **전체 배열 채우기**.
   - **데이터 요소**: `%product list items%`
   - **필드 그룹**: `productListItems` > `ProductImageUrl`
   - **ProductImageUrl**: **값** = `%product image%`
   - **필드 그룹**: `commerce` > `order`
   - **고유 식별자**: **값** = `%commerce order%`
   - **필드 그룹**: `commerce` > `shipping`
   - **고유 식별자**: **값** = `%order shipping%`
   - **필드 그룹**: `commerce` > `promotionID`
   - **프로모션 ID**: **값** = `%promotion id%`
   - **필드 그룹**: `commerce` > `purchases` > `value`
   - **값**: **값** = `1`
   - **개인 이메일 주소**: **값** = `%account email%`
   - **필드 그룹**: `personalEmail` > `address`
   - **주소**: **값** = `%account email%`

#### 규칙 

- **이름**: `place order`
- **확장**: `Adobe Client Data Layer`
- **이벤트 유형**: `Data Pushed`
- **특정 이벤트**: `place-order`

##### 작업

- **확장**: `Adobe Experience Platform Web SDK`
- **작업 유형**: `Send event`
- **유형**: `commerce.order`
- **XDM 데이터**: `%place order%`

## 상점 전면 이벤트에 ID 설정

Storefront 이벤트에는 다음을 기반으로 하는 프로필 정보가 포함되어 있습니다. `personalEmail` (계정 이벤트의 경우) 및 `identityMap` (다른 모든 상점 이벤트의 경우) 필드. 다음 [!DNL Data Connection] 확장은 이 두 필드를 기반으로 프로필을 결합하고 생성합니다. 그러나 각 필드에는 프로필을 만들기 위해 따라야 할 단계가 다릅니다.

>[!NOTE]
>
>다른 필드를 사용하는 이전 설정이 있는 경우 해당 필드를 계속 사용할 수 있습니다.

- `personalEmail` - 계정 이벤트에만 적용됩니다. 설명된 단계, 규칙 및 작업 준수 [위](#createaccount)
- `identityMap` - 다른 모든 상점 이벤트에 적용됩니다. 다음 예를 참조하십시오.

### 예

다음 단계는 를 구성하는 방법을 보여 줍니다 `pageView` 이벤트 포함 `identityMap` 위치: [!DNL Data Connection] 확장:

1. ECID에 대한 사용자 지정 코드로 데이터 요소 구성:

   ![사용자 지정 코드로 데이터 요소 구성](assets/set-custom-code-ecid.png)
   _사용자 지정 코드로 데이터 요소 구성_

1. 선택 [!UICONTROL Open Editor] 다음 사용자 지정 코드를 추가합니다.

   ```javascript
   return alloy("getIdentity").then((result) => {
       var identityMap = {
           ECID: [
           {
               id: ecid,
               primary: true
           }
           ],
           email: [
           {
               id: email,
               primary: false
           }
           ]
       };
     _satelite.setVar("identityMap", identityMap);
   });
   ```

1. XDM 스키마 업데이트 `identityMap` ecid로 설정:

   ![identityMap을 ECID로 설정](assets/identity-map-data-element.png)
   _identityMap을 ECID로 설정_

1. ECID를 검색하는 규칙 작업을 정의합니다.

   ![ECID 검색](assets/rule-retrieve-ecid.png)
   _ECID 검색_

## 백오피스 이벤트에서 ID 설정

프로필 정보를 식별하고 연결하는 데 ECID를 사용하는 상점 이벤트와 달리, 백 오피스 이벤트 데이터는 SaaS 기반이므로 ECID를 사용할 수 없습니다. 백오피스 이벤트의 경우 구매자를 고유하게 식별하기 위해 이메일을 사용해야 합니다. 이 섹션에서는 이메일을 사용하여 Office 이벤트 데이터를 ECID에 연결하는 방법을 알아봅니다.

1. ID 맵 요소를 만듭니다.

   ![백오피스 ID 맵](assets/custom-code-backoffice.png)
   _백오피스 ID 맵 만들기_

1. 선택 [!UICONTROL Open Editor] 다음 사용자 지정 코드를 추가합니다.

```javascript
const IdentityMap = {
  "ECID": [
    {
      id:  _satellite.getVar('ECID'),
      primary: true,
    },
  ],
};
 
if (_satellite.getVar('account email')) {
    IdentityMap.email = [
        {
            id: _satellite.getVar('account email'),
            primary: false,
        },
    ];
}
return IdentityMap;
```

1. 이 새 요소를 각각에 추가 `identityMap` 필드.

   ![각 identityMap 업데이트](assets/add-element-back-office.png)
   _각 identityMap 업데이트_

## 동의 설정

설치 시 [!DNL Data Connection] Adobe Commerce에서 확장 기능은 데이터 수집 동의가 기본적으로 활성화되어 있습니다. 옵트아웃은 [`mg_dnt` 쿠키](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html). 을(를) 사용하도록 선택한 경우 여기에 설명된 단계를 따를 수 있습니다 `mg_dnt` 동의를 관리합니다. 다음 [Adobe Experience Platform Web SDK 설명서](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html) 에는 동의 관리를 위한 몇 가지 추가 옵션이 있습니다.

1. 만들기 **핵심 사용자 지정 코드** 데이터 요소(`%do not track cookie%`)에 사용됩니다. `mg_dnt` 쿠키:

   ![데이터 요소를 추적하지 않음 만들기](assets/element-dnt-cookie.png)
   _데이터 요소를 추적하지 않음 만들기_

1. 만들기 **핵심 사용자 지정 코드** 데이터 요소(`%consent%`를 반환합니다. `out` 쿠키가 설정되고 `in` 그렇지 않은 경우:

   ![동의 데이터 요소 만들기](assets/element-consent-dnt-cookie.png)
   _동의 데이터 요소 만들기_

1. 을 사용하여 Adobe Experience Platform 웹 SDK 확장 구성 `%consent%` 데이터 요소:

   ![동의를 얻어 SDK 업데이트](assets/config-sdk-consent.png)
   _동의를 얻어 SDK 업데이트_

## 경고

- Experience Platform 컬렉션을 해제하기 위한 단계를 따르지 않으면 이벤트가 두 번 계산됩니다
- 이 항목에 설명된 대로 매핑/이벤트를 설정하지 않으면 Adobe Analytics 보드에 영향을 줄 수 있습니다
- 다음을 통해 Target을 설정할 수 없습니다. [!DNL Data Connection] 데이터 수집이 비활성화된 경우 확장
