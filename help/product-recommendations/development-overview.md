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

제품 Recommendations은 전환율을 높이고 매출을 증대하며 쇼핑객 참여를 촉진하는 데 사용할 수 있는 강력한 마케팅 도구입니다. 제품 Recommendations은 &quot;이 제품을 본 고객도 본 고객&quot;, &quot;이 제품을 구매한 고객도 구매함&quot;, &quot;추천 고객&quot; 등과 같은 단위의 형태로 상점 앞에 표시됩니다. Adobe Commerce 제품 Recommendations 제공 [Adobe Sensei](https://www.adobe.com/sensei.html): 인공 지능과 머신 러닝 알고리즘을 사용하여 집계된 쇼핑객 데이터를 심층 분석합니다. 이 데이터를 상거래 카탈로그와 결합하면 쇼핑객에게 매우 매력적이고 관련성이 높으며 개인화된 경험을 제공합니다.

>[!NOTE]
>
>Storefront가 PWA Studio을 사용하여 구현된 경우 다음을 참조하십시오. [PWA 설명서](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). React 또는 Vue JS와 같은 사용자 지정 프론트엔드 기술을 사용하는 경우 사용자 안내서에서 제품 Recommendations을 통합하는 방법에 대해 알아보십시오. [headless](headless.md) 환경. Headless 인스턴스는 제품 추천 작업 영역을 향상시키기 위해 이벤트를 구현해야 합니다.

## 아키텍처 개요

높은 수준에서 Commerce Product Recommendations은 SaaS로 배포됩니다. 상거래 측에는 이벤트 수집기 및 권장 사항 레이아웃 템플릿이 포함된 상점 및 데이터 서비스, SaaS 내보내기 모듈 및 관리 UI가 포함된 백엔드가 포함됩니다. Adobe Sensei 인텔리전스 서비스는 SaaS 측면에서 활용됩니다.

![제품 추천 아키텍처 다이어그램](assets/arch-diag-sensei.svg)

권장 사항 모듈을 설치하고 구성하면 상점 첫 화면에서 동작 데이터 수집을 시작합니다. Adobe Sensei은 카탈로그 데이터와 함께 이 행동 데이터를 처리하고 recommendations 서비스에서 활용하는 제품 연결을 계산합니다. 이 시점에서 판매자는 관리 UI에서 직접 제품 추천 단위를 만들고, 관리하고, 상점 앞에 배포할 수 있습니다.

## 데이터 유형

제품 Recommendations에는 다음 데이터가 필요합니다.

- **동작** - 제품 보기, 장바구니에 추가한 항목, 구매 등 사이트에 대한 쇼핑객 참여의 데이터. Commerce 및 Adobe Sensei은 개인 식별 정보를 수집하지 않습니다.

- **카탈로그** - 이름, 가격, 가용성 등과 같은 제품 메타데이터.

설치 시 `magento/product-recommendations` 모듈 Adobe Sensei은 행동 및 카탈로그 데이터를 집계하여 각 권장 사항 유형에 대한 제품 Recommendations을 만듭니다. 그런 다음 제품 Recommendations 서비스는 이러한 권장 사항을 상점 앞에 배포합니다.

## 다음 단계

Product Recommendations을 시작하려면 다음 항목을 참조하십시오.

- [제품 Recommendations 구현 방법](implementation-workflow.md)

- [Product Recommendations 설치 및 구성](install-configure.md)

- [제품 Recommendations 만들기](create.md)
