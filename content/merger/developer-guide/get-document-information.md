---
id: "get-document-information"
url: "merger/get-document-information"
title: "Get Document Information"
productName: "GroupDocs.Merger Cloud"
weight: 2
description: ""
keywords: ""
---

## Introduction ##

This REST API allows us to obtain basic information about the document and it's pages properties. The endpoint accepts the document storage path as input payload.
Here is the list of properties that can be obtained for a document:

* Document file extension;
* Document size in bytes;
* Document file format.

Here is the list of properties that can be obtained for document pages:

* Page width in pixels (when converted to the image);
* Page height in pixels (when converted to image);
* Page number;
* Visible property that indicates whether the page is visible or not.

## Resource URI ##

```html

HTTP POST ~/info

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Info/GetInfo) lets you call this REST API directly from the browser.

### cURL Example ###

{{< tabs tabTotal="2" tabID="1" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html
* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/info" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{ FilePath: '/wordprocessing/four-pages.docx' }"

```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
 {
  "extension": ".docx",
  "pages": [
   {
    "width": 612,
   "height": 792,
   "pageNumber": 1,
   "visible": true
   },
   {
   "width": 612,
   "height": 792,
    "pageNumber": 2,
    "visible": true
   },
   {
    "width": 612,
   "height": 792,
   "pageNumber": 3,
   "visible": true
   },
   {
   "width": 612,
    "height": 792,
   "pageNumber": 4,
   "visible": true
   }],
 "size": 8651,
 "fileFormat": "Microsoft Word Open XML Document"
}
```

{{< /tab >}} {{< /tabs >}}

## SDKs ##

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the [Get Document Information](https://apireference.groupdocs.cloud/merger/#/Info/GetInfo) article to learn how to add an SDK to your project.

## Get Document Information ##

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_GetDocumentInformation.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_GetDocumentInformation.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_GetDocumentInformation.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_GetDocumentInformation.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_GetDocumentInformation.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_GetDocumentInformation.py >}}

{{< /tab >}} {{< /tabs >}}
