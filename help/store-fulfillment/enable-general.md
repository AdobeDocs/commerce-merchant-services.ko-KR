---
title: 일반 구성
description: 일반 설정을 구성하여 사용 [!DNL Store Fulfillment] 스토어용. 전역 확장 설정, 로깅, 데이터 동기화 및 보안에 대한 시스템 설정을 구성합니다. Adobe Commerce과 스토어 이행 서비스 간의 통합을 가능하게 하는 주요 데이터를 제공합니다.
role: Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '2419'
ht-degree: 0%

---

# 서비스 및 판매 구성 저장

사용 [!DNL Store Fulfillment] 에서 확장명 [!DNL Commerce] 확장 설정, 스토어 지원 앱 사용자에 대한 보안 설정 및 배달 방법 옵션을 구성하여 관리자.

>[!IMPORTANT]
>
>스토어 이행 서비스 구성은 Adobe Commerce 인스턴스와 를 연결한 후에만 적용됩니다 [!DNL Store Fulfillment] 앱. 다음을 참조하십시오 [저장소 이행 연결](connect-set-up-service.md).

## 스토어 이행 서비스 설정 관리

에서 스토어 이행 서비스에 대한 설정을 관리합니다. [!DNL Commerce Admin Store Configuration] 메뉴 아래의 제품에서 사용할 수 있습니다.

- 를 선택하여 확장을 활성화하고, 전역 설정을 구성하고, Store Assist 앱 사용자 연결 및 계정에 대한 보안 옵션을 지정합니다. **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

  ![스토어 이행 관리를 위한 Admin Store 서비스 구성](assets/store-services-admin-sf-config.png)

- 을 선택하여 게재 방법 구성 **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

  ![스토어 이행 관리를 위한 관리자 스토어 판매 구성](assets/store-sales-admin-sf-deliver-config.png)

## 기본 설정

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>매장 내 픽업 비용을 고객에게 청구하는 가격입니다. 기본값은 0입니다.</td>
<td>웹 사이트</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>쇼핑객이 상점 앞의 계산대에서 상점 픽업 위치를 검색할 때 사용할 반경(킬로미터)입니다. 검색 결과는 지정된 검색 반경 내에 있는 저장소만 반환합니다.</td>
<td>웹 사이트</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>고객이 매장 내 픽업에 사용할 수 없는 항목에 대해 매장 내 픽업을 선택할 때 표시되는 메시지입니다. 필요한 경우 기본 텍스트를 사용자 정의할 수 있습니다.
</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>다음 [!UICONTROL Search Radius] 설정은 다음을 구성한 경우에만 사용됩니다. [저장소 위치 및 매핑 설정](store-location-map-provider-setup.md) Adobe Commerce용

## 스토어 이행 솔루션 활성화

활성화 [!DNL Store Fulfillment] Adobe Commerce 상점 첫 화면의 쇼핑 및 체크아웃 경험에 매장 내 및 매장 내 픽업 기능을 추가하는 솔루션입니다.

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>솔루션을 활성화하거나 비활성화합니다. 활성화된 경우 스토어 이행 기능을 구성 및 사용하고 Adobe Commerce 스토어와 간에 연결을 설정하십시오. [!DNL Store Fulfillment] 서비스. 비활성화되면 모든 스토어 이행 기능이 비활성화되고, Adobe Commerce과 스토어 이행 서비스 간에 통신이 없습니다. 주문 정보를 처리하거나 수신할 수 없습니다.</td>
<td>웹 사이트</td>
<td>예</td>
</tr>
</tbody>
</table>

## 계정 자격 증명 추가

