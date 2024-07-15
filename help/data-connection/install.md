---
title: ' [!DNL Data Connection] 설치'
description: Adobe Commerce에서  [!DNL Data Connection] 확장을 설치, 업데이트 및 제거하는 방법을 알아봅니다.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 9001cd24db0941b7c7edcfd5b10464dc90084fd7
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# [!DNL Data Connection] 설치

확장을 설치하기 전에 [필수 구성 요소를 검토하십시오](overview.md#prereqs).

## 확장 설치

[!DNL Data Connection] 확장은 [Adobe 마켓플레이스](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html)에서 사용할 수 있습니다. 서버의 명령줄에서 이 확장을 설치하면 Adobe Commerce 설치에 [서비스](../landing/saas.md)(으)로 연결됩니다. 프로세스가 완료되면 **[!DNL Data Connection]** 및 **Commerce 서비스 커넥터**&#x200B;가 Commerce _관리_&#x200B;의 **서비스** 아래의 **시스템** 메뉴에 나타납니다.

![[!DNL Data Connection] 확장 관리자 보기](assets/epc-adminui.png)

>[!IMPORTANT]
>
>확장 이름이 Experience Platform 커넥터에서 [!DNL Data Connection](으)로 변경된 동안 이전 버전과의 호환성을 지원하기 위해 패키지 이름은 `experience-platform-connector` 상태로 유지됩니다.

1. `experience-platform-connector` 패키지를 다운로드하려면 명령줄에서 다음을 실행하십시오.

   ```bash
   composer require magento/experience-platform-connector
   ```

   이 메타패키지에는 다음 모듈 및 확장이 포함되어 있습니다.

   * `module-experience-connector-admin` - 특정 Adobe Commerce 인스턴스에 대한 데이터 스트림 ID를 선택할 수 있도록 관리 UI를 업데이트합니다.
   * `module-experience-connector` - Storefront Events SDK에서 `Organization ID` 및 `datastreamId`을(를) 설정합니다.
   * `data-services` - storefront 이벤트에 대한 특성 컨텍스트를 제공합니다. 예를 들어 체크아웃 이벤트가 발생하면 장바구니에 들어 있는 항목 수에 대한 정보와 해당 항목에 대한 제품 속성 데이터가 포함됩니다.
   * `services-id` - 샌드박스 및 프로덕션 API 키를 사용하여 Adobe Commerce 인스턴스를 [Adobe Commerce SaaS](../landing/saas.md)에 연결하고 Adobe Experience Platform에 연결하여 IMS 조직 ID를 검색합니다.
   * `orders-connector` - 주문 상태 서비스를 Adobe Commerce 인스턴스에 연결합니다.

1. (선택 사항) [검색 이벤트](events.md#search-events)를 구성하는 [!DNL Live Search] 데이터를 포함하려면 [[!DNL Live Search]](../live-search/install.md) 확장을 설치하십시오.

1. (선택 사항) [구매요청 이벤트](events.md#b2b-events)를 구성하는 B2B 데이터를 포함하려면 [B2B 확장](#install-the-b2b-extension)을 설치하십시오.

### Adobe I/O 이벤트 설치

`experience-platform-connector` 확장을 설치한 후에는 Adobe Commerce에 대한 Adobe I/O 이벤트를 설치해야 합니다.

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

클라우드 인프라의 Adobe Commerce에서 `.magento.env.yaml`에서 `ENABLE_EVENTING` 전역 변수를 사용하도록 설정합니다. [자세히 알아보기](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

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

B2B 판매자의 경우 [구매요청 목록](events.md#b2b-events) 이벤트 데이터를 포함하도록 다음 확장을 설치하십시오.

명령줄에서 다음을 실행하여 `magento/experience-platform-connector-b2b` 확장을 다운로드합니다.

```bash
composer require magento/experience-platform-connector-b2b
```

## [!DNL Data Connection] 확장 업데이트 {#update}

[!DNL Data Connection] 확장을 업데이트하려면 명령줄에서 다음을 실행하십시오.

```bash
composer update magento/experience-platform-connector --with-dependencies
```

또는 B2B 판매자의 경우:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

2.0.0에서 3.0.0으로 등 주요 버전으로 업데이트하려면 다음과 같이 프로젝트의 루트 [!DNL Composer] `.json` 파일을 편집하십시오.

1. 루트 `composer.json` 파일을 열고 `magento/experience-platform-connector`을(를) 검색합니다.

1. `require` 섹션에서 버전 번호를 다음과 같이 업데이트합니다.

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

## [!DNL Data Connection] 확장 제거 {#uninstall}

[!DNL Data Connection] 확장을 제거하려면 [제거 모듈](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html)을 참조하세요.
