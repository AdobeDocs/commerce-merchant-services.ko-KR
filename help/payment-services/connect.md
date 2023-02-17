---
title: 인스턴스 연결
description: API 키 및 개인 키를 사용하여 상거래 인스턴스를 연결하고 구성에 데이터 공간을 지정합니다.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 5aba246ce2a7802954a90c08c7dac2247a71ff6d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# 인스턴스 연결

[!DNL Payment Services] 는 Commerce Services를 기반으로 하여 SaaS(Software as a Service)로 배포됩니다. API 키 및 개인 키를 사용하여 상거래 인스턴스를 연결하고, [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **이 연결을 한 번만 설정합니다.**

* 만약 *인스턴스가 이미 연결됨*, API 자격 증명을 획득하고 사용하고 Commerce Services를 구성하여 다음 작업을 진행할 수 있습니다 [테스트 샌드박스 설정](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* 그래도 *인스턴스를 연결해야 함*&#x200B;에 대해서는 이 항목의 정보를 참조하십시오 [API 자격 증명 가져오기](#obtain-api-credentials) 및 [commerce Services 구성](#configure-commerce-services).
* 만약 *인스턴스가 연결되었는지 확실하지 않음*, 다음 위치로 이동합니다. **시스템** > 서비스 > **Commerce Services 커넥터** 및에서 공개 및 개인 API 키 값을 봅니다. [!UICONTROL Sandbox Keys] 및 [!UICONTROL Production Keys] 섹션 및 *프로젝트* 및 *데이터 공간* 의 필드 [!UICONTROL SaaS Identifier] 섹션을 참조하십시오. 해당 값이 있으면 인스턴스가 연결됩니다.

## API 자격 증명 가져오기

Commerce SaaS 서비스를 사용하려면 샌드박스 및 프로덕션 모두에 인스턴스의 API 키(Commerce Public API 키 및 개인 키)를 사용해야 하며, 이 키는 사용자 내에서 생성 및 관리됩니다 [내 계정 대시보드](https://account.magento.com/customer/account/login). [키 쌍](https://docs.magento.com/user-guide/configuration/services/saas.html) 한 번에 한 쌍만 능동적으로 사용할 수 있지만, 샌드박스 1개와 프로덕션용 1개씩 상거래 계정에 대해 만들 수 있습니다.

>[!NOTE]
>
>액세스 관련 도움말 필요 [!UICONTROL My Account] 대시보드? 자세한 내용은 [상거래 계정 만들기](https://docs.magento.com/user-guide/magento/magento-account-create.html).

만든 공개 API 키는 항상 내 계정 대시보드에서 사용할 수 있습니다. 필요에 따라 복사하거나 삭제할 수 있습니다. 개인 API 키는 샌드박스 또는 프로덕션에 대한 공개 API 키를 만들 때 표시됩니다. 다음 대화 상자에서 복사 또는 저장에만 사용할 수 있으며 나중에 액세스할 수 없습니다.

지정된 API 키 쌍은 환경의 모든 Commerce Services에 대해 유효하므로, 인스턴스에 대해 Commerce Services가 이미 구성되어 있다면 API 키 쌍이 이미 Commerce Services 커넥터에 있습니다.

API 키가 손실된 경우 새 API 키 쌍은 [생성](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 및 [적용됨](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) ( 관리자의 Commerce Services Connector 구성 참조). 잘못된 키가 구성되거나 구성에 아무 것도 없는 경우, 계정이 확인되지 않았음을 알리는 계정 확인 오류 대화 상자가 지급 서비스에 나타납니다.

다음을 참조하십시오 [API를 사용하는 사용 가능한 상거래 서비스 목록](https://docs.magento.com/user-guide/system/saas.html#available-services).

샌드박스 또는 프로덕션 환경용 API 키를 생성하는 방법에 대해 알아보려면 [자격 증명](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>API 키 쌍을 다시 생성하지 않는 것이 좋습니다 *및* 활성 프로덕션 인스턴스에서 SaaS 식별자 및/또는 데이터 공간을 변경합니다. 수정된 경우 인스턴스에 대한 데이터가 손실됩니다.

## Commerce Services 구성

동일한 API 키를 여러 인스턴스에 사용할 수 있지만 각 인스턴스에는 고유한 API 키가 있어야 합니다 [SaaS 데이터 공간](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

자격 증명을 획득했으므로 SaaS 프로젝트 및 Saas 데이터 공간을 구성할 수 있습니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 클릭 **[!UICONTROL Configure Commerce Services]**.

   이 옵션은 계정에 대해 Commerce Services를 아직 구성하지 않은 경우 표시됩니다.

   관리자의 구성 영역으로 이동됩니다. **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**를 입력하여 Commerce Services Connector를 구성하십시오.

1. 상거래 서비스를 구성하려면 다음 단계에 설명된 단계를 수행합니다. [SaaS 구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
