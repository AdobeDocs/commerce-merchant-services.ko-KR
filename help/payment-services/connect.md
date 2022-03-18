---
title: 인스턴스 연결
description: API 키 및 개인 키를 사용하여 상거래 인스턴스를 연결하고 구성에 데이터 공간을 지정합니다.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# 인스턴스 연결

[!DNL Payment Services] 는 Commerce Services를 기반으로 하여 SaaS(Software as a Service)로 배포됩니다. API 키 및 개인 키를 사용하여 상거래 인스턴스를 연결하고 구성에 데이터 공간을 지정합니다. 이 연결을 한 번만 설정합니다.

자세한 내용은 [Commerce Services 커넥터](https://docs.magento.com/user-guide/system/saas.html)이 서비스에 대한 자세한 내용은 핵심 사용 안내서의 {target=&quot;_blank&quot;} 를 참조하십시오.

## API 자격 증명 가져오기

Commerce SaaS 서비스를 사용하려면 인스턴스에서 만들고 관리하는 인스턴스의 API 키를 사용해야 합니다 [내 계정 대시보드](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}. 한 번에 한 쌍만 능동적으로 사용할 수 있지만, 한 Commerce 계정에 대해 두 개의 다른 API 키 쌍을 만들 수 있습니다(샌드박스 하나와 프로덕션(라이브 지급)용으로 한 쌍만 만들 수 있음).

>[!NOTE]
>
>액세스 관련 도움말 필요 [!UICONTROL My Account] 대시보드? 자세한 내용은 [상거래 계정 만들기](https://docs.magento.com/user-guide/magento/magento-account-create.html)핵심 사용 안내서의 {target=&quot;_blank&quot;}.

주어진 API 키 쌍은 환경의 모든 Commerce Services에 대해 유효하므로, 상거래 인스턴스에 대해 Commerce Services가 이미 구성되어 있다면 API 키 쌍이 이미 관리자에게 표시됩니다. 개인 API 키가 손실되면 관리자의 상거래 서비스 구성에 새 API 키 쌍을 생성하고 적용해야 합니다.

샌드박스 또는 프로덕션 환경용 API 키를 생성하는 방법에 대해 알아보려면 [Commerce Services 커넥터](https://docs.magento.com/user-guide/system/saas.html)핵심 사용 안내서의 {target=&quot;_blank&quot;}.

>[!IMPORTANT]
>
>API 키 쌍을 다시 생성하고 SaaS 식별자를 변경하면 이 인스턴스에서 사용하는 모든 커머스 서비스가 다른 데이터 저장소에 연결되고 이전에 저장된 데이터 포함)에 액세스할 수 없습니다. API 키 쌍을 재생성하지 않고 활성 프로덕션 인스턴스에서 SaaS 식별자를 변경하는 것이 좋습니다.

### 상거래 API 키 및 개인 키

일부 Adobe Commerce 및 Magento Open Source 기능은 Commerce Services라고 하는 SaaS(Software as a Service)로 배포됩니다. 이러한 서비스를 사용하려면 API 키 및 개인 키를 사용하여 상거래 인스턴스를 이러한 서비스에 연결하고, [구성](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}.

MageID로 식별되는 상거래 계정을 만들 때 상거래 API 키 및 개인 키를 생성할 수 있습니다. 다음과 같은 Commerce Services를 사용하려면 [!DNL Payment Services], [!DNL Product Recommendations], 또는 [!DNL Live Search]를 지정하는 경우, 자격 소유자가 자격 검증을 전달하려면 이러한 키를 생성해야 합니다. 그런 다음 라이센스 보유자를 대신하여 프로젝트 및 환경을 관리하는 시스템 통합자 또는 개발 팀에 이러한 키를 전달할 수 있습니다. 솔루션 통합자인 경우 이러한 서비스를 직접 필요에 따라 사용할 수도 있습니다. 이 경우 상거래 파트너 계약의 서명자는 키를 생성해야 합니다.

### API 키 및 개인 키 생성

1. 다음 위치에서 상거래 계정에 로그인합니다. [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. 아래에 **[!UICONTROL Magento]** 탭, 선택 **[!UICONTROL API Portal]** 클릭합니다.
1. 에서 _[!UICONTROL Environment]_메뉴, 선택&#x200B;**[!UICONTROL Sandbox]**, 그런 다음&#x200B;**[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >API 키는 두 환경에 모두 필요합니다.

1. 에 이름을 입력합니다. _[!UICONTROL API Keys]_섹션을 클릭하고&#x200B;**[!UICONTROL Add New]**.

   새 키를 다운로드하는 대화 상자가 열립니다.

   >[!IMPORTANT]
   >
   >이 대화 상자는 키를 복사하거나 다운로드할 수 있는 유일한 기회입니다.

1. 클릭 **[!UICONTROL Download]** 을 클릭한 다음 **[!UICONTROL Cancel]**.

   다음 _[!UICONTROL API Keys]_이제 섹션에 API 키가 표시됩니다.

1. SaaS 프로젝트를 선택하거나 만들 때 API 키와 개인 키를 모두 복사합니다.

   자세한 내용은 [SaaS](https://docs.magento.com/user-guide/system/saas.html)자세한 내용은 핵심 사용 안내서의 {target=&quot;_blank&quot;} 를 참조하십시오.

동일한 API 키를 여러 인스턴스에 사용할 수 있지만 각 인스턴스에는 고유한 SaaS 데이터 공간이 있어야 합니다.

SaaS 프로젝트를 만들 때, Commerce는 상거래 라이센스에 따라 하나 이상의 SaaS 데이터 공간을 생성합니다.

* Adobe Commerce - 하나의 프로덕션 데이터 공간 두 개의 테스트 데이터 공간
* Magento Open Source - 하나의 프로덕션 데이터 공간 데이터 공간 테스트 안 함

### SaaS 프로젝트 구성

>[!NOTE]
>
>이 표시되지 않으면 _[!UICONTROL Commerce Services Connector]_전자 상거래 구성의 섹션에서 원하는 전자 상거래 서비스에 대한 전자 상거래 모듈을 설치해야 합니다(예: ). [[!DNL Payment Services]](install.md).

SaaS 프로젝트를 선택하거나 만들려면 스토어에 대한 상거래 라이선스 홀더에서 상거래 API 키를 요청합니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. 왼쪽 패널에서 를 확장합니다. **[!UICONTROL Services]** 및 **[!UICONTROL Commerce Services Connector]**.
1. 에서 _[!UICONTROL API Keys]_섹션에서 키 값을 붙여넣습니다.

   >[!IMPORTANT]
   >
   >두 가지 모두에 대한 키 값 추가 **[!UICONTROL sandbox]** 및 **[!UICONTROL production]** 환경.

1. 클릭 **[!UICONTROL Save Config]**.

   저장할 때 API 키와 연결된 SaaS 프로젝트가 있으면 해당 프로젝트가 _[!UICONTROL SaaS Project]_의 필드_[!UICONTROL SaaS Identifier]_ 섹션을 참조하십시오.

1. SaaS 프로젝트가 없는 경우 **[!UICONTROL Create Project]**. 그런 다음 SaaS 프로젝트의 이름을 **[!UICONTROL Project Name]** 필드.
1. 상거래 저장소의 현재 구성에 사용하려면 **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>내 계정의 API 포털 섹션에서 키를 다시 생성하는 경우 관리 구성에서 API 키를 즉시 업데이트합니다. 새 키를 생성하고 관리자에서 해당 키를 업데이트하지 않으면 SaaS 확장이 더 이상 작동하지 않으며 중요한 데이터를 잃게 됩니다.

을 클릭하여 이름을 변경할 수 있습니다 **[!UICONTROL Rename this Project]** 또는 **[!UICONTROL Rename Data Space]** 각 단추.

## Commerce Services 구성

온보딩의 첫 번째 단계 [!DNL Payment Services] 는 관리자에서 상거래 서비스를 구성하는 것입니다.

1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. 클릭 **[!UICONTROL Configure Commerce Services]**.

   이 옵션은 계정에 대해 Commerce Services를 아직 구성하지 않은 경우 표시됩니다.

   관리자의 구성 영역으로 이동됩니다. **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**를 입력하여 Commerce Services Connector를 구성하십시오.

1. 상거래 서비스를 구성하려면 다음 단계에 설명된 단계를 수행합니다. [상거래 서비스](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}.
