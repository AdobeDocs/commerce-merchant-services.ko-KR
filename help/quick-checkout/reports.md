---
title: '[!DNL Quick Checkout] 보고'
description: '[!DNL Quick Checkout] 포괄적인 보고 정보를 제공합니다.'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
source-git-commit: bdfac90aa221f39dfc53eee833c473c7dcb0a042
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# 보고서

[!DNL Quick Checkout] Adobe Commerce 및 Magento Open Source의 경우 스토어의 체크아웃 경험 통계에 대한 자세한 정보를 얻을 수 있도록 포괄적인 보고를 제공합니다.

![보고서 보기](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> Adobe Commerce이 Bolt와 체크아웃 정보를 공유할 수 있도록 [**체크아웃 추적**](../quick-checkout/settings-quick-checkout.md)  관리자는 설정을 활성화해야 합니다. 기본적으로 이 구성 옵션은 **예**. 이 옵션이 로 설정된 경우 **아니요**&#x200B;에 도달하면 보고가 영향을 받습니다. Bolt는 동부 표준시(EST) 오전 3시에 매일 한 번 보고 정보를 새로 고칩니다.

## 개요 보고서

개요 섹션의 차트에는 평균 체크아웃 시간, 체크아웃 또는 체크아웃 포기 중에 생성된 새 계정 등 스토어의 체크아웃 성능에 대한 자세한 정보가 표시됩니다.

![보고서 개요](assets/overview-report-checkout.png)

| 차트 | 설명 |
|---|---|
| [!UICONTROL Checkout abandonment] | 구매를 완료하지 않고 체크아웃 프로세스를 종료한 방문자의 비율입니다. |
| [!UICONTROL Checkout abandonment breakdown] | 체크아웃 포기를 방문자 유형별로 나눈 값입니다. 도구 설명에 볼트와 게스트 간의 백분율 차이가 표시됩니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 방문자가 체크아웃 프로세스를 완료하는 데 걸리는 평균 시간입니다. |
| [!UICONTROL Average checkout time breakdown] | 평균 체크아웃 시간을 방문자 유형으로 나눈 값입니다. 도구 설명에 볼트와 게스트 간의 백분율 차이가 표시됩니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 주문은 방문자 유형별로 나누어집니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 트렌드 보고서

트렌드 섹션의 차트에는 계정 유형별로 필터링된 체크아웃 경험 트렌드 또는 체크아웃 중에 생성된 새 계정이 표시됩니다.

![보고서 트렌드](assets/trends-report-checkout.png)

| 차트 | 설명 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 방문자 유형별로 나눈 체크아웃 포기 트렌드입니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 방문자 유형별로 구분된 주문 트렌드입니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 스토어 트렌드에 대한 새 계정입니다. |

## 데이터 필터링

날짜 또는 과 같은 기존 사전 설정으로 표시된 결과를 필터링할 수 있습니다 **지난 30일**.

![필터 보기](assets/filter-view.png)

| 필드 | 설명 |
|---|---|
| [!UICONTROL Preset] | 특정 데이터 범위를 표시하는 데 사용할 수 있는 기본 사전 설정을 표시하는 드롭다운입니다. 기본적으로, 지난 30일 |
| [!UICONTROL Date range] | 선택한 날짜에 따라 특정 데이터 범위를 선택할 수 있는 드롭다운입니다. |
