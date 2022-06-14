---
title: 영업 이메일
description: 주문 및 주문 처리 프로세스 중에 고객과 통신하고 저장 관리자와 통신하도록 트랜잭션 전자 메일 템플릿에 대한 설정을 구성합니다.
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---

# 영업 이메일

Store Fulfillment는 주문 및 이행 워크플로우를 지원하기 위해 확장된 트랜잭션 전자 메일 템플릿 세트를 제공합니다. 이러한 DM은 여러 채널에서 일관되고 자동화된 커뮤니케이션 및 메시지를 제공합니다. 즉, 고객 및 스토어 관리자에게 주문 상태 변경, 매장 내 픽업 주문에 대한 지침 등을 알립니다.

Store Fulfillment 전자 메일 템플릿은 기본 메시징 및 설정으로 구성됩니다. Adobe Commerce의 머천트 관리자는 구성을 관리 및 수정하고, 다양한 시나리오에서 고객과 통신할 이메일 템플릿을 선택할 수 있습니다. 관리자는 템플릿을 구성하고 사용자 지정할 수도 있습니다.

관리자로부터 영업 이메일 템플릿을 구성합니다. **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## 이메일 - 일반 설정

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수 여부</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>비동기 전송</strong></td>
<td>이 기능을 사용하지 않도록 설정합니다. 비동기 전자 메일 보내기는 지원되지 않습니다. 스토어 픽업에서 가장 빠른 통신 및 응답 시간을 위해 일괄 처리를 하지 않고 즉시 이메일을 보냅니다. </td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>

## Store에서 Recover 준비 주문

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수 여부</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>활성화됨</strong></td>
<td>이 이메일은 스토어 동료가 주문 선택을 완료하면 고객에게 전송됩니다. 이메일 알림을 비활성화하려면 "아니요"로 설정합니다. 이메일 템플릿이 비활성화되어 있어도 스토어 연결에서 주문을 선택할 수 없습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>이메일 발신자를 픽업하기 위한 주문 준비</strong></td>
<td>전자 메일 알림을 보낼 때 사용되는 발신자 ID입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>이메일 템플릿 픽업용 주문 준비</strong></td>
<td>등록된 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<td><strong>게스트용 이메일 템플릿을 픽업할 준비가 되었습니다.</strong></td>
<td>게스트 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>대체 픽업 연락처에 대한 이메일 템플리트 픽업 준비 주문</strong></td>
<td>순서대로 이름이 지정된 추가 연락처를 알리는 데 사용되는 전자 메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 발송 대상 이메일 복사</strong></td>
<td>각 알림의 사본을 보낼 이메일 주소의 쉼표로 구분된 목록입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 전송 준비 이메일 복사 방법</strong></td>
<td>이메일 "탄소 사본"이 을 사용하도록 전송됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>


## 스토어에서 주문이 선택되었습니다.

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수 여부</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>활성화됨</strong></td>
<td>이 이메일은 고객이 스토어에서 주문을 선택했는지 확인하기 위해 고객에게 전송됩니다. 이메일 알림을 비활성화하려면 "아니요"로 설정합니다. 이메일 템플릿이 비활성화되어 있어도 고객이 주문을 선택할 수 없습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문을 받은 이메일 발신자를 찾았습니다.</strong></td>
<td>전자 메일 알림을 보낼 때 사용되는 발신자 ID입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>이메일 템플릿을 주문했습니다.</strong></td>
<td>등록된 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<td><strong>게스트용 이메일 템플릿을 주문했습니다.</strong></td>
<td>게스트 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>보내기에 이메일 사본이 선택되었습니다.</strong></td>
<td>각 알림의 사본을 보낼 이메일 주소의 쉼표로 구분된 목록입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>이메일 복사 방법이 선택되었습니다.</strong></td>
<td>사용할 이메일 "탄소 사본"을 보내는 방법입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>

