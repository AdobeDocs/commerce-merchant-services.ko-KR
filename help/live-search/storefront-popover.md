---
title: "[!DNL Storefront Popover]"
description: "다음 [!DNL Live Search storefront popover] 제안 제품 및 썸네일을 동적으로 반환합니다."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 099a4b9ce3ab71bc3c7ae181be242863a55d0ca9
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# [!DNL Storefront Popover]

날짜 [!DNL Live Search] 은(는) [설치됨](install.md), a [!DNL popover] 쇼핑객이 다음을 입력할 때 상점 앞에 표시됨 [검색](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) 상자. 각 문자를 입력한 상태에서 [!DNL popover] 는 추천 제품 및 상위 검색 결과의 썸네일 이미지로 업데이트됩니다.

[!DNL Live Search] 2자 이상의 쿼리에 대한 결과를 반환합니다. 부분 일치의 경우 단어 당 최대 문자 수는 20자입니다. &quot;입력할 때 검색&quot; 쿼리의 문자 수는 구성할 수 없습니다.

기본적으로, [!DNL Live Search] 지원 [검색어 리디렉션](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] 페이지 크기

의 페이지 크기 [!DNL popover] 자동 완성된 제품의 몇 줄을 반환할 수 있는지 결정합니다. 이전에는 페이지 크기가 6줄로 하드코딩되었습니다. 그러나 `page_size` 값은 이제 다음에서 구성할 수 있는 설정입니다 *관리자*. Live Search를 설치하는 동안 `page_size` 값이 의 현재 값으로 변경됩니다. [카탈로그 검색](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` 설정.

기본적으로 카탈로그 검색 - 자동 완성 제한 값은 8행(또는 행)으로 설정됩니다. 의 페이지 크기를 변경하려면 [!DNL popover]를 사용하여 다음을 수행합니다.

1. 다음에서 *관리자* 사이드바, 이동 **스토어** > 설정 > **구성**.
1. 왼쪽 패널에서 를 확장합니다. **카탈로그** 및 선택 **카탈로그** 설정 목록에서 참조할 수 있습니다.
1. 확장 *카탈로그 검색* 섹션.
1. 설정 **자동 완성 제한** 에서 허용할 라인 수로 변환 [!DNL popover].
1. 완료되면 다음을 클릭하십시오. **구성 저장**.

## 카탈로그 서비스

다음 [Adobe Commerce용 카탈로그 서비스](../catalog-service/overview.md) 확장은 제품 관련 상점 경험을 빠르고 완벽하게 렌더링할 수 있는 풍부한 보기 모델 카탈로그 데이터를 제공합니다. 카탈로그 서비스를 라이브 검색과 함께 사용하여 현재 기본 확장에서 지원하지 않는 기능을 제공할 수 있습니다.

* 확장된 속성
* 다른 제품 정보를 가져올 수 있습니다.

판매자는 카탈로그 서비스를 사용하여 위젯 또는 상점 요소를 사용자 정의하고 확장할 수 있지만 이는 Adobe 지원 팀의 범위를 벗어납니다.

## Headless 구현

Headless 구현이 있는 사용자의 경우 [npm 패키지](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## 제한 사항

* 다음 [!DNL Live Search] [!DNL storefront popover] 는 를 사용하는 스토어에 대해서만 사용할 수 있습니다. *Luma* 테마 또는 를 기반으로 하는 맞춤화된 테마 *Luma*. 검색 결과 페이지의 경로에는 이 없습니다. *Luma* 스타일링.
* 다음 [!DNL popover] 은(는) 을 지원하지 않습니다. *비어 있음* 테마. 다음을 참조하십시오 [스타일링 [!DNL Popover] 요소](storefront-popover-styling.md) 자세히 알아보십시오.
* 다음 [!DNL popover] 은(는) 빠른 주문 양식에서 지원되지 않습니다.
* 위시리스트 및 제품 비교는 지원되지 않습니다.
