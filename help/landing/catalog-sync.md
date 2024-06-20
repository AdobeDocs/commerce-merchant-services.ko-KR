---
title: 카탈로그 동기화
description: 에서 제품 데이터를 내보내는 방법 알아보기 [!DNL Commerce] 서버 대상 [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# 카탈로그 동기화

>[!NOTE]
>
> 카탈로그 동기화 대시보드가 이제 데이터 관리 대시보드입니다. 이렇게 개선된 대시보드는 이제 을 지원합니다. [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md), 및 [[!DNL Catalog Service]](../catalog-service/overview.md). 고객은 해당 서비스 중 하나의 최신 버전으로 업데이트하여 데이터 관리 대시보드를 가져올 수 있습니다. 자세한 내용은 [데이터 관리 대시보드](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 설명서를 참조하십시오. 이 현재 항목은 아직 업그레이드하지 않았으며 여전히 카탈로그 동기화 대시보드가 있는 사용자에게 남아 있습니다.

Adobe Commerce은 인덱서를 사용하여 카탈로그 데이터를 표로 컴파일합니다. 프로세스는 다음 사용자에 의해 자동으로 트리거됩니다. [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 제품 가격 또는 재고 수준 변경 등.

Catalog Sync 서비스가 [!DNL Adobe Commerce] 인스턴스를 [!DNL Commerce Services] 데이터를 최신 상태로 유지하기 위한 지속적인 플랫폼. 예를 들어, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 올바른 이름, 가격 및 가용성으로 권장 사항을 정확하게 반환하려면 현재 카탈로그 정보가 필요합니다. 사용 _카탈로그 동기화_ 카탈로그 동기화를 트리거하고 사용할 제품 데이터를 다시 색인화하기 위해 동기화 프로세스 또는 명령줄 인터페이스를 관찰하고 관리하는 대시보드 [!DNL Commerce Services]. 다음을 참조하십시오 [명령줄 인터페이스 참조](../data-export/data-export-cli-commands.md) 다음에서 _SaaS 데이터 내보내기_ 가이드.

## 카탈로그 동기화 대시보드 액세스

카탈로그 동기화 대시보드에 액세스하려면 다음을 선택합니다. **시스템** > _데이터 전송_ > **카탈로그 동기화**.

포함 **카탈로그 동기화** 대시보드 다음과 같은 작업을 수행할 수 있습니다.

- 동기화 상태 보기(**진행 중**, **성공**, **실패**)
- 동기화된 총 제품 수 보기
- 동기화된 제품을 검색하여 현재 상태 보기
- 이름, SKU 등을 기준으로 한 검색 스토어 카탈로그
- 동기화 불일치를 진단하는 데 도움이 되도록 JSON에서 동기화된 제품 세부 정보 보기
- 동기화 프로세스 다시 시작

### 마지막 동기화

다음의 동기화 상태를 보고합니다.

- **성공** - 동기화가 성공한 날짜와 시간, 업데이트한 제품 수를 표시합니다.
- **실패** - 동기화를 시도한 날짜와 시간을 표시합니다.
- **진행 중** - 마지막으로 성공한 동기화 날짜와 시간을 표시합니다.

카탈로그 동기화 프로세스는 매시간 자동으로 실행됩니다. 상점 맨 앞에 예상 제품이 표시되지 않거나 제품이 최근 변경 사항을 반영하지 않는 경우 다음을 해결할 수 있습니다. [카탈로그 동기화 문제](#resolvesync).

### 제품 동기화됨

에서 동기화된 총 제품 수를 표시합니다. [!DNL Commerce] 카탈로그. 초기 동기화 후에는 변경된 제품만 동기화해야 합니다.

## 다시 동기화 {#resync}

시간별 예약된 동기화가 발생하기 전에 카탈로그 재동기화를 시작해야 하는 경우 강제로 재동기화를 수행할 수 있습니다.

>[!NOTE]
>
> 재동기화를 강제로 수행하면 전체 제품 카탈로그가 재동기화되어 하드웨어 리소스에 대한 부하가 증가할 수 있습니다.

1. 다음에서 _카탈로그 동기화_ 대시보드, 선택 **설정**.

   다음 _카탈로그 동기화 설정_ 페이지가 나타납니다.

1. 다음에서 _데이터 재동기화_ 섹션, 클릭 [!UICONTROL Resync].

   [!DNL Commerce] 다음 예약된 동기화 기간 동안 카탈로그를 동기화합니다. 카탈로그 크기에 따라 이 작업은 시간이 오래 걸릴 수 있습니다.

## 동기화된 카탈로그 제품

다음 **동기화된 카탈로그 제품** 테이블에는 다음 정보가 표시됩니다.

| 필드 | 설명 |
|---|---|
| ID | 제품에 대한 고유 식별자 |
| 이름 | 제품의 상점 이름 |
| 유형 | 단순, 구성 가능 또는 다운로드 가능 등 제품 유형 식별 |
| 마지막으로 내보냄 | 제품을 카탈로그에서 마지막으로 성공적으로 내보낸 날짜 |
| 마지막 수정일 | 카탈로그에서 제품이 마지막으로 수정된 날짜 |
| SKU | 제품에 대한 재고 유지 단위를 표시합니다. |
| 가격 | 제품 가격 |
| 가시성 | 에 정의된 제품의 가시성 설정 [!DNL Commerce] 카탈로그 |

## 카탈로그 동기화 문제 해결 {#resolvesync}

다음을 참조하십시오 [로그 및 문제 해결](../data-export/troubleshooting-logging.md#troubleshooting) 다음에서 _SaaS 데이터 내보내기 안내서_.
