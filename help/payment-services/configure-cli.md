---
title: 명령줄 구성
description: 설치 후 다음을 구성할 수 있습니다. [!DNL Payment Services] 명령줄 인터페이스(CLI) 사용.
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# 명령줄 구성

설치 후 [!DNL Payment Services]에서 쉽게 구성할 수 있습니다. [홈 내](payments-home.md) 또는 CLI를 통해 실행할 수도 있습니다.

## 데이터 내보내기 구성

[!DNL Payment Services] 에서 내보낸 주문 데이터 결합 [!DNL Magento Open Source] 및 [!DNL Adobe Commerce] 유용한 보고서를 작성하기 위해 결제 공급자의 집계 결제 데이터를 사용합니다. 다음 [!DNL Payment Services] 확장은 인덱서를 사용하여 보고서에 필요한 모든 데이터를 효율적으로 수집합니다.

에 사용된 데이터에 대해 알아보려면 [!DNL Payment Services] 보고, 참조 [주문 결제 상태 보고서](order-payment-status.md#data-used-in-the-report).

### 크론 구성 [!DNL Magento Open Source]

을(를) 사용하려면 `BY SCHEDULE` 인덱스 모드 [!DNL Magento Open Source], cron 을 구성해야 합니다. 다음을 참조하십시오 [cron 구성 및 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### 인덱서 설정

주문 데이터를 내보내고 두 가지 인덱스 모드 중 하나를 사용하여 결제 서비스에서 지속합니다.`ON SAVE` (기본값) 또는 `BY SCHEDULE` (권장).

다음 색인은 다음에 대한 것입니다. [!DNL Payment Services]:

| 코드 | 이름 | 설명 |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | 판매 주문 피드 | 주문 데이터의 인덱스를 작성합니다. |
| `sales_order_status_data_exporter` | 판매 주문 상태 피드 | 판매 주문 상태 데이터의 인덱스를 작성합니다. |
| `store_data_exporter` | 피드 저장 | 스토어 데이터의 인덱스를 작성합니다. |

세 개의 모든 인덱서에 대한 인덱스 모드를 변경하려면 다음을 실행합니다.

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>명령에 인덱서를 지정하지 않으면 모든 인덱서가 동일한 값으로 업데이트됩니다. 특정 인덱서를 변경하려면 해당 인덱서를 명령에 나열해야 합니다.

인덱서의 모드를 수동으로 변경하는 방법에 대한 자세한 내용은 [인덱서 구성](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} in the developer documentation. To learn how to change it in the Admin, see [Index management](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} ( 핵심 사용 안내서)를 참조하십시오.

### 수동으로 데이터 다시 인덱싱

데이터가 자동으로 발생할 때까지 기다리지 않고 수동으로 데이터를 다시 인덱싱할 수 있습니다. 다음을 참조하십시오 [색인 재지정](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Manage the Indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} 추가 정보.

날짜 `BY SCHEDULE` 모드가 설정되면 시스템이 변경된 엔티티를 추적하고 cron 작업이 설정된 일정에 따라 변경된 엔티티에 대한 인덱스를 업데이트합니다. 다음을 참조하십시오 [명령줄에서 cron 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) 위치: [cron 구성 및 실행](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) cron 작업을 사용하여 색인화를 수동으로 트리거하는 방법에 대해 알아봅니다.

### 재인덱싱된 데이터를 결제 서비스로 보내기

데이터가 인덱싱되면 자동으로 로 전송됩니다. [!DNL Payment Services]. 다음 명령을 사용하여 인덱싱된 데이터를 전송하는 프로세스를 수동으로 트리거할 수도 있습니다.

```bash
bin/magento saas:resync --feed [feedName]
```

다음 명령 옵션을 사용합니다.

| 명령 | 설명 |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | 지정된 피드의 색인 재지정을 수행하고 해당 서비스로 보냅니다. |
| `bin/magento saas:resync --no-reindex` | 인덱싱을 건너뛰고 인덱스에서 동기화되지 않은 데이터를 보냅니다. |

다음 `--feed` 매개 변수를 사용하면 전송할 피드를 지정할 수 있습니다.

| 피드 | 설명 |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | 프로덕션 모드의 주문 피드 |
| `paymentServicesOrdersSandbox` | 샌드박스 모드의 주문 피드 |
| `paymentServicesOrderStatusesProduction` | 프로덕션 모드의 주문 상태 |
| `paymentServicesOrderStatusesSandbox` | 샌드박스 모드의 주문 상태 |
| `paymentServicesStoresProduction` | 프로덕션 모드로 저장 |
| `paymentServicesStoresSandbox` | 샌드박스 모드로 저장 |

보고서에 필요한 모든 데이터가 (으)로 전송됩니다 [!DNL Payment Services] cron 이 구성되고 설치된 경우 자동으로 표시됩니다. cron 데이터를에 전송하는 프로세스를 수동으로 트리거할 수도 있습니다 [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

리인덱싱 및 인덱서에 대한 자세한 내용은 [인덱서 관리](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) 개발자 설명서의 항목입니다.
