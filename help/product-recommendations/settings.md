---
title: 설정
description: 의 소스를 변경하는 방법 알아보기 [!DNL Product Recommendations] 데이터 및 시각적 권장 사항을 활성화하는 방법.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 75ff893bf5867ededa49807835676ddf9b19adc9
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# 설정

다음을 수행하는 경우 [SaaS 데이터 공간 구성](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) Recommendations의 경우, SaaS 데이터 공간은 카탈로그 데이터와 상점 행동 데이터를 수집합니다. [Adobe Sensei](https://www.adobe.com/sensei.html) 는 해당 데이터를 분석하고 제품 Recommendations을 제공하는 데 사용되는 제품 연결을 계산합니다.

테스트 또는 스테이징을 위한 비프로덕션 환경에는 일반적으로 실제 제품 추천을 제공하는 상점 행동 데이터의 수량이나 품질이 없습니다. 규모에 따른 실제 구매자 행동은 프로덕션 환경에서만 캡처할 수 있습니다. 이 문제를 해결하기 위해 Adobe Commerce에서는 프로덕션 환경의 제품 권장 사항을 다른 비프로덕션 SaaS 데이터 공간과 함께 사용할 수 있습니다. 비프로덕션 환경에서 실제 상점 데이터를 사용하면 쇼핑객이 보는 권장 사항을 미리 보고 다양한 권장 사항 유형 및 배치 위치를 실험할 수 있습니다. 다른 SaaS 데이터 공간의 Recommendations은 쇼핑객이 미리 볼 수 있지만 클릭은 할 수 없습니다.

스테이징 주문은 스테이징을 사용하여 기록됩니다 `environmentId`. 프로덕션 데이터에는 영향을 주지 않습니다. 프로덕션 데이터는 `alternateEnvironmentId`.

>[!NOTE]
>
>REST를 통해 제품 Recommendations을 사용하는 경우 `alternateEnvironmentId` 매개 변수는 다른 데이터 공간을 지정하는 데 사용할 수 있습니다. GraphQL을 통해 Product Recommendations을 사용하는 경우 이 매개 변수를 사용할 수 없습니다.

## 권장 사항 소스 선택

제품 권장 사항 데이터의 소스를 변경하려면 사용할 동작 데이터가 있는 SaaS 데이터 공간을 선택합니다. 시작하기 전에 다음을 확인하십시오.

- Storefront 데이터 수집은 [구성 및 활성화됨](install-configure.md) 프로덕션 환경 및 [확인됨](verify.md) 해당 동작 데이터가 Adobe Commerce으로 전송되고 있습니다.
- 비프로덕션 환경 카탈로그는 기본적으로 프로덕션 카탈로그와 동일해야 합니다. 유사한 카탈로그를 사용하면 반환된 제품 추천 단위가 프로덕션 단위의 추천 단위와 거의 비슷하게 모방됩니다.

1. 비프로덕션 Adobe Commerce 환경의 관리자에 로그인합니다.

1. 다음에서 _관리자_ 사이드바, 이동 **마케팅** > _프로모션_ > **제품 Recommendations**.

1. 클릭 **설정**.

   ![제품 추천 설정](assets/settings.png)
   _설정_

1. 다음에서 _Recommendations 소스_ 섹션, 활성화 **다른 SaaS 데이터 공간에서 권장 사항 가져오기** 옵션을 선택합니다. 다음 _Recommendations 소스_ 섹션은 비프로덕션 환경에만 표시됩니다.

   의 목록 _사용 가능한 SaaS 데이터 공간_ 가 표시됩니다.

   ![제품 추천 설정](assets/settings-select-saas.png)
   _설정_

1. 사용하려는 구매자 데이터가 있는 SaaS 데이터 공간을 선택합니다.

1. 클릭 **변경 내용 저장**.

   이제 Adobe Commerce은 선택한 데이터 공간에서 권장 사항을 가져옵니다.

   >[!NOTE]
   >
   > 비프로덕션 상점 전면의 다른 SaaS 데이터 공간에서 가져온 권장 사항을 볼 수는 있지만 권장 사항을 클릭할 수는 없습니다.

### 새 SaaS 데이터 공간 구성

1. Recommendations 소스 섹션에서 **구성 편집**.

1. 지침에 따라 새 를 구성합니다 [[!DNL Commerce] 서비스](/help/landing/saas.md).

## 시각적 권장 사항 활성화

다음과 같은 경우 [Visual Product Recommendations](install-configure.md) 모듈이 설치되어 있으므로 Visual Recommendations에서 [시각적 유사성](type.md#visualsim) 권장 사항 유형.

다음에서 _Visual Recommendations_ 섹션, 설정 **Visual Recommendations 활성화** 활성 위치로 이동합니다.
