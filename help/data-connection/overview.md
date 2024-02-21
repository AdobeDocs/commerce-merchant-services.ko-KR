---
title: 안내서 개요
description: 를 사용하여 Adobe Commerce 데이터를 Adobe Experience Platform과 통합하는 방법을 알아봅니다. [!DNL Data Connection] 확장명.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: af54529ad037dc99dbc07cf1a6ac270d17f16870
workflow-type: tm+mt
source-wordcount: '1732'
ht-degree: 0%

---

# [!DNL Data Connection] 소개

>[!IMPORTANT]
>
>Experience Platform 커넥터의 이름이 (으)로 변경되었습니다. [!DNL Data Connection].

다음 [!DNL Data Connection] 확장은 Adobe Commerce 웹 인스턴스를 Adobe Experience Platform 및 Edge Network에 연결합니다. 방법 알아보기 [통합](./mobile-sdk-epc.md) Adobe Experience Platform Mobile SDK와 Commerce.

상거래 스토어에는 풍부한 데이터가 있습니다. 쇼핑객이 사이트에서 제품을 검색하고, 보고, 최종적으로 구매하는 방법에 대한 정보는 보다 개인화된 쇼핑 경험을 만들 수 있는 기회를 보여줄 수 있습니다. 해당 데이터는 장바구니 가격 규칙 및 동적 블록과 같은 기본 Commerce 기능에 정보를 제공할 수 있지만 데이터는 Commerce 인스턴스에 격리된 상태로 유지됩니다.

Adobe Experience Platform은 상거래 스토어의 데이터를 하이드레이션할 때 Edge Network를 통해 해당 데이터를 다른 Adobe DX 제품에 배포하여 구매자의 구매 행동에 대한 통찰력을 확보할 수 있는 기술 제품군을 제공합니다. 이러한 심층적인 통찰력을 통해 모든 채널에서 보다 개인화된 쇼핑 경험을 만들 수 있습니다.

다음 이미지는 Commerce 데이터가 저장소에서 다른 Adobe DX 제품으로 이동하는 방식을 보여 줍니다.

![데이터가 Experience Platform 에지로 이동하는 방법](assets/commerce-edge.png)

위의 이미지에서 동작, 백오피스 및 고객 프로필 데이터는 SDK, API 및 소스 커넥터를 사용하여 Experience Platform Edge로 전송됩니다. 확장이 데이터 공유 복잡성을 처리하므로 이러한 부분이 어떻게 작동하는지 완전히 이해할 필요는 없습니다. 이벤트 데이터가 에지에 있으면 해당 데이터를 다른 Experience Platform 애플리케이션으로 가져올 수 있습니다. For example:

