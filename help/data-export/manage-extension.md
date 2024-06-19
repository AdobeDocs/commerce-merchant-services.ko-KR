---
title: "[!DNL Manage the Data Export extension]"
description: "업그레이드 방법 알아보기 [!DNL Data Export] 확장 및 필요하지 않은 데이터 내보내기 서비스를 제거하거나 비활성화합니다."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# SaaS 데이터 내보내기 확장 관리

다음 [!DNL data export] SaaS 서비스용 확장은 Adobe Commerce과 연결된 Commerce 서비스 간의 데이터 수집 및 동기화를 가능하게 하는 모듈의 컬렉션입니다.

다음과 같은 Adobe Commerce Services 확장의 메타패키지에 특정 모듈이 포함되어 있습니다. [라이브 검색](/help/live-search/overview.md), [제품 Recommendations](/help/product-recommendations/overview.md), 및 [카탈로그 서비스](/help/catalog-service/overview.md). 이러한 서비스를 사용하는 경우 데이터 내보내기 확장을 활성화하기 위해 별도의 설치가 필요하지 않습니다.

## Commerce 데이터 내보내기 기능 제거 또는 비활성화

설치된 상거래 데이터 내보내기 모듈 중 하나가 필요하지 않은 경우 `magento:module:disable` CLI 명령을 사용하여 비활성화합니다.

예를 들어 [범주 API](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) 은 내부적으로 카테고리 권한 피드 데이터를 사용합니다. 이 API를 사용하지 않는 경우 카테고리 권한 피드에 대한 데이터 내보내기를 비활성화할 수 있습니다.

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### 특정 버전으로 모듈 업데이트

작성기를 사용하여 설치된 상거래 데이터 내보내기 모듈을 업데이트할 수 있습니다. 예를 들어 모듈을 지정된 버전으로 업데이트하고 필요한 종속성도 모두 업데이트할 수 있습니다.

1. Commerce 애플리케이션 서버에 로그인합니다.

1. 명령줄에서 Composer를 사용하여 모듈을 업데이트합니다.

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

Commerce 인스턴스가 클라우드 인프라에 배포된 경우 클라우드 프로젝트 디렉터리에서 확장을 업데이트합니다. 다음을 참조하십시오 [확장 업그레이드](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) 다음에서 _Adobe Commerce on Cloud Infrastructure 안내서_.




