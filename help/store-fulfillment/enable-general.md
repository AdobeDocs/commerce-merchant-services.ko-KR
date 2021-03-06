---
title: 일반 구성
description: 일반 설정을 구성하여 활성화 [!DNL Store Fulfillment] 내 가게에요 전역 확장 설정, 로깅, 데이터 동기화 및 보안을 위한 시스템 설정을 구성합니다. Adobe Commerce과 Store Fulfillment Services 간의 통합을 사용하려면 주요 데이터를 제공하십시오.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: 556cbf803a0f8569e8561d2b33b7a976065ae814
workflow-type: tm+mt
source-wordcount: '2413'
ht-degree: 0%

---

# 일반 구성

Adobe 상거래 관리자에서 일반 구성 설정을 구성하여 사용하도록 설정합니다. [!DNL Store Fulfillment] 스토어에 대한 서비스를 구성하고, 전역 확장 설정을 구성하고, 를 구성하여 통합을 위한 주요 데이터를 제공합니다 [!UICONTROL Account Credentials].

통합은 Store Fulfillment 서비스에 연결되어 있어야 합니다. 또한 조직의 기능 및 운영 요구 사항에 따라 Store Fulfillment 서비스를 활성화하고 사용자 정의하도록 Store Fulfillment 일반 설정을 구성합니다.

에 대한 일반 구성 [!DNL Store Fulfillment] 에는 다음 구성 설정이 포함되어 있습니다.

