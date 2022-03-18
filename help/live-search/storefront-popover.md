---
title: 스토어프런트포버
description: Live Search storefront 팝오버는 제안된 제품 및 축소판을 동적으로 반환합니다.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 스토어프런트포버

When [!DNL Live Search] is [설치](install.md)고객이 상점 안에 [검색](https://docs.magento.com/user-guide/catalog/search-quick.html) 상자. 각 문자를 입력하면 상위 검색 결과의 추천 제품 및 축소판 이미지로 팝오버가 업데이트됩니다.

[!DNL Live Search] 두 문자 이상의 쿼리에 대한 결과를 반환합니다. 부분 일치의 경우 단어당 최대 문자 수는 20자입니다. &quot;입력한 대로 검색&quot; 쿼리의 문자 수를 구성할 수 없습니다.

>[!NOTE]
>
>다음 [!DNL Live Search] storefront poover는 *루마* 테마 또는 사용자 정의된 테마 *루마*. 다음 *루마* 테마는 [!DNL Commerce] 샘플 데이터. 팝오버는 *비어 있음* 테마. 자세한 내용은 [수정된 테마 작업](#working-with-modified-theme) 추가 정보.

## 검색 가능한 속성

고도로 타겟팅된 결과를 얻으려면 [검색 가능](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) 제품 속성을 사용합니다. 관련성을 보장하기 위해 분명하고 간결한 의미가 있는 컨텐츠가 들어 있는 경우에만 속성을 검색할 수 있도록 하십시오. 처럼 정확하고 긴 텍스트가 들어 있는 속성을 사용하지 마십시오 `description`- 기본적으로 검색 활성화되지만 검색 결과의 정밀도를 줄일 수 있습니다. 예를 들어, 한 사람이 &quot;반바지&quot;를 검색하고 &quot;짧은 소매&quot;라는 용어를 포함하는 셔츠가 있는 경우, 셔츠는 검색 결과에 포함됩니다.

다음 속성은 항상 검색할 수 있습니다.

* `sku`
* `name`
* `categories`

![라이브 검색 팝업](assets/storefront-search-as-you-type.png)
