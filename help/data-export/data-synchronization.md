---
title: SaaS 데이터 내보내기와 데이터 동기화
description: "다음 방법 알아보기 [!DNL SaaS Data Export] Adobe Commerce 인스턴스와 연결된 SaaS 서비스 간에 데이터를 수집하고 동기화합니다."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# SaaS 데이터 내보내기와 데이터 동기화

Catalog Service, Live Search 또는 Product Recommendations과 같이 데이터 내보내기가 필요한 Commerce Service를 설치하면 데이터 수집 및 동기화 프로세스를 관리하기 위해 Saas 데이터 내보내기 모듈 컬렉션이 설치됩니다. 다음 다이어그램은 SaaS 데이터 내보내기 플로우를 보여 줍니다.

![Adobe Commerce을 위한 SaaS 데이터 내보내기 수집 및 동기화 흐름](assets/data-export-flow.png){width="900" zoomable="yes"}

SaaS 데이터 내보내기 흐름의 주요 구성 요소는 다음과 같습니다.

- Adobe Commerce에서 피드에 대한 데이터를 수집하고, 피드 항목을 조합하고, 업데이트를 수신하고, 피드 상태를 유지하는 SaaS 데이터 내보내기 모듈입니다.
- 데이터를 내보내고, 라우팅을 구성하고, 연결된 서비스에 피드를 게시하는 SaaS 내보내기 모듈.
- Adobe Commerce 서비스는 수신 피드의 유효성을 검사하고 연결된 서비스에 대한 업데이트를 지속하기 위해 데이터 수집 프로세스를 관리합니다.

## 동기화 모드

SaaS 데이터 내보내기에는 엔티티 피드를 처리하는 두 가지 모드가 있습니다.

- **즉시 내보내기 모드**—이 모드에서는 데이터가 수집되어 한 번의 반복으로 Commerce 서비스로 즉시 전송됩니다. 이 모드는 Commerce 서비스에 대한 엔티티 업데이트 전달 속도를 높이고 피드 테이블의 저장소 크기를 줄입니다.

- **레거시 내보내기 모드**- 이 모드에서는 데이터가 단일 프로세스로 수집됩니다. 그런 다음 cron 작업은 연결된 상거래 서비스로 수집된 데이터를 전송합니다. 데이터 내보내기 로그 항목에서 기존 모드를 사용하는 피드에 레이블이 지정됩니다 `(legacy)`.

## 동기화 유형

SaaS 데이터 내보내기는 세 가지 동기화 유형(전체 동기화, 부분 동기화 및 실패한 항목 동기화 다시 시도)을 지원합니다.

### 전체 동기화

Adobe Commerce 인스턴스를 Commerce 서비스에 연결한 후 전체 동기화를 수행하여 Adobe Commerce에서 연결된 서비스로 엔티티 피드 데이터를 보냅니다.

>[!NOTE]
>
>전체 동기화는 주로 온보딩 단계에 해당합니다. 데이터베이스 오버로드를 방지하기 위해 정기적으로 사용하지 마십시오. 초기 동기화 후 진행 중인 변경 사항은 부분 동기화를 사용하여 자동으로 동기화됩니다.

### 부분 동기화

부분 동기화를 통해 SaaS 데이터 내보내기는 제품 이름 변경 또는 가격 업데이트와 같은 Commerce 애플리케이션의 업데이트를 연결된 상거래 서비스로 자동으로 전송합니다.

데이터 내보내기 프로세스에서는 다음 cron 작업을 사용하여 부분 동기화 작업을 자동화합니다.

- &quot;index&quot; cron 그룹 작업:
   - 다음 `indexer_reindex_all_invalid` 작업이 모든 잘못된 피드를 다시 인덱싱합니다. 표준 Adobe Commerce 크론 작업입니다.
   - 다음 `saas_data_exporter` 작업은 레거시 내보내기 피드에 사용됩니다.
   - 다음 `sales_data_exporter` 작업은 판매 데이터 내보내기 피드에만 해당됩니다.

이러한 작업은 매 분마다 실행됩니다.

부분 동기화가 작동하려면 Commerce 애플리케이션에 다음 구성이 필요합니다.

- [작업 예약이 cron job을 통해 활성화됨](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- 모든 SaaS 데이터 내보내기 인덱서가에 구성되어 있습니다. `Update by Schedule` 모드.

  SaaS 데이터 내보내기 버전 103.1.0 이상에서 `Update by Schedule` 모드는 기본적으로 활성화되어 있습니다. Commerce CLI 명령을 사용하여 서버에서 인덱스 구성을 확인할 수 있습니다. `bin/magento indexer:show-mode | grep -i feed`

### 실패한 항목 동기화 다시 시도

실패한 항목 동기화 다시 시도는 별도의 프로세스를 사용하여 동기화 프로세스 중 오류(예: 애플리케이션 오류, 네트워크 중단 또는 SaaS 서비스 오류)로 인해 동기화에 실패한 항목을 다시 보냅니다. 이 동기화에 대한 구현도 cron 작업을 기반으로 합니다.

- `resync_failed_feeds_data_exporter` cron 그룹 작업:
   - 다음 `<feed name>_feed_resend_failed_feeds_items` 작업이 동기화에 실패한 항목을 다시 보냅니다. 예: `products_feed_resend_failed_items`.

### 동기화 프로세스 보기 및 관리

대부분의 동기화 활동은 애플리케이션 구성에 따라 자동으로 처리됩니다. 그러나 SaaS 데이터 내보내기는 프로세스를 관리하는 도구도 제공합니다.

- 관리자는 동기화 진행 상황을 확인 및 추적하고 [데이터 관리 대시보드](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

- Commerce 애플리케이션 서버에 액세스할 수 있는 개발자, 시스템 통합자 또는 관리자는 Adobe Commerce 명령줄 도구(CLI)를 사용하여 동기화 프로세스 및 데이터 피드를 관리할 수 있습니다. 다음을 참조하십시오 [데이터 내보내기 명령 참조](data-export-cli-commands.md).

### Commerce 애플리케이션 구성 확인

Commerce 인스턴스가 올바르게 구성된 경우에만 부분 동기화 및 실패한 항목 동기화 다시 시도 가 작동합니다. 일반적으로 Commerce 서비스를 설정할 때 구성이 완료됩니다. 데이터 내보내기가 제대로 작동하지 않으면 다음 구성을 확인하십시오.

- [cron 작업이 실행 중인지 확인](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).

- 인덱서가 다음에서 실행 중인지 확인 [관리자](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 또는 Commerce CLI 명령 사용 `bin/magento indexer:info`.

- 다음 피드에 대한 인덱서가 로 설정되어 있는지 확인합니다. `Update by Schedule`: 카탈로그 속성, 제품, 제품 재정의 및 제품 변형. 인덱서는 다음 위치에서 확인할 수 있습니다. [색인 관리](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) 관리에서 또는 CLI 사용(`bin/magento indexer:show-mode | grep -i feed`).
