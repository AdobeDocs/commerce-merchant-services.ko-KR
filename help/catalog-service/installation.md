---
title: '"온보딩 및 설치"'
description: '"설치 방법 알아보기 [!DNL Catalog Service]"'
source-git-commit: 7f6955ffc52669ff3b95957642b3a115bf1eb741
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# 온보딩 및 설치

파트너와 고객은 Adobe Analytics Mobile Apps 또는 Analytics Premium에서 [!DNL Catalog Service] 2022년 8월 9일에 릴리스된 Adobe Commerce 베타 버전입니다. 참여하려면, Adobe의 [Adobe Commerce 베타 프로그램 용어](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

계약서에 서명하면 다음 사항에 대해 우리 팀에 문의하십시오. [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) 공개 Slack 채널. Adobe에서는 을(를) 사용하여 작업하는 데 필요한 모든 정보와 다음 단계를 제공합니다. [!DNL Catalog Service] 베타 버전.

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

다음 [!DNL Catalog Service] 는 Magento ID([자이드](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 등록 프로세스에서 제공됩니다. 작성기는 초기 설치 중에 이러한 키를 사용합니다 [!DNL Adobe Commerce]또는 작성기 키가 이전에 `auth.json` 파일.

자세한 내용은 [인증 키 가져오기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 작성기 키 가져오기에 대한 자세한 정보.

### Adobe Commerce on cloud 인프라

을 설치하는 데 이 방법 사용 [!DNL Catalog Service] 확장)을 사용할 수 있습니다.

1. 를 엽니다. `<Commerce_root>/composer.json` 파일을 텍스트 편집기에 넣고 `require` 섹션을 다음과 같이 참조하십시오.

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   명령은 모든 종속성을 업데이트합니다.

1. 변경 사항을 커밋하고 푸시합니다.

### 온-프레미스

을 설치하는 데 이 방법 사용 [!DNL Catalog Service] 온-프레미스 인스턴스에 대한 확장.

1. 를 엽니다. `<Commerce_root>/composer.json` 파일을 텍스트 편집기에 넣고 `require` 섹션을 다음과 같이 참조하십시오.

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
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

## 카탈로그 내보내기 구성

설치 후 [!DNL Catalog Service], 다음을 구성해야 합니다. [Commerce Services 커넥터](../landing/saas.md) API 키를 지정하고 SaaS 데이터 공간 선택

카탈로그 내보내기가 올바르게 실행되는지 확인하려면 [직장](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 그리고 [인덱서](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 가 실행 중이며 제품 피드 인덱서가 예약별 업데이트로 설정되어 있습니다.
