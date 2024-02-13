---
title: "스타일링 [!DNL Popover] 요소"
description: "사용자 정의에 대한 기술 참고 사항 [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 67da9016d4bca9750fa9e440cce08ad1ae7100e2
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# 스타일링 [!DNL Popover] 요소

다음 [[!DNL storefront popover]](storefront-popover.md) 항상 제품 표시 `name` 및 `price`및 필드 선택은 구성할 수 없습니다. 그러나 [!DNL popover] 요소는 CSS 클래스를 사용하여 스타일을 지정할 수 있습니다. 예를들어, 다음 선언은 [!DNL popover] 컨테이너 및 바닥글.

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## 컨테이너 가시성

의 상위 구성 요소 `.livesearch.popover-container` 은(는) `.search-autocomplete`.  다음 `.active` 클래스는 컨테이너의 가시성을 나타냅니다. 다음 `.active` 클래스는 [!DNL popover] 열려 있습니다.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

storefront 요소 스타일링에 대한 자세한 내용은 다음을 참조하십시오. [CSS(계단식 스타일 시트)](https://developer.adobe.com/commerce/frontend-core/guide/css/) 다음에서 [프론트엔드 개발자 안내서](https://developer.adobe.com/commerce/frontend-core/guide/).

## 클래스 선택기

다음 클래스 선택기를 사용하여 의 컨테이너 및 제품 요소를 스타일링할 수 있습니다. [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### 컨테이너 클래스 선택기

#### .livesearch.popover-container

![[!DNL Popover] 컨테이너](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![모든 바닥글 보기](assets/livesearch-view-all-footer.png)

### 제품 클래스 선택기

#### .livesearch.products-container

![제품 컨테이너](assets/livesearch-product-container.png)

#### .livesearch.product-result

![제품 결과](assets/livesearch-product-result.png)

#### .livesearch.product-name

![제품 이름](assets/livesearch-product-name.png)

#### .livesearch.product-price

![제품 가격](assets/livesearch-product-price.png)

#### .livesearch product-link

![제품 결과](assets/livesearch-product-link.png)

## 수정된 테마로 작업 {#working-with-modified-theme}

다음 [!DNL storefront popover] 맞춤화된 와 함께 사용할 수 있습니다. [테마](https://developer.adobe.com/commerce/frontend-core/guide/themes/) 에서 필요한 파일을 상속합니다. *Luma*. 다음 `top.search` 의 블록 `header-wrapper` / `Magento_Search` 모듈을 수정해서는 안 됩니다.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## 비활성화 [!DNL popover]

을(를) 비활성화하려면 [!DNL popover] 및 표준 복원 [빠른 검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 기능을 사용하려면 다음 명령을 입력합니다.

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
