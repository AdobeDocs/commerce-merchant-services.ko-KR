---
title: Adobe Commerce에서 Adobe Experience Platform 커넥터 설치 및 구성
description: Adobe Commerce에서 Adobe Experience Platform Connector를 설치, 구성, 업데이트 및 제거하는 방법을 알아봅니다.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 0c8d9498ea7a30a99f834694ef8a865ad24466ab
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Experience Platform 커넥터 설치 및 구성

확장을 설치하기 전에 [사전 요구 사항 검토](overview.md#prereqs).

## 확장 설치

Experience Platform 커넥터 확장은 [Adobe 마켓플레이스](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). 서버의 명령줄에서 이 확장을 설치하면 Adobe Commerce 설치에 다음과 같이 연결됩니다. [서비스](../landing/saas.md). 프로세스가 완료되면 **Experience Platform 커넥터** 및 **Commerce Services 커넥터** 다음에 표시: **시스템** 아래 메뉴 **서비스** 상거래 내 _관리자_.

>[!NOTE]
>
>![Adobe Commerce용 B2B](../assets/b2b.svg) B2B 판매자의 경우 별도의 확장을 설치해야 합니다. 이 확장은 B2B 관련 이벤트에 대한 지원을 추가합니다. [자세히 알아보기](#install-the-b2b-extension).


1. 다운로드하려면 `experience-platform-connector` package, 명령줄에서 다음을 실행합니다.

   ```bash
   composer require magento/experience-platform-connector
   ```

   이 메타패키지에는 다음 모듈 및 확장이 포함되어 있습니다.

   * `module-experience-connector-admin` - 특정 Adobe Commerce 인스턴스에 대한 데이터 스트림 ID를 선택할 수 있도록 관리 UI를 업데이트합니다.
   * `module-experience-connector` - 를 설정합니다. `Organization ID` 및 `datastreamId` Storefront Events SDK에서
   * `data-services` - storefront 이벤트에 대한 특성 컨텍스트를 제공합니다. 예를 들어 체크아웃 이벤트가 발생하면 장바구니에 들어 있는 항목 수에 대한 정보와 해당 항목에 대한 제품 속성 데이터가 포함됩니다.
   * `services-id` - Adobe Commerce 인스턴스를 [Adobe Commerce SaS](../landing/saas.md) 샌드박스 및 프로덕션 API 키와 Adobe Experience Platform을 사용하여 IMS 조직 ID 검색

1. (선택 사항) [!DNL Live Search] 검색 이벤트를 구성하는 데이터 [[!DNL Live Search]](../live-search/install.md) 확장명.

### B2B 확장 설치

B2B 판매자의 경우 다음 확장을 설치하여 다음을 포함합니다. [징발 목록](events.md#b2b-events) 이벤트 데이터.

다운로드 `magento/experience-platform-connector-b2b` 명령줄에서 다음을 실행하여 확장하십시오.

```bash
composer require magento/experience-platform-connector-b2b
```

## Experience Platform 커넥터 업데이트 {#update}

Experience Platform 커넥터를 업데이트하려면 명령줄에서 다음을 실행합니다.

```bash
composer update magento/experience-platform-connector --with-dependencies
```

또는 B2B 판매자의 경우:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

1.0.0에서 2.0.0으로 등 주요 버전으로 업데이트하려면 프로젝트의 루트를 편집합니다 [!DNL Composer] `.json` 파일을 다음과 같이 지정합니다.

1. 루트 열기 `composer.json` 파일 및 검색 `magento/experience-platform-connector`.

1. 다음에서 `require` 섹션에서 버전 번호를 다음과 같이 업데이트합니다.

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
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

## Experience Platform 커넥터 제거 {#uninstall}

Experience Platform 커넥터를 제거하려면 다음을 참조하십시오 [모듈 제거](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
