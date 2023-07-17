---
title: "설치 [!DNL Quick Checkout] for Adobe Commerce extension"
description: "다음 단계에 따라 설치하십시오. [!DNL Quick Checkout] Adobe Commerce 을 참조하십시오."
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
feature: Checkout, Services, Install
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# 설치 [!DNL Quick Checkout]

다음 [!DNL Quick Checkout] Adobe Commerce 및 [!DNL Magento Open Source] 다음을 사용하여 설치 가능 [!DNL Composer keys]- 상거래 계정에 연결됨 [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} 은 등록 프로세스에서 제공됩니다. Composer는 Adobe Commerce을 처음 설치하는 동안 또는 [!DNL Composer keys] 이(가) 이전에 (으)로 저장되지 않았습니다. `auth.json` 파일.

다음을 참조하십시오 [인증 키 받기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} 항목 을 참조하십시오. [!DNL Composer keys].

이 확장을 설치하는 방법에는 두 가지가 있습니다. [클라우드 인프라의 Adobe Commerce](#magento-commerce-cloud) 또는 [온-프레미스](#on-premises) 설치. 이러한 방법을 사용하려면 명령줄 인터페이스(CLI)를 사용해야 합니다.

## 최소 안정성 설정 업데이트

확장을 설치하기 전에 `minimum-stability` 의 필드 `composer.json` 파일이 다음으로 설정됨 `"stable"`:

`"minimum-stability": "stable"`

## 확장 설치

다음을 설치할 수 있습니다. [!DNL Quick Checkout] Adobe Commerce on cloud infrastructure 및 온-프레미스 인스턴스 둘 다에 대한 확장.

### 클라우드 인프라의 Adobe Commerce

이 메서드는 다음을 설치하는 데 사용됩니다. [!DNL Quick Checkout] Commerce Cloud 인스턴스에 대한 확장입니다.

1. 로컬 워크스테이션에서 클라우드 프로젝트 루트 디렉터리로 변경합니다.

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

이 메서드는 다음을 설치하는 데 사용됩니다. [!DNL Quick Checkout] 온-프레미스 인스턴스에 대한 확장.

1. 빠른 체크아웃 모듈을 `require` 의 섹션 `composer.json` 파일:

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

1. 캐시를 지웁니다.

   ```bash
   bin/magento cache:clean
   ```

1. 변경 사항을 커밋합니다.
1. 커밋된 코드가 배포되도록 온-프레미스 인스턴스를 업데이트합니다.

## 확장 업그레이드

의 새 버전을 릴리스할 때 [!DNL Quick Checkout]를 클릭하여 확장을 쉽게 업그레이드할 수 있습니다.

1. 패키지의 최신 버전을 얻으려면:

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/quick-checkout`.

1. 변경 사항을 커밋하고 푸시합니다.

## 문제 해결

설치를 시도할 때 오류가 표시될 수 있습니다. [!DNL Quick Checkout] 확장명.

다음 작업 중에 문제가 발생하는 경우 [!DNL Quick Checkout] 설치 프로세스, 참조 [빠른 체크아웃 문제 해결](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) Adobe Commerce 도움말 센터

## 전제 조건

다음을 참조하십시오. [전제 조건](../quick-checkout/prerequisites.md) 항목 을 참조하십시오.