<table>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>다음 중 하나를 선택합니다. <i>[!UICONTROL Sandbox]</i> 또는 <i>[!UICONTROL Production]</i><br></br>선택 [!UICONTROL Sandbox] 테스트 환경에서 fulfillment services와의 통신을 활성화합니다.<br></br>선택 [!UICONTROL Production] 라이브 환경에서 fulfillment services와의 통신을 활성화합니다.<br></br>각 환경에 대한 자격 증명 세트가 제공되며 동일한 설치에서 두 세트를 모두 관리할 수 있습니다. <br></br>연결의 유효성을 검사하기 전에 자격 증명을 저장합니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>Walmart Store Fulfillment API 엔드포인트에 대한 URL. 값은 온보딩 프로세스 중에 제공되는 정규화된 URL이어야 합니다. 스토어 이행 고객은 샌드박스와 프로덕션 URL을 모두 받습니다. 값을 추가할 때 슬래시 "/"를 포함하여 전체 URL을 복사하여 붙여넣어야 합니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>Walmart Store 이행 인증 엔드포인트의 URL. 값은 온보딩 프로세스 중에 제공되는 정규화된 URL이어야 합니다. 샌드박스와 프로덕션 URL을 모두 받습니다. 값을 추가할 때 슬래시 "/"를 포함하여 전체 URL을 복사하여 붙여넣어야 합니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>온보딩 프로세스 중에 제공된 고유 판매자(테넌트) ID입니다. 이 ID는 판매점에서 주문을 받을 수 있도록 주문을 라우팅하는 데 사용됩니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>온보딩 프로세스 중에 제공된 고유한 통합 ID입니다. 이 ID는 Adobe Commerce과 스토어 이행 서비스 간의 모든 통신을 인증하는 데 사용됩니다</td>
<td>글로벌</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>온보딩 프로세스 중에 제공된 고유한 통합 키. 이 키는 Adobe Commerce과 스토어 이행 서비스 간의 모든 통신을 인증하는 데 사용됩니다.</td>
<td>글로벌</td>
<td>예</td>
</tr>
</table>

을(를) 구성한 후 [!UICONTROL Account Credentials], 선택 <strong>[!UICONTROL Validate Credentials]</strong> 를 사용하여 처음으로 스토어 이행 서비스에 대한 연결을 확인하고 설정합니다.

## 로깅 구성

저장소 이행 서비스에 대한 로그는 로그 파일에서 사용할 수 있습니다. `var/log/walmart-bopis.log`.

API 관련 예외가 방화벽 또는 캐시를 통해 캡처될 수 있도록 시스템 관리자에게 예외 처리를 허용하도록 환경을 구성하도록 요청하십시오.

애플리케이션 로그 파일이 빠르게 늘어날 수 있으므로 필요할 때 단기간 동안만 애플리케이션에 대한 로깅을 활성화하십시오. 예를 들어 의 스토어 이행 문제를 해결할 때 이를 사용합니다. [!DNL Commerce] 주문. 이 구성은 큰 로그 파일로 인해 프로덕션 환경에서 발생하는 응답 시간 문제를 방지합니다.

