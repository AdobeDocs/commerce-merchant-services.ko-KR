---
title: 상거래 데이터를 Adobe Experience Platform에 연결
description: 상거래 데이터를 Adobe Experience Platform에 연결하는 방법을 알아봅니다.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# 상거래 데이터를 Adobe Experience Platform에 연결

Experience Platform 커넥터를 설치하면 **시스템** 아래 메뉴 **서비스** 상거래 내 _관리자_.

- Commerce Services 커넥터
- Experience Platform 커넥터

Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결하려면 Commerce Services 커넥터로 시작한 다음 Experience Platform 커넥터로 마치는 두 커넥터를 모두 구성해야 합니다.

## Commerce Services 커넥터 업데이트

이전에 Adobe Commerce 서비스를 설치한 경우에는 Commerce Services 커넥터를 이미 구성했을 수 있습니다. 그렇지 않으면 다음에 대한 다음 작업을 완료해야 합니다. [상거래 서비스 커넥터](../landing/saas.md) 페이지:

1. 상거래 계정에 로그인 대상 [프로덕션 및 샌드박스 API 키 검색](../landing/saas.md#credentials).
1. 선택 [SaaS 데이터 공간](../landing/saas.md#saas-configuration).
1. Adobe 계정에 로그인 대상 [조직 ID 검색](../landing/saas.md#ims-organization-optional).

Commerce Services 커넥터를 구성한 다음 Experience Platform 커넥터를 구성합니다.

## Experience Platform 커넥터 업데이트

이 섹션에서는 조직 ID를 사용하여 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. 그런 다음 Experience Platform 에지로 전송할 데이터 유형(상점 또는 백오피스)을 지정할 수 있습니다.

![Experience Platform 커넥터 구성](assets/epc-config-dc.png)

## 일반

1. 에서 Adobe 계정에 로그인 [Commerce Services 커넥터](../landing/saas.md#organizationid) 조직 ID를 선택합니다.

   >[!NOTE]
   >
   >이전에 상거래 서비스 커넥터를 구성한 경우 조직 ID가 이미 선택되었으므로 이 단계를 건너뛸 수 있습니다.

1. 관리에서 **시스템** > 서비스 > **Experience Platform 커넥터**.

1. 다음에서 **범위** 드롭다운에서 컨텍스트를 로 설정합니다. **웹 사이트**.

1. 다음에서 **조직 ID** 필드에서 Adobe Experience Platform 계정과 연결된 ID를 확인합니다( [Commerce Services 커넥터](../landing/saas.md#organizationid). 조직 ID는 글로벌입니다. Adobe Commerce 인스턴스당 하나의 조직 ID만 연결할 수 있습니다.

1. (선택 사항) [AEP 웹 SDK(alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 사이트에 배포된 후 확인란을 활성화하고 AEP 웹 SDK의 이름을 추가합니다. 그렇지 않으면 이러한 필드를 비워 두고 Experience Platform 커넥터가 필드를 배포합니다.

   >[!NOTE]
   >
   >고유한 AEP 웹 SDK를 지정하는 경우 Experience Platform 커넥터는 이 페이지에 지정된 데이터스트림 ID가 아닌 해당 SDK와 연결된 데이터스트림 ID를 사용합니다(있는 경우).

## 데이터 수집

이 섹션에서는 Experience Platform 에지로 전송할 데이터 유형을 지정합니다. 데이터에는 클라이언트측과 서버측, 이렇게 두 가지 유형이 있습니다.

클라이언트측 데이터는 상점 첫 화면에서 캡처한 데이터입니다. 여기에는 다음과 같은 구매자 상호 작용이 포함됩니다. `View Page`, `View Product`, `Add to Cart`, 및 [징발 목록](events.md#b2b-events) 정보(B2B 판매자용). 서버측 데이터 또는 백오피스 데이터는 상거래 서버에 캡처된 데이터입니다. 여기에는 주문이 주문, 취소, 환불, 배송 또는 완료 여부와 같은 주문 상태에 대한 정보가 포함됩니다.

다음에서 **데이터 수집** 섹션에서 Experience Platform 에지로 전송할 데이터 유형을 선택합니다. Adobe Commerce 인스턴스가 데이터 수집을 시작할 수 있도록 하려면 다음을 검토하십시오. [전제 조건](overview.md#prerequisites).

자세한 내용은 이벤트 항목을 참조하십시오 [상점 첫 화면](events.md#storefront-events) 및 [후선 근무](events.md#back-office-events) 이벤트.

>[!NOTE]
>
>의 모든 필드 **데이터 수집** 섹션에 섹션 적용 **웹 사이트** 범위 이상.

1. 선택 **Storefront 이벤트** storefront 동작 데이터를 전송하려는 경우.

   >[!NOTE]
   >
   >다음 **Storefront 이벤트** AEP 웹 SDK 및 조직 ID가 유효한 경우 확인란이 자동으로 활성화됩니다.

1. 선택 **백오피스 이벤트** 주문, 취소, 환불 또는 배송 여부 등 주문 상태 정보를 전송하려는 경우.

   >[!NOTE]
   >
   >다음을 선택하는 경우 **백오피스 이벤트**, 모든 백오피스 데이터가 Experience Platform 에지로 전송됩니다. 쇼핑객이 데이터 수집을 옵트아웃하는 경우 Experience Platform에서 쇼핑객의 개인 정보 보호 기본 설정을 명시적으로 설정해야 합니다. 이는 컬렉터가 이미 구매자 환경 설정에 따라 동의를 처리하는 상점 이벤트와는 다릅니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) Experience Platform에서 쇼핑객의 개인 정보 보호 환경 설정 정보.

1. 에 따라 일정에 따라 백 오피스 이벤트 데이터를 업데이트하려면 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 작업, 다음을 변경해야 합니다. `Sales Orders Feed` 색인 대상 `Update by Schedule`.

   1. 다음에서 _관리자_ 사이드바, 이동 **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. 에 대한 확인란을 선택합니다. `Sales Orders Feed` 인덱서.

   1. 설정 **[!UICONTROL Actions]** 끝 `Update by Schedule`.

   1. 백 오피스 데이터를 처음 활성화하는 경우 다음 명령을 실행하여 다시 인덱싱하고 재동기화를 트리거합니다. 다음에 대한 재동기화는 [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) 작업이 올바르게 설정되었습니다.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. (자체 AEP 웹 SDK를 사용하는 경우 이 단계를 건너뜁니다.) [만들기](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) Adobe Experience Platform의 데이터 스트림이나 컬렉션에 사용할 기존 데이터 스트림을 선택합니다.

1. (자체 AEP 웹 SDK를 사용하는 경우 이 단계를 건너뜁니다.) 다음에서 **데이터 스트림 ID** 필드에 새 데이터스트림 또는 기존 데이터스트림의 ID를 붙여넣습니다.

## 필드 설명

| 필드 | 설명 |
|--- |--- |
| 범위 | 구성 설정을 적용할 특정 웹 사이트입니다. |
| 조직 ID (전역) | Adobe DX 제품을 구입한 조직의 ID입니다. 이 ID는 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. |
| AEP 웹 SDK가 이미 사이트에 배포되었습니까 | 자신의 AEP 웹 SDK를 사이트에 배포한 경우 이 확인란을 선택합니다 |
| AEP 웹 SDK 이름(전역) | 사이트에 Experience Platform Web SDK가 이미 배포되어 있는 경우 이 필드에 해당 SDK의 이름을 지정합니다. 이렇게 하면 Storefront 이벤트 수집기 및 Storefront 이벤트 SDK가 Experience Platform 커넥터에 의해 배포된 버전이 아니라 Experience Platform Web SDK를 사용할 수 있습니다. 사이트에 Experience Platform Web SDK가 배포되어 있지 않은 경우 이 필드를 비워 두고 Experience Platform 커넥터에서 배포합니다. |
| Storefront 이벤트 | 조직 ID 및 데이터 스트림 ID가 유효한 경우 기본적으로 선택되어 있습니다. Storefront 이벤트는 사이트를 탐색할 때 쇼핑객으로부터 익명으로 처리된 행동 데이터를 수집합니다. |
| 백오피스 이벤트 | 선택하면 이벤트 페이로드에 주문이 주문, 취소, 환불 또는 배송된 경우와 같이 익명으로 처리된 주문 상태 정보가 포함됩니다. |
| 데이터 스트림 ID(웹 사이트) | Adobe Experience Platform에서 다른 Adobe DX 제품으로 데이터가 흐를 수 있는 ID입니다. 이 ID는 특정 Adobe Commerce 인스턴스 내의 특정 웹 사이트에 연결되어야 합니다. 고유한 Experience Platform Web SDK를 지정하는 경우 이 필드에 데이터 스트림 ID를 지정하지 마십시오. Experience Platform 커넥터는 해당 SDK와 연결된 데이터 스트림 ID를 사용하며 이 필드에 지정된 데이터 스트림 ID는 무시합니다(있는 경우). |

>[!NOTE]
>
>온보딩 후 상점 데이터가 Experience Platform 에지로 흐르기 시작합니다. 백오피스 데이터가 가장자리에 표시되는 데 약 5분이 소요됩니다. cron 일정에 따라 에지에서 후속 업데이트가 표시됩니다.

## 이벤트 데이터 수집 확인

상거래 저장소에서 데이터가 수집되고 있는지 확인하려면 [Adobe Experience Platform 디버거](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) 상거래 사이트를 검사합니다. 데이터가 수집되고 있는지 확인한 후, 의 데이터를 반환하는 쿼리를 실행하여 상점 및 백 오피스 이벤트 데이터가 에지에 표시되는지 확인할 수 있습니다. [생성한 데이터 세트](overview.md#prerequisites).

1. 선택 **쿼리** Experience Platform의 왼쪽 탐색에서 [!UICONTROL Create Query].

   ![쿼리 편집기](assets/query-editor.png)

1. 쿼리 편집기가 열리면 데이터 세트에서 데이터를 선택하는 쿼리를 입력합니다.

   ![쿼리 만들기](assets/create-query.png)

   예를 들어 쿼리는 다음과 같을 수 있습니다.

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. 쿼리가 실행되면 결과는 **결과** 탭, 다음 옆에 있음 **콘솔** 탭. 이 보기는 쿼리의 테이블 형식 출력을 보여 줍니다.

   ![쿼리 편집기](assets/query-results.png)

이 예제에서는에서 이벤트 데이터가 표시됩니다. [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview)등. 이 보기를 통해 상거래 데이터가 에지에 도달했는지 확인할 수 있습니다.

결과가 예상과 다른 경우 데이터 세트를 열고 실패한 일괄 처리 가져오기를 찾습니다. 자세히 알아보기 [일괄 가져오기 문제 해결](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
