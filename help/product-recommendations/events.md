---
title: 데이터 수집
description: 이벤트가 제품 추천에 대한 데이터를 수집하는 방법을 알아봅니다.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 7ed9321a2f4e58a7476aa91e74611fe896e1a7b1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# 데이터 수집

다음과 같은 SaaS 기반 Adobe Commerce 기능을 설치하고 구성할 때 [제품 Recommendations](install-configure.md) 또는 [라이브 검색](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), 모듈은 동작 데이터 수집을 상점 앞에 배포합니다. 이 메커니즘은 쇼핑객으로부터 익명으로 처리된 행동 데이터를 수집하고 제품 추천을 강화합니다. 예를 들어 `view` 이벤트를 사용하여 `Viewed this, viewed that` 권장 사항 유형 및 `place-order` 이벤트를 사용하여 `Bought this, bought that` 권장 사항 유형.

>[!NOTE]
>
>제품 권장 사항을 위한 데이터 수집에는 PII(개인 식별 정보)가 포함되지 않습니다. 쿠키 ID 및 IP 주소와 같은 모든 사용자 식별자는 엄격히 익명으로 처리됩니다. 학습 [기타](https://www.adobe.com/privacy/experience-cloud.html).

다음 이벤트는 제품 Recommendations에만 해당되지 않지만 결과를 반환하는 데 필요합니다.

- `view`
- `add-to-cart`
- `place-order`

다음 [Adobe Commerce Storefront 이벤트 수집기](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) 상점에 배포된 모든 이벤트를 나열합니다. 그러나 이 목록에는 제품 Recommendations과 관련된 이벤트의 하위 집합이 있습니다. 이러한 이벤트는 쇼핑객이 상점 위의 추천 단위와 상호 작용할 때 데이터를 수집하여 추천 실적을 분석하는 데 사용되는 지표에 전원을 공급합니다.

| 이벤트 | 설명 | 지표에 사용됩니까? |
| --- | --- | --- |
| `impression-render` | 권장 사항 단위는 페이지에 렌더링됩니다. | 예 |
| `rec-add-to-cart-click` | 고객이 클릭 **장바구니에 추가** 추천 단위의 항목에 대한 단추입니다. | 예, 다음과 같은 경우: **장바구니에 추가** 단추가 권장 사항 템플릿에 있습니다. |
| `rec-click` | 고객이 추천 단위에서 제품을 클릭합니다. | 예 |
| `view` | 권장 사항 단위는 예를 들어 보기로 스크롤하는 방식으로 페이지에서 볼 수 있습니다. | 예 |

대시보드를 제대로 채우려면 다음 이벤트가 필요합니다.
| 대시보드 열 | 이벤트 | 조인 필드 | | ---------------- | --------- | ----------- | | 노출 횟수 |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId | | 보기 |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId | | 클릭수 |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`    | unitId | | 매출 |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku | | LT 수익 |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku | | CTR |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click`  | unitId, sku | | vCTR |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |

Storefront가 PWA Studio으로 구현된 경우 다음을 참조하십시오. [PWA 설명서](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). React 또는 Vue JS와 같은 사용자 지정 프론트엔드 기술을 사용하는 경우 통합 방법에 대한 자세한 내용은 사용자 안내서를 참조하십시오 [Headless의 Recommendations 제품](headless.md) 환경.

## 주의 사항

광고 차단기 및 개인정보 보호 설정으로 인해 `magento/product-recommendations` 모듈이 이벤트를 캡처하지 못하며, 이로 인해 참여 및 매출이 발생할 수 있음 [지표](workspace.md) 과소 보고됩니다.

이벤트가 판매자의 사이트에서 일어나는 모든 거래를 포착하지는 못한다. 이벤트란 사이트에서 일어나는 사건에 대한 일반적인 아이디어를 판매자에게 제공하는 것이다.

Headless 구현은 제품 Recommendations 대시보드를 구동하는 이벤트를 구현해야 합니다.

>[!NOTE]
>
>If [쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 이 활성화되어 있으면, Adobe Commerce은 쇼핑객이 쿠키 사용에 동의할 때까지 행동 데이터를 수집하지 않습니다. 쿠키 제한 모드 가 비활성화되면 Adobe Commerce은 기본적으로 동작 데이터를 수집합니다.
