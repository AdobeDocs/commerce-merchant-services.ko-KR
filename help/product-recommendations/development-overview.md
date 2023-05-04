---
title: 제품 Recommendations 관리자 개발
description: 제품 Recommendations 아키텍처 및 개발 기능에 대한 개요입니다.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 제품 Recommendations 관리자 개발

제품 Recommendations은 전환을 늘리고, 매출을 증대하고, 구매자 참여를 유도하는 데 사용할 수 있는 강력한 마케팅 도구입니다. 제품 Recommendations은 상점 앞에서 &quot;이 제품을 본 고객도 본 고객&quot;, &quot;이 제품을 구매한 고객도 구매함&quot;, &quot;추천된 고객&quot; 등과 같은 단위 형태로 표시됩니다. Adobe Commerce 제품 Recommendations 지원 [Adobe Sensei](https://www.adobe.com/sensei.html)- 인공 지능 및 기계 학습 알고리즘을 사용하여 집계된 쇼퍼 데이터를 심층적으로 분석합니다. 이 데이터를 상거래 카탈로그와 결합하면 구매자를 위한 매력적인 연관성 있고 개인화된 경험이 생성됩니다.

>[!NOTE]
>
>PWA Studio을 사용하여 스토어를 구현한 경우 [PWA 설명서](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). React 또는 Value JS와 같은 사용자 지정 프런트 엔드 기술을 사용하는 경우 사용 안내서 를 참조하여 Product Recommendations을 [헤드리스](headless.md) 환경. 헤드리스 인스턴스는 제품 권장 사항 작업 공간을 활용하려면 이벤트를 구현해야 합니다.

## 아키텍처 개요

높은 수준에서 Commerce Product Recommendations은 SaaS로 배포됩니다. 상거래 측에는 이벤트 수집기 및 권장 사항 레이아웃 템플릿이 들어 있는 스토어프런트와, 데이터 서비스, SaaS 내보내기 모듈 및 관리 UI를 포함하는 백엔드가 포함됩니다. Adobe Sensei intelligence 서비스는 SaaS 측에서 활용됩니다.

![제품 권장 사항 아키텍처 다이어그램](assets/arch-diag-sensei.svg)

권장 사항 모듈이 설치 및 구성되면 storefront에서 동작 데이터 수집을 시작합니다. Adobe Sensei은 이 행동 데이터를 카탈로그 데이터와 함께 처리하고 recommendations 서비스에서 활용하는 제품 연결을 계산합니다. 이때 머천트는 Admin UI에서 직접 제품 권장 사항 단위를 생성, 관리 및 스토어에 배포할 수 있습니다.

## 데이터 유형

제품 Recommendations에는 다음 데이터가 필요합니다.

- **행동** - 제품 보기, 장바구니에 추가된 항목 및 구매와 같이 사이트에 있는 구매자의 참여에 따른 데이터입니다. Commerce 및 Adobe Sensei은 개인 식별 정보를 수집하지 않습니다.

- **카탈로그** - 이름, 가격, 가용성 등의 제품 메타데이터

를 설치할 때 `magento/product-recommendations` 모듈, Adobe Sensei은 동작 및 카탈로그 데이터를 집계하여 각 권장 사항 유형에 대한 제품 Recommendations을 만듭니다. 그런 다음 제품 Recommendations 서비스에서 이러한 권장 사항을 스토어에 배포합니다.

## 다음 단계

Product Recommendations을 시작하려면 다음 주제를 읽어 보십시오.

- [제품 Recommendations 구현 방법](implementation-workflow.md)

- [제품 Recommendations 설치 및 구성](install-configure.md)

- [제품 Recommendations 만들기](create.md)
