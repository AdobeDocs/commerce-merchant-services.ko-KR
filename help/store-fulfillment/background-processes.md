---
title: 백그라운드 프로세스
description: '"에 대한 일정 구성 [!DNL Store Fulfillment] 데이터를 이행 서비스와 동기화하는 데 사용되는 백그라운드 프로세스"                   '
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 백그라운드 프로세스 구성

Store Fulfillment 통합에서는 최적의 성능과 확장을 위해 백그라운드 프로세스와 메시지 대기열을 사용합니다. 다음을 사용하여 Adobe Commerce 스토어를 위한 환경 구축 [배포 변수](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) 자동으로 시작됩니다 [메시지 큐 주자](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

백그라운드 프로세스는 표준 Adobe Commerce을 사용하여 관리됩니다 [예약된 작업](https://docs.magento.com/user-guide/system/cron.html) 기능을 사용할 수 있습니다. 이러한 프로세스는 주문 및 머천트 스토어 구성 데이터를 스토어 이행 웹 서비스와 동기화해야 합니다.

## 저장소 이행의 예약된 작업 관리

관리자에서 로 이동합니다. **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks)> Cron configuration options for group:store_fulfillment]**.


Store Fulfillment 서비스의 기본 구성을 검토합니다. 주문 처리 볼륨 및 리소스 가용성에 따라 이러한 설정을 조정해야 할 수 있습니다.


