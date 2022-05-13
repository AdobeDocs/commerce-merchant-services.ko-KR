---
title: 스토어프런트포버
description: Live Search storefront 팝오버는 제안된 제품 및 축소판을 동적으로 반환합니다.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 65126f10574801f7ea8d0a863e9bb512dca13f39
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# [!DNL Storefront Popover]

When [!DNL Live Search] is [설치](install.md), [!DNL popover] 고객이 [검색](https://docs.magento.com/user-guide/catalog/search-quick.html) 상자. 각 문자를 입력하면 [!DNL popover] 상위 검색 결과의 추천 제품 및 축소판 이미지로 업데이트됩니다.

[!DNL Live Search] 두 문자 이상의 쿼리에 대한 결과를 반환합니다. 부분 일치의 경우 단어당 최대 문자 수는 20자입니다. &quot;입력한 대로 검색&quot; 쿼리의 문자 수를 구성할 수 없습니다.

>[!NOTE]
>
>다음 [!DNL Live Search] [!DNL storefront popover] 는 *루마* 테마 또는 사용자 정의된 테마 *루마*. 다음 *루마* 테마는 [!DNL Commerce] 샘플 데이터. 다음 [!DNL popover] 은 을 지원하지 않습니다 *비어 있음* 테마. 자세한 내용은 [스타일링 [!DNL Popover] 요소](storefront-popover-styling.md) 추가 정보

## 검색 가능한 속성

고도로 타겟팅된 결과를 얻으려면 [검색 가능](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) 제품 속성을 사용합니다. 관련성을 보장하기 위해 분명하고 간결한 의미가 있는 컨텐츠가 들어 있는 경우에만 속성을 검색할 수 있도록 하십시오. 처럼 정확하고 긴 텍스트가 들어 있는 속성을 사용하지 마십시오 `description`- 기본적으로 검색 활성화되지만 검색 결과의 정밀도를 줄일 수 있습니다. 예를 들어, 한 사람이 &quot;반바지&quot;를 검색하고 &quot;짧은 소매&quot;라는 용어를 포함하는 셔츠가 있는 경우, 셔츠는 검색 결과에 포함됩니다.

다음 속성은 항상 검색할 수 있습니다.

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] 페이지 크기

페이지의 크기 [!DNL popover] 자동 완성된 제품 라인을 반환할 수 있는지 여부를 결정합니다. 이전에는 페이지 크기를 6줄로 하드코딩했습니다. 하지만, `page_size` 값은 이제 *관리*. 라이브 검색 설치 중에 `page_size` 값이 [카탈로그 검색](https://docs.magento.com/user-guide/configuration/catalog/catalog.html#catalog-search) - `Autocomplete Limit` 설정

기본적으로 카탈로그 검색 - 자동 완료 제한 값은 8행(또는 행)으로 설정됩니다. 페이지의 크기를 변경하려면 [!DNL popover]를 채울 때 다음을 수행합니다.

1. 설정 *관리* 사이드바, 다음 위치로 이동 **스토어** > 설정 > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **카탈로그** 및 **카탈로그** 설정 목록에서 을 선택합니다.
1. 를 확장합니다. *카탈로그 검색* 섹션을 참조하십시오.
1. 설정 **자동 완료 제한** 에서 허용할 라인 수로 [!DNL popover].
1. 완료되면 를 클릭합니다. **구성 저장**.
