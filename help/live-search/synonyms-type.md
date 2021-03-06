---
title: '"동의어 유형"'
description: '"일방, 양방향" [!DNL Live Search] 동의어는 키워드 정의를 확장합니다."'
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: cd1b40ffb350a87ea1317be82789f702922881b9
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---

# 동의어 유형

단방향 및 양방향 동의어는 키워드의 정의를 확장합니다. 일부는 키워드와 상호 바꿔서 사용할 수 있고, 다른 항목은 키워드의 하위 집합을 나타냅니다.

## 양방향

양방향 동의어는 같은 의미를 가지고 동일한 검색 결과를 반환합니다. 다음 예에서 굵게 표시된 첫 번째 단어는 카탈로그에서 사용되는 키워드이고 그 뒤에는 원래 키워드와 같은 의미를 갖는 단어가 옵니다. 단순 양방향 동의어 쌍 또는 동일한 키워드에 대해 여러 양방향 동의어의 체인을 생성할 수 있습니다.

**재킷** ![양방향 선택기](assets/btn-two-way.png) 코트
**바지** ![양방향 선택기](assets/btn-two-way.png) 슬랙스 ![양방향 선택기](assets/btn-two-way.png) 바지

## 단방향

단방향 동의어는 키워드의 하위 집합이지만 더 구체적인 의미가 있습니다. 예를 들어, 카피스와 반바지는 팬티지만 모든 바지가 카피나 반바지는 아닙니다. 바지 검색에는 카피스와 반바지가 포함됩니다. 그러나 반바지를 검색해도 캡이 반환되지 않습니다.

**스웨터** ![단방향 선택기](assets/btn-one-way.png) 후드
**바지** ![단방향 선택기](assets/btn-one-way.png) capris ![여러 단방향 선택기](assets/btn-multiple-one-way.png) 종아리 길이 바지 ![여러 단방향 선택기](assets/btn-multiple-one-way.png) 고추

## 우수 사례

라이브 검색 동의어를 최대한 활용하려면 다음 모범 사례를 기억하십시오.

### &quot;stop words&quot; 방지

라이브 검색은 다음과 같은 동의어에서 일반적인 영어 &quot;stop words&quot;를 필터링합니다.

a, an 및, is, as, as, be, but, for, if, in, in, into, is, it, no, not, on, or, that, the, the, their, then, 이것들, 이것들, is, to, is, with,

Stop words는 동의어를 더 의미 있게 만들지 않지만 처리해야 하는 데이터의 양을 증가시킵니다.

### 단일 단어 사용

동의어 용어에 여러 단어가 포함된 경우 단어 사이의 빈 공백이 해당 단어를 별도의 동의어로 처리합니다. 예를 들어 &quot;time pies&quot;를 &quot;watch&quot;의 동의어로 정의하는 경우 &quot;time&quot; 및 &quot;piece&quot;라는 단어는 별도의 동의어로 처리됩니다.

### 단일 및 복수 사용

단수형, 복수형 모두 동의어로 정의할 필요는 없다. 카탈로그에 단일 및 여러 용어가 혼합되어 있는 경우 Search는 올바른 제품 세트를 찾습니다. 예를 들어 제품 이름에 &quot;pant&quot;라는 단어를 사용하고 쇼핑객이 &quot;pants&quot;를 검색하는 경우 올바른 제품 세트가 반환되고 단일 단어 &quot;pant&quot;가 제안으로 제공됩니다. &quot;팬트&quot; 라는 단수는 패션 업계에서 종종 사용되고, 때로는 소매에서도 사용되지만, 몇몇 지역에서는 &quot;팬츠&quot; 형태가 더 흔하다. &#39;반트&#39;라는 단어는 한쪽 다리를 덮는 옷의 부분을 의미하는데, 이것이 두 다리를 덮을 때 &quot;바지 한 벌&quot;이 필요한 이유이다.

### 일관성

카탈로그에서 용어가 사용되는 방식과 일치하십시오. 사용량에 지역적 차이점과 산업 내 차이점이 있을 수 있음을 명심하십시오.

### 키워드 매핑

이 기법은 동의어 대신 검색 가능한 제품 속성을 사용하여 제품 간에 키워드 기반 연결을 만듭니다. 따라서 다른 제품의 검색 결과에 매핑된 제품이 나타날 수 있습니다. 자세한 내용은 [검색 결과](https://docs.magento.com/user-guide/catalog/search-results.html).