- [솔루션 활성화](#enable-the-store-fulfillment-solution)
- [Store Fulfillment 서비스에 연결할 계정 자격 증명을 관리합니다.](#account-credentials)
- [로깅 구성](#configure-logging)
- [주문 및 오류 동기화 작업 관리 옵션을 설정합니다.](#order-synchronization)
- [저장 이행 운송 옵션 사용](#enable-store-fullment-shipping-options)
- [Store Fulfillment 앱에 대한 보안 및 인증 설정을 구성합니다](#store-fulfillment-app)
- [게재 방법 가용성 및 메시징 구성 설정](#in-store-delivery-methods)

## Store Fulfillment 솔루션 사용

| **필드** | **설명** | **범위** | **필수 여부** |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enabled]** | 솔루션을 활성화하거나 비활성화합니다. 활성화되면 Store Fulfillment 기능을 구성 및 사용하고 Adobe Commerce 스토어와 Store Fulfillment 서비스 간의 연결을 설정합니다. 비활성화되면 모든 Store Fulfillment 기능이 비활성화되며 Adobe Commerce과 Store Fulfillment 서비스 간에 통신이 이루어지지 않습니다. 주문 정보를 처리하거나 수신할 수 없습니다. | 글로벌 | 예 |

이 설정을 완료하려면 **Store > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies**.

## 계정 자격 증명 추가

| **필드** | **설명** | **범위** | **필수 여부** |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Environment]** | 선택할 수 있습니다 *샌드박스* 또는 *프로덕션*:</br> Sandbox는 테스트의 이행 서비스와 통신합니다.</br>프로덕션은 라이브 환경과 통신합니다. 사용 **전용** 제작 중입니다.</br>각 환경에 대한 자격 증명 세트가 제공되며 동일한 설치에서 두 세트를 관리할 수 있습니다. </br></br>연결을 검증하기 전에 자격 증명을 저장합니다. | 글로벌 | 예 |
| **[!UICONTROL API Server URL]** | Walmart Store Fulfillment API 끝점의 URL입니다. 이 URL은 온보딩 프로세스 중에 사용자에게 제공되는 정규화된 URL이어야 합니다. Store Fulfillment 고객은 샌드박스 및 프로덕션 URL을 모두 받습니다. 후행 슬래시 &quot;/&quot;를 포함하여 전체 URL을 복사/붙여넣으십시오. | 글로벌 | 예 |
| **[!UICONTROL Token Auth Server URL]** | Walmart Store Fulfillment Authentication 끝점의 URL입니다. 값은 온보딩 프로세스 중에 제공되는 정규화된 URL이어야 합니다. 샌드박스 및 프로덕션 URL을 모두 받습니다. 후행 슬래시를 포함하여 전체 URL을 복사/붙여넣으십시오 `/`&quot;. | 글로벌 | 예 |
| **[!UICONTROL Merchant Id]** | 온보딩 프로세스 중에 제공한 고유한 머천트(테넌트) ID입니다. ID는 주문 경로를 지정하는 데 사용되며, 머천트 지점에서 주문을 수신합니다. | 글로벌 | 예 |
| **[!UICONTROL Consumer Id]** | 고유한 통합 ID입니다. 이것은 온보딩 프로세스 중에 제공됩니다. 변하지 않아요 이행 서비스와의 모든 통신을 인증하는 데 사용됩니다. | 글로벌 | 예 |
| **[!UICONTROL Consumer Secret]** | 고유한 통합 키입니다. 이것은 온보딩 프로세스 중에 제공됩니다. 이행 서비스와의 모든 통신을 인증하는 데 사용됩니다. | 글로벌 | 예 |

계정 자격 증명을 구성한 후 **[!UICONTROL Validate Credentials]** 이행 웹 서비스에 대한 연결을 처음으로 확인하고 설정하려면

## 로깅 구성

로깅이 활성화되면 로그 파일을 빠르게 확장할 수 있습니다. 프로덕션 환경에서 응답 시간 문제를 방지하려면 로깅 활성화에 유의하고 필요한 경우 단시간 동안만 활성화하십시오.

방화벽 또는 캐시를 통해 API 관련 예외를 캡처할 수 있도록 예외 처리를 허용하도록 환경을 구성할 것을 시스템 관리자에게 요청합니다. 시스템 관리자에게 이 파일에 대한 로그 회전을 설정하여 크기를 최소화하도록 요청할 수도 있습니다.

| **필드** | **설명** | **범위** | **필수 여부** |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **디버그 모드** | 디버그 모드는 통합 내에서 로그된 활동을 늘리는 데 사용됩니다. 비활성화하면 디버그 정보가 기록되지 않습니다. 활성화되면 모든 디버그 정보가 기록됩니다.</br> 기록된 모든 데이터는 파일에서 찾을 수 있습니다. `var/log/walmart-bopis.log` | 글로벌 | 아니요 |

## 주문 동기화 관리

주문 동기화 오류 처리, 주문 출하 중에 바코드 스캔에 사용할 카탈로그 속성을 관리하도록 설정을 구성하고, 저장 이행 대기열에 대한 주문 배치 크기를 구성합니다.

관리(
**[!UICONTROL System > Tools > Store Fulfillment Queue]**).

### 동기화 오류 관리

| **필드** | **설명** | **범위** | **필수 여부** |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **재시도 위험 오류** | 중요한 오류가 발생한 후 레코드 동기화 작업의 다시 시도를 지정합니다.</br></br>통합이 이행 서비스에서 긍정적인 응답을 받지 못할 때마다 중요한 오류가 발생합니다. 이 문제는 서비스가 다운되었거나 전송 중인 주문 데이터에 오류가 있을 때 발생할 수 있습니다.</br></br>다시 시도 임계값에 도달하면 항목이 큐에 있지만 다시 처리되지 않습니다. 오류가 있는 모든 항목 보기 **[!UICONTROL System > Tools > Store Fulfillment Queue]** 관리 를 참조하십시오. 일관성 있는 실패 항목을 해결하려면 계정 관리자에게 문의하십시오. | 글로벌 | 아니요 |
| **오류 알림 이메일 활성화** | 오류 알림을 활성화하여 [!UICONTROL Retry Critical Error Threshold] 이(가) 주문에 도달합니다. 알림에는 오류에 대한 사용 가능한 세부 정보가 포함됩니다. | 글로벌 | 아니요 |
| **오류 알림 전자 메일 보내기** | 오류 알림에 대한 수신자 이메일 주소의 쉼표로 구분된 목록입니다. | 글로벌 | 아니요 |
| **주문 동기화 예외 전자 메일 템플릿** | 수신자에게 주문 동기화 오류에 대해 알리는 데 사용되는 전자 메일 템플릿을 지정합니다. 기본 템플릿이 제공됩니다. 사용자 지정을 지원하지 않습니다. | 저장소 보기 | 아니요 |

### 주문 동기화

| **필드** | **설명** | **범위** | **필수 여부** |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Barcode Source]** | 머천트 위치의 해당 항목에 대한 스캐닝 가능한 코드를 저장하는 카탈로그 속성입니다.</br></br>기존 머천트 위치가 한 개만 있는 경우 UPC 코드를 사용할 수 있지만 전자 상거래 채널은 SKU별로 제품을 식별합니다. 시나리오인 경우 UPC 코드가 포함된 카탈로그 속성을 선택합니다.</br></br>이 설정을 사용하면 머천트에 전송된 주문이 목록 항목을 올바른 식별자와 함께 저장하므로 스토어 연결이 피킹 프로세스 중에 항목을 정확하게 스캔할 수 있습니다.</br></br>잘 모르는 경우 배송 및 피킹 부서의 이행 담당자와 함께 문의하여 어떤 속성을 전송해야 하는지 결정합니다. 속성이 현재 데이터베이스에 포함되어 있지 않은 경우 Adobe Commerce 제품 속성 세트에 적절한 속성을 추가해야 할 수 있습니다. | 웹 사이트 | 예 |
| **[!UICONTROL Barcode Type]** | 머천트 위치의 해당 항목에 대한 바코드 소스를 저장하는 카탈로그 속성입니다.</br></br>이 설정을 사용하면 머천트에 전송된 주문이 올바른 식별자와 함께 목록 항목을 저장하므로 스토어 연결이 피킹 프로세스 중에 항목을 정확하게 스캔할 수 있습니다. 옵션에는 SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODEABAR, Price Embedded UPC가 있습니다.</br></br>확실하지 않은 경우, [!UICONTROL Barcode Source] 속성을 사용합니다. Store associates는 여전히 선택 목록에서 항목을 수동으로 일치시킬 수 있습니다. | 웹 사이트 | 예 |
| **[!UICONTROL Max Number of Items]** | 한 번에 저장소 이행 큐에서 보낼 최대 항목 수입니다.</br></br>BOPIS 주문은 정기적으로 이행 서비스로 일괄적으로 전송됩니다. 이 설정을 사용하면 일괄 처리의 크기를 제어할 수 있습니다.</br></br>기본값은 100개 항목입니다. 주문 볼륨과 용량에 따라 이 값을 높이거나 낮아야 할 수 있습니다. | 글로벌 | 아니요 |


## 저장 이행 운송 옵션 사용

Adobe Commerce 스토어에 대한 매장 내 픽업 및 홈 배달 옵션의 가용성을 결정하는 스토어 이행 운송 옵션을 구성합니다.

### 납품처 저장소

| **필드** | **설명** | **범위** | **필수 여부** |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship To Store]** | Ship-to-Store 설정은 기존의 Ship-to-Store 기능을 활용합니다. Inventory management을 사용하거나, 매장 간 재고 이전을 통해 재고가 없는 머천트 위치에서 주문을 수락하고 이행할 수 있는 경우, 이 옵션을 로 설정하십시오 `Yes`.</br></br>납품처 옵션을 지원할 수 없거나 제공하지 않으려면 로 설정합니다. `No`. 비활성화되면, 머천트 스토어에 대해 0 인벤토리가 있는 카탈로그의 항목 또는 해당 위치 아래의 항목 [!DNL Out of Stock Threshold]은 매장 내 픽업 옵션과 함께 제공되지 않습니다.</br></br>머천트 위치별로 조정할 수 있는 글로벌 설정입니다. | 글로벌 | 아니요 |

### Ship From Store

| **필드** | **설명** | **범위** | **필수 여부** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship From Store]** | 머천트 스토어에서 홈 배달 옵션을 활성화하거나 비활성화합니다. 활성화되면 머천트 스토어 위치는 웹 사이트와 연관된 주식의 다른 지정된 소스와 집계되는 것으로 간주됩니다.</br></br>표준 Inventory management 서비스에서는 [!DNL Ship from Store] 이 옵션은 고유하며 비활성화할 수 없습니다. Store Fulfillment 솔루션을 사용하면 이 솔루션을 켜거나 끌 수 있습니다.</br></br>전역 설정입니다. 머천트 위치 및 제품별로 이 설정을 조정할 수도 있습니다. | 글로벌 | 아니요 |


## 저장소 이행 앱 사용 계정 및 권한 관리

Store Fulfillment 앱 사용자 계정 및 암호 보안 및 2단계 인증에 대한 설정을 구성합니다.

### 앱 보안

| **필드** | **설명** | **범위** | **필수 여부** |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL User Session Lifetime]** | 자동 로그아웃 전에 저장소 연결 사용자 세션이 활성 상태로 유지되는 시간(초)입니다. 유효한 값의 범위는 60부터 31536000. | 글로벌 | 아니요 |
| **[!UICONTROL Maximum Login Failures to Lockout Account]** | 저장소 연결이 해당 계정에서 잠기기 전에 허용되는 로그인 실패 횟수를 지정합니다.</br></br>계정 잠금을 비활성화하려면 값을 0으로 설정합니다. | 글로벌 | 아니요 |
| **[!UICONTROL Lockout Time (minutes)]** | 로그인 실패 후 계정을 잠그는 시간(분)입니다. | 글로벌 | 아니요 |
| **[!UICONTROL Force Password Change]** | 사용자 암호를 변경해야 하는지 여부를 결정합니다.</br></br>`Yes`: 계정 설정 후 사용자가 암호를 변경해야 합니다.</br>`No`: 계정 설정 후 사용자가 암호를 변경할 것을 권장합니다. | 글로벌 | 아니요 |
| **암호 수명** | 필요한 암호를 변경하기 전에 암호가 유효한 기간(일)입니다. 이 옵션을 비활성화하려면 비워 둡니다. | 글로벌 | 아니요 |

### 이중 인증

| **필드** | **설명** | **범위** | **필수 여부** |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **앱 사용자 2FA** | 스토어 연결에 대해 2단계 인증을 활성화하거나 비활성화합니다. 활성화되면 저장소 연결에 인증 공급자가 생성한 일회성 암호를 제공하라는 메시지가 표시됩니다. | 글로벌 | 아니요 |
| **APP 2FA 정책** | 이중 인증에 대한 적용 정책을 설정합니다.</br></br>**[!UICONTROL Optional]**: 공급자가 설정되지 않은 경우 저장소 연결이 이중 인증을 무시할 수 있습니다.</br></br>**[!UICONTROL Mandatory]**: 2단계 인증을 완료하려면 저장소 연결이 필요합니다. | 글로벌 | 아니요 |
| **2FA 공급자** | 저장소 연결을 제공할 인증 공급자 서비스를 하나 이상 선택합니다. 2단계 인증을 설정하고 인증하려면 store associates가 모바일 장치에 설치된 사용 가능한 공급자 중 하나에서 인증 앱을 설치해야 합니다. | 글로벌 | 아니요 |

### 배달 방법

Store Fulfillment는 기본 Adobe Commerce을 확장하여 작동합니다 [!DNL In-Store Delivery] 기능.
확장을 설치한 후에 매장 내 게재 방법에 추가 관리 구성 옵션을 사용할 수 있습니다. 관리자에서 다음 추가 옵션을 선택하여 구성합니다 **[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

Store Fulfillment 설정에서 In-Store Pickup 주문에 대해 다음 배달 방법을 구성할 수 있습니다.

- **매장 내 픽업**- 체크아웃 프로세스 동안 매장 내 게재에 대한 오퍼 옵션 BOPIS 주문에 대한 가장 일반적인 배달 시나리오입니다.

- **커브사이드 픽업**&quot;고객이 매장 위치에 주차할 수 있는 옵션을 제공하며, 이 옵션은 매장 직원이 직접 주문해 배송하도록 합니다.

#### 배달 방법 구성

<!---
In-store pickup, says its global setting, but scope is Website.  How do you configure the in-store pickup options at the retail level?
--->

| **필드** | **설명** | **범위** | **필수 여부** |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable In-Store Pickup]** | 스토어 픽업을 선택한 고객에 대해 체크아웃 중에 사용할 수 있는 매장 내 픽업 옵션을 활성화하거나 비활성화합니다. 매장 내 픽업이 비활성화되면 옵션이 표시되지 않습니다.</br></br>이 전역 설정은 모든 소매 스토어 위치에 적용됩니다. 활성화되면 소매 스토어 위치에서 선택적으로 비활성화할 수 있습니다. | 웹 사이트 | 아니요 |
| **Curbside Pickup 활성화** | 스토어 픽업을 선택한 고객에 대해 체크아웃 프로세스 중에 현재 픽업 옵션을 활성화 또는 비활성화합니다.</br></br>이 전역 설정은 모든 소매 스토어 위치에 적용됩니다. 활성화되면 소매 스토어 위치에서 선택적으로 비활성화할 수 있습니다. | 웹 사이트 | 아니요 |

선택한 소매점 위치에서 게재 방법 사용자 지정에 대한 자세한 내용은 **소매 스토어 구성**.

#### 전달 방법 제목 구성

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
<td><strong>홈 게재 제목</strong></td>
<td>제품, 장바구니 및 체크아웃 영역에서 홈 배달 옵션에 표시할 제목을 지정합니다. 집 배달은 창고에서 고객이 제공한 배송 주소로 직접 연락하는 Adobe Commerce의 표준 배송 기능을 의미합니다.</br></br>이 레이블은 선택한 운송 회사 또는 사용 가능한 운송 방법 레이블에 영향을 주지 않습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>홈 배달 설명</strong></td>
<td>고객에게 홈 배달 제목이 표시될 때마다 표시되는 선택적 설명입니다. 대부분의 경우 설명은 게재 약속을 전달하기 위한 정적 메시지입니다. 예:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>저장소 픽업 제목</strong></td>
<td>고객에게 배달 옵션이 표시되고 매장 내 픽업 서비스를 사용할 수 있는 경우 이 레이블이 표시됩니다.</br></br>제품, 장바구니 및 체크아웃 영역에 표시되는 이 레이블을 사용자 지정할 수 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<td><strong>저장소 픽업 설명</strong></td>
<td>저장 픽업 제목이 표시되는 곳마다 설명을 선택적으로 포함할 수 있습니다. 이 정적 메시지는 스토어의 픽업 환경과 관련된 고객 커뮤니케이션을 개선하는 데 도움이 됩니다. 예:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>매장 내 픽업 제목</strong></td>
<td>매장 내 픽업 이 활성화되면 이 제목이 저장소 픽업 배달 옵션으로 고객에게 표시됩니다. 레이블을 사용자 지정할 수 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<tr>
<td><strong>커브사이드 픽업 제목</strong></td>
<td>Curbside Pickup이 활성화되면 옵션이 Store Pickup 배달 옵션의 유형으로 고객에게 표시됩니다. 여기에서 해당 레이블을 사용자 지정할 수 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>매장 내 픽업 지침</strong></td>
<td>소매점에서 주문을 받을 준비가 되면 고객에게 이메일로 통지합니다. 고객이 선택된 경우 [!DNL In-Store Pickup] 체크아웃 중에 여기서 픽업 지침을 사용자 지정할 수 있습니다.</br></br>모든 소매점 위치에 적용되는 전역 설정입니다. 소매 스토어 위치 수준에서 지침을 사용자 지정할 수도 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>커브사이드 픽업 지침</strong></td>
<td>현재 픽업 주문에 대한 고객 이메일 알림에 포함할 사용자 지정된 주문 픽업 지침을 지정합니다.</br></br>모든 소매점 위치에 적용되는 전역 설정입니다. 소매 스토어 위치 수준에서 지침을 사용자 지정할 수도 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>예상 픽업 리드 타임</strong></td>
<td>주문이 접수되고 이행되며 주문할 준비가 되기 전에 필요한 시간(분)입니다. 이 정보는 스토어의 픽업 배달 옵션을 위한 소매점 위치를 선택할 때 고객에게 표시됩니다.</br></br>글로벌 설정이며 모든 소매점 위치에 적용됩니다. 소매점 위치 수준에서 리드 타임을 사용자 지정할 수도 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>예상 픽업 시간 레이블</strong></td>
<td>고객 픽업 시 주문을 사용할 수 있을 때까지 예상되는 시간을 표시합니다. 이 정보는 스토어의 픽업 배달 옵션을 위한 소매점 위치를 선택할 때 고객에게 표시됩니다.</br></br>이 레이블을 사용자 지정할 때 코드를 사용할 수 있습니다 <code>%1</code> 를 삽입하려면 <strong>예상 픽업 리드 타임</strong>.예:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>모든 소매점 위치에 적용되는 전역 설정입니다. 소매점 위치 수준에서 리드 타임을 사용자 지정할 수도 있습니다.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>저장소 보기</td>
<td>아니요</td>
<tr>
<td><strong>픽업 시간 면책조항</strong></td>
<td>저장된 시간, 휴일, 예기치 않은 종료 등을 나열하는 도구 설명에서 제품 페이지에 표시되는 콘텐츠입니다</td>
<td>저장소 보기
</td>
<td>아니요
</td>
</tr>
</tbody></table>

#### Stock Availability 제목 구성

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
<td><strong>인스톡</strong></td>
<td>고객이 소매점 보관처를 사용하는 경우, 각 위치에 대해 현재 품목에 대한 재고 가용성이 표시됩니다.</br></br>여기에서 "재고 내" 상태 레이블을 사용자 지정할 수 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>재고 부족</strong></td>
<td>고객이 소매점 보관처를 사용하는 경우, 각 위치에 대해 현재 품목에 대한 재고 가용성이 표시됩니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
<tr>
<td><strong>일부 재고</strong></td>
<td>고객이 소매점 보관처를 사용하는 경우, 각 위치에 대해 표시된 모든 현재 품목에 대한 재고 가용성입니다.</br></br>여기에서 "부분 재고" 상태 레이블을 사용자 지정할 수 있습니다.</td>
<td>저장소 보기</td>
<td>아니요</td>
</tr>
</tbody></table>
