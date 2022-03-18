---
title: 설치 [!DNL Express Checkout] Adobe Commerce 확장 프로그램
description: 다음 단계에 따라 을(를) 설치합니다 [!DNL Upgrade Compatibility Tool] Adobe Commerce 프로젝트에 사용할 수 있습니다.
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# 설치 [!DNL Express Checkout]

>[!IMPORTANT]
>
> 이 기능은 EAP(Early Adopter Program) 사용자만 사용할 수 있으며 모든 고객이 아직 액세스할 수 없습니다. 현재 미국 고객에게만 제공됩니다. 도움이 필요한 경우 Adobe Commerce 지원 센터에 문의하십시오.

다음 [!DNL Express Checkout] Adobe Commerce의 경우 일회용 게스트 구매자를 단골 고객 보유자로 전환하도록 디자인된 원활한 체크아웃 환경을 제공합니다.

다음 [!DNL Express Checkout] Adobe Commerce 및 Magento Open Source용 확장은 작성기 키와 함께 설치할 수 있으며 [Magento ID(mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions)등록 프로세스에 제공된 {target=&quot;_blank&quot;}. 작성기는 Adobe Commerce의 초기 설치 중에 또는 작성기 키가 이전에 `auth.json` 파일.

자세한 내용은 [인증 키 가져오기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)작성기 키 가져오기에 대한 자세한 내용은 {target=&quot;_blank&quot;} 를 참조하십시오.

이 확장을 설치하는 두 가지 방법이 있습니다. [Adobe Commerce on cloud 인프라](#magento-commerce-cloud) 또는 [온-프레미스](#on-premises) 설치. 이러한 방법에서는 CLI(명령줄 인터페이스)를 사용해야 합니다.

## 최소 안정성 설정 업데이트

확장을 설치하기 전에 `minimum-stability` 요구 사항 `RC` (릴리스 후보)를 사용 중인 `composer.json` 파일 을 사용하십시오. IDE나 즐겨찾는 텍스트 편집기(예: Visual Studio 코드 또는 Giabliant 텍스트)를 사용할 수 있습니다.

사용자 `composer.json` 파일, 변경 `"minimum-stability": "stable"` to `"minimum-stability": "RC"`.

## 확장 설치

을(를) 설치할 수 있습니다 [!DNL Express Checkout] 클라우드 인프라 및 온프레미스 인스턴스 둘 다에 대한 Adobe Commerce 확장.

### Adobe Commerce on cloud 인프라

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Express Checkout] 확장)을 사용할 수 있습니다.

1. 로컬 워크스테이션에서 클라우드 프로젝트 루트 디렉토리로 변경합니다.

1. 업데이트 `composer.json` 파일:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/express-checkout`.

1. 변경 사항을 커밋하고 푸시합니다.

### 온-프레미스

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Express Checkout] 확장 프로그램 을 사용하십시오.

1. 에 Express Checkout 모듈을 추가합니다. `require` 섹션 `composer.json` 파일:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/express-checkout`.

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

의 새 버전을 릴리스할 때 [!DNL Express Checkout]를 사용하면 확장을 쉽게 업그레이드할 수 있습니다.

1. 패키지의 최신 버전을 가져오려면 다음을 수행하십시오.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/express-checkout`.

1. 변경 사항을 커밋하고 푸시합니다.

## 문제 해결

설치를 시도할 때 오류가 표시될 수 있습니다 [!DNL Express Checkout] 확장.

자세한 내용은 [문제 해결](../express-checkout/troubleshooting.md) 설치 시 문제가 발생하는 경우 참조할 항목을 제공합니다 [!DNL Express Checkout].

## 전제 조건

자세한 내용은 [전제 조건](../express-checkout/prerequisites.md) 주제 를 참조하십시오.
