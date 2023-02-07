---
title: 카탈로그 동기화
description: 에서 제품 데이터를 내보내는 방법을 알아봅니다. [!DNL Commerce] 서버 대상 [!DNL Commerce Services] 서비스를 최신 상태로 유지하기 위해 지속적으로.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: dd9ba7171cf6a199701b1abb8083a65326e89f5d
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---

# 카탈로그 동기화

Adobe Commerce 및 Magento Open Source은 인덱서를 사용하여 카탈로그 데이터를 테이블에 컴파일합니다. 이 프로세스는 자동으로 [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) 제품 가격 또는 재고 수준 변경과 같은 변경.

카탈로그 동기화 프로세스는 시간별로 실행되어 [!DNL Commerce] 카탈로그 데이터를 사용할 서비스. 카탈로그 동기화에서 제품 데이터를 내보냅니다. [!DNL Commerce] 서버 대상 [!DNL Commerce] 서비스를 최신 상태로 유지하기 위한 지속적인 서비스 제공 예, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) 올바른 이름, 가격 및 가용성을 가진 권장 사항을 정확하게 반환하려면 현재 카탈로그 정보가 필요합니다. 를 사용할 수 있습니다 _카탈로그 동기화_ 대시보드 를 사용하여 동기화 프로세스 또는 [명령줄 인터페이스](#resynccmdline) 카탈로그 동기화를 트리거하고 다음을 통해 소비할 제품 데이터를 다시 색인화합니다. [!DNL Commerce] 서비스.

>[!NOTE]
>
> 를 사용하려면 _카탈로그 동기화_ 대시보드 또는 명령줄 인터페이스는 반드시 [API 키 및 구성된 SaaS 데이터 공간](saas.md).

## 카탈로그 동기화 대시보드 액세스

>[!NOTE]
>
> 다음 _카탈로그 동기화_ 대시보드는 다음과 같은 경우에만 사용할 수 있습니다 _제품 Recommendations_ 모듈은 설치되며 해당 기능과 관련된 데이터 예측만 반영합니다. 과 같은 다른 Commerce Services 지원 _라이브 검색_ 및 _카탈로그 서비스_ 향후 계획을 세울 예정입니다.

카탈로그 동기화 대시보드에 액세스하려면 다음을 선택합니다 **시스템** > _데이터 전송_ > **카탈로그 동기화**.

사용 **카탈로그 동기화** 대시보드 를 사용하면 다음 작업을 수행할 수 있습니다.

- 동기화 상태 보기(**진행 중**, **성공**, **실패**)
- 성공한 경우 동기화된 총 제품 수 보기
- 동기화된 제품을 검색하여 현재 상태를 확인합니다
- 이름, SKU 등을 기준으로 스토어 카탈로그 검색
- 동기화 불일치를 진단하는 데 도움이 되도록 JSON에서 동기화된 제품 세부 사항을 봅니다
- 동기화 프로세스 다시 시작

### 마지막 동기화

다음과 같은 동기화 상태를 보고합니다.

- **성공** - 동기화가 성공한 날짜 및 시간과 업데이트된 제품 수를 표시합니다
- **실패** - 동기화를 시도한 날짜 및 시간을 표시합니다
- **진행 중** - 마지막으로 성공한 동기화 날짜와 시간을 표시합니다

>[!NOTE]
>
> 카탈로그 동기화 프로세스는 매시간마다 자동으로 실행됩니다. 그러나 스토어에 제품이 보이지 않거나 최근에 변경한 내용이 제품에 반영되지 않으면 문제를 해결할 수 있습니다 [카탈로그 동기화 문제](#resolvesync).

### 동기화된 제품

에서 동기화된 총 제품 수를 표시합니다 [!DNL Commerce] 카탈로그 초기 동기화 후에는 변경된 제품만 동기화되어야 합니다.

## 다시 동기화 {#resync}

시간별 예약된 동기화가 발생하기 전에 카탈로그 재동기화를 시작해야 하는 경우 강제로 재동기화를 수행할 수 있습니다.

>[!NOTE]
>
> 재동기화를 수행하면 전체 제품 카탈로그의 재동기화가 트리거되어 하드웨어 리소스에 대한 로드가 늘어날 수 있습니다.

1. 에서 _카탈로그 동기화_ 대시보드, 선택 **설정**.

   다음 _카탈로그 동기화 설정_ 페이지가 나타납니다.

1. 에서 _데이터 다시 동기화_ 섹션을 클릭합니다. [!UICONTROL Resync].

   [!DNL Commerce] 다음 예약된 동기화 기간 동안 카탈로그를 동기화합니다. 카탈로그 크기에 따라 이 작업은 시간이 오래 걸릴 수 있습니다.

## 동기화된 카탈로그 제품

다음 **동기화된 카탈로그 제품** 테이블에는 다음 정보가 표시됩니다.

| 필드 | 설명 |
|---|---|
| ID | 제품의 고유 식별자입니다 |
| 이름 | 제품의 저장소 이름 |
| 유형 | 단순, 구성 가능, 다운로드 가능 등과 같은 제품 유형을 식별합니다 |
| 마지막으로 내보낸 날짜 | 카탈로그에서 제품을 마지막으로 내보낸 날짜 |
| 마지막 수정 날짜 | 카탈로그에서 제품이 마지막으로 수정된 날짜 |
| SKU | 제품에 대한 재고 유지 단위를 표시합니다 |
| 가격 | 제품 가격 |
| 가시성 | 에 정의된 대로 제품의 가시성 설정 [!DNL Commerce] 카탈로그 |

## 카탈로그 동기화 문제 해결 {#resolvesync}

데이터 재동기화를 트리거할 때 데이터가 업데이트되고 권장 사항 단위와 같은 UI 구성 요소에 반영되는 데 최대 1시간이 걸릴 수 있습니다. 그러나 한 시간을 기다린 후에도 카탈로그와 스토어에 표시되는 내용 간의 불일치를 여전히 감지하거나 카탈로그 동기화가 실패한 경우 다음을 참조하십시오.

### 데이터 불일치

1. 해당 제품의 세부 보기를 검색 결과에 표시합니다.
1. JSON 출력을 복사하고에 있는 콘텐츠와 일치하는지 확인합니다 [!DNL Commerce] 카탈로그
1. 컨텐츠가 일치하지 않는 경우 공백이나 기간 추가 등 카탈로그의 제품을 약간 변경합니다.
1. 재동기화 또는 [수동 재동기화 트리거](#resync).

### 동기화가 실행되고 있지 않음

동기화가 일정에서 실행되고 있지 않거나 아무 것도 동기화되지 않는 경우 [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### 동기화 실패

카탈로그 동기화 상태가 **실패**, 제출 [지원 티켓](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## 명령줄 인터페이스 {#resynccmdline}

다음 `saas:resync` 명령은 다음 중 일부입니다. `magento/saas-export` 패키지. 다음 중 하나를 사용하여 이 패키지를 설치할 수 있습니다 [!DNL Commerce Services] 와 같은 제품 [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) 또는 [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> 처음으로 데이터 동기화를 실행할 때는 `productattributes` 먼저 피드, 그 다음 `productoverrides`를 실행하기 전에 `products` 피드.

명령 옵션:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

다음 표에서는 `saas:resync` 매개 변수 및 설명.

| 매개 변수 | 설명 | 필수? |
|---| ---| ---|
| `feed` | 다시 동기화할 엔터티(예: `products` | 예 |
| `no-reindex` | 기존 카탈로그 데이터를에 다시 제출 [!DNL Commerce Services] 다시 색인화하지 않습니다. 이 매개 변수를 지정하지 않으면 데이터를 동기화하기 전에 명령이 전체 재색인을 실행합니다. | 아니요 |

피드 이름은 다음 중 하나일 수 있습니다.

- `products`— 카탈로그의 제품
- `categories`— 카탈로그의 카테고리
- `variants`— 색상 및 크기와 같은 구성 가능한 제품의 제품 변형
- `productattributes`— 다음과 같은 제품 속성 `activity`, `gender`, `tops`, `bottoms`, 기타 등
- `productoverrides`— 카테고리 권한을 기반으로 하는 규칙과 같은 고객별 가격 및 카탈로그 가시성 규칙

명령줄에서 데이터 재동기화를 트리거하면 데이터가 업데이트되는 데 최대 1시간이 걸릴 수 있습니다.

### 예

다음 예제에서는 [!DNL Commerce] 카탈로그 및 재동기화:

```bash
bin/magento saas:resync --feed products
```

제품의 전체 재색인을 실행하지 않으려면 이미 생성된 제품 데이터를 대신 동기화할 수 있습니다.

```bash
bin/magento saas:resync --feed products --no-reindex
```