>[!TIP]
>
>Adobe Commerce 온-프레미스 설치의 경우 시스템 관리자에게 다음에 대한 로그 순환을 설정하도록 요청하십시오. `var/log/walmart-bopis.log` 파일 을 입력하여 크기를 최소화합니다. Adobe Commerce 온-프레미스 설치의 경우 [로그 회전](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) 다음에서 _Adobe Commerce 설치 안내서_. 클라우드 인프라 프로젝트의 Adobe Commerce에 대해서는 다음을 참조하십시오. [로그 보기 및 관리](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>디버그 모드는 통합 내에서 로그된 활동을 늘리는 데 사용됩니다. 비활성화되면 디버그 정보가 기록되지 않습니다. 활성화되면 모든 디버그 정보가 기록됩니다 <br></br>모든 로그 데이터는 파일에서 찾을 수 있습니다. <pre>var/log/walmart-bopis.log</pre>
<td>글로벌</td>
<td>아니요</td>
</tr>
</tbody>
</table>

## 주문 동기화 관리

주문 동기화에 대한 오류 처리를 관리하고, 주문 피킹 동안 바코드 스캔에 사용할 카탈로그 속성을 관리하며, 스토어 이행 대기열에 대한 주문 배치 크기를 구성하십시오.

관리자( )의 스토어 이행 대기열 관리 대시보드에서 주문 동기화 작업에 대한 세부 정보를 볼 수 있습니다.
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### 동기화 오류 관리

<table>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>심각한 오류가 발생한 후 레코드 동기화 작업을 다시 시도하도록 지정합니다.<br></br>통합이 이행 서비스에서 긍정적인 응답을 얻지 못할 때마다 심각한 오류가 발생합니다. 이러한 문제는 서비스가 중단되거나 전송되는 주문 데이터에 오류가 있을 때 발생합니다.<br></br>다시 시도 임계값에 도달하면 항목이 큐에 남아 있지만 다시 처리되지 않습니다. 다음에서 오류가 발생한 모든 항목 보기: <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> 관리에서의 관리. 지속적으로 오류가 발생하는 항목의 문제를 해결하려면 계정 관리자에게 문의하십시오.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>다음의 경우에 이메일을 수신하도록 오류 알림 활성화 [!UICONTROL Retry Critical Error Threshold] 주문에 도달했습니다. 알림에는 오류에 대해 사용 가능한 모든 세부 정보가 포함됩니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>오류 알림에 대한 수신자 이메일 주소의 쉼표로 구분된 목록입니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>주문 동기화 오류에 대해 수신자에게 알리는 데 사용되는 전자 메일 템플릿을 지정합니다. 기본 템플릿이 제공됩니다. 사용자 지정을 지원하지 않습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
</table>

### 주문 동기화

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>판매자 위치의 해당 항목에 대한 훑어볼 수 있는 코드를 저장하는 카탈로그 속성.<br></br>기존 판매자 위치가 한 곳뿐인 경우 전자 상거래 채널이 SKU별로 제품을 식별하는 동안 UPC 코드를 사용할 수 있습니다. 이 시나리오에서는 UPC 코드가 포함된 카탈로그 속성을 선택합니다.<br></br>이 설정을 사용하면 스토어로 보낸 주문에서 올바른 식별자를 사용하여 목록 항목을 검색할 수 있으므로 스토어 관계자가 피킹 프로세스 중에 항목을 정확하게 스캔할 수 있습니다.<br></br>확실하지 않은 경우 운송 및 피킹 부서의 이행 담당자에게 문의하여 어떤 속성을 전송해야 하는지 확인하십시오. 속성이 현재 데이터베이스에 포함되어 있지 않으면 Adobe Commerce 제품 속성 세트에 속성을 추가할 수 있습니다.</td>
<td>웹 사이트</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>판매자 위치의 해당 품목에 대한 바코드 소스를 저장하는 카탈로그 속성.<br></br>이 설정을 사용하면 스토어로 보낸 주문에서 올바른 식별자를 사용하여 목록 항목을 검색할 수 있으므로 스토어 관계자가 피킹 프로세스 중에 항목을 정확하게 스캔할 수 있습니다. 옵션에는 SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC가 포함됩니다.<br></br>확실하지 않은 경우 다음에 포함된 값과 가장 유사한 옵션을 선택합니다. [!UICONTROL Barcode Source] 특성. 스토어 연합은 여전히 선택 목록에서 항목을 수동으로 일치시킬 수 있습니다.</td>
<td>웹 사이트</td>
<td>예</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>저장소 이행 대기열에서 한 번에 보낼 최대 항목 수입니다.<br></br>BOPIS 주문은 일정한 간격으로 이행 서비스로 일괄적으로 전송됩니다. 이 설정을 사용하면 일괄 처리의 크기를 제어할 수 있습니다.<br></br>기본값은 100개 항목입니다. 주문량과 용량에 따라 최대값을 위 또는 아래로 조정할 수 있습니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
</tbody>
</table>

## 스토어 이행 운송 옵션 사용

Adobe Commerce 스토어에 대한 매장 내 픽업 및 홈 배송 옵션의 가용성을 결정하는 스토어 이행 배송 옵션을 구성합니다.

### 배송처 저장소

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>납품처 스토어 설정은 기존 납품처 스토어 기능을 기반으로 합니다. Inventory management을 사용하거나, 점포 간 재고 이전을 통해 재고가 없는 판매자 위치에서 주문을 수락하고 이행할 수 있는 경우, 이 옵션을 '예'로 설정합니다.<br></br>납품처 스토어 옵션을 지원할 수 없거나 제공을 원하지 않는 경우 '아니요'로 설정합니다. 비활성화되면, 카탈로그에 있는 품목과 판매점에 대한 재고가 0인 품목 또는 [!DNL Out of Stock Threshold] 해당 위치에서는 매장 내 픽업 옵션이 제공되지 않습니다.<br></br>판매자 위치에 따라 이 설정의 값을 조정할 수 있습니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
</tbody>
</table>

### 출고처 상점

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>가맹점에서 택배 옵션을 활성화하거나 비활성화합니다. 활성화하면 가맹점 위치는 웹 사이트와 연계된 재고에서 지정된 다른 출처와 합산되어 고려됩니다.<br></br>표준 Inventory management 서비스에서 [!DNL Ship from Store] is 옵션은 고유하며 비활성화할 수 없습니다. Store Fulfillment 솔루션을 사용하면 이 기능을 켜거나 끌 수 있습니다.<br></br>판매자 위치 및 제품에 따라 이 설정을 조정할 수 있습니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
</tbody>
</table>


## 스토어 이행 앱 사용 계정 및 권한 관리

스토어 이행 앱 사용자 계정 및 암호 보안과 2단계 인증에 대한 설정을 구성합니다.

### 앱 보안

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>자동 로그아웃 전에 저장소 연결 사용자 세션이 활성 상태로 유지되는 기간(초)입니다. 유효한 값의 범위는 60에서 31536000까지입니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>저장소 연결이 해당 계정에서 잠기기 전에 허용되는 로그인 시도 실패 횟수를 지정합니다.<br></br>계정 잠금을 비활성화하려면 값을 0으로 설정합니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>로그인 실패 후 계정을 잠그는 시간(분)입니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>: 계정 설정 후 사용자가 암호를 변경해야 합니다.<br></br><em>[!UICONTROL No]</em>: 계정 설정 후 사용자가 암호를 변경할 것을 권장합니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>필수 암호를 변경하기 전 암호가 유효하게 유지되는 일 수입니다. 이 옵션을 비활성화하려면 비워 둡니다.</td>
<td>글로벌</td>
<td>아니요</td>
</tr>
</tbody>
</table>

## 게재 방법

스토어 이행 은 기본 Adobe Commerce을 확장하여 작동합니다 [!DNL In-Store Delivery] 기능. 확장을 설치한 후 관리자에 추가된 다음 확장 설정을 사용하여 매장 내 전달 방법을 구성할 수 있습니다.

- **매장 픽업**—체크아웃 프로세스 중에 매장 게재를 위한 옵션 제공 이러한 설정은 BOPIS 주문에 대한 가장 일반적인 게재 시나리오를 구성합니다.

- **[!UICONTROL Curbside pick up]**- 고객이 매장 위치에 주차하고 매장 직원이 주문한 상품을 배송받을 수 있는 옵션을 제공합니다.

을(를) 선택하여 관리자에서 이러한 설정을 구성합니다. <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>매장 내 배달 옵션 구성에 대한 자세한 내용은 [매장 내 게재](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) 다음에서 _Adobe Commerce 사용 안내서_.


### 게재 방법 구성

매장 내 배송 방법을 통해 고객은 체크아웃 시 픽업 장소로 사용할 소스를 선택할 수 있다.

<table>
<thead>
<tr>
<td><strong>필드</strong></td>
<td><strong>설명</strong></td>
<td><strong>범위</strong></td>
<td><strong>필수</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>매장 픽업을 선택하는 고객의 체크아웃 중에 사용할 수 있는 매장 픽업 옵션을 활성화하거나 비활성화합니다. 매장 픽업이 비활성화된 경우 옵션이 표시되지 않습니다.<br></br>이 전역 설정은 모든 소매점 위치에 적용됩니다. 활성화되면 리테일 스토어 위치에서 선택적으로 비활성화할 수 있습니다.</td>
<td>웹 사이트</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>매장 픽업을 선택하는 고객의 체크아웃 프로세스 중에 커브사이드 픽업 옵션을 활성화하거나 비활성화합니다.<br></br>이 전역 설정은 모든 소매점 위치에 적용됩니다. 활성화되면 리테일 스토어 위치에서 선택적으로 비활성화할 수 있습니다.</td>
<td>웹 사이트</td>
<td>아니요</td>
</tr>
</tbody>
</table>

### 게재 방법 제목 구성

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>홈 게재 제목</strong></td>
<td>제품, 장바구니 및 체크아웃 영역에서 홈 게재 옵션에 대해 표시할 제목을 지정합니다. 가정 배달은 Adobe Commerce의 표준 배송 기능(창고나 운송업체 또는 고객이 제공한 배송 주소로 직접 배송)을 의미합니다. </br></br>이 레이블은 선택한 운송 회사의 운송 방법 레이블에는 영향을 주지 않습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>홈 게재 설명</strong></td>
<td>홈 게재 제목이 고객에게 표시될 때마다 표시되는 선택적 설명입니다. 대부분의 경우 설명은 게재 약속을 전달하기 위한 정적 메시지입니다. 몇 가지 예:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>픽업 제목 저장</strong></td>
<td>고객에게 배달 옵션이 제공되고 매장 픽업을 사용할 수 있는 경우 이 레이블이 표시됩니다. </br></br>제품, 장바구니 및 체크아웃 영역에 표시되는 이 레이블을 사용자 지정할 수 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<td><strong>픽업 설명 저장</strong></td>
<td>스토어 픽업 제목이 표시되는 위치에 관계없이 선택적으로 설명을 포함할 수 있습니다. 이 정적 메시지는 스토어 픽업 경험과 관련된 고객 커뮤니케이션을 개선하는 데 도움이 됩니다. 몇 가지 예:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>매장 픽업 제목</strong></td>
<td>매장 픽업 기능이 활성화되면 이 제목이 매장 픽업 배달 옵션으로 고객에게 표시됩니다. 해당 레이블을 사용자 지정할 수 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<tr>
<td><strong>커브사이드 픽업 제목</strong></td>
<td>Curbside Pickup이 활성화되면 옵션은 Store Pickup 배달 옵션 유형으로 고객에게 표시됩니다. 여기에서 레이블을 사용자 지정할 수 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>매장 내 픽업 지침</strong></td>
<td>소매 상점에서 주문이 수거될 준비가 되면 고객에게 이메일로 통지됩니다. 고객이 선택한 경우 [!DNL In-Store Pickup] 체크아웃하는 동안 여기에서 픽업 지침을 사용자 지정할 수 있습니다. </br></br>이러한 지침은 전 세계적으로 설정되며 모든 소매점 위치에 적용됩니다. 소매점 위치 수준에서 지침을 사용자 지정할 수도 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>커브사이드 픽업 지침</strong></td>
<td>커브사이드 픽업 주문에 대한 고객 이메일 알림에 포함할 사용자 지정 주문 픽업 지침을 지정합니다. </br></br>이러한 지침은 전 세계적으로 설정되며 모든 소매점 위치에 적용됩니다. 소매점 위치 수준에서 지침을 사용자 지정할 수도 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>예상 픽업 리드 타임</strong></td>
<td>주문이 접수, 이행되고 픽업될 때까지 필요한 시간(분)입니다. 이 정보는 매장 픽업 배송 옵션에 대한 소매점 위치를 선택할 때 고객에게 표시됩니다. 이 설정은 모든 소매점 위치에 적용됩니다. 소매점 위치 수준에서 리드 타임을 사용자 지정할 수도 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>예상 픽업 시간 레이블</strong></td>
<td>고객 픽업에 주문을 사용할 수 있을 때까지의 예상 시간을 표시합니다. 이 정보는 고객이 다음에 대한 소매점 위치를 선택할 때 표시됩니다 [!DNL In-Store Pickup] 게재 옵션. </br></br>이 레이블을 사용자 지정할 때 코드를 사용할 수 있습니다 <code>%1</code> 을(를) 삽입하려면 <strong>예상 픽업 리드 타임</strong>. 예:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>이 설정은 모든 소매점 위치에 적용됩니다. 소매점 위치 수준에서 리드 타임을 사용자 지정할 수도 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
<tr>
<td><strong>픽업 시간 면책조항</strong></td>
<td>저장 시간, 휴일, 예기치 않은 종료 등을 나열하는 도구 설명의 제품 페이지에 표시되는 콘텐츠</td>
<td>스토어 뷰
</td>
<td>아니요
</td>
</tr>
</tbody></table>

### 재고 가용성 제목 구성

<table>
<thead>
<tr>
<th><strong>필드</strong></th>
<th><strong>설명</strong></th>
<th><strong>범위</strong></th>
<th><strong>필수</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>재고 있음</strong></td>
<td>고객이 소매점 보관처를 사용하는 경우 각 위치에 대해 현재 품목의 재고 가용성이 표시됩니다. </br></br>다음을 사용자 지정할 수 있습니다. <em>[!UICONTROL in-stock]</em> 여기에 상태 레이블이 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>품절</strong></td>
<td>고객이 소매점 보관처를 사용하는 경우 현재 품목의 재고 가용성이 각 위치에 대해 표시됩니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>부분적으로 입고됨</strong></td>
<td>고객이 소매점 보관처를 사용하는 경우 각 위치에 대해 현재 품목의 재고 가용성이 표시됩니다. </br></br>다음을 사용자 지정할 수 있습니다. <em>[!UICONTROL partially in-stock]</em> 여기에 상태 레이블이 있습니다.</td>
<td>스토어 뷰</td>
<td>아니요</td>
</tr>
</tbody></table>

