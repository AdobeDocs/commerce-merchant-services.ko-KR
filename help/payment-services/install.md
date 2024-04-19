---
title: 설치 [!DNL Payment Services]
description: 결제 서비스 확장을 설치합니다.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 5c4fe370507e4154d4495d4c09e2ff8705e53191
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# 설치 [!DNL Payment Services]

다음에 대한 결제 서비스 사용을 시작하려면 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source], 몇 가지 온보딩 단계를 완료해야 합니다.

>[!INFO]
>
> 다음 참조: [구성 [!DNL Payment Services] Adobe Commerce용](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services) 비디오 를 참조하십시오.

다운로드 및 설치 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 은(는) 을 사용하기 위한 사전 요구 단계입니다. [!DNL Payment Services].

![[!DNL Payment Services] 확장 관리자 보기](assets/admin-view.png){width="300" zoomable="yes"}

## 확장 다운로드

먼저 다음에서 확장을 다운로드해야 합니다. [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) 설치하기 전에.

1. 다음 위치로 이동 [Commerce Marketplace의 결제 서비스 확장](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. 버전 및 버전을 선택하려면 **[!UICONTROL Edition]** 및 **[!UICONTROL Your store version]** 원하는 대로 선택할 수 있습니다.
1. 클릭 **[!UICONTROL Add to Cart]**.
1. 체크아웃을 완료하고 클릭 **[!UICONTROL Place Order]**.
1. 주문 확인 및 세부 사항은 Marketplace 다운로드와 연결된 이메일을 확인하십시오.

## 확장 설치

다음을 설치할 수 있습니다. [!DNL Payment Services] 둘 다 확장 [!DNL Adobe Commerce] Commerce 계정에 연결된 온클라우드 인프라 및 온프레미스 인스턴스 [마게드](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) 은 등록 프로세스에서 제공됩니다.
[!DNL Magento Open Source] 고객은 온-프레미스 지침을 사용합니다.

Composer는 초기 설치 중에 이 키를 사용합니다. [!DNL Adobe Commerce]또는 Composer 키가 이전에 `auth.json` 파일.

다음을 참조하십시오 [인증 키 받기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) composer 키를 가져오는 방법에 대한 자세한 내용은 를 참조하십시오.

다음을 참조하십시오 [확장 설치](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 확장을 다운로드하여 설치하기 전에 고려해야 할 사항에 대한 자세한 정보입니다.

### [!DNL Adobe Commerce] 클라우드 인프라에서

이 메서드는 다음을 설치하는 데 사용됩니다. [!DNL Payment Services] Commerce Cloud 인스턴스에 대한 확장입니다.

1. 업데이트 `composer.json` 파일:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   사용 `composer update` 모든 루트 종속성을 업데이트하는 명령입니다.

1. 변경 사항을 커밋하고 푸시합니다.

### 온-프레미스 및 기타 구성

이 메서드는 다음을 설치하는 데 사용됩니다. [!DNL Payment Services] 온-프레미스 인스턴스 및 [!DNL Magento Open Source] 고객.

1. 확장을 가져오려면 다음 명령을 실행합니다.

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   사용 `composer update` 모든 루트 종속성을 업데이트하는 명령입니다.

1. 인스턴스 업그레이드:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시를 지웁니다.

   ```bash
   bin/magento cache:clean
   ```

1. 변경 사항을 커밋합니다.
1. 커밋된 코드가 배포되었는지 확인하려면 인스턴스 를 업데이트합니다.

## 확장 업그레이드

의 새 버전일 때 [!DNL Payment Services] 이(가) 출시되었으므로 확장을 쉽게 업그레이드할 수 있습니다.

1. 패키지의 최신 버전을 얻으려면:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   사용 `composer update` 모든 루트 종속성을 업데이트하는 명령입니다.

1. 변경 사항을 커밋하고 푸시합니다.

## 문제 해결

설치를 시도할 때 오류가 표시될 수 있습니다. [!DNL Payment Services] 확장명. 다음 문제 해결 방법을 사용하여 오류를 해결하십시오.

### 잘못된 작성기 키

잘못된 작성기 키가 있음을 나타내는 다음 오류가 표시되면

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

작성기 키가 유효하고 다른 Magento 패키지에 액세스할 수 있는지 확인하십시오.

구성된 Composer 키를 보려면 다음 작업을 수행하십시오.

1. 의 위치 찾기 `auth.json` 파일:

   ```bash
   composer config --global home
   ```

1. 보기 `auth.json` 파일:

   ```bash
   cat /path/to/auth.json
   ```

1. 다음을 참조하십시오 [Commerce 계정과 연결된 키 `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### 메모리가 부족하여 PHP를 사용할 수 없습니다.

PHP에 대한 충분한 메모리가 없다는 것을 나타내는 다음 오류가 표시됩니다.

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[메모리 제한 늘리기](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) 의 환경에 있는 PHP용 `php.ini`.

또는 다음 명령을 사용하여 메모리 제한을 지정할 수 있습니다. `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
