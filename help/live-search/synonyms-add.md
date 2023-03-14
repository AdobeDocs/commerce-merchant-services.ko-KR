---
title: "동의어 추가"
description: "추가 [!DNL Live Search] 검색 요청에 대한 응답을 개선하기 위한 동의어입니다."
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: c4bca0c7238be653dd13b051634c662e5891767d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 동의어 추가

조정된 자신의 목록을 추가하여 고객 참여도 향상 [!DNL Live Search] 동의어 [!DNL Live Search] 당 최대 200개의 동의어를 관리할 수 있음 `Data Space ID`.

![[!DNL Live Search] 동의어](assets/synonym-workspace.png)

## 1단계: 동의어 추가

1. 관리에서 **마케팅** > SEO 및 검색 > **[!DNL Live Search]**.
1. 여러 스토어의 경우 다음을 설정합니다. **범위** (으)로 [스토어 뷰](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) 여기서 동의어 설정이 적용됩니다.
1. 다음을 클릭합니다. **동의어** 탭.
1. 다음을 클릭합니다. **동의어 추가** 단추를 클릭합니다.

## 2단계: 유형별 동의어 정의

다음 지침을 따르십시오. [동의어 유형](synonyms-type.md) 원하는 대로 만듭니다.

### 양방향 동의어

1. 기본값 적용 **양방향** 옵션을 선택합니다.

   ![양방향 동의어 추가](assets/synonym-add-two-way.png)


1. 다음을 입력합니다. **키워드** 일치하는 용어 또는 구문입니다.
1. 다음을 입력합니다. **확장** 키워드에 대한 동의어로 추가할 용어입니다. 쉼표로 여러 용어를 구분하십시오.
이 예에서 일치시킬 키워드는 &quot;pants&quot;이고 확장 용어 세트는 &quot;long pants, bars, slacks&quot;입니다.

   ![양방향 동의어 예](assets/synonym-add-two-way-example.png)

1. 완료되면 다음을 클릭하십시오. **저장**.
동의어 집합은 각 용어 사이에 양방향 화살표가 있는 목록에 나타나며, 이 화살표는 각 용어가 상호 교환 가능하다는 것을 의미합니다.

   ![양방향 동의어](assets/synonym-two-way.png)

### 단방향 동의어

1. 다음을 클릭합니다. **단방향** 동의어 유형.

   ![단방향 동의어 추가](assets/synonym-add-one-way.png)

1. 다음을 입력합니다. **키워드** 및 **확장** 용어. 쉼표로 여러 용어를 구분하십시오.

   ![단방향 동의어 예](assets/synonym-add-one-way-example.png)

   이 예에서 키워드는 &quot;pants&quot;이고 단방향 확장 용어 &quot;capris, 종아리 길이 바지, 페달 퍼셔&quot;는 각각 &quot;pants&quot;의 하위 집합이지만 특정 의미를 갖습니다.

1. 완료되면 다음을 클릭하십시오. **저장**.
동의어 집합은 확장 용어에서 키워드로 가리키는 단방향 화살표와 함께 목록에 표시되어 용어가 키워드의 하위 집합임을 나타냅니다. 더하기 기호는 각 확장 항을 구분합니다.

   ![단방향 동의어](assets/synonym-one-way.png)

## 3단계: 변경 사항 게시

1. 동의어가 완료되면 다음을 클릭합니다. **변경 사항 게시**.
1. 스토어에서 업데이트를 사용할 수 있을 때까지 최대 2시간을 기다립니다.

## 필드 설명

| 필드 | 설명 |
|--- |--- |
| [유형](synonyms.md) | 동의어가 키워드와 동일한 의미를 갖는지 또는 키워드의 하위 집합인지 여부를 결정합니다. 옵션:<br />양방향(기본값) - 키워드와 동일한 의미를 가지고 동일한 검색 결과를 반환하는 용어<br />단방향 - 키워드의 하위 집합인 용어입니다. 단방향 동의어는 특정 제품의 더 좁은 목록을 반환합니다. |
| 키워드 | 카탈로그의 제품 선택과 일반적으로 관련된 단어입니다. |
| 확장 | 키워드와 동일하거나 유사한 의미를 갖는 추가 용어입니다. |
