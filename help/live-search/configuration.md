---
title: '상거래 구성 설정 및 [!DNL Live Search] '
description: 다음과 같은 Adobe Commerce 구성 설정에 대해 설명합니다. [!DNL Live Search] 읽을 수 있습니다.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: 888b81683a4e139a35b771d9c573f1f5f0c3b902
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# [!DNL Live Search] 및 Adobe Commerce 구성 설정

다음과 같은 상거래 구성 설정이 있습니다. [!DNL Live Search] 를 지원합니다. 이 항목에서는 이러한 구성 값을 나열합니다.

## 지원되는 구성 값

| 상거래 구성 설정 | 팝오버에서 지원됨 | 어댑터에서 지원 |
|---|---|---|
| 스토어 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 페이지 길이당 모든 제품 허용 | 예. 최대 500개 제품 | 예. 최대 500개 제품 |
| 저장소 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 최소 쿼리 길이 | 예 | 예 |
| 스토어 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 그리드 허용 값의 페이지당 제품 | 예 | 예 |
| 스토어 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 그리드의 페이지당 제품 기본값 | 예. 최대 500개 제품 | 예. 최대 500개 제품 |
| 스토어 > 구성 > 카탈로그 > 재고 > 재고 부족 제품 표시 | 예, v2.0.4+ | 예, v2.0.4+ |
| Stores > Configuration > Currency > Default Display Currency | 예, 3.1.0+ | 예, 3.1.0+ |
| 스토어 > 구성 > 일반 > 통화 설정 > 통화 옵션 > 기본 통화 | 예 | 예 |

이제 위젯 제품 목록 페이지 및 팝오버의 가격이 구성된 환율을 사용하여 기본 표시 통화로 전환됩니다.

## 검색어

[!DNL Live Search] 지원 [검색어 리디렉션](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) Adobe Commerce이 라우팅을 처리하는 구현: Luma 및 기타 php 기반 테마.

## 지원되지 않는 구성 값

[!DNL Live Search] 모든 구성 값을 읽을 수 없습니다. 이 표에는 개발자가 더 관심을 가질 수 있는 값이 나열되어 있습니다.

| 상거래 구성 설정 | 메모 |
|---|---|
| 스토어 > 구성 > 카탈로그 > 상점 > 목록 모드 | 올바르게 렌더링되지만 일부 페이지 상호 작용에 대해 이벤트가 전송되지 않음 |
| 저장소 > 구성 > 카탈로그 > 카탈로그 > 카탈로그 검색 > 최대 쿼리 길이 | 구현되지 않음. 검색 서비스는 최대 255자를 허용합니다. |
| 구성 > 판매 > 세금 > 가격 표시 설정 > 카탈로그에 제품 가격 표시 |  |
