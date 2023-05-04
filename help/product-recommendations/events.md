---
title: 데이터 수집
description: 이벤트가 제품 권장 사항에 대한 데이터를 수집하는 방법을 알아봅니다.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 데이터 수집

다음과 같은 SaaS 기반 Adobe Commerce 기능을 설치하고 구성할 때 [제품 Recommendations](install-configure.md) 또는 [라이브 검색](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html)로 설정되면, 이 모듈은 행동 데이터 수집을 상점 앞에 배포합니다. 이 메커니즘은 구매자로부터 익명으로 처리된 행동 데이터를 수집하고 제품 권장 사항을 강화합니다. 예: `view` 이벤트는 를 계산하는 데 사용됩니다 `Viewed this, viewed that` 권장 사항 유형 및 `place-order` 이벤트는 를 계산하는 데 사용됩니다 `Bought this, bought that` 권장 사항 유형.

>[!NOTE]
>
>제품 권장 사항을 위한 데이터 수집에는 PII(개인 식별 정보)가 포함되지 않습니다. 쿠키 ID 및 IP 주소와 같은 모든 사용자 식별자는 엄격히 익명 처리됩니다. [추가 정보](https://www.adobe.com/privacy/experience-cloud.html).

다음 이벤트는 Product Recommendations에만 국한되지 않고 결과를 반환하는 데 필요합니다.

- `view`
- `add-to-cart`
- `place-order`

다음 [Adobe Commerce Storefront 이벤트 수집기](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) storefront에 배포된 모든 이벤트를 나열합니다. 그러나 이 목록에는 제품 Recommendations과 관련된 이벤트의 하위 세트가 있습니다. 이러한 이벤트는 구매자가 상점 내 권장 사항 단위와 상호 작용할 때 데이터를 수집하고 추천이 얼마나 잘 수행되고 있는지 분석하는 데 사용되는 지표에 전원을 줍니다.

| 이벤트 | 설명 | [지표에 사용됩니까?](workspace.md) |
| --- | --- | --- |
| `impression-render` | 권장 사항 단위가 페이지에 렌더링됩니다. | 예 |
| `rec-add-to-cart-click` | 고객이 **장바구니에 추가** 추천 단위에 있는 항목의 단추입니다. | 예, **장바구니에 추가** 단추가 권장 사항 템플릿에 있습니다. |
| `rec-click` | 고객이 권장 사항 단위의 제품을 클릭합니다. | 예 |
| `view` | 권장 사항 유닛은 보기로 스크롤하는 경우와 같이 페이지에서 볼 수 있게 됩니다. | 예 |

스토어가 PWA Studio으로 구현된 경우 [PWA 설명서](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). React 또는 Value JS와 같은 사용자 지정 프런트 엔드 기술을 사용하는 경우 사용 안내서 를 참조하여 Product Recommendations을 [헤드리스](headless.md) 환경.

## 경고

광고 차단 및 개인 정보 설정은 `magento/product-recommendations` 이벤트 캡처를 통한 모듈 및 이로 인해 참여 및 매출 발생 가능 [지표](workspace.md) 자세한 보고가 필요합니다.

이벤트는 머천트 사이트에서 발생하는 모든 거래를 캡처하지 않습니다. 이벤트는 상인에게 사이트에서 발생하는 이벤트에 대한 일반적인 아이디어를 주기 위한 것입니다.

헤드리스 구현은 제품 Recommendations 대시보드를 사용하려면 이벤트를 구현해야 합니다.

>[!NOTE]
>
>If [쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) 이 활성화되어 있으면 Adobe Commerce은 쇼핑객이 쿠키 사용에 동의하기 전까지 행동 데이터를 수집하지 않습니다. 쿠키 제한 모드가 비활성화되어 있으면 Adobe Commerce에서 기본적으로 동작 데이터를 수집합니다.
