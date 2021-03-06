---
title: 제품 필터링
description: 제품을 권장 사항으로 사용하거나 제외하는 조건을 정의합니다.
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# 제품 필터링

Adobe Commerce은 구성 가능한 기본 필터를 권장 사항 단위에 자동으로 적용합니다. 페이지에 여러 권장 사항 단위가 배포되어 있는 경우, Adobe Commerce은 장치에서 반복되는 모든 제품을 필터링합니다. 반복된 제품에 대한 첫 번째 참조만 사용하여 다른 제품을 추천할 공간을 만듭니다. 또한 Adobe Commerce은 이전에 구입한 제품과 장바구니에 들어 있는 제품을 필터링합니다.

다음 경우에 [만들기](create.md) 권장 사항 단위에서는 권장 사항에 표시할 제품을 제어하는 필터를 정의할 수 있습니다. 이러한 필터는 정의한 포함 또는 제외 조건 세트를 기반으로 합니다. 모든 포함 조건과 일치하는 제품만 권장 사항에 표시됩니다. 제외 조건 중 하나와 일치하는 제품은 권장되지 않습니다.

각 필터 페이지에서 전환을 선택하여 여러 필터를 구성하고 원하는 필터만 활성화할 수 있습니다. 나중에 사용할 수 있도록 필터 초안을 만들 수 있습니다. 각 탭에 활성화된 필터 수가 표시됩니다.

## 조건

조건은 정적 또는 동적일 수 있습니다.

- 정적 조건은 기존 제품 속성을 사용하여 단위에 표시할 수 있는 제품을 결정합니다. 예를 들어 $25보다 큰 가격이 있는 재고 내 제품만 단위에 표시되도록 지정할 수 있습니다. 정적 조건은 모든 페이지 유형에서 사용할 수 있습니다.

- 동적 조건은 현재 본 카테고리 또는 제품과 같이 구매자의 현재 컨텍스트에 대한 키입니다. 예를 들어 제품 세부 사항 페이지에 배포할 제품 권장 사항을 만들 때 현재 표시된 제품의 상대적 가격 범위 내에 있는 제품만 추천하는 조건을 만들 수 있습니다. 동적 조건은 홈 페이지를 제외하고 모든 페이지 유형에서 사용할 수 있으며, 페이지 빌더와 함께 배치된 권장 사항이 있는 페이지에서 사용할 수 있습니다.

### 논리 연산자

논리 연산자 `AND` 및 `OR` 여러 조건을 연결하는 데 사용됩니다. 포함 필터와 제외 필터를 모두 사용하는 경우, 포함을 먼저 평가하여 추천할 수 있는 모든 제품을 결정하면 제외 필터와 일치하는 제품이 목록에서 제거됩니다.

- `AND` - 두 가지 포함 필터링 조건을 결합합니다.
- `OR` - 두 개의 제외 필터링 조건을 조인합니다.

>[!NOTE]
>
> 포함 및 제외 필터는 버전 3.2.2 이상의 기존 카테고리 제외를 대체합니다 `magento/product-recommendations` 모듈. 자세한 내용은 [릴리스 노트](release-notes.md) Adobe Commerce 릴리스에 대해 자세히 알아보십시오 .

## 필터 유형 {#filtertypes}

![필터](assets/rec-conditions.png)

### 카테고리

제품 카테고리를 기반으로 하는 필터는 직접 카테고리 지정 및 해당 하위 카테고리를 사용합니다. 예를 들어 카테고리에 대한 제외 조건 활성화 `Gear` 에 지정된 제품 제외 `Gear` 및 `Gear/Bags` 또는 `Gear/Fitness Equipment`. B2B 판매자의 경우 카테고리 필터는 모든 항목을 준수합니다 [고객별 제품 카테고리](https://docs.magento.com/user-guide/catalog/category-permissions.html) 구성했습니다.

Adobe Commerce에서는 페이지 유형에 권장 사항을 배포할 때 다음 카테고리 필터 구성을 사용하는 것이 좋습니다.

| 페이지 | 필터 기준 |
|---|---|
| 홈 | 제품을 필터링하지 마십시오. |
| 카테고리 | 특정 카테고리의 제품을 필터링합니다. |
| 제품 세부 사항 | 동일한 카테고리의 제품을 필터링합니다. |
| 장바구니 | 장바구니에서 제품의 카테고리를 필터링합니다. |
| 주문 확인 | 구매한 제품의 카테고리를 필터링합니다. |

### 제품

제품 필터는 권장 사항에 표시할 수 있거나 사용할 수 없는 특정 제품을 지정합니다. 비활성화되거나 개별적으로 표시되지 않는 제품은 추천에 표시되지 않으므로 선택할 수 없습니다.

### 유형

제품 유형을 기반으로 하는 필터는 특정 유형의 모든 제품을 포함하거나 제외합니다. 지원되는 유형은 다음과 같습니다 _단순_, _구성 가능_, _가상_, _다운로드 가능_, 또는 _기프트 카드_. _번들_ 및 _그룹화됨_ 제품이 아직 지원되지 않습니다.

### 가시성

다음과 같이 가시성을 기반으로 제품을 필터링합니다. _카탈로그_, _검색_&#x200B;또는 둘 다 사용할 수 있습니다.

### 가격

제품 가격을 기반으로 하는 필터는 최종 가격을 사용하여 비교를 수행합니다. 최종 가격에는 익명의 쇼핑객들에게 이용 가능한 모든 할인 또는 특별 가격이 포함되어 있습니다. B2B 가맹점을 위해 표시되는 가격은 [고객별 그룹 가격 책정](https://docs.magento.com/user-guide/catalog/pricing-advanced.html#customer-group-price) 구성했습니다.

### 재고 상태

다음 제외 필터를 사용하여 재고 상태에 따라 제품을 필터링할 수 있습니다.

- 재고 부족 - (제외 전용) 재고가 없는 제품을 제외합니다.
- 재고 부족 - (제외 전용) 재고가 낮은 제품을 제외합니다. 낮은 재고 상태는 _왼쪽 X 임계값만_ 값 [인벤토리 구성](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).
