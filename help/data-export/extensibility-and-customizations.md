---
title: SaaS 데이터 내보내기 피드 데이터 확장 및 사용자 지정
description: ' [!DNL SaaS Data Export] 피드 데이터를 확장하고 사용자 지정하는 방법을 알아봅니다.'
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 51238f86f36a756b86d07bdf6bb0a5cf0c61cbeb
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# SaaS 데이터 내보내기 피드 데이터 확장 및 사용자 지정

[!DNL Commerce Data Export] 확장을 사용하면 [!DNL Commerce] 응용 프로그램에서 Live Search, Catalog Service 및 Product Recommendations과 같은 Commerce 서비스로 데이터를 내보낼 수 있습니다. 필요한 경우 `Magento\CatalogDataExporter` 모듈을 업데이트하여 추가 데이터를 포함하도록 피드 데이터를 확장 및 사용자 지정하거나 수집된 데이터를 수정할 수 있습니다.

>[!NOTE]
>
>피드에 새 데이터를 추가하거나 기존 데이터를 수정하면 피드 수집 성능에 영향을 줄 수 있으며 Adobe Commerce 측의 처리 논리에 문제가 발생할 수 있습니다. 프로덕션 환경으로 병합하기 전에 사용자 지정된 코드를 테스트해야 합니다.

## 제품 피드에서 속성 데이터 확장

제품 피드에는 제품 처리에 필요하거나 소비자가 일반적으로 사용하는 기본 속성이 포함됩니다. 추가 시스템 속성을 피드에 추가하여 제품 피드에 포함할 수 있습니다.

이 작업을 완료하려면 `magento/catalog-data-exporter` 모듈을 업데이트하여 [종속성 삽입 구성 파일](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/)(`di.xml`)에 추가 시스템 특성을 추가하십시오. 제품 특성 쿼리(`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`)에 특성을 추가합니다.

**예**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
