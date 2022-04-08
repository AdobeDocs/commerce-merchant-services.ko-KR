---
title: 문제 해결 [!DNL Express Checkout]
description: 오류 문제 해결. [!DNL Express Checkout] Adobe Commerce 확장
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 문제 해결 [!DNL Express Checkout] Adobe Commerce

>[!IMPORTANT]
>
> 이 기능은 EAP(Early Adopter Program) 사용자만 사용할 수 있으며 모든 고객이 아직 액세스할 수 없습니다. 현재 미국 고객에게만 제공됩니다. 도움이 필요한 경우 Adobe Commerce 지원 센터에 문의하십시오.

다음의 문제 해결 방법을 사용하여 이러한 특정 문제를 해결하십시오.

## 잘못된 작성기 키

잘못된 작성기 키가 있음을 나타내는 다음 오류가 표시되는 경우

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

작성기 키가 Express Checkout 등록 중에 사용되는 Magento ID에 연결되어 있는지 확인합니다.

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

## 의 최소 안정성 `composer.json` 안정으로 설정됨

잘못된 작성기 키가 있음을 나타내는 다음 오류가 표시되는 경우

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

최소 안정성을 로 설정 `RC` 에서 `composer.json` 파일.

## PHP에 대한 메모리가 부족합니다.

다음 오류가 표시되면 PHP에 대한 메모리가 부족합니다.

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[메모리 제한 증가](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) PHP용 `php.ini`.

또는 다음 명령을 사용하여 메모리 제한을 지정할 수 있습니다. `php -d memory_limit=-1 [path to composer]/composer require magento/express-checkout`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/express-checkout
```

## 잘못된 배송 주소

에 대해 알려진 문제가 있습니다 [!DNL Express Checkout].

기본 배송 주소가 올바르지 않으면 고객이 배송 주소 단계로 리디렉션됩니다. Storefront에는 유효한 배송 주소만 표시됩니다.

>[!WARNING]
>
> 유효한 배송 주소가 없는 경우 고객에게 사용 가능한 배송 주소가 표시되지 않습니다.

자세한 내용은 [배송 세부 사항](../express-checkout/shipping-details.md) 주제 를 참조하십시오.

## 새 배송 주소가 있는 주소 라인을 추가합니다

에 대해 알려진 문제가 있습니다 [!DNL Express Checkout].

다음 경우에 [볼트 계정으로 로그인](https://help.bolt.com/shoppers/guides/checkout/log-in/) 주소 당 4개의 행을 제한하는 새 배송 주소를 추가할 수 있습니다.

Adobe Commerce은 일반적으로 최대 20개의 주소 라인을 지원하도록 구성할 수 있습니다.

## 확인란 `enable terms and conditions` 제대로 표시되지 않음

에 대해 알려진 문제가 있습니다 [!DNL Express Checkout].

를 활성화하면 `Enable terms and conditions` 관리자에서 확인란을 선택하고 [!DNL Bolt] 계정, `Enable terms and conditions` 체크 아웃 중에는 확인란이 표시되지 않습니다. 자세한 내용은 [로그인](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] 페이지를 참조하십시오.

자세한 내용은 [약관](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) 관리자 구성에 대한 자세한 내용을 보려면 를 참조하십시오.

## 다음 경우에 예기치 않은 동작이 발생합니다. `Display Billing Address On` 가 로 설정되어 있습니다. `payment page`

에 대해 알려진 문제가 있습니다 [!DNL Express Checkout].

를 설정하는 경우 `Display Billing Address On` 매개 변수 대상 `payment page` 및 [볼트 계정으로 로그인](https://help.bolt.com/shoppers/guides/checkout/log-in/) 확인할 때 `My billing and shipping address are the same` 확인란:

![동일한 주소](assets/checked-address.png)

라디오 단추가 표시됩니다 `use existing card`.

자세한 내용은 [체크아웃](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 주제 `Display Billing Address On` 매개 변수.

## 번역 [!DNL Express Checkout] 확장

Adobe Commerce을 사용하면 여러 지역 및 시장에 대해 스토어를 현지화할 수 있습니다. 관리자 보기에서 오류 메시지를 현지화할 수도 있습니다.

자세한 내용은 [번역 및 현지화](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) 주제 를 참조하십시오.

## 지원 요청

도움이 필요하면 Adobe Commerce 지원 센터에 문의하십시오.
