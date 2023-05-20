---
title: 인스턴스 연결
description: API 키 및 개인 키를 사용하여 상거래 인스턴스를 연결하고 구성에 데이터 공간을 지정합니다.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# 인스턴스 연결

[!DNL Payment Services] 는 Commerce Services를 기반으로 하며 SaaS(Software as a Service)로 배포됩니다. API 키 및 개인 키를 사용하여 Commerce 인스턴스를 연결하고, 다음을 사용하여 구성의 데이터 공간을 지정합니다. [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **이 연결을 한 번만 설정했습니다.**

* 다음을 보유한 경우: *인스턴스가 이미 연결되었습니다.*, API 자격 증명을 획득 및 사용하고 Commerce Services를 구성하여 다음 작업을 수행할 수 있습니다. [테스트 샌드박스 설정](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* 그래도 *인스턴스를 연결해야 합니다.*&#x200B;에 대해서는 이 항목의 정보를 참조하십시오 [api 자격 증명 가져오기](#obtain-api-credentials) 및 [commerce 서비스 구성](#configure-commerce-services).
* 다음과 같은 경우 *인스턴스가 연결되어 있는지 확인합니다.*, 다음으로 이동 **시스템** > 서비스 > **Commerce Services 커넥터** 및 다음에서 공개 및 비공개 API 키 값 보기 [!UICONTROL Sandbox Keys] 및 [!UICONTROL Production Keys] 섹션 및 *프로젝트* 및 *데이터 공간* 의 필드 [!UICONTROL SaaS Identifier] 섹션. 해당 값이 있으면 인스턴스가 연결됩니다.

## API 자격 증명 가져오기

Commerce SaaS 서비스를 사용하려면 인스턴스에서 만들고 관리하는 샌드박스와 프로덕션에 모두 인스턴스의 API 키(Commerce 공개 API 키 및 개인 키)를 사용해야 합니다 [내 계정 대시보드](https://account.magento.com/customer/account/login). [키 쌍](https://docs.magento.com/user-guide/configuration/services/saas.html) 한 번에 한 쌍만 활발하게 사용할 수 있지만 Commerce 계정(샌드박스 계정 및 프로덕션 계정)에 대해 만들 수 있습니다.

>[!NOTE]
>
>에 액세스하는 데 도움이 필요합니다. [!UICONTROL My Account] 대시보드? 다음을 참조하십시오 [상거래 계정 만들기](https://docs.magento.com/user-guide/magento/magento-account-create.html).

공개 API 키가 생성되면 내 계정 대시보드에서 항상 사용할 수 있습니다. 필요에 따라 복사하거나 삭제할 수 있습니다. 샌드박스 또는 프로덕션용 공개 API 키를 만들면 개인 API 키가 표시됩니다. 이 키는 다음 대화 상자에서 복사하거나 저장하는 데만 사용할 수 있으며 나중에 액세스할 수 없습니다.

지정된 API 키 쌍은 환경의 모든 상거래 서비스에 대해 유효하므로 인스턴스에 대해 Commerce Services가 이미 구성되어 있는 경우 API 키 쌍이 Commerce Services 커넥터에 이미 있습니다.

API 키가 손실되면 새 API 키 쌍은 다음과 같아야 합니다. [생성됨](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) 및 [적용됨](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) (관리자)의 Commerce Services 커넥터 구성 잘못된 키가 구성되었거나 구성에 아무 것도 없는 경우, 계정이 확인되지 않았음을 알리는 계정 확인 오류 대화 상자가 결제 서비스에 나타납니다.

참조: [api를 사용하는 사용 가능한 상거래 서비스 목록](https://docs.magento.com/user-guide/system/saas.html#available-services).

샌드박스 또는 프로덕션 환경에 대한 API 키를 생성하는 방법은 를 참조하십시오. [자격 증명](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>API 키 쌍을 다시 생성하지 않는 것이 좋습니다 *및* 활성 프로덕션 인스턴스에서 SaaS 식별자 및/또는 데이터 공간을 변경합니다. 인스턴스가 수정되면 해당 인스턴스의 데이터가 손실됩니다.

## 상거래 서비스 구성

인스턴스 간에 동일한 API 키를 사용할 수 있지만 각 인스턴스는 자체 키를 가져야 합니다 [SaaS 데이터 공간](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

자격 증명을 받았으므로 SaaS 프로젝트 및 Saas 데이터 공간을 구성할 수 있습니다.

1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 클릭 **[!UICONTROL Configure Commerce Services]**.

   이 옵션은 계정에 대해 Commerce Services를 아직 구성하지 않은 경우 표시됩니다.

   관리자 의 구성 영역으로 이동합니다. **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**를 클릭하여 Commerce Services 커넥터를 구성합니다.

1. 상거래 서비스를 구성하려면 다음에 설명된 단계를 수행합니다 [SaaS 구성](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
