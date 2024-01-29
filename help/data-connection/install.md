---
title: 설치 [!DNL Data Connection]
description: 설치, 업데이트 및 제거 방법 알아보기 [!DNL Data Connection] Adobe Commerce에서 확장되었습니다.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 9001cd24db0941b7c7edcfd5b10464dc90084fd7
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# 설치 [!DNL Data Connection]

확장을 설치하기 전에 [사전 요구 사항 검토](overview.md#prereqs).

## 확장 설치

다음 [!DNL Data Connection] 확장은 다음 위치에서 사용할 수 있습니다. [Adobe 마켓플레이스](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). 서버의 명령줄에서 이 확장을 설치하면 Adobe Commerce 설치에 다음과 같이 연결됩니다. [서비스](../landing/saas.md). 프로세스가 완료되면 **[!DNL Data Connection]** 및 **Commerce Services 커넥터** 다음에 표시: **시스템** 아래 메뉴 **서비스** 상거래 내 _관리자_.

![[!DNL Data Connection] 확장 관리자 보기](assets/epc-adminui.png)

>[!IMPORTANT]
>
>확장 이름이 Experience Platform 커넥터에서 로 변경된 동안 [!DNL Data Connection], 패키지 이름은 그대로 유지됩니다 `experience-platform-connector` 이전 버전과의 호환성을 지원합니다.

1. 다운로드하려면 `experience-platform-connector` package, 명령줄에서 다음을 실행합니다.

   ```bash
   composer require magento/experience-platform-connector
   ```

   이 메타패키지에는 다음 모듈 및 확장이 포함되어 있습니다.

   * `module-experience-connector-admin` - 특정 Adobe Commerce 인스턴스에 대한 데이터 스트림 ID를 선택할 수 있도록 관리 UI를 업데이트합니다.
   * `module-experience-connector` - 를 설정합니다. `Organization ID` 및 `datastreamId` Storefront Events SDK에서
   * `data-services` - storefront 이벤트에 대한 특성 컨텍스트를 제공합니다. 예를 들어 체크아웃 이벤트가 발생하면 장바구니에 들어 있는 항목 수에 대한 정보와 해당 항목에 대한 제품 속성 데이터가 포함됩니다.
   * `services-id` - Adobe Commerce 인스턴스를 [Adobe Commerce SaS](../landing/saas.md) 샌드박스 및 프로덕션 API 키와 Adobe Experience Platform을 사용하여 IMS 조직 ID를 검색합니다.
   * `orders-connector` - 주문 상태 서비스를 Adobe Commerce 인스턴스에 연결합니다.

1. (선택 사항) [!DNL Live Search] 데이터: 다음을 포함 [이벤트 검색](events.md#search-events), 설치 [[!DNL Live Search]](../live-search/install.md) 확장명.

1. (선택 사항) 다음과 같은 B2B 데이터를 포함합니다. [구매요청 이벤트](events.md#b2b-events), 설치 [B2B 확장](#install-the-b2b-extension).

### Adobe I/O 이벤트 설치

를 설치한 후 `experience-platform-connector` 확장을 사용하려면 Adobe Commerce용 Adobe I/O 이벤트 를 설치해야 합니다.

다음 단계는 Adobe Commerce on cloud infrastructure 및 온프레미스 설치 모두에 적용됩니다.

1. Commerce 2.4.4 또는 2.4.5를 실행하는 경우 다음 명령을 사용하여 이벤트 모듈을 로드합니다.

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   Commerce 2.4.6 이상 버전은 이러한 모듈을 자동으로 로드합니다.

1. 프로젝트 종속성을 업데이트합니다.

   ```bash
   composer update
   ```

1. 새 모듈 활성화:

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

배포 유형(온-프레미스 또는 Adobe Commerce on Cloud 인프라)을 기반으로 설치를 완료합니다.

#### 온-프레미스

온-프레미스 환경에서 코드 생성 및 Adobe Commerce 이벤트를 수동으로 활성화해야 합니다.

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### 클라우드 인프라

클라우드 인프라의 Adobe Commerce에서 `ENABLE_EVENTING` 의 전역 변수 `.magento.env.yaml`. [자세히 알아보기](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

업데이트된 파일을 커밋하고 클라우드 환경으로 푸시합니다. 배포가 완료되면 다음 명령을 사용하여 이벤트 전송을 활성화합니다.

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

### B2B 확장 설치

B2B 판매자의 경우 다음 확장을 설치하여 다음을 포함합니다. [징발 목록](events.md#b2b-events) 이벤트 데이터.

다운로드 `magento/experience-platform-connector-b2b` 명령줄에서 다음을 실행하여 확장하십시오.

```bash
composer require magento/experience-platform-connector-b2b
```

## 업데이트 [!DNL Data Connection] 확장 {#update}

를 업데이트하려면 [!DNL Data Connection] 확장에서 명령줄에서 다음을 실행합니다.

```bash
composer update magento/experience-platform-connector --with-dependencies
```

또는 B2B 판매자의 경우:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

2.0.0에서 3.0.0으로 등 주요 버전으로 업데이트하려면 프로젝트의 루트를 편집합니다 [!DNL Composer] `.json` 파일을 다음과 같이 지정합니다.

1. 루트 열기 `composer.json` 파일 및 검색 `magento/experience-platform-connector`.

1. 다음에서 `require` 섹션에서 버전 번호를 다음과 같이 업데이트합니다.

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
      ...
    }
   ```

1. **저장** `composer.json`. 그런 다음 명령줄에서 다음을 실행합니다.

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   또는 B2B 판매자의 경우:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## 제거 [!DNL Data Connection] 확장 {#uninstall}

을(를) 제거하려면 [!DNL Data Connection] 확장자는 을 참조하십시오. [모듈 제거](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
