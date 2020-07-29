---
id: "working-with-files"
url: "merger/working-with-files"
title: "Working With Files"
productName: "GroupDocs.Merger Cloud"
weight: 6
description: ""
keywords: ""
---






# Download File API #

This API allows you to download a file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud).
|---|---

## API Explorer ##

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/) lets you try out [Download a File API](https://apireference.groupdocs.cloud/merger/#/File/DownloadFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.
|---|---|---|---

### Request parameters ###

|#
|---
Parameter
|#
Description

|
**Path**
|
Path of the file including file name and extension e.g. /Folder1/file.ext

 Required. Can be passed as a query string parameter or as part of the URL

|
storageName
|
Name of the storage. If not set, then default storage used

|
versionId
|
File version id


## cURL Example ##



 Request

```html 

curl -X GET "https://api.groupdocs.cloud/v1.0/merger/storage/file/one-page.docx?storageName#MyStorage" -H  "accept: multipart/form-data" -H  "authorization: Bearer [Access Token]"
    
 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [File API](https://apireference.groupdocs.cloud/merger/#/) calls and lets you use GroupDocs Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###



 C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Download_File.cs >}}




 Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Download_File.java >}}




 PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Download_File.php >}}




 Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Download_File.rb >}}




 Node.js

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Download_File.js >}}




 Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Download_File.py >}}





# Upload File API #

This API allows you to upload files to the [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---

## API Explorer ##

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you try out [Upload a File API](https://apireference.groupdocs.cloud/merger/#/File/UploadFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.
|---|---|---|---


### Request Body parameters ###

|#
|---
Parameter
|#
Description

|
**path**
|
Path of the file including file name and extension e.g. /Folder1/file.ext

 Required. Can be passed as a query string parameter or as part of the URL

|
storageName
|
Name of the storage. If not set, then default storage used

|
File
|
File content


## cURL Example ##



 Request

```html 

curl -X POST "https://api.groupdocs.cloud/v1.0/merger/storage/file/conversiondocs%2Fone-page2.docx?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

 ```


 Response
```html 
Http status code: 200 (Returns OK and list of errors, which is empty if success.)
{
  "Uploaded": [
    "string"
  ],
  "Errors": [
    {
      "Code": "string",
      "Message": "string",
      "Description": "string",
      "InnerError": {
        "RequestId": "string",
        "Date": "2019-02-27T06:10:08.884Z"
      }
    }
  ]
}


 ```



## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [File API](https://apireference.groupdocs.cloud/merger/#/File) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###


 C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Upload_File.cs >}}




 Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Upload_File.java >}}




 PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Upload_File.php >}}




 Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Upload_File.rb >}}




 Node.js

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Upload_File.js >}}




 Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Upload_File.py >}}






# Delete File API #

This API allows you to delete a specific file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---

## API Explorer ##
[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you to try out [Delete a File](https://apireference.groupdocs.cloud/merger/#/File/DeleteFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose.

### Request parameters ###

|#
|---
Parameter
|#
Description

|
**path**
|
Path of the file including file name and extension e.g. /Folder1/file.ext

 Required. Can be passed as a query string parameter or as part of the URL

|
storageName
|
Name of the storage. If not set, then default storage used

|
versionId
|
File version id


## cURL Example ##



 Request

```html 
curl -X DELETE "https://api.groupdocs.cloud/v1.0/merger/storage/file/conversiondocs1%2Fone-page1.docx?storageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"

 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [File API](https://apireference.groupdocs.cloud/merger/#/File) calls and lets you use GroupDocs Cloud features natively for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###



 C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Delete_File.cs >}}




 Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Delete_File.java >}}




 PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Delete_File.php >}}




 Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Delete_File.rb >}}




 Node.js

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Delete_File.js >}}




 Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Delete_File.py >}}






# File Copy API #

This API allows you to copy a specific file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---
## API Explorer ##
[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you try out [Copy File](https://apireference.groupdocs.cloud/merger/#/File/CopyFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose. 

###  Request parameters ###

|#
|---
Parameter
|#
Description

|
**srcPath**
|
Path of the source file including file name and extension e.g. /Folder1/file.ext

Required. Can be passed as a query string parameter or as part of the URL

|

**destPath**
|

Path of the destination file. Required.

|
srcStorageName
|
Name of the storage of source file. If not set, then default storage used

|

destStorageName
|

Name of the storage of destination file. If not set, then default storage used

|
versionId
|
Source file version id


## cURL Example ##



 Request

```html 
curl -X PUT "https://api.groupdocs.cloud/v1.0/merger/storage/file/copy/conversiondocs%2Fone-page1.docx?destPath#conversiondocs1%2Fone-page1.docx'&#x26;srcStorageName#MyStorage&#x26;destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
    
 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [File API](https://apireference.groupdocs.cloud/merger/#/File) calls and lets you use GroupDocs Cloud features natively for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###



 C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Copy_File.cs >}}




 Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Copy_File.java >}}




 PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Copy_File.php >}}




 Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Copy_File.rb >}}




 Node.js

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Copy_File.js >}}




 Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Copy_File.py >}}







# File Move API #

This API allows you to copy a specific file from [GroupDocs Cloud Storage](https://dashboard.groupdocs.cloud/).
|---|---

## API Explorer ##

[GroupDocs.Merger Cloud API Reference](https://apireference.groupdocs.cloud/merger/#/) lets you try out [Move File](https://apireference.groupdocs.cloud/merger/#/File/MoveFile) right away in your browser! It allows you to effortlessly interact and try out every single operation our APIs expose. 
|---|---|---|---

###  Request parameters ###

|#
|---
Parameter
|#
Description

|
**srcPath**
|
Path of the source file including file name and extension e.g. /Folder1/file.ext

Required. Can be passed as a query string parameter or as part of the URL

|

**destPath**
|

Path of the destination file. Required.

|
srcStorageName
|
Name of the storage of source file. If not set, then default storage used

|

destStorageName
|

Name of the storage of destination file. If not set, then default storage used

|
versionId
|
Source file version id


## cURL Example ##



 Request

```html 
curl -X PUT "https://api.groupdocs.cloud/v1.0/merger/storage/file/move/conversiondocs%2Fone-page1.docx?destPath#conversiondocs1%2Fone-page1.docx'&#x26;srcStorageName#MyStorage&#x26;destStorageName#MyStorage" -H  "accept: application/json" -H  "authorization: Bearer [Access Token]"
    
 ```


 Response

```html 
{
  "Code": 200,
  "Status": "OK"
}
 ```




## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages to make it easier to integrate with us. If you use [SDK](https://github.com/groupdocs-merger-cloud), it hides the [File API](https://apireference.groupdocs.cloud/merger/#/File) calls and lets you use GroupDocs for Cloud features in a native way for your preferred language.
|---|---|---|---|---|---

### SDK Examples ###



 C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_Move_File.cs >}}




 Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_Move_File.java >}}




 PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_Move_File.php >}}




 Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_Move_File.rb >}}




 Node.js

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_Move_File.js >}}




 Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_Move_File.py >}}




