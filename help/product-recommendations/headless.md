---
title: 헤드리스
description: 통합 방법 알아보기 [!DNL Product Recommendations] 헤드리스 상점.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: 521ea4fc2cce809fc12d3958e37089f3e34e1068
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# 헤드리스

통합할 수 있습니다 [!DNL Product Recommendations] 헤드리스 상점 안에 [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) 또는 React 또는 Value JS와 같은 사용자 지정 프런트 엔드 기술입니다.

사용자 지정 및 헤드리스 통합자는 이러한 Luma 및 PWA 지침을 제안된 구현으로 참조해야 합니다. Product Recommendations을 헤드리스 솔루션으로 구현하는 방법에는 여러 가지가 있으며 이 설명서에는 모든 시나리오가 포함되어 있지 않습니다. 통합자는 구현에 대한 이벤트, 디자인 및 테스트를 다룹니다.

[!DNL Product Recommendations] 필요 [행동 및 카탈로그 데이터](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/development-overview.html) 작동됩니다. 카탈로그 데이터 동기화 프로세스는 헤드리스 구현에서 변경되지 않은 상태로 유지되지만 행동 데이터 수집을 위해 변경 사항이 필요합니다.

>[!NOTE]
>
>헤드리스 인스턴스는 Product Recommendations 대시보드를 사용하려면 이벤트를 구현해야 합니다.

통합하려면 [!DNL Product Recommendations] 헤드리스 스토어프런트에서 다음을 수행해야 합니다.

1. 행동 데이터를 Adobe Sensei에 보내어 제품 권장 사항 결과를 분석하고 계산합니다. 제품 추천을 활성화하기 위해 추가 데이터를 전송할 수도 있습니다 [지표 보고](workspace.md).

1. 제품 권장 사항 결과를 가져오고 페이지에서 해당 결과를 렌더링합니다.

다음 워크플로우에 설명된 대로 사용 가능한 SDK를 사용하여 이러한 두 작업을 모두 수행할 수 있습니다.

1. [설치](install-configure.md) a [!DNL Product Recommendations] 모듈.

1. 설치 및 사용 [Adobe Commerce Storefront 이벤트 SDK](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) 발사하다 [행동 이벤트](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

   반환할 최소 필수 이벤트 [!DNL Product Recommendations] 결과:

   | 이벤트 | 카테고리 |
   |--- | ---|
   | `view` | product |
   | `add-to-cart` | product |
   | `place-order` | 체크아웃 |

   활성화하려면 [지표 보고](workspace.md), 다음 추가 이벤트가 필요합니다.

   | 이벤트 | 카테고리 |
   |--- | ---|
   | `impression-render` | 추천 단위 |
   | `view` | 추천 단위 |
   | `rec-click` | 추천 단위 |
   | `rec-add-to-cart-click` | 권장 사항 단위(권장 사항 템플릿에 &quot;장바구니에 추가&quot; 단추가 있는 경우) |

1. 이벤트가 실행되면 [Adobe Commerce Storefront 이벤트 수집기](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) 를 사용하여 이벤트를 처리하고 Adobe Sensei으로 보냅니다.

1. 동작 데이터가 수집되면 [만들기](create.md) [!DNL Product Recommendations] 관리자.

1. 를 사용하십시오 [Recommendations SDK](https://developer.adobe.com/commerce/services/product-recommendations/) 를 눌러 storfront에서 권장 사항 단위를 가져옵니다. SDK는 페이지에서 권장 사항 단위를 렌더링하기 위해 필요한 제품 데이터를 반환합니다.
