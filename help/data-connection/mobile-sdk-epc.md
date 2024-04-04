---
title: Adobe Experience Platform Mobile SDK와 Commerce 통합
description: Headless 또는 사용자 지정 Commerce 상점 앞에서 Adobe Experience Platform Mobile SDK를 사용하는 방법에 대해 알아봅니다.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 593e92ebf890bd7d9bfef1cd13be727ca6be172b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK와 Commerce 통합

>[!IMPORTANT]
>
>iOS용 Adobe Experience Platform Mobile SDK는 iOS 11 이상을 지원합니다.

통합 [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) 상인이 Commerce를 전송할 수 있도록 Commerce 모바일 앱 사용  [이벤트 데이터](events.md) Experience Platform 가장자리로

Edge에서 Commerce 이벤트 데이터를 사용할 수 있으면 다른 Adobe Experience Cloud 애플리케이션에서 액세스할 수 있습니다. 예를 들어 데이터를 사용하여 Real-Time CDP에서 대상을 작성한 다음 [해당 대상 사용](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) - Commerce 모바일 앱을 개인화합니다.

## 구성

Commerce에서 Adobe Experience Platform Mobile SDK 사용을 시작하려면 Experience Platform에서 SDK를 설치하고 구성합니다. 그런 다음 Commerce에서 구성을 완료합니다.

### Experience Platform

1. 다음을 검토하여 모바일 앱 기능에 대해 알아봅니다. [모바일 앱의 Adobe Experience Cloud 자습서](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [설치 및 구성](https://developer.adobe.com/client-sdks/documentation/getting-started/) Experience Platform의 SDK입니다.

   >[!NOTE]
   >
   >Experience Platform에서 만들고 구성하는 스키마는 Commerce 모바일 앱의 애플리케이션 코드에서 사용하는 것과 동일한 스키마입니다.

### 상거래

Experience Platform에 대한 SDK 구성을 완료한 후 SDK 구성을 Commerce에 추가합니다.

1. SDK를 통해 Experience Platform에게 상거래 이벤트 데이터를 전송하려면 애플리케이션 코드에 XDM 스키마를 제공해야 합니다. 이 스키마는 스키마와 일치해야 합니다. [구성됨](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) Experience Platform의 SDK용입니다.

   다음 예제에서는 를 추적하는 방법을 보여 줍니다. `web.webpagedetails.pageViews` 이벤트 및 설정 `identityMap` 이메일 필드 사용.

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Commerce Cloud 환경에 연결합니다.

   프로젝트의 빌드 설정에서 Commerce GraphQL 엔드포인트에 URL을 추가합니다. 예:

   - 디버그: http://_디버그_.commercesite.cloud/graphql/
   - 릴리스: http://_릴리스_.commercesite.cloud/graphql/

1. Commerce GraphQL 끝점에서 데이터를 검색하려면 먼저 [아폴로 코드 생성기](https://www.apollographql.com/docs/ios/).

   1. 프로젝트 디렉토리에서 [설치](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) 아폴로 iOS

   1. [초기화](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) 아폴로 코드 젠 CLI.

      이렇게 하면 `apollo-codegen-configuration.json` 파일.

   1. 의 컨텐츠를 대체하여 프로젝트에서 필요한 GraphQL 파일 및 디렉토리를 생성합니다. `apollo-codegen-configuration.json` 파일이 포함된 파일:

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [가져오기](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) 상거래 GraphQL 스키마.

      경로가 (으)로 설정되어 있는지 확인합니다. `./apollo-codegen-config.json` Commerce GraphQL 스키마에 대한 참조가 포함된 파일입니다.

   1. [생성](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) 소스 코드.

      경로가 (으)로 설정되어 있는지 확인합니다. `./apollo-codegen-config.json` 필요한 파일 및 디렉터리를 생성하는 구성 정보가 포함된 파일입니다.

   1. 새로 생성된 항목 내부 **GraphQLGgenerated** GraphQL 유형을 폴더, 추가 또는 편집합니다. 예를 들어 다음을 추가할 수 있습니다 `DynamicBlocks.graphql` 다음 내용으로 을 입력합니다.

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   이제 Adobe Experience Platform Mobile SDK를 Commerce 모바일 앱과 통합했습니다. 이벤트 데이터는 앱에서 Experience Platform 에지로 흐릅니다.

## 모바일 애플리케이션에서 생성된 상거래 이벤트를 구분하는 방법

모두 [events](events.md) 라는 필드를 포함합니다. `channel`. 다음 `channel` 필드는 다음을 포함 `channel._id` 및 `channel._type` Luma 상점 첫 화면의 네임스페이스 값은 `"https://ns.adobe.com/xdm/channels/web"` 및 `"https://ns.adobe.com/xdm/channel-types/web"` 각각. 그러나 모바일 상점의 경우 네임스페이스 값은 다음과 같습니다. `"https://ns.adobe.com/xdm/channels/mobile-app"` 및 `"https://ns.adobe.com/xdm/channel-types/mobile"` 각각.

## 다음 단계

모바일 Commerce 앱에서 Real-Time CDP 대상자를 검색하여 장바구니 가격 규칙, 동적 블록 및 관련 제품 규칙을 알리는 방법에 대해 알아보려면 를 참조하십시오. [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html#retrieve-audiences-using-the-adobe-experience-platform-mobile-sdk).
