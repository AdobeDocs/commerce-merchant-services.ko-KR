---
title: 온보딩
description: 에서 요구 사항 및 지원되는 플랫폼에 대해 알아봅니다. [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: ab7bb72826ff3aee1ce93d30dde0a752ef8069de
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# 온보딩

에 대한 온보딩 프로세스 [!DNL Product Recommendations] 서버의 명령줄에 액세스해야 하며 다음 단계로 구성됩니다. 명령줄에서 작업하는 방법을 잘 모를 경우 개발자나 시스템 통합자에게 도움을 요청하십시오.

- [구현 워크플로우](implementation-workflow.md)
- [설치 및 구성](install-configure.md)
- [설정](settings.md)
- [확인](verify.md)
- [스테이징 환경](staging-environment.md)

## 요구 사항

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3 / 7.4 / 8.1
- 작성기

### 지원되는 플랫폼

- Adobe Commerce on prem (EE) : 2.4.x
- Adobe Commerce on Cloud (ECE) : 2.4.x

### Page Builder 지원

[!DNL Product Recommendations] 페이지에 페이지 빌더 컨텐츠 유형으로 추가할 수 있습니다. 제품 Recommendations에 Page Builder 지원을 추가하려면 [설치 및 구성](install-configure.md).

>[!NOTE]
>
>[!DNL Page Builder] 권장 사항 단위는 기본 저장소 보기에 대해서만 만들 수 있습니다.

### B2B 지원 {#b2bsupport}

B2B 스토어프런트에서는 각 구매자나 고객 그룹에 대한 제품 가시성과 가격을 지시하는 복잡한 로직을 필요로 하는 경우가 많습니다. [!DNL Product Recommendations] now [지원](release-notes.md) 이 기능은 [카테고리 권한](https://docs.magento.com/user-guide/catalog/category-permissions.html), [공유 카탈로그](https://docs.magento.com/user-guide/catalog/catalog-shared.html), 및 [고객 그룹별 가격 책정](https://docs.magento.com/user-guide/catalog/pricing-advanced.html). 예를 들어, 소매 고객 세그먼트에서 특정 카테고리를 숨긴 경우 해당 세그먼트의 쇼핑객에게 해당 카테고리의 제품에 대한 권장 사항이 표시되지 않습니다. 또한 특정 고객 그룹 및 회사에 대한 공유 카탈로그를 정의할 때 해당 구매자는 액세스할 수 있는 제품에 대한 권장 사항만 봅니다. 모든 권장 제품은 각 구매자의 고객 그룹을 기준으로 올바른 고객 그룹별 가격을 반영합니다.
