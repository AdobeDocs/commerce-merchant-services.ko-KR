---
title: 쿠키 제한 처리
description: 제품 권장 사항이 쿠키 제한을 처리하는 방법을 알아봅니다.
exl-id: 2f48c47c-569b-455c-a589-8f99b7b74064
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# 쿠키 제한 처리

Adobe Commerce과 Magento Open Source 모두 데이터가 브라우저 쿠키에 저장되기 전에 동의를 요청합니다. 자세한 내용은 다음을 참조하십시오. [쿠키 제한 모드](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

배포 시 `magento/product-recommendations` 프로덕션에 모듈을 할당하면 상점 첫 화면에서 쇼핑객 인터랙션 이벤트를 수집하기 시작합니다. 이러한 이벤트에 대한 데이터는 브라우저 쿠키 또는 로컬 저장소에 저장될 수 있으므로, 이 기능은 구매자가 쿠키에 동의할 때까지 이벤트를 수집하지 않음으로써 쿠키 제한 모드를 지원합니다.

타사 쿠키 동의 솔루션에서는 작동하지 않을 수 있습니다. 법에서 종종 요구하는 대로, 쿠키 동의를 하기 전에 데이터 수집이 발생하지 않도록 하는 것은 각 판매자의 책임입니다. 사용자 지정 코드로 쿠키 동의를 관리하는 경우, `mg_dnt` 데이터 수집을 제한합니다.

- 쿠키 이름:

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- 데이터 수집을 비활성화하려면 추적 안 함 쿠키를 설정하십시오.

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- 사용자가 쿠키를 수락했을 때 쿠키를 지우려면 다음을 수행하십시오.

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
