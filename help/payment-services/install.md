---
title: 설치 [!DNL Payment Services]
description: Payments Services 확장을 설치합니다.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 4d6c9a3017575e9adbf5dc11cf0717511592dbcf
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# 설치 [!DNL Payment Services]

다운로드 및 설치 [!DNL Payment Services] 확장 [!DNL Adobe Commerce] 및 [!DNL Magento Open Source] 는 사용하기 위한 사전 요구 단계입니다 [!DNL Payment Services].

![[!DNL Payment Services] 확장 관리자 보기](assets/admin-view.png)

## 확장 다운로드

먼저 확장을 [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) 설치하기 전에

1. 로 이동합니다 [Commerce Marketplace의 결제 서비스 확장](https://marketplace.magento.com/magento-payment-services.html).
1. 버전과 버전을 선택하려면 을 전환합니다. **[!UICONTROL Edition]** 및 **[!UICONTROL Your store version]** 원하는 항목을 선택합니다.
1. 클릭 **[!UICONTROL Add to Cart]**.
1. 체크 아웃을 완료하고 **[!UICONTROL Place Order]**.
1. 주문 확인 및 세부 사항은 Marketplace 다운로드와 연결된 이메일을 확인하십시오.

## 확장 설치

을(를) 설치할 수 있습니다 [!DNL Payment Services] 둘 다 확장 [!DNL Adobe Commerce] 상거래 계정에 연결된 클라우드 인프라 및 온-프레미스 인스턴스에서 액세스 [자이드](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) 등록 프로세스에서 제공됩니다. [!DNL Magento Open Source] 고객은 온-프레미스 지침을 사용합니다.

작성기는 초기 설치 중에 이러한 키를 사용합니다 [!DNL Adobe Commerce]또는 작성기 키가 이전에 `auth.json` 파일.

자세한 내용은 [인증 키 가져오기](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) 작성기 키 가져오기에 대한 자세한 정보.

자세한 내용은 [확장 설치](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) 확장을 다운로드하여 설치하기 전에 고려해야 할 사항에 대한 자세한 내용을 확인하십시오.

### [!DNL Adobe Commerce] 클라우드 인프라

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Payment Services] 확장)을 사용할 수 있습니다.

1. 업데이트 `composer.json` 파일:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   를 사용하십시오 `composer update` 모든 루트 종속성을 업데이트하는 명령입니다.

1. 변경 사항을 커밋하고 푸시합니다.

### 온-프레미스 및 기타 구성

이 메서드는 을 설치하는 데 사용됩니다 [!DNL Payment Services] 온-프레미스 인스턴스 및 [!DNL Magento Open Source] 고객.

1. 확장을 가져오려면 다음 명령을 실행합니다.

   ```bash
   composer require magento/payment-services --no-update
   ```

1. 종속성을 업데이트하고 확장을 설치합니다.

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   를 사용하십시오 `composer update` 모든 루트 종속성을 업데이트하는 명령입니다.

1. 인스턴스 업그레이드:

   ```bash
   bin/magento setup:upgrade
   ```

1. 캐시 지우기:

   ```bash
   bin/magento cache:clean
   ```

1. 변경 사항을 커밋합니다.
1. 커밋된 코드가 배포되었는지 확인하려면 인스턴스를 업데이트하십시오 .

## 확장 업그레이드

새 버전의 [!DNL Payment Services] 가 출시되면 확장을 쉽게 업그레이드할 수 있습니다.

1. 패키지의 최신 버전을 가져오려면 다음을 수행하십시오.

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   를 사용하십시오 `composer update` 모든 루트 종속성을 업데이트하는 명령입니다.

1. 변경 사항을 커밋하고 푸시합니다.

## 문제 해결

설치를 시도할 때 오류가 표시될 수 있습니다 [!DNL Payment Services] 확장. 다음 문제 해결 방법을 사용하여 오류를 해결하십시오.

### 잘못된 작성기 키

잘못된 작성기 키가 있음을 나타내는 다음 오류가 표시되는 경우:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

작성기 키가 유효하고 다른 Magento 패키지에 액세스할 수 있는지 확인합니다.

구성된 작성기 키를 보려면 다음을 수행하십시오.

1. 의 위치 찾기 `auth.json` 파일:

   ```bash
   composer config --global home
   ```

1. 보기 `auth.json` 파일:

   ```bash
   cat /path/to/auth.json
   ```

1. 자세한 내용은 [상거래 계정과 연결된 키는 무엇입니까? `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

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
