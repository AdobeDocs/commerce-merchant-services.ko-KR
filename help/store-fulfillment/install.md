---
title: 설치
description: 설명 추가
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# 설치

초기 설치 완료 [!DNL Store Fulfillment] 예외 처리를 허용하도록 구성된 큐 관리자 실행 및 캐싱을 사용하는 비프로덕션 환경의 확장 Adobe Commerce 인스턴스의 운영 및 유지 관리에 대한 우수 사례를 보장하려면 환경에 다른 개발 도구가 포함되어 있어야 합니다.

## 전제 조건

를 검토합니다. [요구 사항](solution-requirements.md) 저장 이행 솔루션에 대한 정보를 수집하고 [!DNL Store Fulfillment] Adobe Commerce 확장.

Store Fulfillment for Adobe Commerce 확장의 시험판 또는 베타 버전을 설치한 경우 현재 버전을 설치하기 전에 제거하십시오.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## 설치 요구 사항

- **Walmart Commerce Technologies 소프트웨어 아카이브(.zip 파일)의 Store Fulfillment 액세스**-온보딩 및 사용 프로세스 중에 계정 관리자와 함께 Store Fulfillment 확장의 설치 파일에 액세스할 수 있습니다.

- **Adobe Commerce 계정 정보**-설치 중 [!DNL Channel Manager] 를 사용하려면 [상거래 계정](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. 에 대한 소유자 또는 관리자 액세스 권한이 있는 계정 ID 및 자격 증명이 필요합니다 [!DNL Adobe Commerce] 프로젝트.

- 대상 [!DNL Adobe Commerce] 클라우드 인프라 프로젝트에서 소프트웨어 설치 관리자는 클라우드 프로젝트에 대한 관리자 액세스 권한이 있어야 합니다. 자세한 내용은 [사용자 액세스 관리](https://devdocs.magento.com/cloud/project/user-admin.html).

- **작성기 및 를 사용한 경험[!DNL Commerce CLI]**- 자세한 내용은 [일반 CLI 설치](https://devdocs.magento.com/extensions/install/)이 도구를 사용하여 확장을 설치하고 관리하는 방법에 대한 자세한 내용은 {target=&quot;_blank&quot;} 를 참조하십시오 [!DNL Adobe Commerce] 플랫폼.

- **Adobe Commerce에 타사 확장 설치 경험**-자세한 내용은 Adobe Commerce 설명서를 참조하십시오.

   - [클라우드 인프라 인스턴스에 Adobe Commerce용 확장 설치](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension)

   - [Adobe Commerce 온-프레미스 인스턴스용 확장 설치](https://devdocs.magento.com/extensions/install/)

### 1단계: 확장 번들 다운로드

Store Fulfillment Services 확장을 설치하기 위한 Composer 패키지가 포함된 아카이브 파일을 다운로드하려면 계정 담당자가 제공하는 지침을 따르십시오.

### 2단계: 애플리케이션에 확장 객체 추출

통합 번들이 포함된 아카이브 파일을 추출하여 Store Fulfillment Services 확장을 설치합니다.

1. 추출된 파일에 대한 대상 디렉토리를 만듭니다.

   - 명령줄에서 웹 서버 문서 루트 디렉토리로 이동합니다.

   - 만들기 `artifacts` 디렉토리.

1. 아카이브 파일을 새 디렉토리에 추출합니다.

1. 파일 목록을 검토하여 추출된 파일을 확인합니다.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### 3단계: 작성기를 사용하여 앱 구성

Composer를 사용하여 설치에 대한 소스 디렉토리를 구성하고 Store Fulfillment Services 확장을 설치합니다.

1. 작성기 설치에 대한 소스 저장소를 구성합니다.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Store Fulfillment Services 확장 추가 `composer.json`

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Adobe Commerce 온-프레미스 인스턴스에서 성능을 향상시키기 위해 다음을 수행할 수 있습니다 [자동 로드 구성 업데이트](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### 4단계: 데이터베이스 스키마 및 데이터 업그레이드

를 사용하여 설치를 완료합니다 `bin/magento setup:upgrade` 저장 이행 솔루션을 지원하는 변경 사항으로 데이터베이스 스키마와 데이터를 업데이트하려면

>참고:
>클라우드 인프라 프로젝트에서 Adobe Commerce을 사용하려면 확장을 등록할 필요가 없습니다. 대신 이전 단계의 코드 변경 사항을 커밋하고 환경 분기에 푸시합니다. 데이터베이스 스키마와 데이터를 업데이트하는 명령은 클라우드 빌드 및 배포 프로세스 중에 자동으로 실행됩니다.

### 5단계: 설치 완료

1. 다음을 사용하여 Adobe Commerce에 확장을 등록합니다 `setup:upgrade` Magento CLI 명령.

   ```terminal
   bin/magento setup:upgrade
   ```

1. 메시지가 표시되면 다시 컴파일하십시오 [!DNL Commerce] 프로젝트.

   ```bash
   bin/magento setup:di:compile
   ```

1. 캐시를 지웁니다.

   ```bash
   bin/magento cache:clean
   ```

1. 유지 관리 모드를 비활성화합니다.

   ```bash
   bin/magento maintenance:disable
   ```

### 6단계: 설치 확인

Adobe Commerce 서버에서 Store Fulfillment Services 확장 모듈에 설치 및 활성화되어 있는지 확인합니다.

1. 서버에 로그인합니다.

   클라우드 인프라 상에 Adobe Commerce에 설치하는 경우 SSH를 사용하여 원격 환경에 로그인합니다.

1. Store Fulfillment Services 모듈이 활성화되어 있는지 확인합니다.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   출력에는 다음 모듈이 포함되어야 합니다.

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### 추가 단계

필요한 경우 [설정:static-content: 배포](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#setupstatic-contentdeploy) 운영 환경에 정적 뷰 파일을 배포하는 CLI 명령

```terminal
php bin/magento setup:static-content:deploy -f
```

다음 `-f` 빈 테마를 사용하는 경우 옵션이 필요합니다.

>[!NOTE]
>
>자세한 내용은 [Adobe Commerce에서 정적 콘텐츠 배포 우수 사례](https://support.magento.com/hc/en-us/articles/360031624091) ( Adobe Commerce 도움말 센터)

