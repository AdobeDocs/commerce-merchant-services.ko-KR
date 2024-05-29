---
title: Adobe Journey Optimizer을 사용하여 포기한 장바구니 이메일 보내기
description: Adobe Journey Optimizer을 사용하여 포기한 장바구니 이메일을 보내는 방법을 알아봅니다.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: a94f75dfab1f88f02e217b0e021cc2dfc94244c7
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 0%

---

# Adobe Journey Optimizer을 사용하여 포기한 장바구니 이메일 보내기

장바구니 또는 브라우저 세션이 중단된 경우 개인화된 재참여 이메일 또는 알림을 전달하는 방법을 알아봅니다. 이 문서에서는 여러 제품 및 카테고리를 보거나, 제품에 참여하거나, 페이지에서 시간을 보낸 고객으로부터 생성된 데이터를 사용합니다.

## 어떤 데이터를 사용해야 합니까?

상점 및 백오피스 이벤트의 데이터를 사용하여 포기한 장바구니를 작성하고, 이메일을 검색하거나, 알림을 보냅니다.

| 데이터 유형 | Storefront 데이터(행동 이벤트) | 백오피스 데이터(서버측 이벤트) |
|---|---|---|
| **정의** | 고객이 사이트에서 수행하는 클릭 또는 작업입니다. | 각 주문(과거 및 현재)의 라이프사이클 및 세부 정보에 대한 정보. |
| **Adobe Commerce에 의해 캡처된 이벤트** | [pageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#pageview)<br>[제품 페이지 보기](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events)<br>[추가 장바구니](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#addtocart)<br>[openCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#opencart)<br>[startCheck](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#startcheckout)<br>[completeCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#completecheckout) | [주문](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events-backoffice#orderplaced)<br>[주문 내역](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/fundamentals/connect-data#send-historical-order-data) |

### Adobe Commerce 만으로 무엇을 할 수 있습니까?

Adobe 사용 [!DNL Commerce] 장바구니 역할을 하거나 포기 이메일을 찾아볼 수 있는 규칙 기반 이메일 미리 알림을 설정합니다. 여기에서 방법을 알아보십시오.

### Adobe으로 무엇을 할 수 있습니까 [!DNL Commerce] Experience Cloud?

- **Adobe [!DNL Commerce] Adobe Journey Optimizer 사용** - Adobe 사용 [!DNL Commerce] Adobe Journey Optimizer을 사용하면 다음을 사용할 수 있습니다. [!DNL Commerce] 옴니채널 포기 여정 트리거로서의 데이터. 고객 속성, 포기한 항목, 기타 쇼핑 행동 및 과거 구매 행동을 기반으로 해당 여정을 개인화할 수 있습니다.

- **Adobe Commerce, Adobe Journey Optimizer 및 Adobe Real-Time CDP** - Real-Time CDP을 추가하면 통합 고객 프로필과 중앙 집중식으로 관리되는 규칙 기반 또는 AI 기반 대상자를 기반으로 포기 캠페인을 보다 세분화할 수 있습니다. 예를 들어 다음을 만들 수 있습니다.

   - 포기 비율이 낮은 &quot;강력한 변환기&quot; 대상
   - 특정 카테고리를 여러 번 재방문한 &quot;높은 배려&quot; 대상
   - 높은 지출과 충성도를 가지지만 최근에 포기한 &quot;높은 잠재력&quot; 대상

### 다른 고객들은 어떤 성과를 얻었습니까?

Adobe [!DNL Commerce] 고객은 Adobe을 사용하여 개인화된 포기 캠페인을 구현함으로써 비즈니스에 상당한 영향을 미쳤습니다 [!DNL Commerce], ADOBE [!DNL Journey Optimizer], 및 Adobe [!DNL Real-Time CDP].

글로벌 다중 브랜드 의류 소매업체:

- 새 캠페인에서 클릭 시 1.9배 전환
- 옴니채널 포기 여정으로 인한 매출 57% 증가
- 재참여 캠페인의 전환율 41% 증가
- 주당 1,000명 이상의 신규 고객 참여

한 세계적인 음료 회사는 다음을 달성했습니다.

- 재참여 이메일 열람률 36%
- 클릭스루 비율 21% 향상
- 전환율 8.5% 상승
- 89%의 재계약 포기 자가 전환됨

## 시작하겠습니다.

이 특정 사용 사례는 의 데이터를 사용하여 포기한 장바구니 이메일을 만드는 데 중점을 둡니다. [!DNL Commerce] 인스턴스 및 Adobe으로 보내기 [!DNL Journey Optimizer].

### Adobe Journey Optimizer란?

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) 은 쇼핑객을 위해 상거래 경험을 개인화할 수 있도록 지원합니다. 예를 들어, Journey Optimizer을 사용하여 소매 스토어에 대한 주별 판촉 행사 등 예약된 마케팅 캠페인을 만들고 게재하거나, 고객이 장바구니에 제품을 추가했지만 체크아웃 프로세스를 완료하지 않은 경우 포기한 장바구니 이메일을 생성할 수 있습니다.

