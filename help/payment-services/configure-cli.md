---
title: 명령줄 구성
description: 설치 후 다음을 구성할 수 있습니다 [!DNL Payment Services] 명령줄 인터페이스(CLI) 사용
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 명령줄 구성

설치 후 [!DNL Payment Services]에서 쉽게 구성할 수 있습니다. [집 안에서](payments-home.md) 또는 CLI(명령줄 인터페이스)를 통해

## 데이터 내보내기 구성

[!DNL Payment Services] 에서 내보낸 주문 데이터를 결합합니다. [!DNL Magento Open Source] 및 [!DNL Adobe Commerce] 결제 제공자의 결제 데이터를 집계하여 유용한 보고서를 만들 수 있습니다. 다음 [!DNL Payment Services] 확장은 인덱서를 사용하여 보고서에 필요한 모든 데이터를 효율적으로 수집합니다.

에 사용된 데이터에 대해 알아보려면 [!DNL Payment Services] 보고, [주문 결제 상태 보고서](order-payment-status.md#data-used-in-the-report).

### 크론 구성 [!DNL Magento Open Source]

를 사용하려면 `BY SCHEDULE` 인덱스 모드 [!DNL Magento Open Source]로 지정하는 경우 cron을 구성해야 합니다. 자세한 내용은 [크론 구성 및 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### 인덱스 설정

두 가지 인덱스 모드 중 하나를 사용하여 주문 데이터를 내보내고 결제 서비스에서 유지됩니다.`ON SAVE` (기본값) 또는 `BY SCHEDULE` (권장)

다음 색인은 [!DNL Payment Services]:

| 코드 | 이름 | 설명 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 판매 주문 피드 | 주문 데이터의 인덱스를 만듭니다. |
| `sales_order_status_data_exporter` | 판매 주문 상태 피드 | 판매 주문 상태 데이터의 인덱스 작성 |
| `store_data_exporter` | 저장소 피드 | 저장소 데이터의 인덱스를 만듭니다. |

세 인덱스 모두에 대한 인덱스 모드를 변경하려면 다음을 실행하십시오.

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>명령에 인덱서를 지정하지 않으면 모든 인덱서가 동일한 값으로 업데이트됩니다. 특정 색인을 변경하려면 명령에 나열해야 합니다.

인덱서의 모드를 수동으로 변경하는 방법에 대한 자세한 내용은 [인덱서 구성](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} in the developer documentation. To learn how to change it in the Admin, see [Index management](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} 를 참조하십시오.

### 수동으로 데이터 다시 색인화

데이터가 자동으로 재색인화되기를 기다리는 대신 수동으로 다시 색인화할 수 있습니다. 자세한 내용은 [다시 색인화](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Manage the Indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} 추가 정보.

When `BY SCHEDULE` 모드가 설정되면, 시스템에서 변경된 엔티티를 추적하고 cron 작업은 설정된 일정에 따라 인덱스를 업데이트합니다. 자세한 내용은 [명령줄에서 cron 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [크론 구성 및 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) cron 작업을 사용하여 색인을 수동으로 트리거하는 방법을 알아봅니다.

### 다시 인덱싱된 데이터를 결제 서비스로 보내기

데이터가 색인화되면 자동으로 [!DNL Payment Services]. 다음 명령을 사용하여 인덱싱된 데이터를 전송하는 프로세스를 수동으로 트리거할 수도 있습니다.

```bash
bin/magento saas:resync --feed [feedName]
```

다음 명령 옵션을 사용합니다.

| 명령 | 설명 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 지정된 피드의 색인 재지정을 수행하고 해당 서비스에 보냅니다 |
| `bin/magento saas:resync --no-reindex` | 인덱스를 건너뛰고 인덱스에서 동기화되지 않은 데이터를 보냅니다. |

다음 `--feed` 매개 변수를 사용하면 전송할 피드를 지정할 수 있습니다.

| 피드 | 설명 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 프로덕션 모드의 주문 피드 |
| `paymentServicesOrdersSandbox` | 샌드박스 모드에서 피드 주문 |
| `paymentServicesOrderStatusesProduction` | 프로덕션 모드의 주문 상태 |
| `paymentServicesOrderStatusesSandbox` | 샌드박스 모드의 상태 순서 지정 |
| `paymentServicesStoresProduction` | 프로덕션 모드로 저장 |
| `paymentServicesStoresSandbox` | 샌드박스 모드로 저장 |

보고서에 필요한 모든 데이터를에 보냅니다 [!DNL Payment Services] cron이 구성 및 설치된 경우 자동으로. 에 클라우드 데이터를 전송하는 프로세스를 수동으로 트리거할 수도 있습니다 [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

색인 재지정 및 색인에 대한 자세한 내용은 [인덱서 관리](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 개발자 설명서의 항목.
