---
title: Adobe Experience Platform에 상거래 데이터 연결
description: 상거래 데이터를 Adobe Experience Platform에 연결하는 방법을 알아봅니다.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Experience Platform에 상거래 데이터 연결

Experience Platform 커넥터를 설치하면 **시스템** 메뉴 아래의 **서비스** 상거래 _관리_.

- Commerce Services 커넥터
- Experience Platform 커넥터

Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결하려면 Commerce Services 커넥터로 시작한 다음 Experience Platform 커넥터로 완료하면서 두 커넥터를 구성해야 합니다.

## Commerce Services 커넥터 업데이트

이전에 Adobe Commerce 서비스를 설치한 경우에는 이미 상거래 서비스 커넥터를 구성했을 수 있습니다. 그렇지 않은 경우, [Commerce Services 커넥터](../landing/saas.md) 페이지:

1. 전자 상거래 계정에 다음 위치에 로그인합니다. [프로덕션 및 샌드박스 API 키 검색](../landing/saas.md#credentials).
1. 선택 [SaaS 데이터 공간](../landing/saas.md#saas-configuration).
1. Adobe 계정에 다음 위치에 로그인합니다. [조직 ID 검색](../landing/saas.md#ims-organization-optional).

Commerce Services 커넥터를 구성한 후 Experience Platform 커넥터를 구성합니다.

## Experience Platform 커넥터 업데이트

이 섹션에서는 조직 ID를 사용하여 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. 그런 다음 Experience Platform 에지로 전송할 데이터 유형(storefront 또는 back office)을 지정할 수 있습니다.

![Experience Platform 커넥터 구성](assets/epc-config-dc.png)

## 일반

1. 에서 Adobe 계정에 로그인합니다. [Commerce Services 커넥터](../landing/saas.md#organizationid) 조직 ID를 선택합니다.

   >[!NOTE]
   >
   >이전에 Commerce Services 커넥터를 구성한 경우 조직 ID가 이미 선택되었으므로 이 단계를 건너뛸 수 있습니다.

1. 관리에서 **시스템** > 서비스 > **Experience Platform 커넥터**.

1. 에서 **범위** 드롭다운에서 컨텍스트를 로 설정합니다. **웹 사이트**.

1. 에서 **조직 ID** 필드에서 구성한 대로 Adobe Experience Platform 계정과 연결된 ID를 확인합니다. [Commerce Services 커넥터](../landing/saas.md#organizationid). 조직 ID는 글로벌입니다. Adobe Commerce 인스턴스당 하나의 조직 ID만 연결할 수 있습니다.

1. (선택 사항) 이미 [AEP 웹 SDK(합금)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 사이트에 배포되어 있는 경우 확인란을 활성화하고 AEP 웹 SDK의 이름을 추가합니다. 그렇지 않으면 이러한 필드를 비워 두고 Experience Platform 커넥터가 자동으로 배포합니다.

   >[!NOTE]
   >
   >고유한 AEP Web SDK를 지정하는 경우 Experience Platform 커넥터는 이 페이지에 지정된 데이터 스트림 ID(있는 경우)가 아니라 해당 SDK와 연결된 데이터 스트림 ID를 사용합니다.

## 데이터 수집

이 섹션에서는 Experience Platform 에지에 전송할 데이터 유형을 지정합니다. 데이터에는 두 가지 유형이 있습니다. 클라이언트측 및 서버측

클라이언트측 데이터는 상점 앞에서 캡처된 데이터입니다. 여기에는 다음과 같은 쇼퍼 상호 작용이 포함됩니다. `View Page`, `View Product`, `Add to Cart`, 및 [요청 목록](events.md#b2b-events) 정보(B2B 가맹점) 서버측 데이터 또는 백오피스 데이터는 상거래 서버에 캡처된 데이터입니다. 주문시, 취소, 환불, 출하 또는 완료와 같은 주문 상태에 대한 정보가 포함됩니다.

에서 **데이터 수집** 섹션에서 Experience Platform 에지로 전송할 데이터 유형을 선택합니다. Adobe Commerce 인스턴스에서 데이터 수집을 시작하려면 다음을 검토하십시오 [전제 조건](overview.md#prerequisites).

자세한 내용은 이벤트 항목을 참조하십시오 [상점](events.md#storefront-events) 및 [사무실](events.md#back-office-events) events.

>[!NOTE]
>
>의 모든 필드 **데이터 수집** 섹션에 적용 **웹 사이트** 범위 이상

1. 선택 **Storefront 이벤트** storefront 행동 데이터를 보내려면

   >[!NOTE]
   >
   >다음 **Storefront 이벤트** AEP 웹 SDK 및 조직 ID가 유효한 경우 확인란이 자동으로 활성화됩니다.

1. 선택 **백오피스 이벤트** 주문이 주문되었거나 취소, 환불 또는 출하된 경우와 같은 주문 상태 정보를 발송하려는 경우

   >[!NOTE]
   >
   >선택하는 경우 **백오피스 이벤트**&#x200B;를 입력하면 모든 백오피스 데이터가 Experience Platform 에지로 전송됩니다. 쇼핑객이 데이터 수집을 옵트아웃하도록 선택하는 경우 Experience Platform에서 쇼핑객의 개인 정보 보호 기본 설정을 명시적으로 설정해야 합니다. 수집기가 이미 구매자의 환경 설정에 따라 동의를 처리하는 상점 이벤트와는 다릅니다. [추가 정보](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) Experience Platform에서 쇼핑객의 개인 정보 보호 기본 설정 설정에 대한 정보.

1. 일정에 따라 백오피스 이벤트 데이터를 업데이트하려면 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 작업을 변경해야 합니다. `Sales Orders Feed` 인덱스 대상 `Update by Schedule`.

   1. 설정 _관리_ 사이드바, 다음 위치로 이동 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. 에 대한 확인란을 선택합니다 `Sales Orders Feed` 색인입니다.

   1. 설정 **[!UICONTROL Actions]** to `Update by Schedule`.

   1. 처음으로 백오피스 데이터를 활성화하는 경우 다음 명령을 실행하여 다시 색인화하고 재동기화를 트리거하십시오. 다음 기간 동안 자동으로 재동기화가 발생합니다. [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 작업이 올바르게 설정되어 있습니다.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. (고유한 AEP 웹 SDK를 사용하는 경우 이 단계를 건너뜁니다.) [만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform의 데이터 스트림을 선택하거나 컬렉션에 사용할 기존 데이터 스트림을 선택합니다.

1. (고유한 AEP 웹 SDK를 사용하는 경우 이 단계를 건너뜁니다.) 에서 **데이터 스트림 ID** 필드에 새 데이터 스트림이나 기존 데이터 스트림의 ID를 붙여넣습니다.

## 필드 설명

| 필드 | 설명 |
|--- |--- |
| 범위 | 구성 설정을 적용할 특정 웹 사이트입니다. |
| 조직 ID(글로벌) | Adobe DX 제품을 구입한 조직에 속한 ID입니다. 이 ID는 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. |
| AEP 웹 SDK가 이미 사이트에 배포되어 있습니까? | 사이트에 고유한 AEP 웹 SDK를 배포한 경우 이 확인란을 선택합니다 |
| AEP 웹 SDK 이름(글로벌) | 사이트에 Experience Platform Web SDK를 이미 배포한 경우 이 필드에 해당 SDK의 이름을 지정합니다. 이를 통해 Storefront Event Collector 및 Storefront Event SDK는 Experience Platform 커넥터에 의해 배포된 버전이 아니라 Experience Platform Web SDK를 사용할 수 있습니다. 사이트에 Experience Platform Web SDK를 배포하지 않은 경우 이 필드를 비워 두면 Experience Platform 커넥터가 자동으로 배포합니다. |
| Storefront 이벤트 | 조직 ID 및 데이터 스트림 ID가 유효한 한 기본적으로 선택됩니다. 상점 이벤트는 사이트를 검색할 때 구매자로부터 익명으로 처리된 행동 데이터를 수집합니다. |
| 백 오피스 이벤트 | 이 확인란을 선택하면 이벤트 페이로드에 주문 주문 처리, 취소, 환급 또는 배송과 같은 익명 처리된 주문 상태 정보가 포함됩니다. |
| 데이터 스트림 ID(웹 사이트) | Adobe Experience Platform에서 다른 Adobe DX 제품으로 데이터를 전송할 수 있는 ID입니다. 이 ID는 특정 Adobe Commerce 인스턴스 내의 특정 웹 사이트에 연결되어 있어야 합니다. 고유한 Experience Platform Web SDK를 지정하는 경우 이 필드에 데이터 스트림 ID를 지정하지 마십시오. Experience Platform 커넥터는 해당 SDK와 연결된 데이터 스트림 ID를 사용하고 이 필드에 지정된 모든 데이터 스트림 ID를 무시합니다(있는 경우). |

>[!NOTE]
>
>온보딩 후 상점 전면 데이터가 Experience Platform 에지로 이동하기 시작합니다. 백 오피스 데이터는 가장자리에 나타나는 데 약 5분이 걸립니다. 이후에 업데이트되는 내용은 크론 스케줄에 따라 에지에서 볼 수 있습니다.

## 이벤트 데이터가 수집되는지 확인

상거래 저장소에서 데이터가 수집되고 있는지 확인하려면 [Adobe Experience Platform 디버거](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) 를 입력하여 상거래 사이트를 검사합니다. 데이터가 수집되고 있음을 확인한 후, [만든 데이터 세트](overview.md#prerequisites).

1. 선택 **쿼리** Experience Platform의 왼쪽 탐색에서 를 클릭하고 [!UICONTROL Create Query].

   ![쿼리 편집기](assets/query-editor.png)

1. 쿼리 편집기가 열리면 데이터 집합에서 데이터를 선택하는 쿼리를 입력합니다.

   ![쿼리 만들기](assets/create-query.png)

   예를 들어 쿼리가 다음과 같을 수 있습니다.

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. 쿼리가 실행되면 **결과** 탭, 옆에 있습니다. **콘솔** 탭. 이 보기는 쿼리의 테이블 형식 출력을 표시합니다.

   ![쿼리 편집기](assets/query-results.png)

이 예제에서는 [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview)등 이 보기에서는 상거래 데이터가 가장자리에 도달했는지 확인할 수 있습니다.

결과가 예상과 다른 경우 데이터 세트를 열고 실패한 배치 가져오기를 찾습니다. 추가 정보 [배치 가져오기 문제 해결](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
