---
title: 백그라운드 프로세스 구성
description: "다음에 대한 일정 구성 [!DNL Store Fulfillment] 데이터를 이행 서비스와 동기화하는 데 사용되는 백그라운드 프로세스입니다."
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# 백그라운드 프로세스 구성

Store Fulfillment 통합에서는 최적의 성능과 확장을 위해 백그라운드 프로세스와 메시지 대기열을 사용합니다. 다음을 사용하여 Adobe Commerce 스토어를 위한 환경 구축 [배포 변수](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 자동으로 시작 [메시지 대기열 실행자](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

백그라운드 프로세스는 표준 Adobe Commerce을 사용하여 관리됩니다 [예약된 작업](https://docs.magento.com/user-guide/system/cron.html) 기능. 이러한 프로세스는 주문 및 가맹점 구성 데이터를 매장 이행 웹 서비스와 동기화하는 역할을 합니다.

## 스토어 이행 예약 작업 관리

관리에서 로 이동합니다. **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

스토어 이행 서비스에 대한 기본 구성을 검토하십시오. 주문 처리 볼륨 및 리소스 가용성에 따라 이러한 설정을 조정해야 할 수 있습니다.
