---
title: "[!DNL SaaS Data Export Extension] 릴리스 노트"
description: 의 최신 릴리스 정보 [!DNL Data Export Extension] Adobe Commerce용
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] 확장 릴리스 노트

이 릴리스 노트는 최신 버전의 [!DNL SaaS data export] 확장명. 현재 주요 릴리스 버전에 대한 지원이 제공됩니다. 이전 버전에 대한 릴리스 노트는 참조를 위해 제공됩니다.

업데이트에는 다음이 포함됩니다.

![신규](../assets/new.svg) 새로운 기능
![수정](../assets/fix.svg) 수정 사항 및 향상된 기능
![버그](../assets/bug.svg) 알려진 문제


>[!NOTE]
>
>SaaS 데이터 내보내기 확장은 라이브 검색, 제품 Recommendations 및 카탈로그 서비스와 함께 자동으로 설치되는 모듈 컬렉션입니다. 작성기를 사용하여 시스템에 설치된 버전을 확인할 수 있습니다. 경우에 따라 Commerce 서비스 버전을 업데이트하지 않고 시스템에서 데이터 내보내기 확장 기능을 업그레이드하여 수정 사항이나 새 기능을 선택할 수 있습니다.

## 현재 메이저 버전

## 103.3.5 릴리스

![수정](../assets/fix.svg) SaaS 공통 모듈에 대한 최신 호환 데이터 내보내기 버전에 대한 종속성을 설정합니다.

![수정](../assets/fix.svg) 대체됨 `ScopeConfig` 인스턴스 포함 `ServiceConfigInterface` 다양한 서비스 구성을 지원합니다.

## 103.3.4 릴리스

![수정](../assets/fix.svg) 리인덱싱 프로세스에 대한 자세한 내용을 추가하여 Commerce SaaS 데이터 내보내기 로깅을 개선합니다.

## 103.3.3 릴리스

![신규](../assets/new.svg) 이제 SaaS 데이터 내보내기는 속성 메타데이터 쿼리에 대해 EAV(Entity-Attribute-Value) 속성을 캐시합니다.

![수정](../assets/fix.svg) 이(가) 다음을 포함하는 문제가 해결되었습니다. `InventoryStockStatus` 제품이 삭제된 경우 다시 시도 시 피드가 저장되지 않았습니다.

## 103.3.2 릴리스

![수정](../assets/fix.svg) 이(가) 다음을 포함하는 문제가 해결되었습니다. `modifiedAt` 제거된 엔티티 피드에서 필드가 누락되었습니다.

## 103.3.1 릴리스

![수정](../assets/fix.svg) 을(를) 발생시킨 문제를 해결했습니다. `Invalid Template File` 페이지 빌더를 설치할 때 제품 피드를 다시 색인화하는 동안 표시되는 메시지입니다.

## 103.3.0 릴리스

![신규](../assets/new.svg) 즉시 내보내기 피드 테이블을 통합 구조로 마이그레이션했습니다.
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![신규](../assets/new.svg) 카탈로그 및 인벤토리 피드를 즉시 내보내기 솔루션으로 마이그레이션했습니다.

![신규](../assets/new.svg) 즉시 내보내기 피드 크론 작업 이름이 다음으로 변경됨 `*_feed_resend_failed_items`.

![신규](../assets/new.svg) 즉시 내보내기 피드 및 변경 로그 테이블의 이름이 변경되었습니다.

![수정](../assets/fix.svg) 설정 `modified_at` 필요한 피드에 대해서만 피드 데이터의 필드입니다.

![수정](../assets/fix.svg) 수정 `productAttributes` 제품 속성만 검색하도록 쿼리합니다.

## 103.2.6 릴리스

![수정](../assets/fix.svg) 테이블에 접두사가 있을 때 피드가 다시 인덱싱되지 않던 문제를 수정했습니다.

## 103.2.5 릴리스

![수정](../assets/fix.svg) 가격 쿼리를 최적화했습니다.

## 103.2.4 릴리스

![수정](../assets/fix.svg) Commerce Inventory management이 활성화되면 제품에 대해 표시되는 잘못된 재고 상태를 수정했습니다.

## 103.2.3 릴리스

![수정](../assets/fix.svg) 웹 사이트 수준 특별 가격을 수정했습니다.
![수정](../assets/fix.svg) 처리되는 모든 피드에 대해 뮤텍스를 추가했습니다.


## 103.2.2 릴리스

![수정](../assets/fix.svg) 큰 카탈로그에 대한 피드 일괄 처리 전략이 개선되었습니다. 이제 배치 테이블이 메모리 사용을 줄이기 위해 제한된 수의 ID로 채워집니다.

![수정](../assets/fix.svg) MSI 모듈에 대한 CommerceInventoryDataExporter의 종속성을 제거했습니다.

![수정](../assets/fix.svg) 개선됨 `commerce-data-exporter` 를 로그하여 더 많은 정보를 수집하고 여러 내보내기 단계별로 구성합니다.

## 103.2.1 릴리스

- 업데이트된 버전이 릴리스되었습니다.

## 103.2.0 릴리스

- 제품 및 가격에 대한 다중 스레드 데이터 동기화를 추가했습니다.