## 주문 지연

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수 여부</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>활성화됨</strong></td>
<td>이 이메일은 고객에게 머천트 스토어에서 처리 지연 또는 주문 선택 지연에 대해 통지하기 위해 전송됩니다. 이메일 알림을 비활성화하려면 "아니요"로 설정합니다. 이메일 템플릿이 비활성화되어 있어도 주문이 지연되는 것을 방지할 수 없습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 지연된 이메일 발신자
</strong></td>
<td>전자 메일 알림을 보낼 때 사용되는 발신자 ID입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 지연된 이메일 템플릿</strong></td>
<td>등록된 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<td><strong>게스트용 주문 지연된 이메일 템플릿</strong></td>
<td>게스트 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 지연된 전자 메일 복사본 전송 대상</strong></td>
<td>각 알림의 사본을 보낼 이메일 주소의 쉼표로 구분된 목록입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 지연 복사 전송 방법</strong></td>
<td>사용할 이메일 "탄소 사본"을 보내는 방법입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>



## 주문 취소됨

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수 여부</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>활성화됨</strong></td>
<td>이 이메일은 고객에게 전송되어 머천트 스토어에서 주문이 취소되었음을 알립니다. 을 로 설정합니다. <code>No</code> 이메일 알림을 비활성화하려면 다음을 수행하십시오. 이메일 템플릿이 비활성화되어 있어도 주문이 취소되지 않습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 취소 이메일 발신자
</strong></td>
<td>전자 메일 알림을 보낼 때 사용되는 발신자 ID입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 취소 이메일 템플릿</strong></td>
<td>등록된 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<td><strong>게스트에 대한 주문 취소</strong></td>
<td>게스트 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 취소 전자 메일 복사본 전송 대상</strong></td>
<td>각 알림의 사본을 보낼 이메일 주소의 쉼표로 구분된 목록입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 전송 취소 복사 방법</strong></td>
<td>사용할 이메일 "탄소 사본"을 보내는 방법입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>


## 일부 취소된 주문

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수 여부</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>활성화됨</strong></td>
<td>이 이메일은 고객에게 전송되어 머천트 스토어에서 주문 일부가 취소되었음을 알립니다. 을 로 설정합니다. <code>No</code> 이메일 알림을 비활성화하려면 다음을 수행하십시오. 이메일 템플릿이 비활성화되어 있어도 주문이 일부 취소되지 않습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>일부 취소된 이메일 발신자 주문
</strong></td>
<td>전자 메일 알림을 보낼 때 사용되는 발신자 ID입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 일부가 취소된 이메일 템플릿</strong></td>
<td>등록된 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<td><strong>대체 픽업 연락처에 대해 부분적으로 취소된 이메일 템플릿 주문</strong></td>
<td>순서대로 이름이 지정된 추가 연락처를 알리는 데 사용되는 전자 메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>게스트에 대한 일부 취소 주문</strong></td>
<td>게스트 고객에게 알리는 데 사용되는 이메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 일부에서 취소된 이메일 복사 전송</strong></td>
<td>각 알림의 사본을 보낼 이메일 주소의 쉼표로 구분된 목록입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>주문 일부 취소된 복사 전송 방법</strong></td>
<td>사용할 이메일 "탄소 사본"을 보내는 방법입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>

## 납품처 스토어

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수 여부</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>주문에서 제품을 저장할 배송 배달 이메일 발신자가 있음</strong></td>
<td>재고가 사용 가능한 상태가 될 때까지 머천트 저장소에서 선택할 수 없는 모든 개설 주문에 대한 총괄 보고서로 지정된 머천트 직원에게 보내는 이메일. </br></br> 상인은 이 보고서를 사용하여 매장 간 재고 이전 또는 보충을 시작 및 관리할 수 있습니다. </br></br>이 알림은 [!DNL Ship-to-Store] 기능이 활성화되어 있습니다.
</br></br>이 레이블은 선택한 운송 회사 또는 사용 가능한 운송 방법 레이블에 영향을 주지 않습니다.</br></br></td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>전자 메일 수신자를 저장하기 위한 납품처</strong></td>
<td>각 알림의 사본을 보낼 이메일 주소의 쉼표로 구분된 목록입니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>이메일 템플릿</strong></td>
<td>수신자에게 알리는 데 사용되는 전자 메일 메시지 템플릿입니다. 통합에 기본 템플릿이 제공됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>

>[!NOTE]
>
>미납주문을 허용하는 경우 이러한 주문에 대한 알림을 받으려면 관리자 이메일 주소를 제공해야 합니다. 다음 구성 설정에 주소를 추가합니다. **[!UICONTROL Send Order Delayed Email Copy To]** 에서 [주문 지연](#order-delayed) 템플릿 및 [!UICONTROL Ship To Store Email Recipients] 에서 [납품처 스토어](#ship-to-store) 템플릿.