| 애플리케이션 | 목적 | 사용 사례 |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=ko-KR) | 프로필 관리 및 세분화 서비스 | **구매 내역 세분화**: 판매자는 특정 기간(월별, 분기별, 연간 등)에 따라 품목을 구매하는 고객을 식별할 수 있습니다. 그런 다음 판매자는 이러한 고객을 위한 세그먼트를 만들고 프로모션, 캠페인 및에 타기팅할 수 있습니다. _단계 상단_ 구독 서비스 잠재 고객 데이터.<br> **범주 기반 세분화**: 가맹점은 구매한 제품 카테고리를 볼 수 있습니다.<br> **제공 기반 세분화**: 가맹점은 상품을 일관되게 반품하는 고객을 식별할 수 있습니다. 이제 고객에게 제공되는 오퍼와 할인이 보다 지능적일 수 있습니다. 예를 들어 항상 제품을 반품하는 고객에 대해 무료배송을 제거할 수 있다.<br> **유사 타기팅**: A _유사 대상_ 은 기존 고객과 유사한 특성을 공유하기 때문에 비즈니스에 관심이 있을 가능성이 높은 새로운 사람에게 도달하기 위해 상인이 프로모션을 위해 취하는 방법론입니다. 행동 및 트랜잭션 데이터를 기반으로 유사 세그먼트를 만들 수 있습니다.<br> **고객 성향**: 트랜잭션 데이터에서 만들 수 있는 고객 프로필의 깊이가 깊어지면 고객 행동 변화를 식별할 수 있습니다. 제품 수익률이나 제품 구성 등 계산에 유입되는 데이터가 많을수록 성향 점수에 대한 신뢰도가 높아질 것이다.<br> **크로스셀**: 판매자는 Commerce에서 캡처한 세분화된 정보에서 강력한 크로스셀 및 업셀 기회를 식별할 수 있습니다. |
| [고객 [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | 전체 상거래 여정에 대한 심층 분석 | **계절 트렌드**: 판매자는 계절별 트렌드를 식별하여 특정 제품에 대한 정기적인 수요 변화에 대비할 수 있습니다. 또한 상인들은 수년에 걸쳐 어떤 제품의 전반적인 인기의 변화를 확인할 수 있다.<br> **전환 분석**: 판매자는 제품 구매 시기를 파악하고 상점 노출 이벤트에 대한 액세스를 통해 고객의 풍부한 프로필을 생성하여 전환 분석을 수행할 수 있습니다. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | 고객 행동 및 캠페인 성과에 대한 심층적인 분석 | **반품 주문**: 판매자는 반품 패턴이 있는 고객 및 대규모 고객 세그먼트를 식별할 수 있습니다. 이는 가맹점이 고객 기반 행동이 어떻게 보이는지 이해함으로써 상거래 전략을 개선하는 데 도움이 됩니다.<br> **주문 주소**: 배송 주소를 기반으로 판매자는 고객이 주문을 하는지 또는 다른 개인 또는 엔티티를 위한 것인지 파악할 수 있습니다.<br> **계절성 트렌드**: 판매자는 계절별 트렌드를 식별하여 특정 제품에 대한 정기적인 수요 변화에 대비할 수 있습니다. 또한 상인들은 수년에 걸쳐 어떤 제품의 전반적인 인기의 변화를 확인할 수 있다.<br> **전환 분석**: 판매자는 제품 구매 시기를 파악하고 상점 노출 이벤트에 대한 액세스를 통해 고객의 풍부한 프로필을 생성하여 전환 분석을 수행할 수 있습니다. **참고** Adobe Analytics은 동작(상점) 이벤트 데이터만 지원합니다. Adobe Analytics은 트랜잭션(백오피스) 이벤트 데이터를 지원하지 않습니다. |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | 채널 간 Campaign 오케스트레이션 | **동작 기반 여정**: 가맹점은 2년 전 휴대폰을 구입한 고객을 대상으로 새 모델의 구매를 제안할 수 있습니다. 판매자는 이러한 고객을 위한 개인화된 캠페인과 프로모션을 만들고 이메일 및 SMS 기능을 사용하여 연락할 수 있습니다. 또한, 상인들은 과거 질서와 행동 데이터를 사용하여 동향을 파악할 수 있습니다. 예를 들어 과거에 특정 구성으로 품목을 구매했다가 이제 동일한 제품을 다시 구매하려는 고객은 동일한 제품 구성에 대한 가시성과 액세스 권한을 제공하여 구매 여정을 향상시킬 수 있습니다.<br> **개인화**: 고객 프로필 정보에 액세스할 수 있는 경우 [!DNL Journey Optimizer] 은 상인이 다양한 채널을 통해 고객에게 연락할 수 있도록 고도로 개인화된 여정을 잠금 해제할 수 있습니다.<br> **새 프로필 생성됨**: 환영 이메일 및 프로모션 활동은 신규 고객의 쇼핑 여정을 격려하고 영향을 줄 수 있습니다.<br> **프로필 삭제됨**: 가맹점은 계정을 닫은 고객에게 홍보 이메일 전송을 중지하도록 선택할 수 있습니다. 또는 상인이 잃어버린 고객을 되찾기 위한 캠페인을 구축할 수도 있습니다. |

## Experience Platform 데이터를 Commerce로 다시 가져오기

를 사용하여 상거래 데이터를 Experience Platform에 보내기 [!DNL Data Connection] 확장은 Commerce의 데이터 공유 기능 중 하나입니다. 선택적 확장인 반대쪽은 입니다. [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). 이 확장을 사용하면 Real-Time CDP에서 대상을 작성하고 이러한 대상을 Commerce 스토어에 배포하여 장바구니 가격 규칙, 관련 제품 규칙(베타) 및 동적 블록을 알릴 수 있습니다.

높은 수준에서 Commerce 스토어에서 Experience Platform으로, 그리고 Audience Activation 확장을 통해 다시 이동하는 데이터 흐름은 다음과 같습니다.

![[!DNL Data Connection] 흐름](assets/data-connection.png)

Experience Platform Commerce에서 Commerce로, Experience Platform에서 Commerce로 연결을 설정한 후에도 데이터가 계속 흐릅니다. 업그레이드에서 다시 연결할 필요가 없는 한 다시 연결할 필요가 없습니다.

## 개념

이 두 시스템 간에 데이터를 공유하려면 몇 가지 개념을 이해해야 합니다.

* **데이터** - Experience Platform과 공유되는 데이터는 상점의 브라우저 이벤트, 서버의 백 오피스 이벤트 및 프로필 레코드 데이터에서 수집된 데이터입니다. 상점 이벤트는 사이트의 쇼핑객 상호 작용에서 캡처되며 다음과 같은 이벤트를 포함합니다. [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout)등. 다음을 참조하십시오 [storefront 이벤트](events.md#storefront-events) storefront 이벤트의 전체 목록입니다. 서버측 또는 백오피스 이벤트에는 다음이 포함됩니다 [주문 상태](events-backoffice.md#order-status) 다음과 같은 정보 [`orderPlaced`](events-backoffice.md#orderplaced), [`orderReturned`](events-backoffice.md#orderitemreturncompleted), [`orderShipped`](events-backoffice.md#ordershipmentcompleted), [`orderCancelled`](events-backoffice.md#ordercancelled)등. 다음을 참조하십시오 [백오피스 이벤트](events-backoffice.md) 백 오피스 이벤트의 전체 목록. 프로필 레코드 데이터에는 새 프로필이 생성, 업데이트 또는 삭제될 때의 정보가 포함됩니다. 다음을 참조하십시오 [프로필 레코드 데이터](events-profilerecord.md) 자세히 알아보십시오.

* **Experience Platform 및 에지 네트워크** - 대부분의 Adobe DX 제품을 위한 데이터 웨어하우스 그런 다음 Experience Platform으로 전송된 데이터는 Experience Platform Edge Network를 통해 Adobe DX 제품으로 전파됩니다. 예를 들어 Journey Optimizer을 시작하고, Edge에서 특정 Commerce 이벤트 데이터를 검색하고, Journey Optimizer에서 포기한 장바구니 이메일을 빌드할 수 있습니다. 그러면 Journey Optimizer은 Commerce 스토어에 구매하지 않은 장바구니가 있는 경우 해당 이메일을 보낼 수 있습니다. 에 대해 자세히 알아보기 [Experience Platform 및 에지 네트워크](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **스키마** - 스키마는 전송 중인 데이터의 구조를 설명하는 것입니다. Experience Platform이 상거래 데이터를 수집하려면 먼저 데이터의 구조를 설명하는 스키마를 구성하고 각 필드 내에 포함될 수 있는 데이터 유형에 제약 조건을 제공해야 합니다. 스키마는 기본 클래스와 0개 이상의 스키마 필드 그룹으로 구성됩니다. 스키마는 모든 Adobe DX 제품이 읽을 수 있는 XDM 구조를 사용합니다. 따라서 Experience Platform에 데이터를 보낼 때 모든 DX 제품에서 데이터를 이해할 수 있습니다. 자세히 알아보기 [스키마](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **데이터 세트** - 데이터 수집을 위한 저장소 및 관리 구성으로서, 일반적으로 스키마(열) 및 필드(행)를 포함하는 테이블입니다. 데이터 세트에는 저장하는 데이터의 다양한 측면을 설명하는 메타데이터도 포함됩니다. Adobe Experience Platform에 성공적으로 수집된 모든 데이터는 데이터 세트 내에 포함됩니다. 자세히 알아보기 [데이터 세트](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **데이터스트림** - Adobe Experience Platform에서 다른 Adobe DX 제품으로 데이터가 흐를 수 있는 ID입니다. 이 ID는 특정 Adobe Commerce 인스턴스 내의 특정 웹 사이트에 연결되어야 합니다. 이 데이터 스트림을 만들 때 위에서 만든 XDM 스키마를 지정합니다. 자세히 알아보기 [데이터스트림](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## 지원되는 아키텍처

다음 [!DNL Data Connection] 확장은 다음 아키텍처에서 사용할 수 있습니다.

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## 전제 조건

을(를) 사용하려면 [!DNL Data Connection] 확장에는 다음이 있어야 합니다.

* Adobe Commerce 2.4.4 이상
* Adobe ID 및 조직 ID
* [Adobe 클라이언트 데이터 레이어(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html): 상점 이벤트 데이터를 수집하는 데 필요합니다.
* 다른 Adobe DX 제품에 대한 자격.

## 온보딩 단계

높은 수준에서 [!DNL Data Connection] 확장에는 다음 단계가 포함됩니다.

1. [설치](install.md) 다음 [!DNL Data Connection] 확장명.
1. [로그인](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) Adobe 계정 및 [확인할 보기](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) 조직 ID입니다. 조직 ID 는 공급된 Experience Cloud 회사와 연결된 ID입니다. 이 ID는 24자의 영숫자 문자열과 (포함 필수)로 구성됩니다. `@AdobeOrg`.
1. 다음을 수행했는지 확인 [Experience Platform의 데이터 수집 권한](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html).
1. 리뷰 [데이터 유형](data-ingestion.md) 수집해서 보낼 수 있습니다.
1. 만들기 또는 업데이트 [시계열 이벤트 스키마](update-xdm.md) 또는 [프로필 레코드 데이터 스키마](profile-data.md) (상거래 관련 필드 그룹 포함)
1. [데이터 세트 만들기](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) 생성 또는 업데이트한 스키마를 기반으로 합니다. 이 데이터 세트에는 Experience Platform Edge로 전송된 상거래 데이터가 포함되어 있습니다.
1. [데이터 스트림 만들기](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) 상거래 관련 필드 그룹을 포함하는 XDM 스키마를 선택합니다.
1. [상거래 서비스에 연결](../landing/saas.md).
1. [Adobe Experience Platform에 연결](connect-data.md).

이 안내서의 나머지 부분에서는 이러한 모든 단계를 보다 자세히 안내하므로 Commerce 스토어에서 Adobe DX 제품의 기능을 최대한 빠르게 사용하고 사용할 수 있습니다.

>[!NOTE]
>
>모바일 개발자의 경우 방법 알아보기 [통합](./mobile-sdk-epc.md) Adobe Experience Platform Mobile SDK와 Commerce.

## 대상자

이 안내서는 상점을 풍요롭게 하고 개인화하여 고객의 쇼핑 경험을 향상시키고자 하는 Adobe Commerce 판매자를 위해 설계되었습니다.

## 지원

이 안내서에서 다루지 않는 정보가 필요하거나 질문이 있는 경우 다음 리소스를 사용하십시오.

* [도움말 센터](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}- 추가 지원을 받으려면 티켓을 제출합니다.
