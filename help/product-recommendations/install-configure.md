---
title: 설치 및 구성
description: 설치, 업데이트 및 제거 방법 알아보기 [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# 설치 및 구성

배포 [!DNL Product Recommendations] storefront 및 관리자에게 모듈을 설치하고 [Commerce Services 커넥터](../landing/saas.md). 업데이트가 릴리스되면 설치를 최신 버전으로 쉽게 업데이트할 수 있습니다.

- [설치](#install)
- [Configure](#configure)
- [업데이트](#update)
- [제거](#uninstall)

## 설치 [!DNL Product Recommendations] {#install}

이유: [!DNL Product Recommendations] 모듈은 독립 실행형 메타패키지이며 Adobe Commerce보다 업데이트가 더 자주 릴리스됩니다. 최신 버그 수정 및 기능을 확인하려면 다음을 참조하십시오. [릴리스 정보](release-notes.md).

설치 `magento/product-recommendations` 작성기가 있는 모듈:

```bash
composer require magento/product-recommendations
```

### 페이지 빌더 지원 추가 {#pbsupport}

[!DNL Product Recommendations] for Page Builder는 선택적 모듈이며 별도로 설치됩니다. 사용 [!DNL Product Recommendations] page Builder를 사용하여 다음 명령을 실행하여 모듈을 설치합니다.

```bash
composer require magento/module-page-builder-product-recommendations
```

활성화하여 [!DNL Product Recommendations] 페이지 빌더에서 기존의 활성 상태를 추가할 수 있습니다 [추천 단위](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 페이지, 블록 및 다이내믹 블록과 같이 페이지 빌더에서 만든 모든 콘텐츠입니다.

다음을 참조하십시오 [사용 [!DNL Product Recommendations] 페이지 빌더 콘텐츠 포함](page-builder.md) 추가 지침을 보려면.

### 시각적 유사성 추천 유형 추가 {#vissimsupport}

다음 _시각적 유사성_ 권장 사항 유형 을 사용하면 다음과 같은 제품을 표시하는 제품 세부 사항 페이지에 권장 사항 단위를 배포할 수 있습니다. [외관상 비슷하](type.md#visualsim) 보고 있는 제품에 연결합니다. 이 권장 사항 유형은 제품의 이미지와 시각적 측면이 쇼핑 경험의 중요한 부분인 경우 가장 유용합니다. 설치 _시각적 유사성_ 다음 명령을 실행하여 권장 사항 유형:

```bash
composer require magento/module-visual-product-recommendations
```

## Configure [!DNL Product Recommendations] {#configure}

를 설치한 후 `magento/product-recommendations` 모듈에서는 다음을 구성해야 합니다 [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) api 키를 지정하고 SaaS 데이터 공간을 선택합니다.

카탈로그 내보내기가 올바르게 실행되는지 확인하려면 [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 작업 및 [인덱서](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 실행 중이며 `Product Feed` 인덱서가 (으)로 설정됨 `Update by Schedule`.

API 키를 통해 Commerce Services에 성공적으로 연결하고 SaaS 데이터 공간을 지정하면 카탈로그 동기화가 시작됩니다. 그런 다음 [확인](verify.md) 해당 동작 데이터가 상점 앞으로 전송됩니다.

## 업데이트 [!DNL Product Recommendations] 설치 {#update}

Adobe Commerce 모두와 마찬가지로 [!DNL Product Recommendations] 는 설치 및 업데이트에 Composer를 사용합니다. 를 업데이트하려면 `magento/product-recommendations` 모듈에서 다음을 실행합니다.

```bash
composer update magento/product-recommendations --with-dependencies
```

3.0에서 4.0으로 업데이트와 같은 주요 버전으로 업데이트하려면 루트를 편집해야 합니다 `composer.json` 프로젝트용 파일입니다. (다음을 참조하십시오. [릴리스 정보](release-notes.md) 최신 버전에 대한 정보를 보려면.) 예를 들어 메인을 엽시다 `composer.json` 파일 및 검색 `magento/product-recommendations` 모듈:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

주요 버전을 다음에서 미리 살펴보도록 하겠습니다. `3.0` 끝 `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

저장 `composer.json` 파일 및 실행:

```bash
composer update magento/product-recommendations --with-dependencies
```

또는 을 설치한 경우 `magento/module-visual-product-recommendations` 및 `magento/module-page-builder-product-recommendations` 모듈:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> Product Recommendations 버전 3.x.x에서는 단일 API 키만 있으면 됩니다. 버전 4.x.x 이상에서는 프로덕션 공개 및 개인 API 키와 샌드박스 공개 및 개인 API 키를 제공해야 합니다. 두 쌍의 API 키를 모두 제공하지 않으면 관리에서 제품 Recommendations 기능에 액세스할 수 없습니다. 그러나 데이터 수집은 상점 첫 화면에서 계속되며 기존 권장 사항은 계속해서 쇼핑객에게 표시됩니다.

## 방화벽

제품 Recommendations이 방화벽을 통과할 수 있도록 하려면 다음을 추가하십시오. `commerce.adobe.io` 허용 목록.

## 제거 [!DNL Product Recommendations] {#uninstall}

필요한 경우 다음을 수행할 수 있습니다. [제거](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) 제품 권장 사항 모듈입니다.
