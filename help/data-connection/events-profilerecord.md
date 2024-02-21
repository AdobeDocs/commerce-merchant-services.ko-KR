---
title: 프로필 레코드
description: 프로필 레코드가 캡처하는 데이터를 알아봅니다.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 655b5d18a4fb77232523c9c18a9fb362de93c70a
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# [!DNL Data Connection] 프로필 레코드(베타)

>[!NOTE]
>
>이 기능은 Beta 버전입니다. Beta 프로그램에 참여하려면 다음 대상에게 요청을 전송하십시오. [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

다음은 를 설치할 때 사용할 수 있는 상거래 프로필 레코드 데이터에 대해 설명합니다. [!DNL Data Connection] 확장명. 프로필 레코드의 데이터는 Adobe Experience Platform으로 전송됩니다.

## 프로필 레코드

프로필 레코드 업데이트는 새 프로필이 생성, 업데이트 또는 삭제될 때 Experience Platform에서 사용할 수 있습니다.

### 프로필 레코드에서 수집된 데이터

다음은 프로필 레코드에 대해 캡처된 데이터에 대해 설명합니다.

| 필드 | 설명 |
|---|---|
| `channel` | 데이터 소스에 대한 정보를 포함합니다. 모두 `_id` 및 `_type` contain [이름 공간 값](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | 채널의 고유 식별자(예: ) `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | 는 다음과 같은 채널 데이터의 소스를 식별합니다. `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | 고객에 대한 정보를 포함합니다. |
| `person.name` | 고객 이름에 대한 정보를 포함합니다. |
| `person.name.firstName` | 고객의 이름을 포함합니다. |
| `person.name.lastName` | 고객의 성을 포함합니다. |
| `person.birthDate` | 쇼핑객 생년월일. |
| `personalEmail` | 개인 이메일 주소. |
| `personalEmail.address` | 기술 주소(예: ) `name@domain.com` RFC2822 및 이후 표준에서 일반적으로 정의한 대로. |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `userAccount.startDate` | 프로필이 처음 생성된 날짜입니다. |

>[!NOTE]
>
>각 프로필 레코드에는 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 구매 가능한 경우 구매자의 이메일 주소 및 ECID가 포함된 필드.

방법 알아보기 [프로필 레코드별 스키마 만들기](profile-data.md) 프로필 레코드에서 데이터를 수집할 수 있습니다.
