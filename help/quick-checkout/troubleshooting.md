---
title: '"문제 해결 [!DNL Quick Checkout]"'
description: '"오류 문제 해결, [!DNL Quick Checkout] Adobe Commerce 확장을 위한"'
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# 문제 해결 [!DNL Quick Checkout] Adobe Commerce

다음의 문제 해결 방법을 사용하여 이러한 특정 문제를 해결하십시오.

## 잘못된 [!DNL Composer keys]

다음 오류가 표시된다면 오류가 있음을 나타냅니다 [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

다음 사항을 확인합니다. [!DNL Composer keys] 빠른 체크아웃 등록 중에 사용되는 Magento ID에 연결됩니다.

어떤 항목을 [!DNL Composer keys] 구성됨:

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

다음 오류가 표시된다면 오류가 있음을 나타냅니다 [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

최소 안정성을 로 설정 `RC` 에서 `composer.json` 파일.

## PHP에 대한 메모리가 부족합니다.

다음 오류가 표시되면 PHP에 대한 메모리가 부족합니다.

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[메모리 제한 증가](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) PHP용 `php.ini`.

또는 다음 명령을 사용하여 메모리 제한을 지정할 수 있습니다. `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

For example:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## 잘못된 배송 주소

에 대해 알려진 문제가 있습니다 [!DNL Quick Checkout].

기본 배송 주소가 올바르지 않으면 고객이 배송 주소 단계로 리디렉션됩니다. Storefront에는 유효한 배송 주소만 표시됩니다.

>[!WARNING]
>
> 유효한 배송 주소가 없는 경우 고객에게 사용 가능한 배송 주소가 표시되지 않습니다.

자세한 내용은 [배송 세부 사항](../quick-checkout/shipping-details.md) 주제 를 참조하십시오.

## 새 배송 주소가 있는 주소 라인을 추가합니다

에 대해 알려진 문제가 있습니다 [!DNL Quick Checkout].

다음 경우에 [로 로그인 [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) 주소 당 4개의 행을 제한하는 새 배송 주소를 추가할 수 있습니다.

Adobe Commerce은 일반적으로 최대 20개의 주소 라인을 지원하도록 구성할 수 있습니다.

## 확인란 `enable terms and conditions` 제대로 표시되지 않음

에 대해 알려진 문제가 있습니다 [!DNL Quick Checkout].

를 활성화하면 `Enable terms and conditions` 관리자에서 확인란을 선택하고 [!DNL Bolt] 계정, `Enable terms and conditions` 체크 아웃 중에는 확인란이 표시되지 않습니다. 자세한 내용은 [로그인](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] 주제 를 참조하십시오.

자세한 내용은 [약관](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) 관리자 구성에 대한 자세한 내용을 보려면 를 참조하십시오.

## 다음 경우에 예기치 않은 동작이 발생합니다. `Display Billing Address On` 가 로 설정되어 있습니다. `payment page`

에 대해 알려진 문제가 있습니다 [!DNL Quick Checkout].

를 설정하는 경우 `Display Billing Address On` 매개 변수 대상 `payment page` 및 [을 사용하여 로그인 [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) 확인할 때 `My billing and shipping address are the same` 라디오 단추가 표시되는 확인란 `use existing card`.

![동일한 주소](assets/checked-address.png)

자세한 내용은 [체크아웃](https://docs.magento.com/user-guide/configuration/sales/checkout.html) 항목 을 참조하십시오 `Display Billing Address On` 매개 변수.

## 번역 [!DNL Quick Checkout] 확장

Adobe Commerce을 사용하면 여러 지역 및 시장에 대해 스토어를 현지화할 수 있습니다. 관리자 보기에서 오류 메시지를 현지화할 수도 있습니다.

자세한 내용은 [번역 및 현지화](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) 주제 를 참조하십시오.

## 캐시 초기화

1. 다음으로 이동 **[!UICONTROL System]** > **[!UICONTROL Cache Management]** 을(를) 클릭합니다. **[!UICONTROL Flush Cache]** 잘못된 캐시를 모두 새로 고치려면

## 지원 요청

연락처 [Adobe Commerce 지원](mailto:quick-checkout-support@adobe.com) 지원 요청.
