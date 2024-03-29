---
title: 상거래 데이터를 Adobe Experience Platform에 연결
description: 상거래 데이터를 Adobe Experience Platform에 연결하는 방법을 알아봅니다.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
source-git-commit: 99d1097b98ea18c8a317613b2366a97db131432f
workflow-type: tm+mt
source-wordcount: '2480'
ht-degree: 0%

---

# 상거래 데이터를 Adobe Experience Platform에 연결

설치 시 [!DNL Data Connection] 확장에 새 구성 페이지가 두 개 표시됨 **시스템** 아래 메뉴 **서비스** 상거래 내 _관리자_.

- Commerce Services 커넥터
- [!DNL Data Connection]

Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결하려면 Commerce Services 커넥터로 시작한 다음 로 마무리하는 두 커넥터를 모두 구성해야 합니다. [!DNL Data Connection] 확장명.

## Commerce Services 커넥터 구성

이전에 Adobe Commerce 서비스를 설치한 경우에는 Commerce Services 커넥터를 이미 구성했을 수 있습니다. 그렇지 않으면 다음에 대한 다음 작업을 완료해야 합니다. [상거래 서비스 커넥터](../landing/saas.md) 페이지:

1. 상거래 계정에 로그인 대상 [프로덕션 및 샌드박스 API 키 검색](../landing/saas.md#credentials).
1. 선택 [SaaS 데이터 공간](../landing/saas.md#saas-configuration).
1. Adobe 계정에 로그인 대상 [조직 ID 검색](../landing/saas.md#ims-organization-optional).

Commerce Services 커넥터를 구성한 다음 [!DNL Data Connection] 확장명.

## 구성 [!DNL Data Connection] 확장

이 섹션에서는 다음을 구성하는 방법을 알아봅니다. [!DNL Data Connection] 확장명.

### 서비스 계정 및 자격 증명 세부 정보 추가

수거 및 발송을 계획하시면 [이전 순서 데이터](#send-historical-order-data) 또는 [고객 프로필 데이터](#send-customer-profile-data), 서비스 계정 및 자격 증명 세부 정보를 추가해야 합니다. 또한 을 구성하는 경우 [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) 확장에서 다음 단계를 완료해야 합니다.

상점 또는 백오피스 데이터만 수집 및 전송하는 경우 [일반](#general) 섹션.

#### 1단계: Adobe Developer 콘솔에서 프로젝트 만들기

Experience Platform API 호출을 수행할 수 있도록 Adobe Developer 콘솔에서 상거래를 인증하는 프로젝트를 만듭니다.

프로젝트를 만들려면 다음에 설명된 단계를 수행합니다. [Experience Platform API 인증 및 액세스](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) 튜토리얼.

튜토리얼을 진행할 때 프로젝트에 다음과 같은 사항이 있는지 확인합니다.

- 다음에 대한 액세스 권한 [제품 프로필](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles): **기본 프로덕션 모든 액세스** 및 **AEP 기본 모든 액세스**.
- 올바른 [역할 및 권한이 구성됨](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- JSON 웹 토큰(JWT)을 서버 간 인증 방법으로 사용하려는 경우 개인 키도 업로드해야 합니다.

이 단계의 결과 다음 단계에서 사용하는 구성 파일이 만들어집니다.

#### 2단계: 구성 파일 다운로드

다운로드 [작업 영역 구성 파일](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). 이 파일의 내용을 복사하여 **서비스 계정/자격 증명 세부 정보** 상거래 관리자의 페이지입니다.

1. Commerce 관리에서 다음 위치로 이동합니다. **스토어** > 설정 > **구성** > **서비스** > **[!DNL Data Connection]**.

1. 에서 구현한 서버 간 인증 방법을 선택합니다. **Adobe Developer 인증 유형** 메뉴 아래의 제품에서 사용할 수 있습니다. Adobe은 OAuth를 사용하는 것을 권장합니다. JWT는 더 이상 사용되지 않습니다. [자세히 알아보기](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. (JWT만 해당) 의 콘텐츠를 복사하여 붙여넣습니다. `private.key` 파일을 **클라이언트 암호** 필드. 다음 명령을 사용하여 내용을 복사합니다.

   ```bash
   cat config/private.key | pbcopy
   ```

   다음을 참조하십시오 [서비스 계정(JWT) 인증](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) 에 대한 자세한 내용은 `private.key` 파일.

1. 의 내용을 복사합니다. `<workspace-name>.json` 파일을 **서비스 계정/자격 증명 세부 정보** 필드.

   ![[!DNL Data Connection] 관리자 구성](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. 클릭 **구성 저장**.

### 일반

1. 관리에서 **시스템** > 서비스 > **[!DNL Data Connection]**.

1. 다음에서 **설정** 아래의 탭 **일반**&#x200B;에서 구성한 대로 Adobe Experience Platform 계정과 연결된 ID를 확인합니다. [Commerce Services 커넥터](../landing/saas.md#organizationid). 조직 ID는 글로벌입니다. Adobe Commerce 인스턴스당 하나의 조직 ID만 연결할 수 있습니다.

1. 다음에서 **범위** 드롭다운에서 컨텍스트를 로 설정합니다. **웹 사이트**.

1. (선택 사항) [AEP 웹 SDK(alloy)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) 사이트에 배포된 후 확인란을 활성화하고 AEP 웹 SDK의 이름을 추가합니다. 그렇지 않으면 이러한 필드를 비워 두고 [!DNL Data Connection] 확장은 사용자를 위해 하나를 배포합니다.

   >[!NOTE]
   >
   >고유한 AEP 웹 SDK를 지정하는 경우 [!DNL Data Connection] 확장은 이 페이지에 지정된 데이터 스트림 ID가 아닌 해당 SDK와 연결된 데이터 스트림 ID를 사용합니다(있는 경우).

### 데이터 수집

이 섹션에서는 수집하고 Experience Platform 에지로 전송할 데이터 유형을 지정합니다. 데이터에는 세 가지 유형이 있습니다.

- **동작** (클라이언트측 데이터)는 상점 첫 화면에서 캡처된 데이터입니다. 여기에는 다음과 같은 구매자 상호 작용이 포함됩니다. `View Page`, `View Product`, `Add to Cart`, 및 [징발 목록](events.md#b2b-events) 정보(B2B 판매자용).

- **백오피스** (서버측 데이터)는 Commerce 서버에 캡처된 데이터입니다. 여기에는 주문이 주문, 취소, 환불, 배송 또는 완료 여부와 같은 주문 상태에 대한 정보가 포함됩니다. 이 호에는 다음의 것도 포함된다. [이전 순서 데이터](#send-historical-order-data).

- **프로필** 은 쇼핑객 프로필 정보와 관련된 데이터입니다. 학습 [기타](#send-customer-profile-data).

Adobe Commerce 인스턴스가 데이터 수집을 시작할 수 있도록 하려면 다음을 검토하십시오. [전제 조건](overview.md#prerequisites).

자세한 내용은 이벤트 항목을 참조하십시오 [상점 첫 화면](events.md#storefront-events), [후선 근무](events-backoffice.md), 및 [프로필](events-backoffice.md#customer-profile-events-server-side) 이벤트.

>[!NOTE]
>
>의 모든 필드 **데이터 수집** 섹션에 섹션 적용 **웹 사이트** 범위 이상.

1. 선택 **Storefront 이벤트** storefront 동작 데이터를 전송하려는 경우.

1. 선택 **백오피스 이벤트** 주문, 취소, 환불 또는 배송 여부 등 주문 상태 정보를 전송하려는 경우.

   >[!NOTE]
   >
   >다음을 선택하는 경우 **백오피스 이벤트**, 모든 백오피스 데이터가 Experience Platform 에지로 전송됩니다. 쇼핑객이 데이터 수집을 옵트아웃하는 경우 Experience Platform에서 쇼핑객의 개인 정보 보호 기본 설정을 명시적으로 설정해야 합니다. 이는 컬렉터가 이미 구매자 환경 설정에 따라 동의를 처리하는 상점 이벤트와는 다릅니다. 학습 [기타](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) Experience Platform에서 쇼핑객의 개인 정보 보호 환경 설정 정보.

1. (자체 AEP 웹 SDK를 사용하는 경우 이 단계를 건너뜁니다.) [만들기](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) Adobe Experience Platform의 데이터 스트림이나 컬렉션에 사용할 기존 데이터 스트림을 선택합니다. 데이터 스트림 ID를 입력합니다. **데이터 스트림 ID** 필드.

1. 다음을 입력합니다. **데이터 세트 ID** 상거래 데이터를 포함할 수 있습니다. 데이터 세트 ID 찾기:

   1. Experience Platform UI를 열고 을(를) 선택합니다 **데이터 세트** 을(를) 왼쪽 탐색에서 열어 **데이터 세트** 대시보드입니다. 대시보드에는 조직에서 사용 가능한 모든 데이터 세트가 나열됩니다. 이름, 데이터 세트가 준수하는 스키마, 가장 최근 수집 실행 상태 등 나열된 각 데이터 세트에 대한 세부 사항이 표시됩니다.
   1. 데이터 스트림과 연결된 데이터 세트를 엽니다.
   1. 오른쪽 창에서 데이터 세트에 대한 세부 정보를 봅니다. 데이터 세트 ID를 복사합니다.

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

#### 필드 설명

| 필드 | 설명 |
|--- |--- |
| 범위 | 구성 설정을 적용할 특정 웹 사이트입니다. |
| 조직 ID (전역) | Adobe DX 제품을 구입한 조직의 ID입니다. 이 ID는 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. |
| AEP 웹 SDK가 이미 사이트에 배포되었습니까 | 자신의 AEP 웹 SDK를 사이트에 배포한 경우 이 확인란을 선택합니다 |
| AEP 웹 SDK 이름(전역) | 사이트에 Experience Platform Web SDK가 이미 배포되어 있는 경우 이 필드에 해당 SDK의 이름을 지정합니다. Experience Platform 이렇게 하면 Storefront 이벤트 수집기 및 Storefront 이벤트 SDK는 [!DNL Data Connection] 확장명. 사이트에 Experience Platform Web SDK가 배포되어 있지 않은 경우 이 필드를 비워 두고 [!DNL Data Connection] 확장은 사용자를 위해 하나를 배포합니다. |
| Storefront 이벤트 | 조직 ID 및 데이터 스트림 ID가 유효한 경우 기본적으로 선택되어 있습니다. Storefront 이벤트는 사이트를 탐색할 때 쇼핑객으로부터 익명으로 처리된 행동 데이터를 수집합니다. |
| 백오피스 이벤트 | 선택하면 이벤트 페이로드에 주문이 주문, 취소, 환불 또는 배송된 경우와 같이 익명으로 처리된 주문 상태 정보가 포함됩니다. |
| 데이터 스트림 ID(웹 사이트) | Adobe Experience Platform에서 다른 Adobe DX 제품으로 데이터가 흐를 수 있는 ID입니다. 이 ID는 특정 Adobe Commerce 인스턴스 내의 특정 웹 사이트에 연결되어야 합니다. 고유한 Experience Platform Web SDK를 지정하는 경우 이 필드에 데이터 스트림 ID를 지정하지 마십시오. 다음 [!DNL Data Connection] 확장은 해당 SDK와 연결된 데이터 스트림 ID를 사용하며 이 필드에 지정된 데이터 스트림 ID는 무시합니다(있는 경우). |
| 데이터 세트 ID(웹 사이트) | 상거래 데이터가 포함된 데이터 세트의 ID. 을(를) 선택 해제하지 않은 경우 이 필드는 필수입니다. **Storefront 이벤트** 또는 **백오피스 이벤트** 확인란. 또한 자체 Experience Platform Web SDK를 사용 중이므로 데이터 스트림 ID를 지정하지 않은 경우에도 데이터 스트림과 연결된 데이터 세트 ID를 추가해야 합니다. 그렇지 않으면 이 양식을 저장할 수 없습니다. |

온보딩 후 상점 데이터가 Experience Platform 에지로 흐르기 시작합니다. 백오피스 데이터가 가장자리에 표시되는 데 약 5분이 소요됩니다. cron 일정에 따라 에지에서 후속 업데이트가 표시됩니다.

### 고객 프로필 데이터 보내기

프로필에 보낼 수 있는 Experience Platform 데이터에는 프로필 레코드와 시계열 프로필 이벤트의 두 가지 유형이 있습니다.

프로필 레코드에는 구매자가 상거래 인스턴스에서 구매자 이름과 같은 프로필을 만들 때 저장되는 데이터가 포함됩니다. 스키마 및 데이터 세트가 다음과 같은 경우 [제대로 구성됨](profile-data.md), 프로필 레코드가 Experience Platform으로 전송되고 Adobe의 프로필 관리 및 세분화 서비스로 전달됩니다. [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=ko-KR).

시계열 프로필 이벤트에는 사이트에서 계정을 생성, 편집 또는 삭제하는 경우와 같이 쇼퍼의 프로필 정보에 대한 데이터가 포함됩니다. 프로필 이벤트 데이터가 Experience Platform으로 전송되면 다른 DX 제품에서 사용할 수 있는 데이터 세트에 상주합니다.

1. 다음을 수행했는지 확인하십시오. [제공됨](#add-service-account-and-credential-details) 서비스 계정 및 자격 증명 세부 정보.

1. 에 대해 스키마와 데이터 세트가 지정되었는지 확인합니다. [프로필 레코드 데이터 수집](profile-data.md) 및 [시계열 프로필 이벤트 데이터 수집](update-xdm.md#time-series-profile-event-data).

1. 에 확인 표시 **고객 프로필** Experience Platform 데이터를 프로필에 보내려면 확인란을 선택합니다.

1. 다음을 입력합니다. **프로필 데이터 세트 ID**.

   프로필 레코드 데이터는 행동 및 백 오피스 이벤트 데이터에 현재 사용하고 있는 것과 다른 데이터 세트를 사용해야 합니다.

1. 동작 및 백 오피스 데이터에 사용 중인 동일한 데이터 스트림 ID를 통해 프로필 이벤트를 스트리밍하지 않으려면 **동일한 데이터 스트림 ID를 통해 고객 프로필 스트리밍** 을 누르고 대신 사용할 데이터 스트림 ID를 입력합니다.

Real-Time CDP에서 프로필 레코드를 사용할 수 있도록 하는 데 약 10분 정도 걸릴 수 있습니다. 프로필 이벤트가 즉시 스트리밍을 시작합니다.

#### 필드 설명

| 필드 | 설명 |
|--- |--- |
| 고객 프로필 | 고객 프로필 기록을 수집하고 전송하려면 이 확인란을 선택합니다. |
| 프로필 데이터 세트 ID | 프로필 레코드는 행동 및 백 오피스 이벤트에 사용되는 데이터 세트와 다른 데이터 세트를 사용해야 합니다. |
| 동일한 데이터 스트림 ID를 통해 고객 프로필 스트리밍 | 행동 및 백 오피스 이벤트에 현재 사용되는 것과 동일한 데이터 스트림을 사용할지 여부를 결정합니다. |
| 고객 프로필용 데이터스트림 | 고객 프로필 레코드별 데이터 스트림을 지정합니다. |

### 이전 주문 데이터 보내기

Adobe Commerce은 최대 5년의 [내역 주문 데이터 및 상태](events-backoffice.md#back-office-events). 다음을 사용할 수 있습니다. [!DNL Data Connection] 확장 : 내역 데이터를 Experience Platform으로 전송하여 고객 프로필을 보강하고 과거 주문을 기반으로 고객 경험을 개인화합니다. 데이터는 Experience Platform 내의 데이터 세트에 저장됩니다.

Commerce에서 이미 이전 주문 데이터를 수집하는 동안 해당 데이터를 Experience Platform으로 보내려면 몇 가지 단계를 완료해야 합니다.

이 비디오를 통해 이전 주문에 대해 자세히 알아본 후 다음 단계를 완료하여 이전 주문 수집을 구현합니다.

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### 주문 동기화 서비스 설정

동기화 서비스 주문은 [메시지 큐 프레임워크](https://developer.adobe.com/commerce/php/development/components/message-queues/) 그리고 RabbitMQ. 이러한 단계를 완료하면 주문 상태 데이터가 SaaS에 동기화될 수 있습니다. SaaS는 Experience Platform으로 전송되기 전에 필요합니다.

1. 다음을 수행했는지 확인하십시오. [제공됨](#add-service-account-and-credential-details) 서비스 계정 및 자격 증명 세부 정보.

1. [사용](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ.

   >[!NOTE]
   >
   >RabbitMQ이 Commerce 버전 2.4.7 이상에 대해 이미 설정되었지만 소비자를 활성화해야 합니다.

1. 의 cron job별로 메시지 대기열 소비자 활성화 `.magento.env.yaml` 사용 `CRON_CONSUMERS_RUNNER` 환경 변수입니다.

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >다음을 참조하십시오. [변수 배포 설명서](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) 사용 가능한 모든 구성 옵션에 대해 알아봅니다.

주문 동기화 서비스를 활성화한 상태에서 의 내역 주문 날짜 범위를 지정할 수 있습니다. **[!UICONTROL [!DNL Data Connection]]** 페이지를 가리키도록 업데이트하는 중입니다.

#### 주문 내역 날짜 범위 지정

Experience Platform으로 전송할 과거 주문의 날짜 범위를 지정합니다.

1. 관리에서 **시스템** > 서비스 > **[!DNL Data Connection]**.

1. 다음 항목 선택 **주문 내역** 탭.

1. 아래 **주문 내역 동기화**, **설정에서 데이터 세트 ID 복사** 확인란이 이미 활성화되어 있습니다. 이렇게 하면 다음에 지정된 동일한 데이터 세트를 **설정** 탭.

1. 다음에서 **출처:** 및 **종료** 필드에서는 전송할 내역 주문 데이터의 날짜 범위를 지정합니다. 5년을 초과하는 날짜 범위는 선택할 수 없습니다.

1. 선택 **[!UICONTROL Start Sync]** 동기화를 시작하도록 트리거합니다. 이전 주문 데이터는 스트리밍 데이터인 상점 및 백오피스 데이터가 아닌 일괄 처리된 데이터입니다. 일괄 처리된 데이터가 Experience Platform에 도착하는 데 약 45분이 소요됩니다.

##### 필드 설명

| 필드 | 설명 |
|--- |--- |
| 설정에서 데이터 세트 ID 복사 | 입력한 데이터 세트 ID를 **설정** 탭. |
| 데이터 세트 ID(웹 사이트) | 상거래 데이터가 포함된 데이터 세트의 ID. 을(를) 선택 해제하지 않은 경우 이 필드는 필수입니다. **Storefront 이벤트** 또는 **백오피스 이벤트** 확인란. 또한 자체 Experience Platform Web SDK를 사용 중이므로 데이터 스트림 ID를 지정하지 않은 경우에도 데이터 스트림과 연결된 데이터 세트 ID를 추가해야 합니다. 그렇지 않으면 이 양식을 저장할 수 없습니다. |
| 출처: | 주문 내역 데이터 수집을 시작할 시작 날짜. |
| 종료 | 주문 내역 데이터 수집을 종료할 날짜. |
| 동기화 시작 | 주문 내역 데이터를 Experience Platform 에지와 동기화하는 프로세스를 시작합니다. 이 단추는 다음 경우에 비활성화됩니다. **[!UICONTROL Dataset ID]** 필드가 비어 있거나 데이터 세트 ID가 잘못되었습니다. |

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

## 다음 단계

상거래 데이터가 Experience Platform 에지로 전송되면 Adobe Journey Optimizer과 같은 다른 Adobe Experience Cloud 제품에서 해당 데이터를 사용할 수 있습니다. 예를 들어 특정 이벤트를 수신하고 해당 이벤트 데이터를 기반으로 첫 번째 사용자에 대해 이메일을 트리거하거나 포기한 장바구니가 있는 경우 Journey Optimizer을 구성할 수 있습니다. 다음 방법으로 Commerce 플랫폼을 확장하는 방법을 알아봅니다. [고객 여정 만들기](using-ajo.md) Journey Optimizer.
