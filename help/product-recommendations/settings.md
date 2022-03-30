---
title: 설정
description: 소스 변경 방법 알아보기 [!DNL Product Recommendations] 데이터 및 시각적 권장 사항을 활성화하는 방법.
source-git-commit: 8c85d26474e371d30b76499f312553a07e329a80
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# 설정

다음 경우에 [SaaS 데이터 공간 구성](https://docs.magento.com/user-guide/configuration/services/saas.html) Recommendations의 경우 SaaS 데이터 공간은 카탈로그 데이터와 상점-행동 데이터를 수집합니다. [Adobe Sensei](https://www.adobe.com/sensei.html) 는 해당 데이터를 분석하고 제품 Recommendations을 제공하는 데 사용되는 제품 연결을 계산합니다.

일반적으로 테스트 또는 스테이징을 위한 비프로덕션 환경에는 실제 제품 추천을 제공하는 storefront 행동 데이터의 수량이나 품질이 없습니다. 규모에 맞는 실제 쇼핑객은 프로덕션 환경에서만 캡처할 수 있습니다. 이 문제를 해결하기 위해 Adobe Commerce에서는 프로덕션 환경의 제품 권장 사항을 다른 비프로덕션 SaaS 데이터 공간과 함께 사용할 수 있습니다. 비프로덕션 환경에서 실제 상점 전면 데이터를 사용하면 구매자가 보는 권장 사항을 미리 보고 다양한 권장 사항 유형 및 배치 위치를 실험할 수 있습니다. 다른 SaaS 데이터 공간의 Recommendations을 구매자가 미리 볼 수 있지만 클릭할 수는 없습니다.

## 권장 사항 소스 선택

제품 권장 사항 데이터의 소스를 변경하려면 사용할 동작 데이터로 SaaS 데이터 공간을 선택하십시오. 시작하기 전에 다음을 확인하십시오.

- Storefront 데이터 수집은 [구성 및 활성화](install-configure.md) 프로덕션 환경 및 [확인됨](verify.md) 해당 행동 데이터가 Adobe Commerce으로 전송되고 있습니다.
- 비프로덕션 환경 카탈로그는 기본적으로 프로덕션 카탈로그와 동일해야 합니다. 유사한 카탈로그를 사용하면 제품 권장 사항 단위가 프로덕션에 있는 것과 거의 유사하게 반환되도록 합니다.

1. 비프로덕션 Adobe Commerce 환경의 관리자에 로그인합니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **마케팅** > _프로모션_ > **제품 Recommendations**.

1. 클릭 **설정**.

   ![제품 추천 설정](assets/settings.png)
   _설정_

1. 에서 _Recommendations 소스_ 섹션에서 활성화 **다른 SaaS 데이터 공간에서 권장 사항 가져오기** 선택 사항입니다. 다음 _Recommendations 소스_ 섹션은 비프로덕션 환경에만 나타납니다.

   목록 _사용 가능한 SaaS 데이터 공간_ 이 나타납니다.

   ![제품 추천 설정](assets/settings-select-saas.png)
   _설정_

1. 사용하려는 구매 데이터가 있는 SaaS 데이터 공간을 선택합니다.

1. 클릭 **변경 내용 저장**.

   이제 Adobe Commerce이 선택한 데이터 공간에서 권장 사항을 가져옵니다.

   >[!NOTE]
   >
   > 비프로덕션 스토어의 다른 SaaS 데이터 공간에서 가져온 권장 사항을 볼 수 있지만 권장 사항을 클릭할 수 없습니다.

### 새로운 SaaS 데이터 공간 구성

1. Recommendations 소스 섹션에서 **구성 편집**.

1. 지침에 따라 새 [Commerce Service].

## 시각적 권장 사항 활성화

만약 [Visual Product Recommendations](install-configure.md) 모듈이 설치되어 있으면 Visual Experience Platform에서 [시각적 유사성](type.md#visualsim) 권장 사항 유형.

에서 _Visual Recommendations_ 섹션, 설정 **Visual Recommendations 활성화** 를 활성 위치에 지정합니다.
