---
id: "split-document"
url: "merger/split-document"
title: "Split Document"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

## Split the Document Into Several One-Page Documents

GroupDocs.Merger Cloud REST API provides an ability to split the document into several one-page documents by providing exact page numbers.
The following example demonstrates how to split the document into three one-page documents with 3rd, 6th, and 8th pages. As a result, these documents will be produced:

|Document name|Page numbers
|---|---
|document_0|3
|document_1|6
|document_2|8

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example1">}} {{< tab "Request" >}}

```bash

* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join several documents into one
curl -v "https://api.groupdocs.cloud/v1.0/merger/join" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
    'JoinItems':
    [
        {
            'FileInfo':
            {
                'FilePath': '/WordProcessing/four-pages.docx',
                'Password': 'password'
            }
        },
        {
            'FileInfo':
            {
                'FilePath': '/WordProcessing/one-page.docx'
            }
        }
    ],
    'OutputPath': 'output/joined.docx'
}"
```

{{< /tab >}} {{< tab "Response" >}}

```json

* Response will contain storage path to resultant document
{
  "path": "Output/joined.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.


{{< tabs "example2">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_SplitToSinglePages.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_SplitToSinglePages.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_SplitToSinglePages.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_SplitToSinglePages.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_SplitToSinglePages.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_SplitToSinglePages.py >}}

{{< /tab >}} {{< /tabs >}}

## Split the Document Into Several One-Page Documents by Providing Exact Page Numbers

GroupDocs.Merger Cloud REST API provides an ability to split the document into several one-page documents by specifying only start/end page numbers.
The following example demonstrates how to split the document into several one-page documents starting from 3rd and ending at 7th-page number. As a result, these documents will be produced:

|Document name|Page numbers
|---|---
|document_0|3
|document_1|4
|document_2|5
|document_3|6
|document_4|7

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example3">}} {{< tab "Request" >}}

```bash

*Response will contain storage path to resultant documents
{
  "documents": [
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_0.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_1.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_2.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_3.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_4.docx"
    }
  ]
}

```

{{< /tab >}} {{< tab "Response" >}}

```json
*Response will contain storage path to resultant document
{
  "path": "Output/joined.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check article to learn how to add an SDK to your project.

{{< tabs "example4">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_SplitToSinglePagesByRange.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_SplitToSinglePagesByRange.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_SplitToSinglePagesByRange.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_SplitToSinglePagesByRange.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_SplitToSinglePagesByRange.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_SplitToSinglePagesByRange.py >}}

{{< /tab >}} {{< /tabs >}}

## Split the Document Into Several One-Page Documents by Applying Filter

GroupDocs.Merger Cloud REST API provides an ability to filter even/odd pages while splitting the document into several one-page documents by specifying only start/end page numbers
The following example demonstrates how to document several one-page documents for odd pages starting from 3rd and ending at 7th-page number. As a result, these documents will be produced:

|Document name
|---
|Page numbers
|document_0|3
|document_1|5
|document_2|7

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example5">}} {{< tab "Request" >}}

```bash

* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join pages from several documents into one document
curl -v "https://api.groupdocs.cloud/v1.0/merger/split" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
   'FileInfo': { 'FilePath': 'WordProcessing/sample-10-pages.docx' },
   'StartPageNumber':  3,
   'EndPageNumber' : 7,
   'RangeMode' : 1,
      'Mode': 'Pages',
      'OutputPath': 'output/split-by-start-end-numbers-with-filter'
 }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant documents
{
  "documents": [
    {
      "path": "output/split-by-start-end-numbers-with-filter\sample-10-pages_0.docx"
    },
    {
      "path": "output/split-by-start-end-numbers-with-filter\sample-10-pages_1.docx"
    },
    {
      "path": "output/split-by-start-end-numbers-with-filter\sample-10-pages_2.docx"
    }
  ]
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

{{< tabs "example6">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_SplitToSinglePagesByRangeWithFilter.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_SplitToSinglePagesByRangeWithFilter.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_SplitToSinglePagesByRangeWithFilter.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_SplitToSinglePagesByRangeWithFilter.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_SplitToSinglePagesByRangeWithFilter.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_SplitToSinglePagesByRangeWithFilter.py >}}

{{< /tab >}} {{< /tabs >}}

## Split the Document to Several Multi-Page Documents

GroupDocs.Merger Cloud REST API provides an ability to split the document into several one-page documents by providing exact page numbers.
The following example demonstrates how to split the document into three one-page documents with 3rd, 6th, and 8th pages. As a result, these documents will be produced:

|Document name|Page numbers
|---|---
|document_0|1, 2
|document_1|3, 4, 5
|document_2|6, 7
|document_3|8, 9, 10

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example7">}} {{< tab "Request" >}}

```bash

* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join pages from several documents into one document
curl -v "https://api.groupdocs.cloud/v1.0/merger/split" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
   'FileInfo': { 'FilePath': 'WordProcessing/sample-10-pages.docx' },
    'Pages': [ 3, 6, 8 ],
    'Mode': 1,
    'OutputPath': '/output/split-to-multipage-document'
 }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant documents

{
  "documents": [
    {
      "path": "output/split-to-multipage-document\sample-10-pages_0.docx"
    },
    {
      "path": "output/split-to-multipage-document\sample-10-pages_1.docx"
    },
    {
      "path": "output/split-to-multipage-document\sample-10-pages_2.docx"
    },
 {
      "path": "output/split-to-multipage-document\sample-10-pages_3.docx"
    }
  ]
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check  article to learn how to add an SDK to your project.

{{< tabs "example8">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_SplitToMultiPageDocuments.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_SplitToMultiPageDocuments.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_SplitToMultiPageDocuments.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_SplitToMultiPageDocuments.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_SplitToMultiPageDocuments.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_SplitToMultiPageDocuments.py >}}

{{< /tab >}} {{< /tabs >}}
