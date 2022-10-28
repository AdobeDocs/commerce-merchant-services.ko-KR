---
title: 쿠키 제한 처리
description: 제품 추천이 쿠키 제한을 처리하는 방법을 알아봅니다.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 쿠키 제한 처리

Adobe Commerce과 Magento Open Source 모두 데이터가 브라우저 쿠키에 저장되기 전에 동의를 요청합니다. 자세한 내용은 [쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

를 배포할 때 `magento/product-recommendations` 프로덕션에 대한 모듈로서, 상점 전면에서 쇼핑객의 상호 작용 이벤트를 수집하기 시작합니다. 이러한 이벤트에 대한 데이터는 브라우저 쿠키 또는 로컬 저장소에 저장할 수 있으므로 이 기능은 구매자가 쿠키 동의를 제공할 때까지 이벤트를 수집하지 않음으로써 쿠키 제한 모드를 지원합니다.

타사 쿠키 동의 솔루션에서는 작동하지 않을 수 있습니다. 법에 의해 요구되는 경우가 많으므로 쿠키 동의가 있기 전에 데이터 수집이 발생하지 않도록 하는 것은 각 상인의 책임입니다. 사용자 지정 코드로 쿠키 동의를 관리하는 경우 `mg_dnt` 데이터 수집을 제한하기 위해

- 쿠키 이름:

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- 데이터 수집을 비활성화하려면 do-not-track 쿠키를 설정합니다.

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- 사용자가 쿠키를 수락했을 때 쿠키를 지우려면:

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
