---
title: Adobe Experience Platform에 상거래 데이터 연결
description: 상거래 데이터를 Adobe Experience Platform에 연결하는 방법을 알아봅니다.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# Adobe Experience Platform에 상거래 데이터 연결 {#connectaep}

Adobe Commerce 데이터를 Adobe Experience Platform에 연결하기 전에 [Commerce Services 커넥터](../landing/saas.md#organizationid). 로그인하고 조직 ID를 선택한 후에 **Experience Platform 커넥터** 페이지에 있을 수도 있습니다.

1. 관리에서 **시스템** > 서비스 > **Experience Platform 커넥터**.

1. 에서 **범위** 드롭다운에서 컨텍스트 또는 저장소 보기의 &quot;범위&quot;를 선택합니다.

   조직 ID는 글로벌입니다. Adobe Commerce 인스턴스당 하나의 조직 ID만 연결할 수 있습니다.

1. 에서 **IMS 조직** 필드에서는 구성한 대로 Adobe Experience Platform 계정과 연결된 ID가 표시됩니다. [Commerce Services 커넥터](../landing/saas.md#organizationid).

1. 에서 **데이터 스트림 ID** 필드를 입력한 후 데이터 스트림의 ID를 붙여넣습니다. [생성됨](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) Adobe Experience Platform.

## 데이터 스트림 ID 및 상거래 인스턴스 저장소 보기의 관계

데이터 스트림 ID를 사용하면 Adobe Experience Platform에서 다른 Adobe DX 제품으로 이벤트를 전달하여 특정 Adobe Commerce 인스턴스 내의 특정 저장소 보기에 연결할 수 있습니다. 여러 저장소 보기를 동일한 데이터 스트림 ID에 연결할 수도 있습니다. 사업에 가장 적합한 것이 무엇인지에 따라 다릅니다.

## 필드 설명

| 필드 | 설명 |
|--- |--- |
| 범위 | 구성 설정을 적용할 특정 저장소 보기입니다. |
| IMS 조직(글로벌) | Adobe DX 제품을 구입한 조직에 속한 ID입니다. 이 ID는 Adobe Commerce 인스턴스를 Adobe Experience Platform에 연결합니다. |
| 데이터 스트림 ID(Storeview) | Adobe Experience Platform에서 다른 Adobe DX 제품으로 데이터를 전송할 수 있는 ID입니다. 이 ID는 특정 Adobe Commerce 인스턴스 내의 특정 storeView에 연결할 수 있습니다. |

Experience Platform 커넥터 확장이 설치되어 있는 경우, 생성된 Adobe Commerce과 Adobe Experience Platform 간 링크와 지정된 데이터 스트림 ID가 [!DNL Commerce] 데이터가 Adobe Experience Platform 에지 및 기타 Adobe DX 제품으로 이동합니다.

## 엣지의 상거래 데이터

Adobe Experience Platform Edge로 전자 상거래 데이터가 전송되면 다음과 같은 보고서를 작성할 수 있습니다.

![Adobe Experience Manager의 상거래 데이터](assets/aem-data-1.png)
_Adobe Experience Manager의 상거래 데이터_
