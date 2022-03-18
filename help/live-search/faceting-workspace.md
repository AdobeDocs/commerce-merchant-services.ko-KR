---
title: Faceting Workspace
description: Live Search Faceting 작업 공간에 대해 알아봅니다.
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Facting workspace

다음 [!DNL Live Search] 작업 영역에는 현재 사용 가능한 모든 패싯이 나열되며 패싯을 설정하고 관리하는 데 필요한 도구에 액세스할 수 있습니다. 고정된 패싯은 기존 패싯 목록에 먼저 나타나고 동적 패싯이 표시됩니다. 목록을 필터링하여 모든 패싯을 표시하거나 고정되거나 동적 패싯만 표시할 수 있습니다.

![Facting workspace](assets/faceting-workspace.png)

## 범위 설정

Adobe Commerce 설치에 여러 저장소 보기가 포함된 경우 **범위** 변환 후 [저장소 보기](https://docs.magento.com/user-guide/configuration/scope.html) 패싯 설정이 적용되는 위치.

## 목록 필터링

1. 을(를) 클릭합니다. **필터 기준** 제어.
1. 다음 옵션 중 하나를 선택합니다.

   * 모든 필터
   * 고정
   * 동적

   ![Facting workspace](assets/facets-filter-by.png)

## 패싯 추가

1. 클릭 **패싯 추가**.
1. 자세한 내용은 [패싯 추가](facets-add.md) 자세한 지침

## 열 설명

| 열 | 설명 |
|--- |--- |
| (첫 번째 열) | 를 통해 고정되고 동적 패싯을 나열합니다. [레이블](facets-type.md) 쇼핑객에게 보입니다. |
| 유형 선택 | 다음 [선택 방법](facets-type.md) 해당 제품 속성에 할당됩니다. 다음 `single select` 모든 항목에 사용 [!DNL Commerce] 상점 전구. 헤드리스 구현의 경우, `multi-select` 논리 연산자로 유형을 할당할 수 있습니다(`or` 또는 `and`)를 클릭하여 반환된 제품 세트를 결정합니다. |
| 정렬 유형 | 다음 [정렬 순서](facets-type.md) 패싯 값 아래에 표시됩니다. 패싯은 모든 패싯에 대해 알파벳순으로 정렬됩니다 [!DNL Commerce] 상점 전구. 대상 [헤드리스] 구현, 패싯은 알파벳순 또는 카운트별로 정렬할 수 있습니다. 옵션: 알파벳, 카운트(헤드리스만) |
| 최대 값 | 스토어프런트에서 필터로 사용할 수 있는 패싯 값의 수는 최대 10개입니다. |

## 컨트롤

| 제어 | 설명 |
|--- |--- |
| 패싯 추가 | 를 엽니다. [패싯 편집기](facets-add.md). |
| 필터 기준 | 을(를) 결정합니다 [패싯 유형](facets-type.md) 목록에 표시됩니다. 옵션: 모두, 고정, 동적 |
