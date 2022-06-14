---
title: Merchant Store 구성
description: 'Merchant Store로 향상된 Inventory management 소스를 설정합니다. '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# Merchant Store(소스) 구성

이 솔루션은 영업 중심 기능으로 스톡 소스를 확장하여 네이티브 Inventory management 기능을 향상시킵니다.

- 저장소 위치에 대한 지리적 좌표를 추가합니다
- 소스로 지정 [!DNL Store Pickup Location] 사용 가능한 운송 기능(납품처 스토어, 출고처 스토어) 지정
- 사용 가능한 픽업 옵션(매장 내 또는 커사이드), 사용자 정의된 픽업 지침 및 기타 정보를 지정하여 고객에게 픽업 세부 정보와 지침을 제공합니다

용어 _소스_ 및 _가맹점 위치_ 서로 교환하여 사용할 수 있습니다. 모든 레코드는 재고 소스이지만 구성 설정에 따라 소스가 머천트 저장소 위치일 수도 있습니다.

Merchant Store 구성을 관리자로부터 관리합니다. **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>설정 프로세스 중에 소스를 만들거나 기존 소스를 업데이트한 후 캐시를 플러시해야 할 수 있습니다.

## **일반**

<table>
<tbody>
<tr>
<th>필드</th>
<th>설명</th>
<th>범위</th>
<th>필수 여부</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>머천트 스토어 위치의 위도 좌표입니다. 이 필수 정보는 상점 경험의 위치 검색 및 맵 배치에 사용됩니다. 유효성 검사를 전달하려면 값이 저장소의 정확한 주소와 일치해야 합니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>머천트스토어 위치의 종방향 좌표입니다. 이 필수 정보는 상점 경험의 위치 검색 및 맵 배치에 사용됩니다. 유효성 검사를 전달하려면 값이 저장소의 정확한 주소와 일치해야 합니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>소스를 사용 가능한 저장소 픽업 위치로 지정합니다. 이 설정은 소스가 동기화되고 방문자에게 표시되는지 여부를 결정합니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>소스 수준에서 납품처 저장 기능을 구성합니다. 자세한 내용은 [일반 구성](enable-general.md) 옵션, <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>머천트 스토어 위치의 위도 좌표입니다. 이 필수 정보는 상점 경험의 위치 검색 및 맵 배치에 사용됩니다. 유효성 검사를 전달하려면 값이 저장소의 정확한 주소와 일치해야 합니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>머천트스토어 위치의 종방향 좌표입니다. 이 필수 정보는 상점 경험의 위치 검색 및 맵 배치에 사용됩니다. 유효성 검사를 전달하려면 값이 저장소의 정확한 주소와 일치해야 합니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>소스를 사용 가능한 저장소 픽업 위치로 지정합니다. 이 설정은 소스가 동기화되고 방문자에게 표시되는지 여부를 결정합니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>소스 수준에서 납품처 저장 기능을 구성합니다. 자세한 내용은 [일반 구성](enable-general.md) 옵션, <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>소스 수준에서 Ship-from-Store 기능을 구성합니다. 자세한 내용은 [일반 구성](enable-general.md) 옵션, [!UICONTROL Enable Ship From Store].</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **필드** | **설명** | **범위** | **필수 여부** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | 머천트 스토어 위치의 위도 좌표입니다. 이 필수 정보는 상점 경험의 위치 검색 및 맵 배치에 사용됩니다. 유효성 검사를 전달하려면 값이 저장소의 정확한 주소와 일치해야 합니다. | 글로벌 | 예 |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | 머천트스토어 위치의 종방향 좌표입니다. 이 필수 정보는 상점 경험의 위치 검색 및 맵 배치에 사용됩니다. 유효성 검사를 전달하려면 값이 저장소의 정확한 주소와 일치해야 합니다. | 글로벌 | 예 |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | 소스를 사용 가능한 저장소 픽업 위치로 지정합니다. 이 설정은 소스가 동기화되고 방문자에게 표시되는지 여부를 결정합니다. | 글로벌 | 아니요 |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | 소스 수준에서 납품처 저장 기능을 구성합니다. 자세한 내용은 [일반 구성](enable-general.md) 옵션, **[!UICONTROL Enable Ship To Store]**. | 글로벌 | 아니요 |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | 소스 수준에서 Ship-from-Store 기능을 구성합니다. 자세한 내용은 [일반 구성](enable-general.md) 옵션, [!UICONTROL Enable Ship From Store] | 글로벌 | 아니요 |

{style=&quot;table-layout:auto&quot;}

## 픽업 위치 구성

