---
title: 카탈로그 동기화
description: 에서 제품 데이터를 내보내는 방법 알아보기 [!DNL Commerce] 서버 대상 [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 289ac6ac464955f18f3a2448099ad459e6264941
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# 카탈로그 동기화

>[!NOTE]
>
> 카탈로그 동기화 대시보드가 이제 데이터 관리 대시보드입니다. 이렇게 개선된 대시보드는 이제 을 지원합니다. [!DNL Product Recommendations], [!DNL Live Search], 및 [!DNL Catalog Service]. 고객은 해당 서비스 중 하나의 최신 버전으로 업데이트하여 데이터 관리 대시보드를 가져올 수 있습니다. 자세한 내용은 [데이터 관리 대시보드](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) 설명서를 참조하십시오. 이 현재 항목은 아직 업그레이드하지 않았으며 여전히 카탈로그 동기화 대시보드가 있는 사용자에게 남아 있습니다.

Adobe Commerce은 인덱서를 사용하여 카탈로그 데이터를 표로 컴파일합니다. 프로세스는 다음 사용자에 의해 자동으로 트리거됩니다. [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 제품 가격 또는 재고 수준 변경 등.

Catalog Sync 서비스가 [!DNL Adobe Commerce] 인스턴스를 [!DNL Commerce Services] 데이터를 최신 상태로 유지하기 위한 지속적인 플랫폼. 예를 들어, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 올바른 이름, 가격 및 가용성으로 권장 사항을 정확하게 반환하려면 현재 카탈로그 정보가 필요합니다. 사용 _카탈로그 동기화_ 동기화 프로세스를 관찰하고 관리하는 대시보드 [명령줄 인터페이스](#resynccmdline) 카탈로그 동기화를 트리거하고 다음에 의해 소비될 제품 데이터를 다시 색인화하기 [!DNL Commerce Services].

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

데이터 재동기화를 트리거할 때 데이터를 업데이트하고 추천 단위와 같은 UI 구성 요소에 반영되기까지 최대 1시간이 걸릴 수 있습니다. 여전히 카탈로그와 상점 데이터의 불일치가 표시되거나 카탈로그 동기화가 실패한 경우 다음을 참조하십시오.

### 데이터 불일치

1. 검색 결과에 해당 제품에 대한 세부 보기를 표시합니다.
1. JSON 출력을 복사하고 콘텐츠가 의 내용과 일치하는지 확인합니다. [!DNL Commerce] 카탈로그.
1. 콘텐츠가 일치하지 않으면 공백 또는 마침표 추가와 같이, 카탈로그의 제품에 약간의 변경 작업을 수행합니다.
1. 재동기화 대기 또는 [수동 재동기화 트리거](#resync).

### 동기화가 실행되고 있지 않음

동기화가 일정에 따라 실행되고 있지 않거나 동기화되지 않은 경우 다음을 참조하십시오. [기술 자료](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) 기사.

### 동기화 실패

카탈로그 동기화 상태가 인 경우 **실패**, 제출 [지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 명령줄 인터페이스 {#resynccmdline}

다음 `saas:resync` 명령은 의 일부임 `magento/saas-export` 패키지 및 는 다음 중 하나와 함께 즉시 사용 가능합니다. [!DNL Commerce Services] 다음과 같은 제품 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 또는 [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> 데이터 동기화를 처음 실행할 때 `productattributes` 먼저 피드, 그 다음 `productoverrides`, 를 실행하기 전에 `products` 피드.

명령 옵션:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

다음 표에서는 `saas:resync` 매개 변수 및 설명.

| 매개 변수 | 설명 | 필수? |
|---| ---| ---|
| `feed` | 재동기화할 엔터티(예: ) 지정 `products` | 예 |
| `no-reindex` | 기존 카탈로그 데이터를 (으)로 다시 제출 [!DNL Commerce Services] 색인 재지정 없이 이 매개 변수를 지정하지 않으면 명령은 데이터를 동기화하기 전에 전체 색인 재지정을 실행합니다. | 아니요 |
| `cleanup-feed` | 동기화 전에 피드 인덱서 테이블을 정리합니다. | 아니요 |

피드 이름은 다음 중 하나일 수 있습니다.

- `products`— 카탈로그의 제품
- `productattributes`— 다음과 같은 제품 속성 `activity`, `gender`, `tops`, `bottoms`등
- `variants`— 구성 가능한 제품의 색상 및 크기와 같은 제품 변형
- `prices` — 제품 가격
- `scopesCustomerGroup` — 고객 그룹
- `scopesWebsite` — 스토어 조회수가 있는 웹 사이트
- `categories`— 카탈로그의 범주
- `categoryPermissions` - 각 범주에 대한 권한
- `productoverrides`— 고객별 가격 책정 및 카탈로그 표시 규칙(예: 범주 권한에 따른 규칙)

다음에 따라 [상거래 서비스](../landing/saas.md) 이(가) 설치되면 다른 피드 세트를 사용할 수 있습니다. `saas:resync` 명령입니다.

를 실행하지 않는 것이 좋습니다. `saas:resync` 정기적으로 명령합니다. 다음 두 가지 시나리오에서 명령을 수동으로 실행해야 할 수 있습니다.

- 초기 동기화
- 다음 [SaaS 데이터 공간 ID](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) 이(가) 변경되었습니다.

### 초기 동기화

다음을 트리거할 때 `saas:resync` 명령줄에서 카탈로그 크기에 따라 데이터를 업데이트하는 데 몇 분에서 몇 시간이 걸릴 수 있습니다.

초기 동기화의 경우 다음 순서로 명령을 실행하는 것이 좋습니다.

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### 문제 해결

에 예상 데이터가 표시되지 않는 경우 [!DNL Commerce Service]에서 동기화하는 동안 문제가 발생했는지 확인 [!DNL Adobe Commerce] 인스턴스를 [!DNL Commerce Service] 플랫폼.

에는 두 개의 로그 파일이 있습니다. `var/log/` 디렉터리:

- `commerce-data-export-errors.log` - 다음 기간 동안 오류가 발생한 경우 _수집_ 단계
- `saas-export-errors.log` - 다음 기간 동안 오류가 발생한 경우 _전송 중_ 단계

#### 피드 페이로드 확인

에 전송된 피드 페이로드를 확인하는 것이 유용할 수 있습니다. [!DNL Commerce Service]. 이 작업은 환경 변수를 전달하여 수행할 수 있습니다 `EXPORTER_EXTENDED_LOG=1`. 다음 `no-reindex` 플래그는 현재 수집된 데이터만 전송됨을 의미합니다.

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

페이로드는에서 사용할 수 있습니다. `var/log/saas-export.log`.

#### 피드 인덱스 테이블의 페이로드 유지

다음 날짜 이후 `magento/module-data-exporter:103.0.0` 일부 피드: 제품 피드, 가격 피드, 색인 테이블에는 필요한 최소 데이터만 유지됩니다.

프로덕션 환경에서는 인덱스 테이블의 페이로드 데이터를 보존하지 않는 것이 좋지만, 개발자 인스턴스에서는 유용할 수 있습니다. 다음을 전달하여 이 작업을 수행합니다. `PERSIST_EXPORTED_FEED=1` 환경 변수:

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### 프로파일링

특정 피드의 색인 재지정 프로세스에 불합리한 시간이 걸리는 경우 프로파일러를 실행하여 지원 팀에 유용할 수 있는 추가 데이터를 수집합니다. 이렇게 하려면 다음을 전달하십시오. `EXPORTER_PROFILER=1`환경 변수:

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

프로파일러 데이터는에 저장됩니다. `var/log/commerce-data-export.log` 형식:

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### 지원 요청 제출

구성 또는 타사 확장과 관련이 없는 오류가 표시되면 [지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) 가능한 많은 정보를 제공합니다.
