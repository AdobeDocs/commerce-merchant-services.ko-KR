---
title: Headless
description: 통합 방법 알아보기 [!DNL Product Recommendations] 헤드리스 상점 앞에서요.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# Headless

다음을 통합할 수 있습니다. [!DNL Product Recommendations] 다음 중 하나를 사용하여 헤드리스 상점 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 또는 React 또는 Vue JS와 같은 사용자 지정 프론트엔드 기술입니다.

사용자 정의 및 Headless 통합자는 이 Luma 및 PWA 지침을 권장 구현으로 참조해야 합니다. Product Recommendations을 Headless 솔루션에 구현하는 방법에는 여러 가지가 있으며 이 설명서에서는 모든 시나리오를 다루지 않습니다. 통합자는 해당 구현에 대한 이벤트, 설계 및 테스트를 다룹니다.

[!DNL Product Recommendations] 필요 [동작 및 카탈로그 데이터](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) 수술하기 위해. 카탈로그 데이터 동기화 프로세스는 Headless 구현에서 변경되지 않지만 동작 데이터 수집에는 변경이 필요합니다.

>[!NOTE]
>
>Headless 인스턴스는 제품 Recommendations 대시보드를 구동하는 이벤트를 구현해야 합니다.

통합하려면 [!DNL Product Recommendations] headless 상점 앞에서 다음을 수행해야 합니다.

1. 행동 데이터를 Adobe Sensei으로 전송하여 제품 추천 결과를 분석하고 계산합니다. 추가 데이터를 전송하여 제품 추천을 활성화할 수도 있습니다 [지표 보고](workspace.md).

1. 제품 추천 결과를 가져오고 페이지에서 해당 결과를 렌더링합니다.

다음 워크플로에 설명된 대로 사용 가능한 SDK를 사용하여 이러한 작업을 모두 수행할 수 있습니다.

1. [설치](install-configure.md) 다음 [!DNL Product Recommendations] 모듈.

1. 설치 및 사용 [Adobe Commerce Storefront 이벤트 SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 을(를) 실행하려면 [동작 이벤트](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   반환에 필요한 최소 이벤트 [!DNL Product Recommendations] 결과:

   | 이벤트 | 범주 |
   |--- | ---|
   | `view` | 제품 |
   | `add-to-cart` | 제품 |
   | `place-order` | 체크아웃 |

   활성화하려면 [지표 보고](workspace.md)를 사용하려면 다음 추가 이벤트가 필요합니다.

   | 이벤트 | 범주 |
   |--- | ---|
   | `impression-render` | recommendation-unit |
   | `view` | recommendation-unit |
   | `rec-click` | recommendation-unit |
   | `rec-add-to-cart-click` | 권장 사항 단위(&quot;장바구니에 추가&quot; 단추가 권장 사항 템플릿에 있는 경우) |

1. 이벤트가 실행되면 [Adobe Commerce Storefront 이벤트 수집기](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) 이벤트를 처리하고 Adobe Sensei으로 전송합니다.

1. 동작 데이터가 수집되면 다음을 수행할 수 있습니다. [만들기](create.md) [!DNL Product Recommendations] 관리에서.

1. 사용 [RECOMMENDATIONS SDK](https://developer.adobe.com/commerce/services/product-recommendations/) 상점 첫 화면에서 추천 단위를 가져올 수 있습니다. SDK는 페이지에서 추천 단위를 렌더링하는 데 필요한 제품 데이터를 반환합니다.
