---
title: 사용자 지정
description: 제품 권장 사항을 사용자 지정하는 방법을 알아봅니다.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: a34c3c8a5caca1bbf611b2df650c562aeeab297b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 사용자 지정

제품 Recommendations 모듈을 설치하면 Adobe Commerce이 `ProductRecommendationsLayout` 디렉토리. 이 디렉토리에는 스토어에 권장 사항이 표시되는 방식을 변경하기 위해 사용자 정의할 수 있는 템플릿 파일이 있습니다. 특히 다음 템플릿을 수정하거나 재정의할 수 있습니다.

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

템플릿 파일 수정에 대한 자세한 내용은 [템플릿 사용자 지정](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) 를 참조하십시오.

를 수정하는 경우 `recommendations.html` 파일의 경우, Adobe Commerce이 저장소에서 권장 사항 지표를 수집할 수 있도록 파일에 다음 태그를 보존해야 합니다.

| 태그 | 사용 |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | 보기 이벤트를 수집합니다. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | 클릭 이벤트를 수집합니다. <br/>**참고:** 앵커 태그를 추가하는 경우 이러한 속성을 포함해야 합니다. |

추가 `recommendations.html` 파일, `ProductRecommendationsLayout` 디렉토리에는 다음 하위 디렉토리가 있습니다.

| 디렉토리 | 목적 |
|---|---|
| `layout` | 다음 포함 `*.xml` 각 페이지 유형에 대한 파일 |
| `templates` | 가져오기 및 렌더링 스크립트를 호출하는 파일을 포함합니다 |
| `web/js` | 저장소에 대한 권장 사항을 가져오고 렌더링하는 JavaScript 파일을 포함합니다 |
| `web/template` | 에 대한 템플릿을 포함합니다. `magento/product-recommendations` 모듈 |

## 추천 단위 포지셔닝

다음 경우에 [만들기](create.md) 권장 사항을 지정하고 [위치](placement.md) 이 페이지에서 나타납니다. 추천 단위는 메인 컨텐츠 컨테이너의 상단 또는 하단에 배치할 수 있다. 그러나 이 배치를 사용자 지정할 수 있습니다. Page Builder 권장 사항 컨텐츠 유형을 만드는 경우, Page Builder 도구를 사용하여 페이지에 권장 사항 단위를 배치합니다. 다른 모든 페이지 유형에 대해 `*.xml` 권장 사항을 만들 때 생성되는 파일입니다.

1. 로 변경 `layout` 디렉토리:

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   다음 표에는 이 디렉토리에 있는 XML 파일이 나와 있습니다.

   | 파일 이름 | 페이지 |
   |---|---|
   | `catalog_category_view.xml` | 카테고리 |
   | `catalog_product_view.xml` | 제품 세부 사항 |
   | `checkout_cart_index.xml` | 장바구니 |
   | `checkout_onepage_success.xml` | 체크아웃 |
   | `cms_index_index.xml` | 홈 |

   >[!NOTE]
   >
   >파일 이름 `layout` 저장소가 타사 확장을 사용하는 경우 디렉터리가 다를 수 있습니다.

1. 수정 `catalog_product_view.xml` 제품 세부 사항 페이지의 제품 이미지 뒤에 권장 사항 단위가 표시되도록 파일을 지정합니다. 이 XML 파일을 사용자 지정하기 전에 파일을 살펴보고 수정해야 하는 섹션을 이해하겠습니다.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   위의 코드 조각에서 `main.content` 참조 블록은 권장 사항 단위가 해당 요소를 기준으로 어딘가에 배치됨을 나타냅니다. It `block` 요소에 포함되는 항목 `after="-"` 속성. 기본 컨텐츠 블록 뒤에 권장 사항 단위가 페이지에 표시되도록 지정합니다.

1. 다른 콘텐츠 블록을 지정하여 이 파일을 수정하겠습니다.

   참조 블록을 변경합니다 `name` 변환 전: `main.content` to `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   이 변경 사항은 제품 세부 사항 페이지의 제품 이미지 뒤에 권장 사항 단위가 표시됩니다. 권장 사항 단위를 `product.info.media`, 변경 `after="-"` 속성 `before="-"`. 다음 `pagePlacement` 인수는 수정할 수 없는 내부 인수입니다.

을(를) 참조하십시오. [레이아웃 개요](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) 를 참조하십시오.

## 사용자 지정 제품 속성

개발자는 이러한 속성을 기반으로 제품에 시각적 처리를 추가할 수 있도록 상점 전선의 권장 사항 단위에 있는 사용자 지정 제품 속성 값에 액세스해야 하는 경우가 많습니다.

예를 들어 스토어에 일부 유기 제품이 판매되면 해당 제품에 대해 사용자 지정 속성이 있을 수 있습니다 `Organic = Yes`. 이러한 제품이 Recommendations에 표시될 때 특별한 시각적 처리를 제공할 수 있도록 상점 전면에서 이 속성 값에 액세스해야 할 수 있습니다. 마찬가지로, 이러한 사용자 지정 제품 속성 값에 액세스하면 제품의 배지를 지정하거나 사이트의 프레젠테이션 레이어에서 사용자 지정 로직을 수행할 수 있습니다.

![배지 추가](assets/unit-custom.png)

페이지에서 권장 사항 단위를 렌더링할 때 사용자 지정 제품 속성을 사용할 수 있도록 하려면 `Used in Product Listing` 속성 대상 `Yes` 에서 [제품 속성](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) 페이지에 있을 수도 있습니다.

이 속성이 설정되면 JSON 페이로드에는 다음이 포함됩니다 `attributes` 속성 코드 및 값의 배열을 포함하는 객체입니다. 그런 다음 이전에 언급한 대로 특별 시각적 처리나 배지 추가와 같은 이러한 속성 값을 기반으로 사용자 지정 상점 프론트 스타일링을 적용할 수 있습니다.

>[!NOTE]
>
>제품 속성 변경 사항은 JSON 페이로드에 표시되는 데 최대 1시간이 걸릴 수 있습니다.
