---
id: "generate-document-pages-preview"
url: "merger/generate-document-pages-preview"
title: "Generate Document Pages Preview"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
---






# Introduction #

This REST API provides an ability to generate document pages of image representations.
There are several ways to specify page numbers needed for preview:

* Provide exact page numbers via Pages collection;
* Specify pages range start/end page numbers. There is also an ability to get only even/odd pages from the specified page range by setting RangeMode property. 

For protected documents, it is also required to provide a password.
The following properties of preview may be customized:



|#
|---
Name
|#
Description
|#
Comment

|

FilePath
|
The file path in the storage
|
Required property

|

StorageName
|
Storage name
|
Could be omitted for default storage

|

VersionId
|
File version Id
|
Useful for storages that support file versioning

|


Password
|

The password to open file
|

Should be specified only for password-protected documents

|

Pages
|

Collection of page numbers to use in a Join operation
|

The first page should have number 1

|

StartPageNumber
|

Start page number
|

Ignored if Pages collection is not empty

|

EndPageNumber
|

End page number
|

Ignored if Pages collection is not empty

|

RangeMode
|

Page range mode: Even, Odd, All. The default value is All
|

Ignored if Pages collection is not empty

|


Width
|

Image width in pixels
|

Optional

|


Height
|

Image height in pixels
|

Optional

|

Format
|

Image format - JPG, PNG, BMP
|

The default value is JPG

|


OutputPath
|

Path format to resultant images
|

Required



## Resource URI ##

```html 

HTTP POST ~/preview

 ```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Preview) lets you call this REST API directly from the browser.  
|---|---

## cURL Example ##


 Request

```html 
* First get JSON Web Token
* Please get your App Key and App SID from https://dashboard.groupdocs.cloud/#/apps. Kindly place App Key in "client_secret" and App SID in "client_id" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type#client_credentials&#x26;client_id#xxxx&#x26;client_secret#xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"
 
* cURL example to join pages from several documents into one document
curl -v "https://api.groupdocs.cloud/v1.0/merger/preview" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer 
<jwt token>"
-d "{
    'FileInfo': { 'FilePath': 'WordProcessing/four-pages.docx' },
  'OutputPath': '/Output/preview-page',
  'Pages': [1, 3],
  Format: 'Png'
 }"


 ```


 Response

```html 
 
* Response will contain storage path to resultant documents
{
  'documents': [
    {
      'path': '\Output\page_1.png'
    },
    {
      'path': '\preview\page_3.png'
    }
  ]
}
 ```




# SDKs #

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.
|---|---

## Generate Document Pages Preview ##



 C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_PreviewDocument.cs >}}




 Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_PreviewDocument.java >}}




 PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_PreviewDocument.php >}}




 Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_PreviewDocument.rb >}}




 Node.js

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_PreviewDocument.js >}}




 Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_PreviewDocument.py >}}




