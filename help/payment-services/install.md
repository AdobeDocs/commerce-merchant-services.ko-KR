---
title: 설치 [!DNL Payment Services]
description: Payments Services 확장을 설치합니다.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# 설치 [!DNL Payment Services]

설치 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 는 사용하기 위한 사전 요구 단계입니다 [!DNL Payment Services].

![[!DNL Payment Services] 확장 관리자 보기](assets/admin-view.png)

다음 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] Magento ID([자이드](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 등록 프로세스에서 제공됩니다. 작성기는 초기 설치 중에 이러한 키를 사용합니다 [!DNL Adobe Commerce]또는 작성기 키가 이전에 `auth.json` 파일.

자세한 내용은 [인증 키 가져오기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 작성기 키 가져오기에 대한 자세한 정보.

이 확장을 설치하는 두 가지 방법이 있습니다. [[!DNL Adobe Commerce] 클라우드 인프라](install.md#adobe-commerce-on-cloud-infrastructure) 또는 [온-프레미스](install.md#on-premises) 설치. 이러한 방법에서는 CLI(명령줄 인터페이스)를 사용해야 합니다.

## 최소 안정성 설정 업데이트

확장을 설치하기 전에 `minimum-stability` 요구 사항 `RC` (릴리스 후보)를 사용 중인 `composer.json` 파일. IDE나 즐겨찾는 텍스트 편집기(예: Visual Studio 코드 또는 Giabliant 텍스트)를 사용할 수 있습니다.

사용자 `composer.json` 파일, 변경 `"minimum-stability": "stable"` to `"minimum-stability": "RC"`.

## 확장 설치

을(를) 설치할 수 있습니다 [!DNL Payment Services] 둘 다 확장 [!DNL Adobe Commerce] 클라우드 인프라 및 온-프레미스 인스턴스에서 사용됩니다.

### [!DNL Adobe Commerce] 클라우드 인프라

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Payment Services] 확장)을 사용할 수 있습니다.

1. 업데이트 `composer.json` 파일:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer require magento/payment-services`.

1. 변경 사항을 커밋하고 푸시합니다.

### 온-프레미스

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Payment Services] 확장 프로그램 을 사용하십시오.

1. 확장을 가져오려면 다음 명령을 실행합니다.

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer require magento/payment-services`.

1. 업그레이드 [!DNL Adobe Commerce]:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시 지우기:

   ```bash
   bin/magento cache:clean
   ```

1. 변경 사항을 커밋합니다.
1. 커밋된 코드가 배포되었는지 확인하려면 온-프레미스 인스턴스 를 업데이트하십시오.

## 확장 업그레이드

새 버전의 [!DNL Payment Services] 가 출시되면 확장을 쉽게 업그레이드할 수 있습니다.

1. 패키지의 최신 버전을 가져오려면 다음을 수행하십시오.

   ```bash
   composer update
   ```

   다음 `composer update` 명령은 모든 종속성을 업데이트합니다. 모든 종속성을 동시에 업데이트하지 않으려면 이 명령을 대신 사용하십시오. `composer update magento/payment-services`.

1. 변경 사항을 커밋하고 푸시합니다.

## 문제 해결

설치를 시도할 때 오류가 표시될 수 있습니다 [!DNL Payment Services] 확장. 다음 문제 해결 방법을 사용하여 오류를 해결하십시오.

### 잘못된 작성기 키

잘못된 작성기 키가 있음을 나타내는 다음 오류가 표시되는 경우:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

작성기 키가 [!DNL Payment Services] 등록.

구성된 작성기 키를 보려면 다음을 수행하십시오.

1. 의 위치 찾기 `auth.json` 파일:

   ```bash
   composer config --global home
   ```

1. 보기 `auth.json` 파일:

   ```bash
   cat /path/to/auth.json
   ```

1. 자세한 내용은 [Magento ID와 연결된 키는 무엇입니까?](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### PHP에 대한 메모리가 부족합니다.

다음 오류가 표시되면 PHP에 대한 메모리가 부족합니다.

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[메모리 제한 증가](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) PHP용 `php.ini`.

또는 다음 명령을 사용하여 메모리 제한을 지정할 수 있습니다. `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
