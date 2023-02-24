---
title: 저장소 이행 솔루션 연결
description: Adobe Commerce 통합을 만들고 인증하고 Store Fulfillment 계정 자격 증명을 Adobe Commerce 서비스 구성에 추가하여 Adobe Commerce과 Store Fulfillment 솔루션 간의 연결을 설정합니다.
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 저장소 이행 솔루션 연결

필요한 인증 자격 증명 및 연결 데이터를 Adobe Commerce Admin에 추가하여 Store Fulfillment Services와 Adobe Commerce을 연결합니다.

- **[구성 [!DNL Commerce integration settings]](#create-the-commerce-integration)**-Store Fulfillment Services에 대한 Adobe Commerce 통합을 만들고 액세스 토큰을 생성하여 Store Fulfillment 서버에서 들어오는 요청을 인증합니다.

- **[Store Fulfillment Services에 대한 계정 자격 증명 구성](#configure-store-fulfillment-account-credentials)**-자격 증명을 추가하여 Adobe Commerce을 저장소 이행 계정에 연결합니다.

>[!NOTE]
>
>테스트를 시작하기 전에 연결 구성을 완료하고 연결을 확인합니다.

## Adobe Commerce 통합 만들기

Adobe Commerce을 Store Fulfillment 서비스와 통합하려면 Commerce 통합을 생성하고 Store Fulfillment 서버의 요청을 인증하는 데 사용할 수 있는 액세스 토큰을 생성합니다.

1. 관리자에서 Store Fulfillment용 통합을 만듭니다.

   - 확장 이름을 지정합니다
   - 이메일 주소를 입력합니다
   - Admin 계정 암호를 입력합니다

1. 구성 [!UICONTROL API Resource Access permissions] 통합에 대해—을 선택합니다. `[!UICONTROL All]`

1. 통합을 저장하고 활성화하여 인증에 대한 액세스 토큰을 생성합니다.

1. 액세스 토큰을 복사하여 안전한 암호화된 위치에 저장합니다.

1. 계정 관리자와 함께 저장소 이행 측에서 구성을 완료하고 통합을 승인합니다.


>[!NOTE]
>
>자세한 지침은 [통합](https://docs.magento.com/user-guide/system/integrations.html) 에서 _Adobe Commerce 사용 안내서_.

## 저장소 이행 계정 자격 증명 구성

흡입 양식을 완료하면 Walmart Store Fulfillment 계정이 생성됩니다. 자격 증명이 있으면 다음 자격 증명을 받을 수 있습니다.

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (일반적으로 위의 구성과 동일함)

이러한 자격 증명은 Store Fulfillment를 구성하고 사용하는 데 필요합니다.

>[!NOTE]
>
>계정 생성 프로세스를 완료하는 데 시간이 걸릴 수 있습니다. 자격 증명을 기다리는 동안 [저장소 이행 솔루션의 다른 설정을 검토하고 구성합니다.](service-config-settings-overview.md).

### 자격 증명을 추가하여 저장 이행

1. 구성 [계정 자격 증명](enable-general.md) 프로덕션 및 샌드박스 환경

1. 관리자에서 로 이동합니다. **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. 에 제공된 계정 자격 증명을 입력합니다. **[!UICONTROL Production environment]**. 모든 필드가 필요합니다.

1. 선택 **[!UICONTROL Save Config]**.

1. 을 선택하여 연결을 테스트합니다 **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>자격 증명이 올바르지 않으면 각 환경에 올바른 값을 입력했는지 확인하고 유효성을 다시 확인합니다. 연결에 문제가 있으면 계정 담당자에게 문의하십시오.
