---
title: 저장소 이행 테스트 및 배포
description: 저장 이행 기능을 검증하기 위한 테스트 계획. 테스트에서는 Inventory Sync API, 취소된 주문에 대한 종단 간 이행 워크플로우, Store Fulfillment 앱 사용자 관리 및 고객 체크인 경험을 다룹니다.
role: User, Admin
level: Intermediate
exl-id: 77285a66-5161-407b-94cd-b3f412d7949d
source-git-commit: 556cbf803a0f8569e8561d2b33b7a976065ae814
workflow-type: tm+mt
source-wordcount: '2652'
ht-degree: 0%

---

# Adobe Commerce에 대한 스토어 이행 테스트 및 배포

개발 환경에서 온보딩 프로세스를 완료한 후 Store Fulfillment 솔루션을 테스트하고 프로덕션 환경에 배포할 프로세스를 시작할 수 있습니다.

**전제 조건**

정보, 저장 또는 주문을 테스트하거나 동기화하기 전에 다음 작업을 완료했는지 확인하십시오.

- 을(를) 완료했습니다. [일반 구성](enable-general.md) 저장 이행 서비스용.

- [샌드박스 및 프로덕션 환경에 대한 계정 자격 증명과 연결 세부 정보를 추가하고 확인합니다](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- 에서 [Adobe Commerce 통합](connect-set-up-service.md#configure-store-fulfillment-account-credentials) 저장 이행 솔루션을 사용할 수 있으며 권한을 부여합니다.

## 테스트 준비

테스트 주문을 만들거나 통합 테스트를 수행하려면 먼저 연결 구성을 완료해야 합니다. 테스트하기 전에 저장소 데이터가 동기화되었는지 확인해야 합니다.

1. Store Fulfillment 소스를 동기화합니다.

   - 이동 **[!UICONTROL Stores > Sources]**.

   - 선택 **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. 저장소 그리드에서 저장소가 `Synced` 테스트 주문을 만들기 전에

## 샘플 테스트 계획

소매점은 배포의 구성 및 테스트 단계에서 Store Fulfillment 솔루션의 기본 기능을 검증합니다. 이 샘플 테스트 계획은 테스트의 시작점을 제공합니다. 요구 사항에 따라 시나리오를 추가로 추가합니다.

>[!NOTE]
>
>Store Fulfillment 솔루션에 대한 초기 온보딩을 완료하거나 기존 설치를 업데이트한 후 항상 프로덕션에 배포하기 전에 비프로덕션 환경에서 애플리케이션을 테스트하십시오.

이 샘플 테스트 계획은 다음과 같은 기능 영역을 다룹니다.

| 기능 영역 | 함수 | 역할 |
|-------------------------------------|------------------------------------------|----------------------------------|
| 재고 및 주문 동기화 | 인벤토리 API 동기화 | Adobe Commerce 관리 |
| 종단 간 | 주문 취소 워크플로우 | 고객, 관리자, 저장소 연결 |
| 관리 | Store Fulfillment 앱 권한 | 관리 |
| Adobe Commerce 프론트엔드 | 제품 유형 | 고객, 관리자 |
| 프런트 엔드 체크아웃</br>체크인 양식 | 체크인 경험 | 고객, 관리자 |
| 스토어 지원 앱 | 주문</br>선택</br>단계</br>및 핸드오프 | 저장소 연결 |

### 인벤토리 API 동기화

테스트 계획의 이 섹션에서는 재고 및 주문 동기화를 포함하여 픽업 소스 및 주식에 대한 업데이트가 Adobe Commerce과 Store Fulfillment 솔루션 간에 올바르게 동기화되는지 확인합니다.

**기능 영역**: 재고 및 주문 동기화</br>
**역할:** 관리</br>
**테스트 유형:** 모두 양수

<table>
<thead>
<tr>
<th>함수</th>
<th>테스트 시나리오</th>
<th>예상 결과</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>픽업 스톡 소스 추가</strong></td>
<td>새 픽업 증권 소스를 저장합니다.</td>
<td>실시간 동기화는 소스 세부 사항을 5분 내에 Walmart GIF 서비스로 보냅니다.</td>
</tr>
<tr>
<td><strong>기존 픽업 스톡 소스 업데이트</strong></td>
<td>기존 픽업 스톡 소스에 대한 업데이트를 저장합니다.</td>
<td>실시간 동기화 작업은 5분 내에 세부 정보를 Walmart GIF에 보냅니다</td>
</tr>
<tr>
<td><strong>픽업 증권 소스</br><code>Is Synced</code> 상태</br><code>Is Synced</code></strong></td>
<td>기존 픽업 스톡 소스에 대한 업데이트를 저장합니다.</td>
<td>작업이 성공하면 <code>Is Synced</code> 소스 관리 페이지 업데이트 열 <code>No</code> to <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>수정된 주식 예약 프로세스</strong></td>
<td>제품에 대한 새 주문을 작성하고 제출합니다.</td>
<td>이에 따라 제품의 판매 수량이 감소한다.</td>
</tr>
<tr>
<td><strong>새로운 주문 푸시, API 동기화 - 고객 주문</strong></td>
<td>고객이 상점 픽업 주문을 제출합니다.</td>
<td><ul><li>관리자 순서 보기에서 <strong>Adobe Commerce 관리 사용자</strong> 주문 동기화 상태가 <code>Sent</code></li><li>주문 세부 사항 로그에 메시지가 포함됩니다 <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>새로운 주문 푸시, API 동기화 - 관리자가 주문을 제출합니다.</strong></td>
<td>Adobe Commerce <strong>관리</strong> 픽업 주문을 제출합니다.</td>
<td><ul><li>관리 주문 보기에서 주문 동기화 상태는 <code>Sent</code>.</li><li>주문 세부 사항 로그에 메시지가 포함됩니다 <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>새 주문 푸시, 예외 큐<strong></td>
<td>Fulfillment Service(Faa)와의 상호 작용 없이 Adobe Commerce을 통해 이행될 수 있는 Adobe Commerce Admin에서 몇 가지 가상 및 다운로드 가능한 제품을 식별합니다.</td>
<td>이러한 제품들은 Faa와의 다운스트림 충돌을 방지하기 위해 내보내기에서 적절하게 제거되거나 플래그가 지정됩니다.</td>
</tr>
</tbody>
</table>

### 주문 취소 워크플로우

테스트 계획의 이 섹션에는 Adobe Commerce을 통해 취소된 주문에 대해 종단 간 워크플로우를 테스트하는 시나리오가 포함되어 있습니다.

**기능 영역:** Adobe Commerce 관리</br>
**역할:** 엔드 투 엔드(관리, 스토어 연결, 고객)</br>
**테스트 결과 유형:** 모든 시나리오에 대해 양수

<table style="table-layout:fixed">
<tr>
<th>함수</th>
<th>시나리오</th>
<th>예상 결과</th>
</tr>
<tr>
<td><strong>전체 주문 취소</strong></td>
<td><ol>
<li>주문.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장 전자 메일의 송장 생성(승인 및 캡처인 경우)을 확인합니다.</li>
<li>송장 뷰의 모든 주문 제품이 있는 대변 메모를 생성합니다.</li>
</ol>
</td>
<td>
<ul>
<li>주문 내역이 <code>We refunded $X online. Transaction ID: transactionID</code> 및 <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>주문 상태는 <code>Closed</code>. (지금 지급 검토를 설정했습니다.)</li>
<li>Adobe Commerce에서 만든 대변 메모입니다. (크론이 작동할 때까지 기다립니다.)</li>
<li>모든 항목을 선택한 경우 전자 메일 픽업 준비 <code>DISPLAY COMMENT HISTORY</code> 표시 <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> 플래그 <code>true</code>)</li>
<li>모든 항목을 선택하지 않으면 취소 전자 메일 및 설명 기록 표시가 표시됩니다 <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> 플래그 <code>true</code>)</li>
</ul>
</td>
</tr>
<tr><td><strong>부분 주문 취소<strong></td>
<td>
<ol>
<li>적어도 두 개의 제품을 주문하십시오.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었고(승인 및 캡처된 경우) 송장 이메일이 수신되었는지 확인합니다.</li>
<li>거래 결제를 위해 2시간 대기하세요.</li>
<li>송장 뷰에서 주문 제품의 일부만 사용하여 대변 메모를 생성합니다.</li>
</td>
<td>
<ul>
<li>주문 내역 업데이트: <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>주문 내역 업데이트: <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>주문 환급 이메일 수신: <code>$x amount was refunded</code></li>
<li>주문 상태는 <code>Processing</code>.</li>
<li>Adobe Commerce에서 만든 대변 메모(크론이 작동할 때까지 대기).</li>
<li>일부 항목을 선택하지 않은 경우 [!UICONTROL Ready for Pickup] 닐피킹 또는 환불 섹션이 포함된 이메일이 표시됩니다. <code>DISPLAY COMMENT HISTORY</code> 표시 <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> 플래그 <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>픽업 준비</br></br>전체 취소</br>(모든 제품이 0 수량이 있는 선택으로 설정됨)</br></strong></td>
<td>
<ol>
<li>주문하세요.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었고(승인 및 캡처된 경우) 송장 이메일이 수신되었는지 확인합니다.</li>
<li>Postman으로 이동하여 모든 제품이 로 설정된 픽업 준비 요청을 실행합니다. <code>picked</code> with <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>주문 내역이 업데이트되었습니다. <code>We refunded $X offline</code></li>
<li>주문 상태는 입니다. <code>CLOSED</code>.
<li>대변 메모가 생성됩니다. (크론이 작동할 때까지 기다립니다.)</li>
<li>받은 환불 이메일: <code>$x amount was refunded</code></li>
<li>주문 취소 이메일을 보냈습니다.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>픽업 준비 - 부분 취소</strong></br></br><strong>(일부 제품을 선택하고 <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>주문하세요.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었고(승인 및 캡처된 경우) 송장 이메일이 수신되었는지 확인합니다.</li>
<li>Postman으로 이동하여 0 수량 및 나머지 제품 선택과 함께 제품 중 일부가 설정된 픽업 준비 요청을 실행합니다.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] 및 [!UICONTROL Canceled Items] 표. </li>
<li>주문 상태가 픽업 준비가 되었습니다. </li>
<li>주문 내역이 업데이트되었습니다. <code>We refunded $X offline.</code>
<li>주문 내역이 업데이트되었습니다. <code>Order notified as partly canceled at: Date and hour</code>
<li>받은 환불 이메일: <code>$x amount was refunded</code>
<li>대변 메모가 생성됩니다. (크론이 작동할 때까지 기다립니다.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>픽업 준비 - 부분 취소</br></br>일부 제품이 선택되고 어떤 제품은 <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>주문하세요.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었고(승인 및 캡처된 경우) 송장 이메일이 수신되었는지 확인합니다.</li>
<li>Postman으로 이동하여 0 수량 및 나머지 제품 선택과 함께 제품 중 일부가 설정된 픽업 준비 요청을 실행합니다.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> with [!UICONTROL Ready for Pickup Items] 및 [!UICONTROL Canceled Items] 표. </li>
<li>주문 상태가 픽업 준비가 되었습니다. </li>
<li>주문 내역이 업데이트되었습니다. <code>We refunded $X offline.</code>
<li>주문 내역이 업데이트되었습니다. <code>Order notified as partly canceled at: Date and hour</code>
<li>받은 환불 이메일: <code>$x amount was refunded</code>
<li>대변 메모가 생성됩니다. (크론이 작동할 때까지 기다립니다.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>조제한(조제한 중) </br></br>전체 취소(모든 제품이 거부됨으로 설정됨)</strong>
</td>
<td>
<ol>
<li>주문하세요.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었고(승인 및 캡처된 경우) 송장 이메일이 수신되었는지 확인합니다.</li>
<li>Postman으로 이동하여 모든 제품이 선택된 상태로 설정된 픽업 준비 요청을 실행합니다.</li>
<li>사서함을 열고 픽업 준비 이메일을 찾습니다. 그런 다음 를 **[!UICONTROL Confirm Arrival]**.</li>
<li>체크인.</li>
<li>Postman으로 이동하여 거부됨으로 설정된 모든 제품과 함께 디스펜서 요청을 실행합니다.</li>
</ol>
<td><ul>
<li>주문 내역이 업데이트되었습니다. <code>We refunded $X offline.</code></li>
<li>받은 환불 이메일: <code>$x amount was refunded</code></li>
<li>상태 설정 <code>CLOSED</code>.</li>
<li>대변 메모가 생성되었습니다. (크론이 작동할 때까지 기다립니다.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>조제한(조제한 중)</br></br>부분 취소</br>(1) 조제하는 제품 일부 항목은 거부됩니다.)</strong>
</br></td>
<td>
<ol>
<li>주문하세요.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었고(승인 및 캡처된 경우) 송장 이메일이 수신되었는지 확인합니다.</li>
<li>Postman으로 이동하여 모든 제품이 선택된 상태로 설정된 픽업 준비 요청을 실행합니다.</li>
<li>사서함을 엽니다. Ready for Pickup 이메일을 찾아 <code>Confirm Arrival</code>.</li>
<li>체크인.</li>
<li>Postman으로 이동하고 디스펜싱이 설정된 일부 제품과 거부됨으로 설정된 디스펜싱 요청을 실행합니다</li>
</ol>
</td>
<td>
<li>주문 내역이 업데이트되었습니다. <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>받은 환불 이메일: <code>$x amount was refunded</code>
<li>주문 상태 설정 <code>Ready for pickup Dispensed</code>
<li>대변 메모가 생성되었습니다. (크론이 작동할 때까지 기다립니다.)</li>
</td>
</tr>
<tr>
<td> <strong>반품 후 신규 RMA(전체)</strong>
</td>
<td>
<ol>
<li>주문하세요.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었는지(승인 및 캡처된 경우) 확인하고 송장 이메일을 수신했는지 확인합니다.</li>
<li>Postman을 사용하여 모든 제품을 선택합니다.</li>
<li>체크인.</li>
<li>조제하세요.</li>
<li>주문으로 이동하고 을 선택합니다.<strong>[!UICONTROL Create returns]=
<li>RMA를 생성합니다.</li>
</ol>
</td>
<td>
<ul>
<li>RMA가 생성되었으며 아래에 표시됩니다 <strong>[!UICONTROL Returns]</b> 탭을 클릭합니다.</li>
<li>고객이 RMA 확인 이메일을 받았습니다.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>반품 후 신규 RMA — 일부</strong>
</td>
<td>
<ol>
<li>주문하세요.</li>
<li>주문이 동기화될 때까지 기다립니다.</li>
<li>송장이 생성되었고(승인 및 캡처된 경우) 송장 이메일이 수신되었는지 확인합니다.</li>
<li>Postman을 사용하여 모든 제품을 선택합니다.</li>
<li>체크인.</li>
<li>조제하세요.</li>
<li>주문으로 이동한 다음  <strong>[!UICONTROL Create returns]</strong></li>
<li>주문 제품의 일부로 RMA를 생성합니다.</li>
</ol>
<td>
<ul>
<li>RMA는 <strong>[!UICONTROL Returns]</strong> 탭을 클릭합니다.</li>
<li>고객이 RMA 확인 이메일을 받았습니다.</li>
<li>RMA를 생성한 후 RMA 인증을 받습니다. 관리자에서 로 이동합니다. <strong>[!UICONTROL Sales > Returns]</strong>. 생성한 RMA를 선택하고 권한을 부여합니다.</li>
<li>고객이 RMA 인증 확인 이메일을 수신했는지 확인합니다.</li>
<li>환불이 거래 및 주문 내역에 추가되었는지 확인하십시오.</li>
</ul>
</td>
</tr>
</table>


### Store Fulfillment 앱 권한

테스트 계획의 이 섹션에서는 Store Fulfillment App 사용자의 계정 관리를 다룹니다.

- Store Associate가 Adobe Commerce 관리자에서 만든 새 사용자 계정으로 인증할 수 있는지 확인합니다.
- 기존 계정에 대한 업데이트가 성공적으로 적용되었는지 확인합니다.

**기능 영역:** Adobe Commerce 관리</br>
**역할:** 관리, 저장 연결</br>
**테스트 유형:** 모두 양수

<table style="table-layout:auto">
<tr>
<th>함수</th>
<th>시나리오</th>
<th>예상 결과</th>
</tr>
<tr>
<td><strong>사용자 계정 관리 - 계정 만들기</strong></br></br>
</td>
<td>
<ol>
<li><strong>관리</strong> — Adobe Commerce 관리자에 로그인</li>
<li>이동 <strong>[!UICONTROL System] &gt; Store Fulfillment 앱 권한 &gt; 모든 Store Fulfillment 앱 사용자</strong></li>
<li><strong>새 사용자를 추가합니다.</strong></li>
</ol>
<td>
<ul>
<li>계정을 만들었습니다.</li>
<li>새 사용자 계정이 [!UICONTROL Store Fulfillment Users] 대시보드 .</li>
<li><strong>저장소 연결</strong> 새 사용자 계정으로 스토어 지원 앱에 로그인합니다.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>사용자 계정 관리 - 기존 사용자 계정 업데이트</strong>
</td>
<td>
<ol>
<li>관리자 사용자 계정을 사용하여 Adobe Commerce 관리자에 로그인합니다.</li>
<li>이동 <strong>[!UICONTROL System] &gt; Store Fulfillment 앱 권한 &gt; 모든 Store Fulfillment 앱 사용자</strong>.</li>
<li>사용자 계정 목록에서 기존 활성 사용자 계정을 선택하여 엽니다 <strong>[!UICONTROL Edit]</strong>.
<li>다음을 변경하여 계정 비활성화 <strong>[!UICONTROL Is Active]</strong> to <strong>아니요</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>설정 <strong>[!UICONTROL Store Fulfillment App Users]</strong> 대시보드, 업데이트된 계정의 상태가 <strong>[!UICONTROL Inactive]</strong>.</li>
<li>저장소 연결은 비활성 계정 자격 증명으로 스토어 지원 앱에 로그인할 수 없습니다.</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce 제품 유형

Adobe Commerce 제품 유형에 대한 테스트 시나리오는 고객이 다양한 제품 유형에 대한 올바른 제품, 재고 및 전달 방법 정보를 보고 있는지 확인합니다.

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] Adobe Commerce 상점.

**기능 영역:** Adobe Commerce 프론트엔드</br>
**역할:** 스토어 지원 앱 사용자(스토어 연결)</br>
**테스트 유형:** 모두 양수

<table style="table-layout:auto">
<tr>
<th>함수</th>
<th>시나리오</th>
<th>댓글</th>
</tr>
<tr>
<td><strong>구성 가능한 제품</strong>
</td>
<td>
<ul>
<li>사용자가 소스가 사용으로 설정되고, 재고가 지정되며, 일부 품목이 재고에 있는지, 하위 제품을 체크 인하는 구성 가능한 옵션만 볼 수 있는지 확인합니다.</li>
<li>다른 저장소를 선택할 때 사용할 수 없는 옵션이 잘못 표시된 것으로 표시되는지 확인합니다.</li>
<li>사용자가 다른 저장소를 선택하는 경우 구성 가능한 옵션이 선택 취소되는지 확인합니다.</li>
<li>구성 가능한 제품이 이미 장바구니에 있고 사용자가 다른 스토어를 선택하면 제품이 재고 부족 상태로 표시되는지 확인합니다.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>그룹화된 제품</strong>
</td>
<td>
<ul>
<li>게재 방법 및 [!UICONTROL Add to cart] 모든 하위 제품에 대해 단추가 비활성화되어 있습니다
<code>qty</code> 설정 <code>0</code>.</li>
<li>하위 제품 중 하나 이상이 있는 경우 고객에 대해 게재 방법이 활성화되어 있는지 확인합니다 <code>qty</code> 설정 <code>0.</code></li>
<li>확인 [!UICONTROL Store Pickup Delivery] 메서드는 [!UICONTROL Available for Store Pickup] 활성화되었습니다. (하위 제품 확인)</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>가상 제품</strong>
</td>
<td>
가상 제품이  [!UICONTROL In-store Pickup] 전달 방법.
<td></td>
</td>
</tr>
<tr>
<td><strong>번들 제품</strong>
</td>
<td>
<ul>
<li>하나 이상의 하위 제품에 가 있는지 확인합니다. [!UICONTROL Available for Store Pickup] 비활성화되어 있으면 고객이 Store Pickup 배달 옵션을 사용할 수 없습니다.</li>
<li>하나 이상의 하위 제품에 가 있는지 확인합니다. [!UICONTROL Available for Home Delivery] 비활성화되어 있으면 고객이 [홈 배달] 옵션을 사용할 수 없습니다.</li>
<li>번들에 있는 하위 제품 중 하나 이상이 재고가 있는지, 번들(상위 제품)도 [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## 체크인 경험

테스트 계획의 이 섹션에서는 다음 기능에 대한 스토어 픽업 주문에 대한 체크인 경험을 다룹니다.

- 대체 픽업 연락처 - 추가 작업 과정을 확인합니다. [!UICONTROL Alternate Pickup Contact] 및 선택 [!UICONTROL Preferred Contact] 매장 픽업 주문

- 체크인 양식 - 저장 픽업 주문에 대한 체크인 요청을 제출하는 워크플로우를 확인합니다.

**기능 영역:** 장바구니 체크아웃, 저장소 픽업 주문을 위한 체크인 양식</br>
**역할:** 관리자, 고객, 저장소 연결</br>
**테스트 유형:** 모두 양수

### 대체 픽업 연락처


**기능 영역:** 장바구니 체크아웃</br>
**역할:** 고객</br>
**테스트 유형:** 모두 양수

<table style="table-layout:auto">
<tr>
<th>함수</th>
<th>시나리오</th>
<th>예상 결과</th>
</tr>
<tr>
<td><strong>대체 픽업 연락처</br>
체크인</br><strong>
</td>
<td>
고객이 매장 내 픽업 옵션을 사용하여 주문을 제출합니다.</td>
<td>체크아웃 프로세스 중에 고객이 를 확인합니다. [!UICONTROL Alternate Pickup Contact] 운송 단계의 옵션.
</td>
</tr>
<tr>
<td><strong>대체 픽업 기본 연락, 체크 인</strong>
<td>
고객이 매장 내 픽업 옵션을 사용하여 주문을 제출합니다. 이 고객은 체크아웃 중에 [!UICONTROL Alternate Pickup Contact].</td>
<td>체크아웃 프로세스 중에 고객이 를 확인합니다. [!UICONTROL Preferred Contact] 옵션을 선택합니다.</td>
</td>
</tr>
<tr>
<td><strong>대체 픽업 연락처 정보, 체크 인</strong>
</td>
<td>
고객이 매장 내 픽업 옵션을 사용하여 주문을 제출합니다. 체크아웃 중에 고객이 선택합니다 [!UICONTROL Alternate Pickup Contact] 운송 단계에서
</td>
<td>고객은 연락처 정보를 입력하는 입력 옵션을 봅니다. [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone], 및 [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>대체 픽업, 이메일 체크 인</strong>
</td>
<td>고객이 매장 내 픽업 옵션을 사용하여 주문을 제출합니다. 체크아웃 중에 고객이 선택합니다 [!UICONTROL Alternate Pickup Contact] 운송 단계에서 담당자 상세내역을 추가하고 주문을 실행합니다.</td>
<td>고객과 대체 담당자가 모두 주문에 대한 체크인 이메일을 받게 됩니다.</td>
</tr>
<td><strong>대체 픽업, 주문 상세내역</strong></td>
<td>고객이 매장 내 픽업 옵션을 사용하여 주문을 제출합니다. 체크아웃 중에 고객이 선택합니다 [!UICONTROL Alternate Pickup Contact] 운송 단계에서 담당자 상세내역을 추가하고 주문을 실행합니다.</td>
<td>관리자는 저장된 주문에 대한 추가 연락처 정보를 볼 수 있습니다.</td>
</tr>
<tr>
<td><strong>대체 픽업 담당자, 저장 연관 주문 뷰</strong>
</td>
<td>고객이 매장 내 픽업 옵션을 사용하여 주문을 제출합니다. 체크아웃 중에 고객이 선택합니다 [!UICONTROL Alternate Pickup Contact] 운송 단계에서 담당자 상세내역을 추가하고 주문을 실행합니다.</td>
<td>스토어 연합은 FaaS/ChaS에서 주문에 대한 추가 연락 정보를 볼 수 있습니다.</td>
</td>
</tr>
</tbody>
</table>

### 체크인 양식


**기능 영역:** 체크인 양식</br>
**역할:** 고객</br>
**테스트 유형:** 모두 양수

<table style="table-layout:auto">
<tr>
<th>함수</th>
<th>시나리오</th>
<th>예상 결과</th>
</tr>
<tr>
<td><strong>체크 인 작업 - 요청 제출</strong>
</td>
<td>체크인 양식에서 고객이 모든 필수 필드를 완료하고 요청을 제출합니다.</td>
<td>고객이 성공 응답을 수신합니다.</td>
</tr>
<tr>
<td><strong>체크 인 작업 - 요청 세부 정보 보기</strong></td>
<td>고객이 체크 인 요청을 제출했습니다.</td>
<td>Faa 시스템의 주문 상태 갱신과 스토어 연관은 Faa에서 체크인 요청 상세내역을 볼 수 있습니다.
</td>
</tr>
<tr>
<td><strong>체크 인 작업 - 요청을 한 번만 제출합니다</strong></td>
<td>주문에 대한 체크인 요청을 제출한 후 고객이 다시 체크인할 링크를 선택합니다.</td>
<td>체크인 양식에서 고객에게 양식을 편집하거나 다시 제출할 수 있는 옵션이 표시되지 않습니다.</td>
</tr>
<tr>
<td><strong>체크 인 작업 - 도착 확인</strong></td>
<td>매장 내 픽업 주문이 FAA에서 픽업할 준비가 된 것으로 표시되었습니다. 고객은 픽업 준비 이메일을 수신하고 을 선택합니다 [!UICONTROL Confirm Arrival].</td>
<td>고객은 주문에 대한 체크인 양식이 표시됩니다.</td>
</tr>
</tbody>
</table>

## 스토어 지원 앱

테스트 계획의 이 섹션에서는 스토어 지원 앱의 테스트 순서, 선택 및 핸드오프 워크플로우에 대한 시나리오를 다룹니다.

**기능 영역:** 스토어 지원 앱</br>
**역할:** 저장소 연결</br>
**테스트 유형:** 모두 양수

<table style="table-layout:auto">
<tr>
<th>함수</th>
<th>시나리오</th>
<th>예상 결과</th>
</tr>
<tr>
<td>
<strong>단일 주문 피킹—행복한 경로, 커브사이드 픽업</strong></td>
<td>단일 및 복수 수량 품목을 선택합니다. 밀림 없음 및 커브사이드 픽업(스테이징 포함).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>다중 주문 피킹—행복한 경로, 커브사이드 픽업하기</strong></td>
<td>단일 및 다중 수량 품목. 닐코핑 없음 및 커브사이드 픽업(스테이징 포함)</td>
<td></td>
</tr>
<tr>
<td><strong>단일 주문 피킹—저장 내 경로 픽업</strong></td>
<td>단일 및 다중 수량 품목. Nilpick 없음 및 Instore Pick-up(스테이징 포함)</td>
<td>
</td>
</tr>
<tr>
<td><strong>다중 주문 선택—행복한 경로, 매장 내 픽업</strong></td>
<td>단일 및 복수 수량 품목을 선택합니다. 밀림 없음 및 커브사이드 픽업(스테이징 포함).</td>
<td></td>
</tr>
<tr>
<td><strong>단일 주문 피킹—행복한 경로 아님, 매장 내 픽업</strong></td>
<td>부분적 및 하위 출고 및 설치(스테이징 포함)가 있는 단일 및 다중 수량 품목 선택</td>
</td>
<td></td>
</tr>
<td><strong>다중 주문 피킹(Multi Order Picking) - 행복한 경로 조정 픽업이 아님</strong></td>
<td>부분적 및 하위 출고 및 설치(스테이징 포함)가 있는 단일 및 다중 수량 품목 선택</td>
<td></td>
</tr>
<td><strong>단일 주문 피킹—행복한 경로 아님, 커브사이드 픽업</strong></td>
<td>부분적 및 하위 출고 및 조정 픽업(스테이징 포함)이 있는 단일 및 다중 수량 품목 선택</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>주문 - 피킹 전 취소됨</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>주문 - 핸드오프 전에 취소됨</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>주문 - 검색 순서 모듈</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>주문 - 핸드오프에 대한 검색 및 수동 체크 인</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>주문 - 선택기에서 선택되었거나 선택기에서 표시할 수 없는 모든 항목</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>번들 품목이 포함된 주문 - 피킹 및 핸드오프</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>주문 배치됨 - 거부 상태로 핸드오프</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>주문 - 모든 품목에 대한 거부 상태로 핸드오프</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## 배포

솔루션이 사양에 맞게 구성 및 테스트되었는지 확인했으면 스테이징에서 프로덕션에 배포할 준비가 된 것입니다.

배포 및 테스트는 인프라 및 기능에 따라 다릅니다.

>[!TIP]
>
>클라우드 인프라 프로젝트에서 Adobe Commerce에 대한 배포 지침, 확인 목록 및 우수 사례에 대해서는 다음을 참조하십시오 [스토어 배포](https://devdocs.magento.com/cloud/live/stage-prod-live.html) ( Adobe Commerce 개발자 설명서).
