---
title: 프로필 레코드
description: 프로필 레코드가 캡처하는 데이터를 알아봅니다.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bd04730d-e37a-48a9-822b-0f4aa68a4651
source-git-commit: 89607d22ba8e69e0c98fce97e041022e33d01c07
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# [!DNL Data Connection] 프로필 레코드(베타)

다음은 를 설치할 때 사용할 수 있는 Commerce 프로필 레코드 데이터에 대해 설명합니다. [!DNL Data Connection] 확장명. 프로필 레코드의 데이터는 Adobe Experience Platform으로 전송됩니다.

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
| `billingAddress` | 청구 우편 주소. |
| `billingAddress.street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명. |
| `billingAddress.street2` | 2차선 도로 정보(선택 사항). |
| `billingAddress.city` | 도시 이름. |
| `billingAddress.state` | 상태 이름. 자유 형식의 필드입니다. |
| `billingAddress.country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `billingAddressPhone` | 청구 주소와 연결된 전화번호. |
| `billingAddressPhone.number` | 전화번호. 전화번호는 문자열이고 대괄호와 같은 의미 있는 문자를 포함할 수 있습니다 `()`, 하이픈 `-`, 또는 확장과 같은 서브다이얼 식별자를 보여 주는 문자 `x` 예를 들어,  `1-353(0)18391111` 또는 `+613 9403600x1234`. |
| `shippingAddress` | 배송 우편 주소. |
| `shippingAddress.street1` | 기본 도로 정보, 아파트 번호, 도로 번호 및 도로명. |
| `shippingAddress.street2` | 2차선 도로 정보(선택 사항). |
| `shippingAddress.city` | 도시 이름. |
| `shippingAddress.state` | 상태 이름. 자유 형식의 필드입니다. |
| `shippingAddress.country` | 정부가 관리하는 지역의 이름입니다. 제외 `xdm:countryCode`, 모든 언어로 국가 이름을 사용할 수 있는 자유 형식의 필드입니다. |
| `shippingAddressPhone` | 배송 주소와 연계된 전화번호. |
| `shippingAddressPhone.number` | 전화번호. 전화번호는 문자열이고 대괄호와 같은 의미 있는 문자를 포함할 수 있습니다 `()`, 하이픈 `-`, 또는 확장과 같은 서브다이얼 식별자를 보여 주는 문자 `x` 예를 들어,  `1-353(0)18391111` 또는 `+613 9403600x1234`. |
| `userAccount` | 고객 충성도 세부 정보, 환경 설정, 로그인 프로세스 및 기타 계정 환경 설정을 나타냅니다. |
| `userAccount.startDate` | 프로필이 처음 생성된 날짜입니다. |

>[!NOTE]
>
>각 프로필 레코드에는 [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) 프로필의 기본 식별자로 시스템에서 생성한 Commerce 고객 ID와 보조 식별자로 사용되는 이메일 ID가 포함된 필드.

방법 알아보기 [프로필 레코드별 스키마 만들기](profile-data.md) 프로필 레코드에서 데이터를 수집할 수 있습니다.
