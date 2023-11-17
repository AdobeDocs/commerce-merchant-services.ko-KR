---
title: 제품 목록 페이지 위젯
description: 활성화 및 스타일링 [!DNL Live Search Product Listing Page Widget]
exl-id: f7346a06-a8c7-4a33-8437-ea4f61d9281f
source-git-commit: c77b2f9cb55d3eb339dcc900ce606b94c592f559
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# 제품 목록 페이지 위젯

다음 [!DNL Live Search Product Listing Page Widget] PLP(Commerce Services)는 Commerce Services 플랫폼을 사용하여 성능, 검색 및 패싯 가능한 제품 목록 페이지를 제공합니다. 이 항목에서는 PLP 위젯을 활성화하고 스타일링하는 방법을 설명합니다.

## PLP 위젯 활성화

다음의 경우 [!DNL Live Search] 서비스가 설치되면 기본 검색 기능이 [!DNL Live Search] 자동으로 표시됩니다.

다음 [!DNL Live Search] PLP 위젯은 새 설치에 대해 기본적으로 활성화되어 있습니다. 업그레이드 중인 경우 [!DNL Live Search] 그리고 PLP 위젯은 이미 꺼져 있으므로 그대로 유지됩니다.

PLP 위젯을 비활성화하려면 다음과 같이 하십시오.

1. 다음으로 이동 **스토어** > 설정 > **구성** > **[!DNL Live Search]** > **Storefront 기능** 및 설정 **제품 목록 위젯 활성화** &quot;아니요&quot;로 변경되었습니다.
1. 선택 **구성 저장** 설정을 저장합니다.

## 스타일 예

를 사용하여 사이트에 맞게 PLP 위젯의 모양과 느낌을 사용자 정의할 수 있습니다. [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Adobe Commerce 테마 내에 사용자 지정 클래스가 있는 요소는 상속되지 않습니다. 사용자 정의 클래스와 일치하도록 이러한 요소를 특정 클래스에서 타깃팅해야 합니다. 기본 작업 클래스는 위젯 단추에서 작동하지 않습니다.
>CSS 내의 제네릭 타깃팅된 요소는 상속됩니다. `button` 위젯 단추에 적용됩니다.

강조 표시된 div에는 타겟 클래스가 포함되어 있습니다 `ds-sdk-product-item__product-name`.

![쪽 매기기](assets/plp-css-example.png)

제품 이름을 대문자로 만드는 규칙을 추가하여 사용자 지정합니다.

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![쪽 매기기](assets/plp-css-example-after.png)

## CSS 클래스

### 제품 목록

* `.ds-sdk-product-list`: 외부 div
* `.ds-sdk-product-list__grid`: 내부 div

![쪽 매기기](assets/plp-css-product-list.png)

#### 제품 목록 페이지 매김

* `.ds-plp-pagination`

![쪽 매기기](assets/plp-css-pagination.png)

* `.ds-plp-pagination_item`

![페이지 매김 항목](assets/plp-css-pagination-item.png)

* `.ds-plp-pagination_item--current`

![페이지 매김 현재 항목](assets/plp-css-pagination-item-current.png)

### 위젯

* `.ds-widgets`: 외부 div
* `.ds-widgets__actions`: 왼쪽 내부 div
* `.ds-widgets__results`: 오른쪽 내부 div

![위젯 결과](assets/plp-css-widgets.png)

### 정렬 드롭다운

* `.ds-sdk-sort-dropdown`

![정렬 드롭다운](assets/plp-css-dropdown.png)

* `.ds-sdk-sort-dropdown__button`

![드롭다운 단추](assets/plp-css-dropdown-button.png)

* `.ds-sdk-sort-dropdown__items`

![드롭다운 항목](assets/plp-css-dropdown-items.png)

* `.ds-sdk-sort-dropdown__items--item`

![드롭다운 항목](assets/plp-css-dropdown-item.png)

* `.ds-sdk-sort-dropdown__items--item-selected`

![선택한 항목 드롭다운](assets/plp-css-dropdown-selected.png)

* `.ds-sdk-sort-dropdown__items--item-active`

![드롭다운 활성 선택](assets/plp-css-dropdown-active.png)

### 패싯

* `.ds-plp-facets`
* `.ds-plp-facets__header`
* `.ds-plp-facets__header_title`
* `.ds-plp-facets__header__clear-all`

![패싯 헤더 제목](assets/plp-css-facets-title-clear.png){width="350"}

* `.ds-plp-facets__pills`
* `.ds-sdk-pill`

![패싯 알약](assets/plp-css-facets-pill.png){width="350"}

* `.ds-sdk-pill__label`
* `.ds-sdk-pill__cta`

![패싯 레이블](assets/plp-css-pill-label-cta.png){width="350"}

* `.ds-plp-facets__list`

![패싯 목록](assets/plp-css-facets-list.png){width="350"}

* `.ds-sdk-input`
* `.ds-sdk-input__label`
* `.ds-sdk-product-item__product-swatch-group`
* `ds-sdk-product-item__product-swatch-item`
* `.ds-sdk-input_fieldset_show-more`

![입력](assets/plp-css-sdk-input.png)

* `.ds-sdk-labelled-input`

![레이블이 지정된 입력](assets/plp-css-labelled-input.png)

* `.ds-sdk-labelled-input__input`
* `.ds-sdk-labelled-input__label`

![입력 레이블](assets/plp-css-labelled-input-label.png)

### 제품 항목

* `.ds-sdk-product-item`
* `.ds-sdk-product-item__image`
* `.ds-sdk-product-item__product-name`
* `.ds-sdk-product-item__product-options`
* `.ds-sdk-product-price`
   * `.ds-sdk-product-price--no-discount`
   * `.ds-sdk-product-price--grouped`
   * `.ds-sdk-product-price--bundle`
   * `.ds-sdk-product-price--discount`

![제품](assets/plp-css-product.png)

### 로드 중

* `.ds-sdk-loading`
* `.ds-sdk-loading__spinner`
* `.ds-sdk-loading__spinner-label`

![표시기 로드 중](assets/plp-css-loading.png)
