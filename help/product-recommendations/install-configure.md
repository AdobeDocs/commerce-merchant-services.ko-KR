---
title: 설치 및 구성
description: 설치, 업데이트 및 제거 방법을 알아봅니다 [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# 설치 및 구성

배포 [!DNL Product Recommendations] 를 설치 및 구성하려면 모듈을 설치하고 [Commerce Services 커넥터](../landing/saas.md). 업데이트가 릴리스되면 최신 버전으로 설치를 쉽게 업데이트할 수 있습니다.

- [설치](#install)
- [구성](#configure)
- [업데이트](#update)
- [제거](#uninstall)

## 설치 [!DNL Product Recommendations] {#install}

왜냐하면 [!DNL Product Recommendations] 모듈은 독립형 메타패키지입니다. 업데이트는 Adobe Commerce보다 자주 릴리스됩니다. 최신 버그 수정 및 기능을 사용하여 최신 정보를 확인하려면 [릴리스 노트](release-notes.md).

설치 `magento/product-recommendations` 모듈(작성기 포함):

```bash
composer require magento/product-recommendations
```

### 페이지 빌더 추가 지원 {#pbsupport}

[!DNL Product Recommendations] 용 Page Builder 는 선택적 모듈이며 별도로 설치됩니다. 를 사용하려면 [!DNL Product Recommendations] 페이지 빌더를 사용하여 다음 명령을 실행하여 모듈을 설치합니다.

```bash
composer require magento/module-page-builder-product-recommendations
```

사용 [!DNL Product Recommendations] 페이지 빌더에서 활성 상태의 기존 를 추가할 수 있습니다 [추천 단위](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) 페이지, 블록 및 동적 블록과 같이 페이지 빌더에서 만든 모든 컨텐츠에 매핑해야 합니다.

자세한 내용은 [사용 [!DNL Product Recommendations] Page Builder 컨텐츠 사용](page-builder.md) 추가 지침

### 시각적 유사성 권장 사항 유형 추가 {#vissimsupport}

다음 _시각적 유사성_ 권장 사항 유형을 사용하면 제품을 표시하는 제품 세부 사항 페이지에 권장 사항 단위를 배포할 수 있습니다 [시각적으로 유사](type.md#visualsim) 보려는 제품에 연결할 수 있습니다. 이 권장 사항 유형은 제품의 이미지와 시각적 측면이 쇼핑 경험의 중요한 부분인 경우 가장 유용합니다. 설치 _시각적 유사성_ 다음 명령을 실행하여 권장 사항 유형:

```bash
composer require magento/module-visual-product-recommendations
```

## 구성 [!DNL Product Recommendations] {#configure}

를 설치한 후 `magento/product-recommendations` 모듈, 구성 [Commerce Services 커넥터](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) API 키를 지정하고 SaaS 데이터 공간 선택

카탈로그 내보내기가 올바르게 실행되는지 확인하려면 [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) 작업 및 [인덱서](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) 실행 중이며 `Product Feed` 인덱서가 `Update by Schedule`.

API 키를 통해 Commerce Services에 연결하고 SaaS 데이터 공간을 지정하면 카탈로그 동기화가 시작됩니다. 그러면 다음 작업을 수행할 수 있습니다 [확인](verify.md) 해당 행동 데이터가 스토어에 전송됩니다.

## 업데이트 [!DNL Product Recommendations] 설치 {#update}

모든 Adobe Commerce과 마찬가지로 [!DNL Product Recommendations] 설치 및 업데이트에 작성기 를 사용합니다. 를 업데이트하려면 `magento/product-recommendations` 모듈에서 다음을 실행합니다.

```bash
composer update magento/product-recommendations --with-dependencies
```

3.0에서 4.0과 같은 주요 버전으로 업데이트하려면 루트를 편집해야 합니다 `composer.json` 파일을 만들 수 있습니다. (자세한 내용은 [릴리스 노트](release-notes.md) 최신 버전에 대한 정보) 예를 들어, 기본 `composer.json` 파일 및 검색 `magento/product-recommendations` 모듈:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

주요 버전을 `3.0` to `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

를 저장합니다 `composer.json` 파일 및 실행:

```bash
composer update magento/product-recommendations --with-dependencies
```

또는 를 설치한 경우 `magento/module-visual-product-recommendations` 및 `magento/module-page-builder-product-recommendations` 모듈:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> 제품 Recommendations 버전 3.x.x에서는 단일 API 키만 필요했습니다. 4.x.x 이상에서는 프로덕션 공용 및 개인 API 키와 Sandbox 공용 및 개인 API 키를 제공해야 합니다. 두 API 키 쌍을 모두 제공하지 않으면 관리자의 제품 Recommendations 기능에 액세스할 수 없습니다. 그러나 데이터 수집은 상점 앞에서 계속 진행될 것이며 기존 권장 사항은 계속해서 고객에게 표시됩니다.

## 제거 [!DNL Product Recommendations] {#uninstall}

필요한 경우 다음을 수행할 수 있습니다 [제거](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) 제품-권장 사항 모듈.
