---
title: '[!DNL Live Search] 이벤트'
description: 이벤트가에 대한 데이터를 수집하는 방법 알아보기 [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search] 이벤트

[!DNL Live Search] 는 이벤트를 사용하여 &quot;가장 많이 본 항목&quot; 및 &quot;이 항목을 보고 다른 항목을 본 항목&quot;과 같은 검색 알고리즘을 실행합니다. LUMA 사용자는 즉시 이벤트를 사용할 수 있지만 Headless 및 기타 사용자 지정 구현은 자체 요구 사항에 맞게 이벤트를 구현해야 합니다.

다음 이후 [!DNL Live Search] 및 [!DNL Product Recommendations] 동일한 백엔드 알고리즘을 사용합니다. 일부 이벤트는 두 서비스에서 공유됩니다. Recommendations 대시보드를 채우려면 일부 제품 Recommendations 이벤트가 필요합니다.

이 표에서는 다음에서 사용하는 이벤트에 대해 설명합니다. [!DNL Live Search] 전략.

| 전략 | 제품 | 이벤트 | 페이지 |
| --- | --- | --- | ---|
| 가장 많이 본 항목 | 라이브 검색<br>제품 Recs | 페이지 보기<br>제품 보기 | 제품 세부 사항 페이지 |
| 최다 구매 | 라이브 검색<br>제품 Recs | 페이지 보기<br>체크아웃 완료 | 장바구니/체크아웃 |
| 장바구니에 가장 많이 추가됨 | 라이브 검색<br>제품 Recs | 페이지 보기<br>장바구니에 추가 | 제품 세부 사항 페이지<br>제품 목록 페이지<br>장바구니<br>위시리스트 |
| 이 항목을 보고 다른 항목도 보았습니다. | 라이브 검색<br>제품 Recs | 페이지 보기<br>제품 보기 | 제품 세부 사항 페이지 |
| 트렌딩 | 라이브 검색<br>제품 Recs | 페이지 보기<br>제품 보기 | 제품 세부 사항 페이지 |
| 이 항목을 보고 다른 항목을 구입함 | 제품 Recs | 페이지 보기<br>제품 보기 | 제품 세부 사항 페이지<br>장바구니/체크아웃 |
| 구매, 구매 | 제품 Recs | 페이지 보기<br>제품 보기 | 제품 세부 사항 페이지 |
| 전환: 구매로 보기 | 제품 Recs | 페이지 보기<br>제품 보기 | 제품 세부 사항 페이지 |
| 전환: 구매로 보기 | 제품 Recs | 페이지 보기<br>체크아웃 완료 | 장바구니/체크아웃 |
| 전환: 장바구니로 보기 | 제품 Recs | 페이지 보기<br>제품 보기 | 제품 세부 사항 페이지 |
| 전환: 장바구니로 보기 | 제품 Recs | 페이지 보기<br>장바구니에 추가 | 제품 세부 사항 페이지<br>제품 목록 페이지<br>장바구니<br>위시리스트 |

>[!NOTE]
>
>데이터 수집 용도 [!DNL Live Search] PII(개인 식별 정보)는 포함하지 않습니다. 쿠키 ID 및 IP 주소와 같은 모든 사용자 식별자는 엄격히 익명으로 처리됩니다. [자세히 알아보기](https://www.adobe.com/privacy/experience-cloud.html).

## 필수 대시보드 이벤트

을(를) 채우려면 일부 이벤트가 필요합니다. [라이브 검색 대시보드](performance.md)

| 대시보드 영역 | 이벤트 | 조인 필드 |
| ------------------- | ------------- | ---------- |
| 고유 검색 | `page-view`, `search-request-sent`, | searchRequestId |
| 결과 없음 검색 | `page-view`, `search-request-sent`, | searchRequestId |
| 결과 없음 비율 | `page-view`, `search-request-sent`, | searchRequestId |
| 자주 찾는 검색 | `page-view`, `search-request-sent`, | searchRequestId |
| 평균 클릭 위치 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| 클릭스루 비율 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId, sku |
| 전환율 | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | searchRequestId, sku |

### 필수 컨텍스트

모든 이벤트에는 `Page` 및 `Storefront` 컨텍스트. 이는 개별 이벤트를 생성할 때가 아니라 페이지 수준/상점 응용 프로그램 계층에서 발생해야 합니다(예를 들어, PHP 상점 앞에서는 PHP 응용 프로그램 컨테이너가 런타임 시 설정을 담당합니다).

## 사용

다음은 의 샘플 구현입니다. `search-request-sent` 이벤트:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## 주의 사항

광고 차단기 및 개인정보 보호 설정은 이벤트가 캡처되지 않도록 할 수 있으며, 이로 인해 참여 및 매출이 발생할 수 있습니다 [지표](workspace.md) 과소 보고됩니다.

이벤트가 판매자의 사이트에서 일어나는 모든 거래를 포착하지는 못한다. 이벤트란 사이트에서 일어나는 사건에 대한 일반적인 아이디어를 판매자에게 제공하는 것이다.

Headless 구현은 다음을 지원하기 위해 이벤트를 구현해야 합니다. [제품 Recommendations 대시보드](../product-recommendations/events.md).

>[!NOTE]
>
>If [쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 이 활성화되어 있으면, Adobe Commerce은 쇼핑객이 쿠키 사용에 동의할 때까지 행동 데이터를 수집하지 않습니다. 쿠키 제한 모드 가 비활성화되면 Adobe Commerce은 기본적으로 동작 데이터를 수집합니다.