이 항목에서는 의 설명을 듣고 포기한 장바구니 이메일을 작성하는 방법을 알아봅니다. `checkout` 에서 이벤트가 생성됨 [!DNL Commerce] 인스턴스 및 Journey Optimizer의 해당 이벤트에 대한 응답.

>[!IMPORTANT]
>
>데모 목적으로 다음을 사용하십시오. [!DNL Commerce] 샌드박스 환경 을 사용하면 프로덕션 이벤트 데이터를 Experience Platform으로 보내는 storefront 및 back office 이벤트 데이터로 희석하지 않습니다.

### 전제 조건

이 단계를 시작하기 전에 다음을 확인하십시오.

- Adobe을 사용할 수 있도록 프로비저닝되었습니다. [!DNL Journey Optimizer]. 확실하지 않은 경우 프로젝트 및 환경을 관리하는 시스템 통합자나 개발 팀에 문의하십시오.
- 본인 [설치됨](install.md) 및 [구성됨](connect-data.md) 다음 [!DNL Data Connection] 의 확장 [!DNL Commerce].
- 본인 [확인됨](connect-data.md#confirm-that-event-data-is-collected) 내 [!DNL Commerce] 이벤트 데이터가 Experience Platform 에지에 도착합니다.

## 1단계: [!DNL Commerce] 샌드박스 환경

샌드박스 환경에서 사용자를 만들고 사용자 계정 정보가 Experience Platform에 표시되는지 확인합니다. 지정한 이메일이 이 섹션의 뒷부분에서 포기한 장바구니 이메일을 보내는 데 사용된 이메일과 같이 유효한지 확인합니다.

1. 로그인 또는 계정 만들기 [!DNL Commerce] 샌드박스 환경.

   ![테스트 계정에 로그인](assets/sign-in-account.png){width="700" zoomable="yes"}

   포함 [!DNL Data Connection] 확장이 설치 및 구성되면 이 계정 정보가 프로필로 Experience Platform에게 전송됩니다.

1. 사용자 계정 정보가 **[!UICONTROL Profile]** Experience Platform 섹션에 있는 마지막 항목이 될 필요가 없습니다.

   다음으로 이동 **[!UICONTROL Profiles]** Adobe Experience Platform. 클릭 **[!UICONTROL Detail]** 을 클릭하여 만든 프로필을 확인합니다.

   ![프로필 확인](assets/check-event-profile.png){width="700" zoomable="yes"}

## 2단계: Journey Optimizer에서 이벤트 보기

내 [!DNL Commerce] 샌드박스 환경, 제품 페이지를 보고, 장바구니에 항목을 추가하고, 쇼핑객이 수행할 다양한 기타 활동을 완료하여 상점 첫 화면에서 이벤트를 트리거합니다. 그런 다음 이러한 이벤트가 Journey Optimizer으로 전달되는지 확인합니다.

1. 시작 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. 선택 **[!UICONTROL Profiles]**.
1. 설정 **[!UICONTROL Identity namespace]** 끝 `Email`.
1. 설정 **[!UICONTROL Identity value]** 이메일 주소로 보냅니다.
1. 프로필을 선택한 다음 **[!UICONTROL Events]** 탭.

   ![이벤트 세부 정보 확인](assets/check-event-details.png){width="700" zoomable="yes"}

   다음 항목을 찾습니다. `commerce.checkouts` 이벤트 및 이벤트 페이로드를 검사합니다.

       &quot;json
       &quot;personID&quot;: &quot;84281643067178465783746543501073369488&quot;,
       &quot;eventType&quot;: &quot;commerce.checkouts&quot;,
       &quot;_id&quot;: &quot;4b41703f-e42e-485b-8d63-7001e3580856-0&quot;,
       &quot;commerce&quot;: {
       &quot;장바구니&quot;: {},
       &quot;체크아웃&quot;: {
       &quot;value&quot;: 1
       }
       &quot;
   
   알 수 있듯이 전체 이벤트 페이로드에는 풍부한 이벤트 데이터가 포함되어 있습니다. 다음 섹션에서는 를 수신하고 응답하도록 Journey Optimizer에서 이벤트를 구성합니다. `commerce.checkouts` 에서 이벤트가 생성됨 [!DNL Commerce] 가게 앞이야

## 3단계: Journey Optimizer에서 이벤트 구성

Journey Optimizer에서 두 개의 이벤트를 구성합니다. 한 개의 이벤트는 `commerce.checkouts` Commerce의 이벤트이며, 다른 하나는 포기한 장바구니 이메일을 트리거하기 전에 특정 시간이 경과할 때까지 기다리는 기본 시간 초과 이벤트입니다.

### 리스너 이벤트 만들기

1. 시작 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. 클릭 **[!UICONTROL Configurations]** 다음 아래에 **[!UICONTROL Administration]** 왼쪽 창의 섹션입니다.

1. 다음에서 **[!UICONTROL Events]** 타일, 클릭 **[!UICONTROL Manage]**.

   ![Journey Optimizer 이벤트 구성](assets/ajo-config.png){width="700" zoomable="yes"}

1. 다음에서 **[!UICONTROL Events]** 페이지, 클릭 **[!UICONTROL Create Event]**.

1. 오른쪽 탐색에서 다음과 같이 이벤트를 설정합니다.

   1. 설정 **[!UICONTROL Name]** 끝: `firstname_lastname_checkout`.
   1. 설정 **[!UICONTROL Type]** 끝 **[!UICONTROL Unitary]**.
   1. 설정 **[!UICONTROL Event id typ]e** 끝 **[!UICONTROL Rule based]**.
   1. 설정 **[!UICONTROL Schema]** (으)로 [!DNL Commerce] [스키마](update-xdm.md).
   1. 선택 **[!UICONTROL Fields]** 을(를) 열려면 **[!UICONTROL Fields]** 페이지를 가리키도록 업데이트하는 중입니다. 그런 다음 이 이벤트에 유용한 필드를 선택합니다. 예를 들어 **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]**, 및 **[!UICONTROL Web]**.
   1. 클릭 **[!UICONTROL OK]** 을 눌러 선택한 필드를 저장합니다.
   1. 내부를 클릭합니다. **[!UICONTROL Event id condition]** 필드. 그런 다음 조건을 만듭니다. `eventType` 다음과 같음 `commerce.checkouts` 및 `personalEmail.address` 은 이전 섹션에서 프로필을 만들 때 사용한 이메일 주소와 같습니다.

      ![Journey Optimizer 조건 설정](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. 클릭 **[!UICONTROL OK]**.
   1. 클릭 **[!UICONTROL Save]** 이벤트를 저장합니다.

### 시간 초과 이벤트 만들기

1. 이전과 마찬가지로 Journey Optimizer에서 이벤트를 만듭니다.

1. 오른쪽 탐색에서 다음과 같이 이벤트를 설정합니다.

   1. 설정 **[!UICONTROL Name]** 끝: `firstname_lastname_timeout`.
   1. 설정 **[!UICONTROL Type]** 끝 **[!UICONTROL Unitary]**.
   1. 설정 **[!UICONTROL Event id type]** 끝 **[!UICONTROL Rule based]**.
   1. 설정 **[!UICONTROL Schema]** (으)로 [!DNL Commerce] [스키마](update-xdm.md).
   1. 설정 **[!UICONTROL Schema]**, **[!UICONTROL Fields]**, 및 **[!UICONTROL Event id condition]** 을 위의 과 동일하게 설정합니다.
   1. 클릭 **[!UICONTROL Save]** 이벤트를 저장합니다.

이 두 이벤트를 구성하여 포기한 장바구니 이메일을 보내는 여정을 만듭니다.

## 4단계: 체크아웃 여정 작성

를 수신하는 여정 만들기 `commerce.checkouts` 지정된 시간이 경과하면 중단된 장바구니 이메일을 전송합니다.

1. Journey Optimizer에서 **[!UICONTROL Journeys]** 아래에 **J[!UICONTROL OURNEY MANAGEMENT]**.
1. 클릭 **[!UICONTROL Create Journey]**.
1. 여정 이름을 지정합니다.
1. 클릭 **[!UICONTROL OK]** 여정을 저장합니다.
1. 왼쪽 탐색( 아래) **[!UICONTROL EVENTS]** 섹션에서 이전에 만든 체크아웃 이벤트를 검색합니다. `firstname_lastname_checkout` 캔버스에 끌어서 놓으세요.

   >[!TIP]
   >
   >이벤트를 두 번 클릭하면 캔버스에 자동으로 추가됩니다.

1. 시간 초과 이벤트를 검색하고 캔버스에 추가합니다.
1. 시간 초과 이벤트를 두 번 클릭합니다.

   1. 다음에서 **[!UICONTROL Timeout]** 섹션에서 **[!UICONTROL Define the event time]** 확인란.
   1. 다음에서 **[!UICONTROL Wait for]** 필드 입력 `1` 및 `Minute`.
   1. 다음 항목 선택 **[!UICONTROL Set a timeout path]** 확인란.

   이 시간 초과 구성을 사용하면 체크아웃을 수행하지만 1분 이내에 주문을 완료하지 않는 쇼퍼가 이 시간 초과 분기를 트리거합니다. 실제 프로덕션 환경에서는 이 값을 24시간과 같이 더 긴 기간 동안 설정합니다.

1. 아래의 왼쪽 탐색에서 **[!UICONTROL ACTIONS]**, 추가 **[!UICONTROL Email]** 작업을 시간 초과 분기에 추가합니다. 여정은 다음과 같아야 합니다.

   ![Journey Optimizer 캔버스](assets/ajo-canvas.png){width="700" zoomable="yes"}

### 포기한 장바구니 이메일 만들기

포기한 장바구니가 감지될 때 전송되는 포기한 장바구니 이메일을 만듭니다.

1. 위에서 만든 여정에서 **[!UICONTROL Email]** 아이콘으로 표시됩니다.

1. 다음 [단계](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) 포기한 장바구니 이메일을 만들려면 Journey Optimizer 안내서를 참조하십시오.

여정 이제 Journey Optimizer에서 `commerce.checkouts` 의 이벤트 [!DNL Commerce] 일정 시간이 지난 후 전송된 포기한 장바구니 이메일을 저장합니다. 다음 섹션에서는 여정을 테스트하는 방법을 보여줍니다.

## 5단계: 실시간으로 체크아웃 이벤트 트리거

이 섹션에서는 이벤트를 실시간으로 테스트합니다.

1. Journey Optimizer에서 테스트 모드를 전환합니다.

   ![테스트 모드 활성화](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. 이 여정을 실시간으로 테스트하려면 다른 브라우저 탭을 열고 [!DNL Commerce] 샌드박스 환경의 웹 사이트

   1. 장바구니에 제품을 추가합니다.
   1. 체크아웃 페이지로 이동합니다.
   1. 체크아웃 페이지에서 기본 페이지로 돌아가거나 탭을 닫아 장바구니를 포기합니다.

      이제 여정이 트리거됩니다. 확인하려면 Journey Optimizer에서 여정이 있는 탭을 엽니다. 사용자가 이동한 경로를 표시하는 녹색 화살표가 표시됩니다.

1. 받은 편지함에서 이메일을 확인합니다.
