---
title: 구현 워크플로
description: 을(를) 성공적으로 구현하는 단계 알아보기 [!DNL Product Recommendations] 가게 앞에서요
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# 구현 워크플로

[!DNL Product Recommendations] 은 비헤이비어 데이터와 카탈로그 데이터를 모두 사용합니다.

- 행동 - 제품 보기, 장바구니에 추가한 항목 및 구매와 같이, 사이트에 대한 쇼핑객 참여의 데이터. Adobe Commerce 및 Adobe Sensei은 개인 식별 정보를 수집하지 않습니다.

- 카탈로그 - 이름, 가격 및 가용성과 같은 제품 메타데이터.

설치 시 `magento/product-recommendations module`, Adobe Sensei은 행동 및 카탈로그 데이터를 집계하고 다음을 생성합니다. [!DNL Product Recommendations] 각 권장 사항 유형에 대해 설명합니다. 다음 [!DNL Product Recommendations] 그런 다음 서비스는 이러한 권장 사항을 상점 앞에 배포합니다. 상점에서 제품 권장 사항을 구현하는 데 도움이 되도록 하려면 다음 워크플로를 사용하십시오.

>[!NOTE]
>
> Storefront가 PWA Studio을 사용하여 구현된 경우 다음을 참조하십시오. [PWA 설명서](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). React 또는 Vue JS와 같은 사용자 지정 프론트엔드 기술을 사용하는 경우 [통합](headless.md) [!DNL Product Recommendations] headless 상점 앞까지.

## 워크플로

1. **프로덕션에 데이터 수집 배포**

   배포 [!DNL Product Recommendations] 기본 두 개 필요 [데이터 소스](type.md): 카탈로그 및 동작. 프로덕션은 쇼핑객의 작업을 캡처하고 분석하는 유일한 환경이므로 가능한 한 빨리 프로덕션에 데이터 수집을 시작하는 것이 가장 좋습니다. [학습](behavioral-data.md) Adobe Sensei에서 고품질 추천을 생성하는 머신 러닝 모델을 교육하는 방법. 추가로, 프로덕션에서 동작 데이터를 수집하기 시작할 때 다음을 수행할 수 있습니다. [권장 사항 가져오기](verify.md) 비프로덕션 환경에서 작동하는 동안 이 프로덕션 데이터를 기반으로 합니다. 그런 다음 프로덕션에서 수집된 실제 구매자 데이터를 기반으로 계산되는 다양한 권장 사항을 테스트하고 실험할 수 있습니다.

   데이터 수집을 프로덕션에 배포하려면 다음을 수행해야 합니다. [설치 및 구성](install-configure.md) 다음 [!DNL Product Recommendations] 다음을 제공하는 모듈 [API 키](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > 데이터 수집을 배포해도 상점 모습이나 쇼핑객 경험은 변경되지 않습니다. 권장 사항 단위를 만들고 배포하기만 하면 상점 내 고객 환경이 변경됩니다. 프로덕션에 배포하기 전에 비프로덕션 환경에서 테스트해야 합니다. 또한 템플릿을 사용자 정의할 때까지 추천 단위를 만들지 마십시오. 다음 단계를 참조하십시오.

1. **내 스타일에 맞게 템플릿 맞춤화**

   상점은 브랜드를 나타내므로 사이트 테마에 맞게 제품 추천 템플릿을 수정하십시오.

   >[!TIP]
   >
   > 템플릿을 사용자 정의하여 스타일시트를 지정하고 페이지에서 권장 사항 단위가 나타나는 위치를 덮어쓰는 등의 작업을 수행할 수 있습니다.

   다음을 참조하십시오 [사용자 지정](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) 이 단계를 완료하는 방법을 알아보려면 개발자 설명서에서 를 참조하십시오.

1. **비프로덕션 환경에서 권장 사항 테스트**

   프로덕션에 배포하기 전에 비프로덕션 환경에서 새 기술을 테스트하는 것이 항상 모범 사례입니다. 비프로덕션 환경에서 권장 사항을 테스트하면 다양한 권장 사항 단위 유형, 위치 및 페이지로 재생할 수 있습니다. 비프로덕션 환경에서 테스트하는 동안 프로덕션에 이미 수집된 행동 데이터를 기반으로 권장 사항을 가져올 수 있으므로 권장 사항 결과는 실제 고객의 쇼핑 행동을 기반으로 합니다.

   >[!TIP]
   >
   > 비프로덕션 환경 카탈로그가 프로덕션에 있는 카탈로그와 동일한지 확인합니다. 유사한 카탈로그를 사용하면 추천 단위에서 반품된 제품이 생산 중인 제품을 가깝게 모방할 수 있습니다.

   다음을 참조하십시오 [가져오기](staging-environment.md) 이 단계를 완료하는 방법을 배울 프로덕션 환경의 동작 데이터입니다.

1. **프로덕션 스토어에 권장 사항 만들기 및 배포**

   이제 프로덕션에 행동 데이터 수집을 배포하고, 제품 권장 사항 템플릿을 수정하고, 실제 구매자 행동을 사용하여 권장 사항을 테스트했으므로 모든 코드를 프로덕션에 홍보하고, [만들기](create.md) 라이브 제품 추천
