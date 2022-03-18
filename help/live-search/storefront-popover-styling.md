---
title: 스타일링 팝오버 요소
description: Live Search Storefront poover 사용자 지정에 대한 기술 참고 사항.
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 팝오버 요소 스타일링

다음 [상점 앞에 있는 팝오버](storefront-popover.md) 항상 제품 표시 `name` 및 `price`, 그리고 필드 선택을 구성할 수 없습니다. 그러나 팝오버 요소는 CSS 클래스를 사용하여 스타일을 지정할 수 있습니다. 예를 들어, 다음 선언에서는 팝업 컨테이너 및 바닥글의 배경색을 변경합니다.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## 컨테이너 가시성

의 상위 구성 요소입니다 `.livesearch.popover-container` is `.search-autocomplete`.  다음 `.active` 클래스는 컨테이너의 가시성을 나타냅니다. 다음 `.active` popoover가 열려 있으면 클래스가 조건부로 추가됩니다.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

storefront 요소 스타일링에 대한 자세한 내용은 [CSS(계단식 스타일 시트)](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/css-topics/css-overview.html) 에서 [Frontend Developers 안내서](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/bk-frontend-dev-guide.html).

## 클래스 선택기

다음 클래스 선택기를 사용하여 팝오버에서 컨테이너, 제안 및 제품 요소의 스타일을 지정할 수 있습니다.

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.suggestions-container`
* `.livesearch.suggestions-header`
* `.livesearch.suggestion`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### 컨테이너 클래스 선택기

`.livesearch.popover-container`

![팝오버 컨테이너](assets/livesearch-popover-container.png)

`.livesearch.view-all-footer`

![모든 바닥글 보기](assets/livesearch-view-all-footer.png)

### 제안 클래스 선택기

`.livesearch.suggestions-container`
![제안 컨테이너](assets/livesearch-suggestions-container.png)

`.livesearch.suggestions-header`
![추천 헤더](assets/livesearch-suggestions-header.png)

`.livesearch.suggestion`
![제안](assets/livesearch-suggestion.png)

### 제품 클래스 선택기

`.livesearch.products-container`
![제품 컨테이너](assets/livesearch-product-container.png)

`.livesearch.product-result`
![제품 결과](assets/livesearch-product-result.png)

`.livesearch.product-name`
![제품 이름](assets/livesearch-product-name.png)

`.livesearch.product-price`
![제품 가격](assets/livesearch-product-price.png)

## 수정된 테마 작업 {#working-with-modified-theme}

상기 상점 전면 팝오버는 사용자 정의 제품에 사용할 수 있다 [테마](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/themes/theme-overview.html) 에서 필요한 파일을 상속함 *루마*. 다음 `top.search` 블록 `header-wrapper` 의 `Magento_Search` 모듈을 수정할 수 없습니다.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## 팝오버 비활성화

팝오버를 비활성화하고 표준을 복원하려면 [빠른 검색](https://docs.magento.com/user-guide/catalog/search-quick.html) 기능을 사용하려면 다음 명령을 입력합니다.

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
