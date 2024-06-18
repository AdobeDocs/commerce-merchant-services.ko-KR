---
title: "[!DNL Storefront Popover]"
description: "다음 [!DNL Live Search storefront popover] 제안 제품 및 썸네일을 동적으로 반환합니다."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

날짜 [!DNL Live Search] 은(는) [설치됨](install.md), a [!DNL popover] 쇼핑객이 다음을 입력할 때 상점 앞에 표시됨 [검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 상자. 각 문자를 입력한 상태에서 [!DNL popover] 는 추천 제품 및 상위 검색 결과의 썸네일 이미지로 업데이트됩니다.

[!DNL Live Search] 2자 이상의 쿼리에 대한 결과를 반환합니다. 부분 일치의 경우 단어 당 최대 문자 수는 20자입니다. &quot;입력할 때 검색&quot; 쿼리의 문자 수는 구성할 수 없습니다.

기본적으로, [!DNL Live Search] 지원 [검색어 리디렉션](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>제품 속성을 다음에서 검색 가능한 것으로 설정하는 방법 알아보기 [라이브 검색 설정](workspace.md) 기사.

## [!DNL Popover] 페이지 크기

의 페이지 크기 [!DNL popover] 자동 완성된 제품의 몇 줄을 반환할 수 있는지 결정합니다. Live Search를 설치하는 동안 `page_size` 값이 의 현재 값으로 변경됩니다. [카탈로그 검색](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 설정.

기본적으로 카탈로그 검색 - 자동 완성 제한 값은 8행(또는 행)으로 설정됩니다. 의 페이지 크기를 변경하려면 [!DNL popover]를 사용하여 다음을 수행합니다.

1. 다음에서 *관리자* 사이드바, 이동 **스토어** > 설정 > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **카탈로그** 및 선택 **카탈로그** 설정 목록에서 참조할 수 있습니다.
1. 확장 *카탈로그 검색* 섹션.
1. 설정 **자동 완성 제한** 에서 허용할 라인 수로 변환 [!DNL popover].
1. 완료되면 다음을 클릭하십시오. **구성 저장**.

## 스타일링 [!DNL Popover] 예

의 모양과 느낌을 사용자 지정할 수 있습니다. [!DNL Popover] 회사의 스타일 및 브랜딩 지침에 맞는 위젯.

다음 [!DNL storefront popover] 항상 제품 표시 `name` 및 `price`및 필드 선택은 구성할 수 없습니다. 그러나 [!DNL popover] 요소를 다음과 같이 스타일을 지정할 수 있습니다. [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) 클래스입니다. 예를들어, 다음 선언은 [!DNL popover] 컨테이너 및 바닥글.

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

다음 클래스 선택기를 사용하여 의 컨테이너 및 제품 요소의 스타일을 지정할 수 있습니다 [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

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

다음을 사용할 수 있습니다. [!DNL storefront popover] 맞춤화된 [테마](https://developer.adobe.com/commerce/frontend-core/guide/themes/) 에서 필요한 파일을 상속합니다. *Luma*. 다음 `top.search` 의 블록 `header-wrapper` / `Magento_Search` 모듈을 수정해서는 안 됩니다.

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

## Headless 구현

Headless 구현을 사용하는 사용자의 경우 [!DNL Live Search popover] 사용 [npm 패키지](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