| **필드** | **설명** | **범위** | **필수 여부** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | 두 가지 픽업옵션 중 하나예요 [!DNL In-Store Pickup] 는 고객이 머천트 스토어 위치를 입력하여 주문을 검색할 수 있도록 허용하는 기능을 나타냅니다. </br></br>이 옵션이 활성화되면 체크아웃 중에 고객에게 이 옵션이 표시될 수 있습니다. </br></br>이 옵션은 또한 전역 구성을 다음으로 무시합니다. [!UICONTROL Enable In-store Pickup] 이 구성 요소는 [!UICONTROL Delivery Method] 대상 [!UICONTROL In-store Pickup] | 글로벌 | 아니요 |
| **매장 내 픽업 지침**</br>`Extension Attribute: store_pickup_instructions` | 에서 고객에게 전달되는 사용자 지정 가능한 메시지 **Store에서 픽업 준비 주문** 이메일 알림. | 글로벌 | 아니요 |
| **조정 허용**</br>`Extension Attribute: curbside_enabled` | 두 가지 픽업옵션 중 하나예요 현재 배송을 통해 고객은 머천트 가게 위치의 지정된 장소에 차를 주차할 수 있습니다. 이 시나리오에서 주문은 상점 조인에 의해 고객에게 전달됩니다. </br></br>이 옵션이 활성화되면 체크아웃 중에 고객에게 이 옵션이 표시될 수 있습니다. 또한 고객이 체크인 프로세스 중에 차량 및 주차 장소를 설명하도록 요청받을 수도 있습니다. </br></br>이 옵션은 또한 전역 구성을 다음으로 무시합니다. **Curbside Pickup 활성화** 이 구성 요소는 **배달 방법** 대상 **매장 내 픽업** | 글로벌 | 아니요 |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | 에서 고객에게 전달되는 사용자 지정 가능한 메시지 [!UICONTROL Order Ready For Pickup in Store] 이메일 알림. | 글로벌 | 아니요 |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | 주문을 받고 선택하며 선택할 준비가 되기 전에 필요한 시간(분)입니다. </br></br>이 정보는 웹 사이트의 고객에게 주문 픽업 시간을 표시하는 데 사용됩니다.</br></br> 이 옵션을 설정하면 **예상 픽업 리드 타임** 에 대해 **배달 방법** 에서 **매장 내 픽업** 구성. | 글로벌 | 아니요 |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | 주문을 선택할 준비가 될 때까지 시간(분)을 표시하는 레이블입니다.</br></br> 이 레이블을 사용자 지정할 때 코드 %1을(를) 사용하여 **예상 픽업 리드 타임**.</br></br> 이 옵션을 설정하면 [!UICONTROL Estimated Pickup Time Label] 에 대해 [!UICONTROL Delivery Method] 에서 [!UICONTROL In-store Pickup]. | 글로벌 | 아니요 |

### **시작 시간**

| **필드** | **설명** | **범위** | **필수 여부** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | 머천트 스토어 위치의 시간대. 각 날에 대해 열기 및 닫기 시간을 설정합니다.</br></br>이러한 설정은 예상 픽업 시간을 최적화하고 이행 서비스 보고에 사용됩니다. | 글로벌 | 예 |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | 상점 위치의 작동 시간입니다. </br></br>이 정보는 예상 픽업 시간을 최적화하고 이행 서비스 보고에서 최적화할 수 있습니다. | 글로벌 | 예 |

### Experience Cloud 인터페이스 옵션 구성



| **필드** | **설명** | **범위** | **필수 여부** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | 머천트 스토어 위치에 경측 픽업용 지정 주차 공간이 있는지 여부를 지정합니다. </br></br>활성화된 경우 사용 가능한 주차 공간을 구성할 수 있습니다. | 글로벌 | 아니요 |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | 쇼핑 경험 중에 고객에게 주차 공간 식별이 필요한지 여부를 지정합니다.</br></br>활성화된 경우 도착 시 주차 장소를 지정하라는 메시지가 표시됩니다. 비활성화하면 고객이 이 입력을 건너뛸 수 있습니다. | 글로벌 | 아니요 |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | 이 상점에 있는 주차 공간을 이용할 수 있어 경차로 픽업할 수 있다. 제공된 인터페이스를 사용하여 각 스점의 이름을 지정합니다.</br></br> 모든 주차 장소에는 이름을 지정할 필요가 없고, 경사로 지정된 장소만 지정할 수 있습니다. 예를 들어, A-G행만 사용할 수 있지만, 행 A의 처음 8개 지점만 경측 픽업용으로 지정됩니다. 이 시나리오에서는 8개의 지점을 정의할 수 있습니다. ex: A1, A2, A3 등. | 글로벌 | 아니요 |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | 이 설정을 사용하면 고객이 체크인 중 주차 위치를 설명할 수 있습니다. | 글로벌 | 아니요 |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | 체크 인 중에 고객의 차량 색상 수집을 지원할지 여부를 지정합니다. </br></br> 사용 가능한 선택 사항 [!UICONTROL Car Color] 는 관리자에서 구성됩니다 [체크인 경험에 대한 시스템 설정](check-in-experience-setup.md). | 글로벌 | 아니요 |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | 체크인 중에 고객에게 차량 색상 식별이 필요한지 여부를 지정합니다.</br></br>활성화된 경우 도착 시 고객의 차량 색상을 지정하라는 메시지가 표시됩니다. 비활성화하면 고객이 이 입력을 건너뛸 수 있습니다. | 글로벌 | 아니요 |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | 체크인 중에 고객으로부터 차량 만들기를 지원할지 여부를 지정합니다.</br></br> 사용 가능한 선택 사항 [!UICONTROL Car Make] 는 관리자에서 구성됩니다 [체크인 경험에 대한 시스템 설정](check-in-experience-setup.md). | 글로벌 | 아니요 |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | 체크인 중에 고객에게 차량 식별이 필요한지 여부를 지정합니다.</br></br>활성화된 경우 도착 시 차량 제조 상태를 지정하라는 메시지가 표시됩니다. 비활성화하면 고객이 이 입력을 건너뛸 수 있습니다. | 글로벌 | 아니요 |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | 체크인 중에 고객의 추가 정보 수집을 지원할지 여부를 지정합니다. | 글로벌 | 아니요 |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | 체크인 중에 고객에게 추가 정보가 필요한지 여부를 지정합니다. </br></br>활성화된 경우 도착 시 추가 정보를 입력하라는 메시지가 표시됩니다. 비활성화하면 고객이 이 입력을 건너뛸 수 있습니다. | 글로벌 | 아니요 |







