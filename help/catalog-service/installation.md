---
title: 온보딩 및 설치
description: 설치 방법 알아보기 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: c740e75c9fe12b062683fa957d0c6623d8180e4f
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# 온보딩 및 설치

## 전제 조건

에 대한 온보딩 프로세스 [!DNL Catalog Service] 서버의 명령줄에 액세스해야 합니다. 명령줄에서 작업하는 방법을 잘 모를 경우 개발자나 시스템 통합자에게 도움을 요청하십시오.

### 소프트웨어 요구 사항

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- 작성기: 2.x, 1.x

### 지원되는 플랫폼

- Adobe Commerce on cloud 인프라: 2.4.x
- Adobe Commerce 온-프레미스: 2.4.x

## 확장 설치

을(를) 설치할 수 있습니다 [!DNL Catalog Service] 클라우드 인프라 및 온프레미스 인스턴스 둘 다에 대한 Adobe Commerce 확장.

다음 [!DNL Catalog Service] 은 상거래 계정에 연결된 작성기 키와 함께 설치됩니다 [자이드](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 등록 프로세스에서 제공됩니다. 작성기는 초기 설치 중에 이러한 키를 사용합니다 [!DNL Adobe Commerce]또는 작성기 키가 이전에 `auth.json` 파일.

자세한 내용은 [인증 키 가져오기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 작성기 키 가져오기에 대한 자세한 정보.

### Adobe Commerce on cloud 인프라

을 설치하는 데 이 방법 사용 [!DNL Catalog Service] 확장)을 사용할 수 있습니다.

1. 를 엽니다. `<Commerce_root>/composer.json` 파일을 텍스트 편집기에 넣고 `require` 섹션을 다음과 같이 참조하십시오.

   ```json
   "require":{
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/magento-cloud-metapackage":">=2.4.5 <2.4.6",
   "magento/catalog-service": "^1.0.0"
      }
   ```

1. 로컬에서 새 구성을 테스트하고 종속성을 업데이트합니다.

   ```bash
   composer update
   ```

   명령은 모든 종속성을 업데이트합니다.

1. 변경 내용 커밋 및 푸시 `composer.json` 및 `composer.lock`.

### 온-프레미스

을 설치하는 데 이 방법 사용 [!DNL Catalog Service] 온-프레미스 인스턴스에 대한 확장.

1. 를 엽니다. `<Commerce_root>/composer.json` 파일을 텍스트 편집기에 넣고 `require` 섹션을 다음과 같이 참조하십시오.

   ```json
   "require": {
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/catalog-service": "^1.0.0"
   }
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   명령은 모든 종속성을 업데이트합니다.

1. Adobe Commerce 업그레이드:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시 지우기:

   ```bash
   bin/magento cache:clean
   ```


## 카탈로그 서비스 및 API Mesh

다음 [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 개발자는 Adobe IO를 사용하여 개인 또는 타사 API 및 기타 인터페이스를 Adobe 제품과 통합할 수 있습니다.

API Mesh를 카탈로그 서비스와 함께 사용하는 첫 번째 단계는 API Mesh를 인스턴스에 연결하는 것입니다. 자세한 지침은 [메쉬 만들기](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

설정을 완료하려면 [Adobe IO CLI 패키지](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) 설치되었습니다.

Adobe IO에 Mesh가 구성되면 다음 명령을 실행하여 새 메쉬를 연결합니다.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph"
```

이 명령을 실행한 후 카탈로그 서비스가 API Mesh를 통해 실행되어야 합니다.

## 카탈로그 내보내기 구성

설치 후 [!DNL Catalog Service], 다음을 구성해야 합니다. [Commerce Services 커넥터](../landing/saas.md) API 키를 지정하고 SaaS 데이터 공간 선택

카탈로그 내보내기가 올바르게 실행되는지 확인하려면:

- 확인 [직장](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 실행 중입니다.
- 확인 [인덱서](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 실행 중입니다.
- 다음을 확인합니다. `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`, 및 `Product Variant Feed` 인덱서가 `Update by Schedule`.

## [!DNL Catalog Service] 데모

자세한 내용은 이 비디오 를 참조하십시오 [!DNL Catalog Service] 설치 및 테스트:

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
