---
title: Adobe Experience Platform에 쇼퍼 프로필 업로드
description: 쇼퍼 프로필을 Adobe Experience Platform에 업로드하는 방법을 알아봅니다.
exl-id: fd0ee7fa-5274-4640-ba00-bcb2ec78f314
source-git-commit: 9bf28159fdac3a7237956a536f6a522b4e2918fe
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Adobe Experience Platform에 쇼퍼 프로필 업로드

Adobe Commerce 가맹점은 고객 프로필 데이터를 [실시간 고객 프로필](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html): Adobe Experience Platform의 일부입니다. 프로필을 사용하면 고객 데이터를 통합 보기로 통합하여 모든 고객 상호 작용에 대해 실행 가능하고 타임스탬프가 지정된 계정을 제공할 수 있습니다.

>[!NOTE]
>
> 프로필 데이터에는 쇼핑객과 상점 행동 데이터 간의 링크가 만들어지는 방식이므로 이메일 주소가 포함되어야 합니다.

쇼핑객의 프로필을 업로드하면 쇼핑객이 사이트에서 수행하는 상호 작용과 관련된 이벤트 데이터가 Experience Platform 커넥터를 통해 프로필로 전송되고 해당 쇼핑객의 프로필에 연결됩니다.

>[!NOTE]
>
> 다음 `createAccount` [storefront 이벤트](events.md) 은 프로필에서 고객 프로필을 자동으로 생성하지 않습니다. 이것은 보안상의 이유로 제한되며 의도적입니다.

이 항목에서는 Adobe Commerce 고객 프로필을 Experience Platform의 실시간 고객 프로필에 업로드하는 방법을 알아봅니다.

1. 고객 데이터를 저장하는 위치를 결정합니다. 일부 판매자의 경우 이 데이터는 Adobe Commerce에 저장되며 [내보낸](https://docs.magento.com/user-guide/system/data-export.html) CSV 파일로 내보낼 때 시간별 세부기간이 작동하지 않는 문제를 해결했습니다. 다른 사용자의 경우 별도의 CRM(고객 관계 관리) 시스템에 있을 수 있습니다.

1. 고객 데이터를 저장하는 위치를 결정한 후 적절한 를 찾습니다 [소스 커넥터](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) 고객 데이터가 저장되는 위치를 기반으로 합니다. 적절한 소스 커넥터가 표시되지 않으면 [로컬 파일 업로드](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) 커넥터를 사용하여 CSV 파일에서 쇼퍼 프로필을 가져옵니다.

   >[!NOTE]
   >
   > 로컬 파일 업로드 커넥터를 사용하는 경우 **프로필 데이터 세트** 옵션 [데이터 세트 정의](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). 데이터 세트를 프로필 데이터로 식별합니다.

프로필에서 쇼퍼 프로필을 만들면 해당 구매자와 연결된 모든 상점 데이터는 해당 프로필과 연결됩니다.

## 자주 프로필 업로드

향상된 구매자 경험을 만들려면 프로필 데이터를 정기적으로 가져와야 합니다. 일부 소스 커넥터를 사용하면 일정에 따라 프로필 데이터를 가져올 수 있습니다.
