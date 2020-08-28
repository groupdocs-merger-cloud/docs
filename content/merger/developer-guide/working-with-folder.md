---
id: "working-with-folder"
url: "merger/working-with-folder"
title: "Working With Folder"
productName: "GroupDocs.Merger Cloud"
weight: 7
description: ""
keywords: ""
---

# Get the File Listing of a Specific Folder #

This API allows you to get a list of all files of a specific folder from the specified Cloud Storage. If you do not pass storage name API will find the folder in GroupDocs Cloud Storage.

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/) lets you try out [List Files in a Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/GetFilesList) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|Parameter|Description
|---|---
|**path**|Path of the file including file name and extension e.g. /Folder1/file.ext. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL Example ###

{{< tabs tabTotal="2" tabID="1" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
curl -X GET "https://api.groupdocs.cloud/v1.0/merger/storage/folder/conversiondocs?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
{
  "value": [
    {
      "name": "four-pages.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:35:38+00:00",
      "size": 8651,
      "path": "/conversiondocs/four-pages.docx"
    },
    {
      "name": "one-page.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:17:34+00:00",
      "size": 351348,
      "path": "/conversiondocs/one-page.docx"
    },
    {
      "name": "password-protected.docx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:35:40+00:00",
      "size": 10240,
      "path": "/conversiondocs/password-protected.docx"
    },
    {
      "name": "sample.mpp",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:29:10+00:00",
      "size": 289792,
      "path": "/conversiondocs/sample.mpp"
    },
    {
      "name": "three-layouts.dwf",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:26:42+00:00",
      "size": 15433,
      "path": "/conversiondocs/three-layouts.dwf"
    },
    {
      "name": "two-hidden-pages.vsd",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:17:36+00:00",
      "size": 457728,
      "path": "/conversiondocs/two-hidden-pages.vsd"
    },
    {
      "name": "uses-custom-font.pptx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:32:30+00:00",
      "size": 39823,
      "path": "/conversiondocs/uses-custom-font.pptx"
    },
    {
      "name": "with-hidden-rows-and-columns.xlsx",
      "isFolder": false,
      "modifiedDate": "2019-03-20T12:17:37+00:00",
      "size": 15986,
      "path": "/conversiondocs/with-hidden-rows-and-columns.xlsx"
    }
  ]
}

```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Folder API](https://apireference.groupdocs.cloud/merger/#/Folder) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Get_Files_List.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Get_Files_List.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Get_Files_List.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Get_Files_List.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Get_Files_List.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Get_Files_List.py >}}

{{< /tab >}} {{< /tabs >}}

## Create a New Folder ##

This API allows you to create a new folder in the specified Cloud Storage. If you do not pass storage name API will create New Folder in default Cloud Storage.

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/) lets you try out [Create Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/CreateFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|Parameter|Description
|**path**|Target folder’s path e.g. Folder1/Folder2/. The folders will be created recursively. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL Example ###

{{< tabs tabTotal="2" tabID="2" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
curl -X POST "https://api.groupdocs.cloud/v1.0/merger/storage/folder/conversiondocs3?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="6" tabID="11" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Create_Folder.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Create_Folder.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Create_Folder.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Create_Folder.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Create_Folder.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Create_Folder.py >}}

{{< /tab >}} {{< /tabs >}}

## Delete a Particular Folder ##

This API allows you to delete a particular folder in the specified Cloud Storage. If you do not pass storage name API will create New Folder in default Cloud Storage. To remove recursively inner folder/files you need to pass true value to a recursive parameter inRequest. If it is set to false and folder contains data then API throws the exception.

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you try out [Delete a Particular Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/DeleteFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|Parameter|Description
|---|---
|**path**|Folder path e.g. /Folder1. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL Example ###

{{< tabs tabTotal="2" tabID="3" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
curl -X DELETE "https://api.groupdocs.cloud/v1.0/merger/storage/folder/conversiondocs3?storageName#MyStorage&recursive#true" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Delete Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/DeleteFolder) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="6" tabID="12" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Delete_Folder.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Delete_Folder.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Delete_Folder.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Delete_Folder.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Delete_Folder.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Delete_Folder.py >}}

{{< /tab >}} {{< /tabs >}}

## Copy  Specific Folder ##

This API allows you to copy a folder to another location in the GroupDocs Cloud Storage. If you do not pass source and destination storage names API will copy Folder within default Cloud Storage.

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you to try out [Copy Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/CopyFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.

### Request parameters ###

|Parameter|Description
|---|---
|**srcPath**|Source folder path e.g. /Folder1. Required. Can be passed as a query string parameter or as part of the URL
|**destPath**|Destination folder path. Required
|srcStorageName|Name of the storage of source folder. If not set, then default storage used
|destStorageName|Name of the storage of destination folder. If not set, then default storage used

### cURL Example ###

{{< tabs tabTotal="2" tabID="4" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
curl -X PUT "https://api.groupdocs.cloud/v1.0/merger/storage/folder/copy/conversiondocs?destPath#conversiondocs1&srcStorageName#MyStorage&destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Copy Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/CopyFolder) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="6" tabID="13" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Copy_Folder.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Copy_Folder.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Copy_Folder.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Copy_Folder.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Copy_Folder.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Copy_Folder.py >}}

{{< /tab >}} {{< /tabs >}}

## Move a Specific Folder ##

This API allows you to move a folder to another location in the GroupDocs Cloud Storage. If you do not pass source and destination storage names API will move Folder within default Cloud Storage.

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you try out [Move a Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/MoveFolder) right away in your browser. It allows you to effortlessly interact and try out every single operation that our APIs expose.
|---|---|---|---

### Request parameters ###

|Parameter|Description
|---|---
|**srcPath**|Source folder path e.g. /Folder1. Required. Can be passed as a query string parameter or as part of the URL
|**destPath**|Destination folder path. Required
|srcStorageName|Name of the storage of source folder. If not set, then default storage used
|destStorageName|Name of the storage of destination folder. If not set, then default storage used

### cURL Example ###

{{< tabs tabTotal="2" tabID="5" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
curl -X PUT "https://api.groupdocs.cloud/v1.0/merger/storage/folder/move/conversiondocs?destPath#conversiondocs1&srcStorageName#MyStorage&destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
{
  "code": 200,
  "status": "OK"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Move Folder API](https://apireference.groupdocs.cloud/merger/#/Folder/MoveFolder) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

{{< tabs tabTotal="6" tabID="14" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Move_Folder.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Move_Folder.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Move_Folder.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Move_Folder.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Move_Folder.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Move_Folder.py >}}

{{< /tab >}} {{< /tabs >}}
