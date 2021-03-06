---
title: '"저장 지원 이행 워크플로우"'
description: '"스토어 지원 앱에서 사용할 수 있는 선택, 단계, 핸드오프 및 주문 모듈에 대해 알아봅니다. 이러한 모듈은 BOPIS 주문에 대해 전체 저장소 이행 워크플로우를 활성화합니다. Store Associates는 이러한 모듈을 사용하여 고객을 위한 스토어 픽업 주문을 관리하고 제공합니다."'
role: User
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# 저장 지원 이행 워크플로우

Store Assist 앱에서는 Store Associates와 네 개의 모듈을 함께 제공하여 온라인 구매와 매장 주문 구매를 위한 매장 내 이행 프로세스를 관리합니다.

- **[선택](#pick-module)**- 모든 주문된 품목과 공구를 전체 가시성을 통해 적합한 품목과 적절한 수량을 선택했는지 확인합니다. Store Associate는 효율성을 높이기 위해 하나 또는 여러 개의 주문을 동시에 선택할 수 있습니다.

- **[단계](#stage-module)**- Store Associates에서 주문 핸드오프에 대한 주문을 쉽게 찾을 수 있도록 고객이 스토어로 이동하는 동안 주문이 이루어지는 위치를 입력합니다

- **[손 끄기](#hand-off-module)**—고객이 스토어에 도착한 후 실시간 알림을 수신하여 대기 시간 및 주문 핸드오프를 원활하게 수행할 수 있습니다

- **[주문](#orders-module)**- 모든 사람이 각 주문의 주문 수와 상태를 알 수 있도록 스토어에 대해 수행한 모든 주문 목록을 확인합니다.

>[!NOTE]
>
>Store Associates에서 Store Assist 앱을 사용하려면 관리자가 먼저 [앱 설정 프로세스](app-setup.md).

## 선택 모듈

Pick 모듈은 Associate가 고객이 주문한 품목을 검색하고 스캔하여 수거하도록 도와줍니다. 얼마나 많은 주문이 지연되었는지 보고 즉시 주문을 받기 시작합니다. 먼저 선택할 다른 주문을 선택할 수도 있습니다. 주문은 연체 주문이 먼저 이루어진 납품 만기 시간별로 정렬됩니다. Store Associates는 작업에 필요한 순서대로 어떤 주문을 선택할지 선택할 수 있습니다.

제휴사는 한 번에 하나의 주문이나 동시에 여러 주문을 선택하도록 선택할 수도 있습니다.

피킹 시, 저장소는 카탈로그의 각 주문, 수량, 가격 및 제품 설명에 대해 피킹할 모든 품목 목록을 표시합니다. 주문을 선택하는 동안 스토어 지원 내에서 탐색하는 데 도움이 되는 진행률 표시줄이 표시됩니다.

동료가 피킹을 시작하고 선택할 품목을 선택하면 다음과 같은 모든 관련 품목 정보가 표시됩니다. 크기, 색상, 수량, 가격, 설명, 맞춤, SKU/UPC 연관에는 주문을 선택할 때 사용할 수 있는 두 가지 작업이 있습니다.

- 항목을 찾을 수 없음을 표시하고 환불을 트리거합니다.
- 항목의 바코드를 스캔합니다. 스캔의 목적은 그들이 올바른 항목을 선택했는지 확인하는 것입니다. 카메라가 바코드를 읽을 수 없는 경우 스토어 연결에서 선택한 항목의 SKU를 수동으로 입력해야 합니다.

동료가 항목을 찾을 수 없으면 건너뛰고 나중에 다시 찾을 수 있습니다.  위에서 언급한 환불은 주문 단계인 출고 지시 단계를 완료하기만 하면 됩니다.

## 스테이지 모듈

단계 모듈은 고객이 도착하여 주문이 접수될 때까지 포장된 주문이 배치되는 위치를 보여줍니다. 이 위치를 설정하는 것은 store associates가 고객이 도착하기 전에 근무조를 완료할 때 또는 주문이 많은 경우 주문 분실을 방지하기 위한 주요 단계입니다. 어느 경우든지, 이 서비스는 관련된 모든 정보를 이용하여 올바른 주문을 신속하게 찾을 수 있도록 설계되었습니다.

자유 양식 텍스트 막대를 사용하여 순서가 지정된 위치를 표시할 수 있습니다. 카운터 아래, 뒷방 또는 B3 위치에 있는 모든 작업을 기준으로 합니다.

동료가 다른 위치에 배치해야 하는 경우 앱의 스테이징 위치를 쉽게 업데이트할 수도 있습니다.

## 핸드오프 모듈

다음 [!UICONTROL Hand Off] 모듈은 고객이 주문 수신을 위해 체크인한 고객 및 주문이 스테이징되어 대기하는 위치를 보여줍니다. 고객은 상점 또는 외부/경부 주차장에서 주문을 받을 수 있습니다. 정확한 위치에 대한 정보는 체크 인된 후 이 모듈에 표시됩니다.

고객이 핸드오프할 준비가 된 주문을 선택하면 찾지 못한 품목, 고객 대기 위치, 대기 시간, 주문이 준비된 위치 및 가능한 경우 고객 전화 번호를 포함한 주문 정보를 모든 사람이 볼 수 있습니다.

고객이 주문을 받을 다른 사람을 선택했을 수도 있습니다. 이 경우 주문을 선택할 사람의 이름과 연락처 정보가 표시됩니다.

주문을 고객에게 제공하면, Store Associate는 주문을 수락하거나 특정 품목을 거부해야 합니다. 고객이 만족하면, 회사에서 서명을 요구하는 경우, 동료 장치의 주문에 서명해야 합니다.

고객이 체크인하지 않고 도착하면, 제휴사는 수동으로 체크인할 수 있습니다.

## 주문 모듈

주문 모듈은 모든 기존 주문 및 해당 상태를 표시합니다. 고객이 주문 확인을 호출하면 Store Associates에서 주문 모듈에서 번호를 조회하거나 검색하여 정보를 빠르게 찾을 수 있습니다.
