---
title: 온보딩 및 설치
description: 설치 방법 알아보기 [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 747cf01eb9c270a727c970c4dec7dbec64a884fe
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# 온보딩 및 설치

카탈로그 서비스 프로세스에 대한 설명을 참조하십시오.

1부:

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

2부:

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## 전제 조건

에 대한 온보딩 프로세스 [!DNL Catalog Service] 서버의 명령줄에 대한 액세스 권한이 필요합니다. 명령줄 작업에 익숙하지 않은 경우 개발자 또는 시스템 통합자에게 도움을 요청하십시오.

### 소프트웨어 요구 사항

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- 작성기: 2.x

### 지원되는 플랫폼

- 클라우드 인프라의 Adobe Commerce: 2.4.4+
- Adobe Commerce 온프레미스: 2.4.4+

## 환경

카탈로그 서비스에는 온보딩에 사용할 수 있는 두 가지 환경이 있습니다.

- 샌드박스(https://catalog-service-sandbox.adobe.io/graphql) - 시작하기 전 테스트 및 유효성 검사에 사용됨
- 프로덕션(https://catalog-service.adobe.io/graphql)- 상거래 판매자 및 웹 사이트의 라이브 트래픽에 사용됨)

## 설치 및 구성

Adobe Commerce용 카탈로그 서비스를 시작하려면 다음 단계를 수행해야 합니다.

- 데이터 내보내기 확장 설치
- 서비스 및 데이터 내보내기 구성
- 서비스 액세스

### 데이터 내보내기 확장 설치

카탈로그 서비스에 대한 온보딩 프로세스를 수행하려면 서버의 명령줄에 액세스해야 합니다.

카탈로그 서비스 확장은 Adobe Commerce 클라우드 인프라와 온프레미스 인스턴스 모두에 설치할 수 있습니다.

카탈로그 서비스가 상거래 계정에 연결된 작성기 키와 함께 설치됩니다 [마게드](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) 등록 프로세스 중에 제공됩니다. Composer는 Adobe Commerce을 처음 설치하는 동안 또는 이전에 Composer 키가 외부에 저장되지 않은 상황에서 이 키를 사용합니다 `auth.json` 파일.

다음을 참조하십시오 [인증 키 받기](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) composer 키를 가져오는 방법에 대한 자세한 내용은 를 참조하십시오.

#### 클라우드 인프라의 Adobe Commerce

Commerce Cloud 인스턴스에 대한 카탈로그 서비스 확장을 설치하는 데 이 메서드를 사용합니다.

1. 를 엽니다. `<Commerce_root>/composer.json` 텍스트 편집기의 파일을 만들고 필수 섹션을 다음과 같이 업데이트합니다.

```json
"require": {
  "magento/catalog-service": "^1.0.2"
}
```

1. 로컬에서 새 구성을 테스트하고 종속성을 업데이트합니다.

```bash
composer update
```

이 명령은 모든 종속성을 업데이트합니다.

1. 변경 사항 커밋 및 푸시 `composer.json` 및 `composer.lock`.

#### 온-프레미스

온-프레미스 인스턴스에 대한 카탈로그 서비스 확장을 설치하는 데 이 방법을 사용합니다.

1. 를 엽니다. `<Commerce_root>/composer.json` 텍스트 편집기의 파일을 만들고 필수 섹션을 다음과 같이 업데이트합니다.

```json
"require": {
    "magento/catalog-service": "^1.0.2"
}
```

1. 종속성을 업데이트하고 확장을 설치합니다.

```bash
composer update
```

이 명령은 모든 종속성을 업데이트합니다.

1. Adobe Commerce 업그레이드:

```bash
bin/magento setup:upgrade
```

1. 캐시를 지웁니다.

```bash
bin/magento cache:clean
```

### 서비스 및 데이터 내보내기 구성

카탈로그 서비스를 설치한 후 다음을 구성해야 합니다. [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) api 키를 지정하고 SaaS 데이터 공간을 선택합니다.

SaaS 구성이 완료되면 다음을 수행하여 초기 데이터 동기화를 수행합니다. [카탈로그 동기화](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) 가이드.

카탈로그 내보내기가 올바르게 실행되는지 확인하려면 다음을 수행하십시오.

- cron 작업이 실행 중인지 확인합니다.
- 인덱서가 실행 중인지 확인합니다.
- 다음을 확인합니다. `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, 및 `Product Variant Feed` 인덱서가 &quot;일정별로 업데이트&quot;로 설정되어 있습니다.

초기 동기화는 카탈로그 크기에 따라 몇 분에서 몇 시간 정도 소요될 수 있습니다. 초기 동기화 후 카탈로그는 Commerce 서버의 제품 데이터를 Commerce 서비스로 내보내 서비스를 최신 상태로 유지합니다.

### 서비스 액세스

카탈로그 서비스 API는 HTTPS를 통해 POST 명령을 사용하여 액세스할 수 있습니다.

API 키를 가져오려면 관리자의 Commerce Service Connector 영역으로 이동하여 공개 API 키를 복사합니다.

읽기 [GraphQL 설명서](https://developer.adobe.com/commerce/webapi/graphql/) api 요청 생성에 필요한 헤더를 쿼리하고 전송하는 방법을 이해합니다.

## 카탈로그 서비스 및 API 메쉬

다음 [Adobe Developer 앱 빌더용 API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) 을 사용하면 개발자가 Adobe IO를 사용하여 개인 또는 서드파티 API 및 기타 인터페이스를 Adobe 제품과 통합할 수 있습니다.

다음을 참조하십시오.  [카탈로그 서비스 및 API 메쉬](mesh.md) 항목 설치 및 구성 세부 정보.
