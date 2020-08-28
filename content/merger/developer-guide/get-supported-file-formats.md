---
id: "get-supported-file-formats"
url: "merger/get-supported-file-formats"
title: "Get Supported File Formats"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
---

# Introduction #

This REST API allows getting a list of all [file formats supported ]({{< ref "merger/getting-started/supported-document-formats.md" >}}))by GroupDocs.Merger Cloud product.

## Resources ##

The following GroupDocs.Editor Cloud REST API resource has been used in the [get supported file types](https://apireference.groupdocs.cloud/merger/#/Info/GetSupportedFileFormats) example.
|---|---

|
|---

HTTP POST ~~/formats

## cURL Example ##

The following example demonstrates how to get supported file types.

 Request

```html
* First get JSON Web Token
* Please get your App Key and App SID from https://dashboard.groupdocs.cloud/#/apps. Kindly place App Key in "client_secret" and App SID in "client_id" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type#client_credentials&client_id#xxxx&client_secret#xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/formats" \
-X GET \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer <jwt token>"

 ```

 Response

```html
{
  "formats": [
    {
      "extension": ".doc",
      "fileFormat": "Microsoft Word Document"
    },
    {
      "extension": ".docm",
      "fileFormat": "Word Open XML Macro-Enabled Document"
    },
    {
      "extension": ".docx",
      "fileFormat": "Microsoft Word Open XML Document"
    },
   ...
    {
      "extension": ".xlsx",
      "fileFormat": "Microsoft Excel Open XML Spreadsheet"
    }
  ]
}

 ```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Info/GetSupportedFileFormats) lets you call this REST API directly from the browser. 

## SDKs ##

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-editor-cloud) for a complete list of GroupDocs.Editor Cloud SDKs along with working examples, to get you started in no time. Please check [Available SDKs]({{< ref "merger/getting-started/available-sdks.md" >}}) article to learn how to add an SDK to your project.

### Get Supported File Types Examples ###

 C#

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_GetSupportedFileTypes.cs >}}

 Java

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_GetSupportedFileTypes.java >}}

 PHP

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_GetSupportedFileTypes.php >}}

 Ruby

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_GetSupportedFileTypes.rb >}}

 Node.js

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_GetSupportedFileTypes.js >}}

 Python

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_GetSupportedFileTypes.py >}}

