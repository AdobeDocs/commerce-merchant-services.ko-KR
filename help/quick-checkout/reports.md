---
title: "[!DNL Quick Checkout] 보고"
description: "[!DNL Quick Checkout] 포괄적인 보고 정보를 제공합니다."
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---


# 보고서

[!DNL Quick Checkout] Adobe Commerce 및 Magento Open Source의 경우 스토어의 체크아웃 경험 통계에 대한 자세한 정보를 가져올 수 있도록 포괄적인 보고를 제공합니다.

![보고서 보기](assets/reports-view-big-checkout.png)

>[!WARNING]
>
> 활성화 [**체크아웃 추적**](../quick-checkout/settings-quick-checkout.md) 을(를) 관리자 패널에서 사용할 수 있으므로 Adobe Commerce은 볼트와 체크아웃 정보를 공유할 수 있습니다. 기본적으로 이 구성 옵션은 **예**. 이 옵션을 비활성화한 경우( **아니요**), 보고에 영향을 줍니다.

## 개요 보고서

개요 섹션의 차트는 평균 체크아웃 시간, 체크아웃 또는 체크아웃 포기 중에 생성된 새 계정 등 저장소의 체크아웃 성능에 대한 자세한 정보를 보여줍니다.

![보고서 개요](assets/overview-report-checkout.png)

| 차트 | 설명 |
|---|---|
| [!UICONTROL Checkout abandonment] | 구매를 완료하지 않고 체크아웃 프로세스를 종료한 방문자의 비율. |
| [!UICONTROL Checkout abandonment breakdown] | 방문자 유형으로 나눈 체크아웃 포기. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | 방문자가 체크아웃 프로세스를 완료하는 데 걸리는 평균 시간입니다. |
| [!UICONTROL Average checkout time breakdown] | 방문자 유형으로 나눈 평균 체크아웃 시간. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 방문자 유형으로 나눈 주문입니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## 트렌드 보고서

트렌드 섹션의 차트는 계정 유형별로 필터링된 체크아웃 경험 트렌드 또는 체크아웃 중에 생성된 새 계정을 보여줍니다.

![보고서 트렌드](assets/trends-report-checkout.png)

| 차트 | 설명 |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | 체크아웃 포기 트렌드를 방문자 유형으로 나눈 값입니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | 주문에서 트렌드를 방문자 유형으로 나누었습니다. 옵션: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | 저장소 트렌드의 새 계정. |

## 데이터 필터링

날짜별로 표시된 결과 또는 다음과 같은 기존 사전 설정을 필터링할 수 있습니다 **최근 30일**.

![필터 보기](assets/filter-view.png)

| 필드 | 설명 |
|---|---|
| [!UICONTROL Preset] | 특정 데이터 범위를 표시하는 데 사용할 수 있는 기본 사전 설정을 표시하는 드롭다운입니다. 기본적으로 최근 30일 |
| [!UICONTROL Date range] | 선택한 날짜에 따라 특정 데이터 범위를 선택할 수 있는 드롭다운입니다. |

