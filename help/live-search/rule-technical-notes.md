---
title: 규칙 기술 정보
description: 라이브 검색 규칙 사용에 대한 기술 참고 사항.
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# 규칙 기술 정보

[!DNL Live Search] 규칙은 다양한 쿼리 조건에 따라 작업을 트리거하며 판매자에게 다양한 시나리오에 대한 검색 경험을 형성할 수 있는 기능을 제공합니다.

의 현재 릴리스 [!DNL Live Search] 규칙은 반환된 결과 세트가 아니라 구매자가 입력하는 쿼리 문자열을 기반으로 합니다. 쿼리 문자열에는 영숫자 문자가 포함될 수 있으며 대문자는 무시됩니다. 패싯 및 동의어와 마찬가지로 규칙은 다음 위치에 저장됩니다. `protobuf dynamo`. 쿼리 시간에 검색 서비스는 다음을 통해 규칙을 검색합니다 `grpc` 호출 `search-admin-service`.
