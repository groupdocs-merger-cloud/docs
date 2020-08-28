---
id: "extract-pages"
url: "merger/extract-pages"
title: "Extract Pages"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
---

## Extract Pages by Exact Page Numbers ##

This REST API allows extracting pages from source documents by providing exact page numbers via Pages collection. The result is a new document that contains only specified pages from a source document. For protected documents, it is also required to provide a password.

The following example demonstrates how to extract pages 2,4,7 from a source document into a new document.

## Resource URI ##

```html

HTTP POST ~/Pages/Extract

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Extract) lets you call this REST API directly from the browser.

### cURL Example ###

{{< tabs tabTotal="2" tabID="1" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html

* First get JSON Web Token
* Please get your App Key and App SID from https://dashboard.groupdocs.cloud/#/apps. Kindly place App Key in "client_secret" and App SID in "client_id" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join several documents into one
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/extract" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
     'FileInfo': { 'FilePath': '/WordProcessing/sample-10-pages.docx'},
     'Pages':  [ 2, 4, 7 ],
     'OutputPath': 'output/extract-pages-by-numbers.docx'
 }"
```

{{< /tab >}} {{< tab tabNum="2" >}}

```html

*Response will contain storage path to resultant document
{
  "path": "output/extract-pages-by-numbers.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

### Extract Pages by Exact Page Numbers ###

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_ExtractPagesByNumbers.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_ExtractPagesByNumbers.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_ExtractPagesByNumbers.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_ExtractPagesByNumbers.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_ExtractPagesByNumbers.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_ExtractPagesByNumbers.py >}}

{{< /tab >}} {{< /tabs >}}

## Extract Pages by Exact Page Number Range ##

This REST API allows extracting pages from source documents by providing only start/end page numbers of the desired page range. There is also an ability to get only even/odd pages from the specified page range by setting RangeMode property.
The result is a new document that contains only specified pages from a source document. For protected documents, it is also required to provide a password.
The following example demonstrates how to extract even pages from a document in a range from 1st to 10th page.
The resultant document will contain pages 2, 4, 6, 8, 10 from the source document.

## Resource URI ##

```html

HTTP POST ~/Pages/Extract

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Extract) lets you call this REST API directly from the browser.

### cURL Example ###

{{< tabs tabTotal="2" tabID="2" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html

* First get JSON Web Token
* Please get your App Key and App SID from https://dashboard.groupdocs.cloud/#/apps. Kindly place App Key in "client_secret" and App SID in "client_id" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join several documents into one
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/extract" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
     'FileInfo': { 'FilePath': '/WordProcessing/sample-10-pages.docx'},
  'StartPageNumber': 1,
  'EndPageNumber': 10,
        'RangeMode': 'EvenPages',
     'OutputPath': 'output/extract-pages-by-range.docx'
 }"
```

{{< /tab >}} {{< tab tabNum="2" >}}

```html

*Response will contain storage path to resultant document
{
  "path": "output/extract-pages-by-range.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

### Extract Pages by Exact Page Number Range ###

{{< tabs tabTotal="6" tabID="11" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_ExtractPagesByRange.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_ExtractPagesByRange.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_ExtractPagesByRange.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_ExtractPagesByRange.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_ExtractPagesByRange.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_ExtractPagesByRange.py >}}

{{< /tab >}} {{< /tabs >}}
