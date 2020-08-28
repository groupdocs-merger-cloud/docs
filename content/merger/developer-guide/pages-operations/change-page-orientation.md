---
id: "change-page-orientation"
url: "merger/change-page-orientation"
title: "Change Page Orientation"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
---

## Introduction ##

This REST API allows setting **Portrait** or **Landscape** page orientation for specific or all document pages. The result is a new document that has orientation changed for specified pages.
There are several ways to specify desired page numbers:

* Provide exact page numbers via Pages collection;
* Specify pages range start/end page numbers. There is also an ability to get only even/odd pages from the specified page range by setting RangeMode property.

For protected documents, it is also required to provide a password.
The table below contains the full list of properties that can be specified when changing orientation for document pages.

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|Could be omitted for default storage
|version|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|Pages|Collection of page numbers to use in a Join operation|The first page should have number 1
|StartPageNumber|Start page number|Ignored if Pages collection is not empty
|EndPageNumber|End page number|Ignored if Pages collection is not empty
|RangeMode|Page range mode: Even, Odd, All. The default value is All|Ignored if Pages collection is not empty
|Mode|Orientation mode - Portrait or Landscape.|Required property
|OutputPath|Path to resultant document|Required

## Resource URI ##

```html

HTTP POST ~/pages/orientation

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Orientation) lets you call this REST API directly from the browser.

### cURL Example ###

Request

```html

* First get JSON Web Token
* Please get your App Key and App SID from https://dashboard.groupdocs.cloud/#/apps. Kindly place App Key in "client_secret" and App SID in "client_id" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join several documents into one
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/orientation" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
     'FileInfo': { 'FilePath': '/WordProcessing/four-pages.docx'},
     'Pages':  [ 2, 4 ],
  'Mode': 'Landscape',
     'OutputPath': 'output/change-page-orientation.docx'
 }"

```

Response

```html
*Response will contain storage path to resultant document
{
  "path": "output/change-page-orientation.docx"
}
```

### SDKs ###

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

### Change Page Orientation ###

C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_ChangePageOrientation.cs >}}

Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_ChangePageOrientation.java >}}

PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_ChangePageOrientation.php >}}

Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_ChangePageOrientation.rb >}}

Node

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_ChangePageOrientation.js >}}

Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_ChangePageOrientation.py >}}
