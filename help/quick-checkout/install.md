---
title: '"설치 [!DNL Quick Checkout] Adobe Commerce 확장 프로그램'
description: '"다음 단계에 따라 설치합니다 [!DNL Quick Checkout] Adobe Commerce 프로젝트에서 다음을 수행하십시오."'
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 27e91a640999cf83a0f0d6701e616f7ceecde12d
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# 설치 [!DNL Quick Checkout]

다음 [!DNL Quick Checkout] Adobe Commerce 및 Magento Open Source용 확장은 [!DNL Composer keys]: [Magento ID(mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions)등록 프로세스에 제공된 {target=&quot;_blank&quot;}. 작성기는 Adobe Commerce의 초기 설치 중에 또는 [!DNL Composer keys] 이 이전에 `auth.json` 파일.

자세한 내용은 [인증 키 가져오기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} 항목을 참조하십시오 [!DNL Composer keys].

이 확장을 설치하는 두 가지 방법이 있습니다. [Adobe Commerce on cloud 인프라](#magento-commerce-cloud) 또는 [온-프레미스](#on-premises) 설치. 이러한 방법에서는 CLI(명령줄 인터페이스)를 사용해야 합니다.

## 최소 안정성 설정 업데이트

확장을 설치하기 전에 `minimum-stability` 필드 `composer.json` 파일이 `"stable"`:

`"minimum-stability": "stable"`

## 확장 설치

을(를) 설치할 수 있습니다 [!DNL Quick Checkout] 클라우드 인프라 및 온프레미스 인스턴스 둘 다에 대한 Adobe Commerce 확장.

### Adobe Commerce on cloud 인프라

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Quick Checkout] 확장)을 사용할 수 있습니다.

1. 로컬 워크스테이션에서 클라우드 프로젝트 루트 디렉토리로 변경합니다.

1. 업데이트 `composer.json` 파일:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/quick-checkout`.

1. 변경 사항을 커밋하고 푸시합니다.

### 온-프레미스

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Quick Checkout] 확장 프로그램 을 사용하십시오.

1. 에 빠른 체크아웃 모듈 추가 `require` 섹션 `composer.json` 파일:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/quick-checkout`.

1. Adobe Commerce 업그레이드:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시 지우기:

   ```bash
   bin/magento cache:clean
   ```

1. 변경 사항을 커밋합니다.
1. 온-프레미스 인스턴스를 업데이트하여 커밋된 코드가 배포되었는지 확인합니다.

## 확장 업그레이드

의 새 버전을 릴리스할 때 [!DNL Quick Checkout]를 사용하면 확장을 쉽게 업그레이드할 수 있습니다.

1. 패키지의 최신 버전을 가져오려면 다음을 수행하십시오.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/quick-checkout`.

1. 변경 사항을 커밋하고 푸시합니다.

## 문제 해결

설치를 시도할 때 오류가 표시될 수 있습니다 [!DNL Quick Checkout] 확장.

다음 기간 동안 문제가 발생하는 경우 [!DNL Quick Checkout] 설치 프로세스 [빠른 체크아웃 문제 해결](https://support.magento.com/hc/en-us/articles/6909450342541) ( Adobe Commerce 도움말 센터)

## 전제 조건

자세한 내용은 [전제 조건](../quick-checkout/prerequisites.md) 주제 를 참조하십시오.
