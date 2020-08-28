---
id: "working-with-storage"
url: "merger/working-with-storage"
title: "Working With Storage"
productName: "GroupDocs.Merger Cloud"
weight: 8
description: ""
keywords: ""
---

## Storage existence API ##

This API intended for checking the existence of cloud storage with a given name from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).
|---|---

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you try out [Storage existence API](https://apireference.groupdocs.cloud/conversion/#/Storage/StorageExists) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|Parameter|Description
|---|---
|**storageName**|Storage name

### cURL Example ###

Request

```html
curl -X GET "https://api.groupdocs.cloud/v1.0/merger/storage/MyStorage/exist" -H  "accept: application/json" -H  "authorization: Bearer  [Access Token]"

```

Response

```html
{
  "exists": true
}
```

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Storage existence](https://apireference.groupdocs.cloud/merger/#/Storage/StorageExists) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Storage_Exist.cs >}}

Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Storage_Exist.java >}}

PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Storage_Exist.php >}}

Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Storage_Exist.rb >}}

Node

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Storage_Exist.js >}}

Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Storage_Exist.py >}}

## Storage object existence API ##

This API intended for checking the existence of a file or folder in [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you try out [Storage existence API](https://apireference.groupdocs.cloud/merger/#/Storage/StorageExists) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|Parameter|Description
|---|---
|**path**|Path of the file or folder. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used
|versionId|File version id

### cURL Example ###

Request

```html
curl -X GET "https://api.groupdocs.cloud/v1.0/merger/storage/exist/conversiondocs?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

```html
{
  "exists": true,
  "isFolder": true
}
```

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Storage Object existence](https://apireference.groupdocs.cloud/merger/#/Storage/ObjectExists) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Object_Exists.cs >}}

Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Object_Exists.java >}}

PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Object_Exists.php >}}

Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Object_Exists.rb >}}

Node

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Object_Exists.js >}}

Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Object_Exists.py >}}

## Storage Space Usage API ##

This API intended for getting total and used space of the[ GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud)

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you to try out [storage space usage API](https://apireference.groupdocs.cloud/merger/#/Storage/GetDiscUsage) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|Parameter|Description
|---|---
|storageName|Name of the storage. If not set, then default storage used

### cURL Example ###

Request

```html
curl -X GET "https://api.groupdocs.cloud/v1.0/merger/storage/disc?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

```html
{
  "usedSize": 31032368,
  "totalSize": 3221225472
}
```

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [storage space usage API](https://apireference.groupdocs.cloud/merger/#/Storage/GetDiscUsage) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Get_Disc_Usage.cs >}}

Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Get_Disc_Usage.java >}}

PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Get_Disc_Usage.php >}}

Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Get_Disc_Usage.rb >}}

Node

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Get_Disc_Usage.js >}}

Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Get_Disc_Usage.py >}}

## Storage File Versions API ##

This API intended for getting the list of file versions, stored in the [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud)

### API Explorer ###

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you to try out [Storage File Versions API](https://apireference.groupdocs.cloud/merger/#/Storage/GetFileVersions) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

##### Request parameters #####

|Parameter|Description
|---|---
|**path**|Path of the file including file name and extension e.g. /Folder1/file.ext. Required. Can be passed as a query string parameter or as part of the URL
|storageName|Name of the storage. If not set, then default storage used

### cURL Example ###

Request

```html
curl -X GET "https://api.groupdocs.cloud/v1.0/merger/storage/version/one-page.docx?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
```

Response

```html
{
  "value": [
    {
      "versionId": "null",
      "isLatest": true,
      "name": "one-page.docx",
      "isFolder": false,
      "modifiedDate": "2018-08-16T19:45:05+00:00",
      "size": 347612,
      "path": "/one-page.docx"
    }
  ]
}
```

### SDKs ###

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [Storage File Versions API](https://apireference.groupdocs.cloud/merger/#/Storage/GetFileVersions) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.

### SDK Examples ###

C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Get_File_Versions.cs >}}

Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Get_Disc_Usage.java >}}

PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Get_Disc_Usage.php >}}

Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Get_Disc_Usage.rb >}}

Node

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Get_Disc_Usage.js >}}

Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Get_Disc_Usage.py >}}
