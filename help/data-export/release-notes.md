---
title: '[!DNL SaaS Data Export Extension] 릴리스 노트'
description: Adobe Commerce의  [!DNL Data Export Extension] 에 대한 최신 릴리스 정보입니다.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 11ea98069dcc6d06e9ab90add8239fef2c8edc7d
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# [!DNL SaaS Data Export] 확장 릴리스 노트

이 릴리스 노트는 [!DNL SaaS data export] 확장의 최신 버전에 대해 설명합니다. 현재 주요 릴리스 버전에 대한 지원이 제공됩니다. 이전 버전에 대한 릴리스 노트는 참조를 위해 제공됩니다.

업데이트에는 다음이 포함됩니다.

새 기능 ![개](../assets/new.svg)개
![수정](../assets/fix.svg) 수정 사항 및 개선 사항
![버그](../assets/bug.svg) 알려진 문제


>[!NOTE]
>
>SaaS 데이터 내보내기 확장은 라이브 검색, 제품 Recommendations 및 카탈로그 서비스와 함께 자동으로 설치되는 모듈 컬렉션입니다. 작성기를 사용하여 시스템에 설치된 버전을 확인할 수 있습니다. 경우에 따라 Commerce 서비스 버전을 업데이트하지 않고 시스템에서 데이터 내보내기 확장 기능을 업그레이드하여 수정 사항이나 새 기능을 선택할 수 있습니다.

## 현재 메이저 버전

## 103.3.9 릴리스

![수정](../assets/fix.svg) 엔터티가 삭제되면 이제 `deleted` 플래그가 웹 사이트(`scopesWebsite`) 및 고객 그룹(`scopesCustomerGroup`)의 범위 서비스 피드에 대해 전파됩니다.<!--MDEE-839-->

## 103.3.8 릴리스

![수정](../assets/fix.svg) 비활성화된 구성 옵션은 더 이상 활성 옵션으로 내보내지 않습니다.<!--MDEE-812-->
![수정](../assets/fix.svg) 이제 하위 제품에 변경 사항이 적용되면 구성 가능한 제품에 대한 옵션 및 값이 업데이트됩니다. <!--MDEE-835-->
![새로 만들기](../assets/new.svg) 제품 특성 피드에 추가 시스템 특성 데이터를 포함하는 기능이 추가되었습니다.

## 103.3.7 릴리스

![수정](../assets/fix.svg)이(가) InventoryDataExporter 모듈에서 불필요한 종속성을 제거했습니다.
![수정](../assets/fix.svg) Adobe Commerce 버전 2.4.4를 지원하도록 CatalogInventoryDataExporter 모듈에 포함된 인벤토리 모듈에 대한 필수 버전을 변경했습니다.

## 103.3.6 릴리스

![수정](../assets/fix.svg) 다중 스레드 모드에서 피드를 다시 인덱싱하는 동안 발생한 교착 상태를 해결했습니다. 이제 쿼리가 삽입 및 업데이트 작업으로 구분됩니다.
![수정](../assets/fix.svg) 많은 웹 사이트가 있는 큰 카탈로그의 가격 쿼리를 최적화했습니다.
![새로 만들기](../assets/new.svg) 교착 상태가 발생할 때 실패한 트랜잭션을 다시 실행하기 위한 다시 시도 논리를 추가했습니다.

## 103.3.5 릴리스

![수정](../assets/fix.svg) SaaS 공통 모듈에 대해 호환되는 최신 데이터 내보내기 버전에 대한 종속성을 설정합니다.

![수정](../assets/fix.svg)이(가) 다른 서비스 구성을 지원하기 위해 `ScopeConfig` 인스턴스를 `ServiceConfigInterface`(으)로 대체했습니다.

## 103.3.4 릴리스

![수정](../assets/fix.svg) 리인덱싱 프로세스에 대한 자세한 내용을 추가하여 Commerce SaaS 데이터 내보내기 로깅을 개선합니다.

## 103.3.3 릴리스

![새로 만들기](../assets/new.svg) SaaS 데이터 내보내기가 이제 특성 메타데이터 쿼리에 대해 EAV(Entity-Attribute-Value) 특성을 캐시합니다.

![수정](../assets/fix.svg) 제품을 삭제한 경우 다시 시도할 때 `InventoryStockStatus` 피드가 저장되지 않는 문제를 해결했습니다.

## 103.3.2 릴리스

![수정](../assets/fix.svg) 제거된 엔터티 피드에서 `modifiedAt` 필드가 누락되는 문제를 해결했습니다.

## 103.3.1 릴리스

![수정](../assets/fix.svg) 페이지 빌더를 설치할 때 제품 피드를 다시 인덱싱하는 동안 `Invalid Template File` 메시지가 표시되는 문제를 해결했습니다.

## 103.3.0 릴리스

![새로 만들기](../assets/new.svg) 바로 내보내기 피드 테이블을 통합 구조로 마이그레이션했습니다.
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![새로 만들기](../assets/new.svg) 카탈로그 및 인벤토리 피드를 즉시 내보내기 솔루션으로 마이그레이션했습니다.

![새로 만들기](../assets/new.svg) 피드를 즉시 내보내는 크론 작업이 `*_feed_resend_failed_items`(으)로 이름이 변경되었습니다.

![새로 만들기](../assets/new.svg) 바로 내보내기 피드 및 변경 로그 테이블의 이름이 변경되었습니다.

![수정](../assets/fix.svg) 필요한 피드에 대해서만 피드 데이터의 `modified_at` 필드를 설정합니다.

![수정](../assets/fix.svg) 제품 특성만 검색하려면 `productAttributes` 쿼리를 수정하십시오.

## 103.2.6 릴리스

![수정](../assets/fix.svg) 테이블에 접두사가 있을 때 피드가 다시 인덱싱되지 않는 문제를 해결했습니다.

## 103.2.5 릴리스

![수정](../assets/fix.svg) 가격 쿼리를 최적화했습니다.

## 103.2.4 릴리스

![수정](../assets/fix.svg) Commerce Inventory management이 활성화된 경우 제품에 대해 표시되는 잘못된 재고 상태를 수정했습니다.

## 103.2.3 릴리스

![수정](../assets/fix.svg) 웹 사이트 수준의 특별 가격을 수정했습니다.
![수정](../assets/fix.svg) 처리되는 모든 피드에 대해 뮤텍스를 추가했습니다.


## 103.2.2 릴리스

![수정](../assets/fix.svg) 큰 카탈로그에 대한 피드 일괄 처리 전략을 개선했습니다. 이제 배치 테이블이 메모리 사용을 줄이기 위해 제한된 수의 ID로 채워집니다.

![수정](../assets/fix.svg)으로 인해 MSI 모듈에 대한 CommerceInventoryDataExporter의 엄격한 종속성이 제거되었습니다.

![수정](../assets/fix.svg) 더 많은 정보를 수집하고 여러 내보내기 단계로 구성할 수 있도록 `commerce-data-exporter` 로그를 개선했습니다.

## 103.2.1 릴리스

- 업데이트된 버전이 릴리스되었습니다.

## 103.2.0 릴리스

- 제품 및 가격에 대한 다중 스레드 데이터 동기화를 추가했습니다.
