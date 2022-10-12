---
title: 결제 보고서
description: 지급 금액, 처리된 볼륨 및 재무 조정을 위한 거래 레벨에 대한 상세 보고의 전체 투명도를 위해 지급 보고서 사용.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: ddd9fa9b2a709858239c88477f19e8787a0b65c2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 결제 보고서

[!DNL Payment Services] 대상 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 는 저장소의 주문 및 지불을 명확하게 파악할 수 있도록 포괄적인 보고를 제공합니다.

![재무 보고서 보기](assets/reports-justpayouts.png)

모든 지불에 대한 심층적인 정보를 볼 수 있도록 사용할 수 있는 Payouts 보고 보기는 두 가지가 있습니다.

* **[페이아웃 데이터 시각화 보기](#payouts-data-visualization-view)**- Payment Services 홈에서 사용할 수 있는 차트로, Payouts 보고서 보기에서 일별 합계된 금액을 시각적으로 나타냅니다.
* **[결제 보고서 보기](#payouts-report-view)**- 모든 트랜잭션에 대한 자세한 지급 정보를 보여주는 Payouts에서 사용할 수 있는 보고서

지급 뷰(Payouts)는 포괄적인 지급 정보를 한 눈에 표시하여 지급 금액, 처리된 볼륨 및 재무 조정을 위한 거래 레벨에 대한 자세한 보고를 완전히 투명하게 할 수 있습니다.

>[!NOTE]
>
>지급 보고서는 캡처된 주문만 표시합니다(지급 조치는 [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method))—또는 [표시 `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## 페이아웃 데이터 시각화 보기

페이아웃 데이터 시각화 보기는 Payment Services 홈에서 사용할 수 있습니다. 이것은 상세 테이블 형식의 일별 합계된 금액을 시각적으로 나타냅니다 [결제 보고서 보기](#payouts-report-view).

설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** 시간 경과에 따른 크레딧과 차변량 및 이동 평균의 데이터 시각화 차트를 볼 수 있습니다.

![관리에서 지급 데이터 시각화](assets/payouts-report.png)

클릭 **[!UICONTROL View Report]** 세부 테이블 형식으로 이동 [결제 보고서 보기](#payouts-report-view).

### 트랜잭션 일정 사용자 지정

기본적으로 30일 동안의 트랜잭션이 표시됩니다.

지급 데이터 시각화 보기에서 날짜 범위를 선택하여 보려는 지급 트랜잭션에 대한 기간을 사용자 지정할 수 있습니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. 페이아웃 데이터 시각화 보기는 페이아웃 섹션에 표시됩니다.
1. 을(를) 클릭합니다. **[!UICONTROL Range]** 선택기 필터.
1. 적용 가능한 날짜 범위(30일, 15일 또는 7일)를 선택합니다.
1. 지정한 날짜에 대한 트랜잭션 정보를 봅니다.

### 트랜잭션 정보

선택한 날짜 범위에 대한 트랜잭션 금액이 페이아웃 데이터 시각화 보기 왼쪽에 표시됩니다. 선택한 날짜 범위의 날짜가 보기 하단에 표시됩니다. 특정 날짜에 급여가 없다면 해당 날짜가 표시되지 않습니다.

페이아웃 데이터 시각화 보기에는 다음 정보가 포함됩니다.

| 데이터 | 설명 |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | 지정된 기간의 트랜잭션에 대한 금액 범위 Y축의 데이터(왼쪽) |
| 날짜 범위 | 지정된 기간 날짜 범위 X축의 데이터(아래쪽) |
| 신용 | 지정된 기간 동안의 지급 |
| 차변 | 지정된 기간에 대한 디베이트(환불) |
| 이동 평균 | 지정된 기간 내의 각 날짜에 대한 평균 지급 표시 |
| 범위 지정 | 지정된 기간(범위)에 대한 순지급금 금액 |

## 결제 보고서 보기

페이아웃 보고서 보기는 지급 서비스의 페이아웃 보기에서 사용할 수 있습니다. 여기에는 스토어의 페이아웃에 대한 사용 가능한 모든 정보가 포함됩니다. 다음 [페이아웃 데이터 시각화 보기](#payouts-data-visualization-view) 지급 서비스 홈에서는 보다 자세한 보고서 보기에서 일별 합계된 금액을 시각적으로 나타냅니다.

설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]** 상세 테이블 형식 페이아웃 보고서 보기를 보려면

![관리자의 지급 트랜잭션](assets/payouts-report-new.png)

이 항목의 섹션에 따라 이 보기를 구성하여 원하는 데이터를 가장 잘 표현할 수 있습니다.

관리자의 Payouts 보고서 내에서 연결된 상거래 주문 및 거래 ID, 거래 금액, 트랜잭션당 결제 방법 등을 참조하십시오.

기존 회계 또는 주문 관리 소프트웨어에 사용하기 위해 .csv 파일 형식으로 지급 트랜잭션을 다운로드할 수 있습니다.

>[!NOTE]
>
>이 표에 표시된 데이터는 내림차순으로 정렬됩니다(`DESC`) 기본적으로 `TRANS DATE`. 다음 `TRANS DATE` 은 트랜잭션이 시작된 날짜 및 시간입니다.

### 데이터 소스 선택

페이아웃 보고서 보기에서 데이터 소스를 선택할 수 있습니다._[!UICONTROL Live]_또는_[!UICONTROL Sandbox]_- 보고서 결과를 보려는 경우

![데이터 소스 선택](assets/datasource.png)

If _[!UICONTROL Live]_는 선택한 데이터 소스입니다. 라이브 스토어에 대한 보고서 정보를 볼 수 있습니다. If [!UICONTROL Sandbox]_ 은 선택한 데이터 소스이므로 샌드박스 환경에 대한 보고서 정보를 볼 수 있습니다.

데이터 소스 선택 기능은 다음과 같이 작동합니다.

* 라이브 모드에 있는 저장소가 없는 경우 데이터 소스 선택 기본값은 입니다 _[!UICONTROL Sandbox]_.
* 라이브 모드에 저장소(하나 또는 여러 개)가 있는 경우 데이터 소스 선택 기본값은 입니다. _[!UICONTROL Live]_.
* 보고서 내보내기는 항상 데이터 소스를 선택합니다.

주문 지급 상태 보고서에 대한 데이터 출처를 선택하려면

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. 클릭 **[!UICONTROL Data source]** 을(를) 선택합니다. _[!UICONTROL Live]_또는_[!UICONTROL Sandbox]_.

   보고서 결과는 선택한 데이터 소스에 따라 다시 생성됩니다.

### 트랜잭션 보기

기본적으로 30일 동안의 트랜잭션이 표시됩니다.

검색에서 반환되거나 기본 30일 동안의 트랜잭션에 표시된 행 수가 트랜잭션 날짜 달력 선택기 필터와 함께 페이아웃 보기 그리드 위에 표시됩니다.

보려면 왼쪽 및 오른쪽으로 스크롤합니다. [각 지급 트랜잭션에 대한 정보](#column-descriptions) 트랜잭션 날짜, 참조 ID, 송장 번호 및 결제 방법 세부 사항을 포함하는 일별 보고서에서 확인할 수 있습니다.

#### 트랜잭션 일정 사용자 지정

지급 보고서 보기에서 특정 날짜를 입력하거나 일자 선택기에서 날짜 범위를 선택하여 보려는 지급 트랜잭션에 대한 기간을 사용자 지정할 수 있습니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. 트랜잭션 날짜 달력 선택기 필터를 클릭합니다.
1. 적용 가능한 날짜 범위를 선택합니다.
1. 지정된 날짜에 대한 그리드에서 결제 상태를 봅니다.

### 열 표시 및 숨기기

페이아웃 보고서 보기에는 기본적으로 사용 가능한 대부분의 정보 열이 표시됩니다. 그러나 보고서에 표시되는 열을 사용자 지정할 수 있습니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. 을(를) 클릭합니다. _열 설정_ 아이콘 (![열 설정 아이콘](assets/column-settings.png)).
1. 보고서에 표시되는 열을 사용자 지정하려면 목록에서 열을 선택하거나 선택 취소합니다.

   페이아웃 보고서 보기에는 열 설정 메뉴에서 변경한 내용이 즉시 표시됩니다. 열 환경 설정이 저장되며 보고서 보기에서 멀리 탐색하는 경우 그대로 유지됩니다.

### 트랜잭션 다운로드

페이아웃 보기 그리드에 표시되는 모든 트랜잭션이 포함된 .csv 파일을 다운로드할 수 있습니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [트랜잭션에 대한 날짜 범위 기간을 사용자 지정합니다](#customize-transactions-timeframe).
1. 을(를) 클릭합니다. _다운로드_ (![](assets/icon-download.png)) 아이콘을 클릭합니다.

지급 트랜잭션은 .csv 형식으로 다운로드됩니다.

### 열 설명

지급 보고서에는 다음 정보가 포함됩니다.

| 열 | 설명 |
| ------------ | -------------------- |
| [!UICONTROL Provider] | 결제 공급자 |
| [!UICONTROL Provider trans] | 거래 ID |
| [!UICONTROL Trans date] | 트랜잭션이 시작된 날짜 및 시간 |
| [!UICONTROL Type] | 트랜잭션 유형—*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>자세한 내용은 [트랜잭션 유형](#transaction-types) 추가 정보. |
| [!UICONTROL Status] | 거래의 현재 상태—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | 대변(*CR*) 또는 차변(*DR*) |
| [!UICONTROL Reference ID] | 이 이벤트와 관련된 원래 거래 ID |
| [!UICONTROL Invoice] | 거래의 송장 ID(주문당 하나) |
| [!UICONTROL Commerce order] | 상거래 주문 ID <br> <br>관련 항목을 보려면 [주문 정보](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, ID를 클릭합니다. |
| [!UICONTROL Commerce trans] | 상거래 거래 ID <br> <br>관련 항목을 보려면 [트랜잭션 정보](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}, ID를 클릭합니다. |
| [!UICONTROL Pay method] | 신용 카드 유형—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL APPLE_PAY]*, *[!UICONTROL CREDIT_CARD]*—및 관련 카드 공급자(예: *비자* 또는 *마스터 카드*) |
| [!UICONTROL Trans amt] | 거래 금액 |
| [!UICONTROL Cur] | 거래 금액에 대한 통화 단위 |
| [!UICONTROL Pending] | 아직 지급되지 않은 금액 |
| [!UICONTROL Cur] | 보류 금액에 대한 통화 단위 |
| [!UICONTROL Seller amt] | 고객에게 이전되거나 고객으로부터 이전된 자금 금액 <br> <br>판매자 계정에서 이동하는 자금은 대시(-) 접두사를 표시합니다. |
| [!UICONTROL Cur] | 판매자 금액에 대한 통화 단위 |
| [!UICONTROL Partner fee] | 거래와 관련된 파트너 비용 <br> <br>파트너 요금 계정에서 이동하는 자금은 대시(-) 접두사를 표시합니다. |
| [!UICONTROL Cur] | 파트너 비용에 대한 통화 단위 |
| [!UICONTROL Prov fees] | 거래와 관련된 수수료 <br> <br>공급자의 유료 계정에서 이동하는 자금은 대시(-) 접두사를 표시합니다. |
| [!UICONTROL Cur] | 공급자 요금에 대한 통화 단위 |
| [!UICONTROL Fee %] | 수수료로 부과된 거래 금액의 퍼센트 |
| [!UICONTROL Fixed fee] | 고정 공급자 수수료 금액 |
| [!UICONTROL Chbk fee] | 거래 관련 비용 산출 <br> <br>대시(-) 접두사는 채권갱신 비용이 취소되었음을 나타냅니다. |
| [!UICONTROL Cur] | 채권갱신 비용에 대한 통화 단위 |
| [!UICONTROL Hold amt] | 보류 또는 보류 해제 금액 <br> <br>대기 중인 자금이 릴리즈되고 있음을 나타내는 대시(-) 접두어 |
| [!UICONTROL Cur] | 보류 금액에 대한 통화 단위 |
| [!UICONTROL Recoup amt] | 회수 계정에서 회수된 금액 <br> <br>복구 계정에서 이동하는 자금은 대시(-) 접두사를 표시합니다. |
| [!UICONTROL Cur] | 회수 금액에 대한 통화 단위 |

### 트랜잭션 유형

이러한 거래 유형은 지급 트랜잭션에 기록될 수 있습니다.

| 보고서 | 설명 |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | 구매자와 판매자 간에 주문하기 위해 돈이 이동했다 |
| [!UICONTROL AUTH] | 승인 및 승인 무효 거래 |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | 채권갱신 요금 및 채권갱신 요금 취소 거래 |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | 파트너 수수료, 결제 수수료 및 요금 취소 거래 |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | 은행 또는 손실 계좌에서 회수 |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
