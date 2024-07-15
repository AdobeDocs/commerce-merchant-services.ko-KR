---
title: '[!DNL Product Recommendations] Workspace'
description: 제품 추천 성능을 구성, 관리 및 모니터링하는 방법에 대해 알아봅니다.
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: 25d5321b6f29bab5d8cf329170f3644f35100438
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---

# [!DNL Product Recommendations] Workspace

[!DNL Product Recommendations] 작업 영역에는 각 권장 사항의 성공을 추적하는 데 도움이 되는 지표와 함께 이전에 구성된 권장 사항 목록이 표시됩니다. 마지막 일, 주 또는 월에 대한 지표를 계산하도록 목록을 구성할 수 있습니다. 지표를 사용하여 권장 사항 단위를 보거나 클릭한 빈도에 따라 실행 가능한 통찰력을 만들거나 권장 사항이 얼마나 잘 작동하는지 분석할 수 있습니다.

![Recommendations 작업 공간](assets/workspace.png)
_Recommendations Workspace_

## 범위 설정

처음에는 모든 권장 설정 중 [범위](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)가 `Default Store View`(으)로 설정되어 있습니다. Commerce 설치에 여러 스토어 보기가 포함된 경우 **범위**&#x200B;를 권장 사항이 적용되는 [스토어 보기](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)(으)로 설정하십시오.

## 지표 날짜 범위 설정

1. **달력** ![달력 선택기](assets/icon-calendar.png) 컨트롤을 클릭합니다.

1. 다음 중 하나를 선택합니다.

   - 지난 24시간
   - 지난 7일
   - 지난 30일

   지표 열의 계산된 값이 현재 날짜 범위를 반영하도록 변경됩니다.

## 열 표시/숨기기

1. 왼쪽 상단 모서리에서 **표시/숨기기** ![열 선택기](assets/icon-show-hide-columns.png)열을 클릭합니다.

   표시되는 열에는 파란색 확인 표시가 있습니다.

1. 메뉴에서 다음 중 하나를 수행합니다.

   - 숨겨진 열을 표시하려면 확인 표시 없이 열 이름을 클릭합니다.
   - 표시되는 열을 숨기려면 확인 표시가 있는 열 이름을 클릭합니다.

   선택한 열만 포함하도록 테이블이 새로 고쳐집니다.

   ![Recommendations 작업 공간](assets/workspace-select-columns.png)
   _열 표시/숨기기_

## 설정

설정은 추천-행동 데이터를 제공하는 SaaS 데이터 공간을 결정합니다.

- 권장 사항 동작 데이터의 출처를 변경하려면 다른 SaaS 데이터 공간을 선택합니다.

- 새 SaaS 데이터 공간을 구성하려면 **구성 편집**&#x200B;을 클릭하십시오. 자세한 내용은 [설정](settings.md)을 참조하세요.

![Recommendations 설정](assets/settings.png)
_Recommendations 설정_

## 세부 정보 보기

1. 표에서 검사할 권장 사항을 클릭합니다.

   ![Recommendations 작업 공간](assets/recommendation-detail.png)
   _홈 페이지 전환율 세부 정보_

1. 권장 사항의 상태를 변경하려면 **활성화** 또는 **비활성화**&#x200B;를 클릭하십시오.

## 권장 사항 편집

권장 사항 세부 정보 페이지에서 **편집**&#x200B;을 클릭합니다. 자세한 내용을 보려면 [Recommendations 편집](edit.md)(으)로 이동하세요.

## 추천 만들기

권장 사항 세부 정보 페이지에서 **만들기**&#x200B;를 클릭합니다. 자세한 내용을 보려면 [Recommendations 만들기](create.md)(으)로 이동하세요.

## Workspace 컨트롤

| 제어 | 설명 |
|---|---|
| ![일정 선택기](assets/icon-calendar.png) | 지표 계산에 사용되는 시간 범위를 결정합니다. 옵션: 24시간 / 7일 / 30일 |
| ![열 선택기](assets/icon-show-hide-columns.png) | [!DNL Product Recommendations] 테이블에 나타나는 열을 결정합니다. |
| 설정 | 추천 행동 데이터를 가져오는 SaaS 데이터 공간을 결정하고 시각적 유사성 추천 유형도 활성화합니다. |
| 추천 만들기 | [새 권장 사항 만들기](create.md) 페이지를 엽니다. |

## 열 설명

| 열 | 설명 |
|---|---|
| 이름 | 권장 사항의 이름입니다. |
| 페이지 | 권장 사항이 나타나는 페이지입니다. |
| 유형 | 권장 사항 유형. |
| 상태 | 권장 사항 상태. 옵션: 비활성/활성/초안 |
| 생성됨 | 권장 사항이 생성된 날짜입니다. |
| 마지막으로 편집됨 | 권장 사항이 마지막으로 편집된 날짜입니다. |
| 노출 횟수 | 페이지에서 추천 단위가 로드되고 렌더링되는 횟수입니다. 브라우저의 뷰포트에 접힌 부분 아래에 있는 추천 단위는 페이지에서 렌더링되지만 쇼핑객이 볼 수 없습니다. 이 경우, 렌더링된 유닛은 임프레션으로 계산되지만, 뷰는 사용자가 유닛을 뷰로 스크롤하는 경우에만 계산된다. |
| 노출 횟수 | (볼 수 있는 노출 횟수) 하나 이상의 보기를 등록하는 추천 단위 수입니다. |
| 보기 | 쇼핑객 브라우저의 뷰포트에 나타나는 추천 단위 수입니다. 이 이벤트는 페이지에서 여러 번 실행될 수 있습니다. |
| 클릭수 | 쇼핑객이 추천 단위에서 항목을 클릭한 횟수와 쇼핑객이 추천 단위에서 **장바구니에 추가** 단추를 클릭한 횟수의 합계입니다. |
| 매출 | 현재 시간 범위에 대한 권장 사항에 의해 유도된 매출입니다. |
| Lt 수익 | (라이프타임 수익) 추천에 의해 유도된 라이프타임 수익. |
| 가시성 | 보기에 등록하는 추천 단위의 백분율입니다. |
| Ctr | (클릭스루 비율) 클릭을 등록하는 추천에 대한 단위 노출 횟수의 백분율입니다. |
| vCtr | (조회 클릭스루 비율) 클릭을 등록하는 추천 단위에 대한 조회 노출의 백분율입니다. |
