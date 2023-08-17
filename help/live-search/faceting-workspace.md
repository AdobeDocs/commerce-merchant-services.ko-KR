---
title: "작업 영역 구성"
description: "Learn your way around the [!DNL Live Search] 작업 영역 전체에 영향을 미칩니다."
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: e166c8cb9d715dce573195a188b5335c02d8fd0c
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# 작업 영역 구성

다음 [!DNL Live Search] 작업 영역에는 현재 사용 가능한 모든 패싯이 나열되며 패싯을 설정하고 관리하는 데 필요한 도구에 대한 액세스 권한을 제공합니다. 고정된 패싯이 기존 패싯 목록에 먼저 나타나고 그 뒤에 동적 패싯이 나타납니다. 목록을 필터링하여 모든 패싯을 표시하거나 고정되거나 동적인 패싯만 표시할 수 있습니다.

![작업 영역 구성](assets/faceting-workspace.png)

## 범위 설정

Adobe Commerce 설치에 여러 스토어 보기가 포함된 경우 다음을 설정하십시오. **범위** (으)로 [스토어 뷰](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 패싯 설정이 적용되는 위치입니다.

## 목록 필터링

1. 다음을 클릭합니다. **필터링 기준** 제어.
1. 다음 옵션 중 하나를 선택합니다.

   * 모든 필터
   * 고정됨
   * 동적

## Facet 추가

1. 클릭 **패싯 추가**.
1. 다음을 참조하십시오 [패싯 추가](facets-add.md) 자세한 지침은 을 참조하십시오.

## 열 설명

| 열 | 설명 |
|--- |--- |
| (첫 열) | 다음을 통해 고정 및 동적 패싯을 나열합니다. [레이블](facets-type.md) 그것은 쇼핑객에게 보인다. |
| 정렬 유형 | 다음 [정렬 순서](facets-type.md) Facet 값. 패싯은 모든 패싯에 대해 알파벳순으로 정렬됩니다. [!DNL Commerce] 상점 앞들. 대상 [headless] 구현에서 패싯을 알파벳순으로 또는 횟수별로 정렬할 수 있습니다. 옵션: 알파벳, 개수(Headless만 해당) |
| 최대 값 | 상점에서 필터로 사용할 수 있는 최대 10개의 Facet 값 수입니다. |

## 컨트롤

| 제어 | 설명 |
|--- |--- |
| 패싯 추가 | 다음을 엽니다. [Facet 편집기](facets-add.md). |
| 필터링 기준 | 다음을 결정합니다. [패싯 유형](facets-type.md) 목록에 표시됩니다. 옵션: 모두, 고정됨, 동적 |
