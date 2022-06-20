---
title: Adobe Commerce에서 Adobe Experience Platform 커넥터 설치 및 구성
description: Adobe Commerce에서 Adobe Experience Platform 커넥터를 설치, 구성, 업데이트 및 제거하는 방법을 알아봅니다.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Experience Platform 커넥터 설치 및 구성

확장을 설치하기 전에 [전제 조건 검토](overview.md#prereqs).

## 확장 설치

1. Experience Platform 커넥터 메타패키지를 설치합니다.

   ```bash
   composer require magento/platform-connector
   ```

   이 메타 태그는 다음 모듈을 포함합니다.

   * `module-platform-connector-admin` - 관리자 UI 업데이트
   * `module-platform-connector` - 을 설정합니다. `ImsOrgId` 및 `datastreamId` Magento Storefront 이벤트 SDK에서

1. 프로필 및 체크아웃 이벤트를 포함하도록 상거래 데이터 서비스 확장을 설치합니다.

   ```bash
   composer require magento/data-services
   ```

   Commerce Data Services 확장은 상점 이벤트에 대한 속성 컨텍스트를 제공합니다. 예를 들어 체크아웃 이벤트가 발생하면 장바구니에 있었던 항목 수와 해당 항목에 대한 제품 속성 데이터가 포함된 정보입니다.

1. Commerce Service Connector를 설치합니다.

   ```bash
   composer require magento/commerce-services
   ```

   상거래 서비스 커넥터를 사용하면 Adobe Commerce 인스턴스를 [Adobe Commerce SaaS](../landing/saas.md) Adobe Experience Platform에 연결할 수도 있습니다.

1. (선택 사항) 다음을 포함합니다 [!DNL Live Search] 검색 이벤트를 포함하는 데이터를 설치합니다 [[!DNL Live Search]](../live-search/install.md) 확장.

## Experience Platform 커넥터 업데이트 {#update}

Experience Platform 커넥터를 업데이트하려면 명령줄에서 다음을 실행합니다.

```bash
composer update magento/platform-connector --with-dependencies
```

1.0.0에서 2.0.0과 같은 주요 버전으로 업데이트하려면 프로젝트의 루트를 편집하십시오 [!DNL Composer] `.json` 파일:

1. 루트 열기 `composer.json` 파일 및 검색 `magento/platform-connector`.

1. 에서 `require` 섹션에서 버전 번호를 다음과 같이 업데이트합니다.

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **저장** `composer.json`. 그런 다음 명령줄에서 다음을 실행합니다.

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Experience Platform 커넥터 제거 {#uninstall}

Experience Platform 커넥터를 제거하려면 다음을 참조하십시오. [모듈 제거](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
