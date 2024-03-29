---
id: "security-operations"
url: "merger/security-operations"
title: "Security Operations"
productName: "GroupDocs.Merger Cloud"
weight: 5
description: ""
keywords: ""
toc: True
---

## Add Document Password Protection

This REST API allows adding document password protection. API endpoint accepts document storage path as input payload and returns path to the created a password-protected document.

The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|Path to resultant document|Required

### Resource URI

```html

HTTP PUT ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/AddPassword) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password" \
-X PUT
-H "Authorization: Bearer
<jwt token>"
-d "{
        'FileInfo': { 'FilePath': 'words/four-pages.docx'},
        'Password':  'Password',
        'OutputPath': 'output/add-password.docx'
    }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

{
  "path": "output/add-password.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_AddDocumentPassword.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_AddDocumentPassword.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_AddDocumentPassword.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_AddDocumentPassword.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_AddDocumentPassword.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_AddDocumentPassword.py >}}

{{< /tab >}} {{< /tabs >}}

## Check the Document for Password Protection

This REST API allows checking the document for password-protection. The result will be **true** if the document has a password for the opening set, in another case **false** will be returned. The endpoint accepts the file path as a query string parameter and returns the IsPasswordSet flag.

The description of the important API parameters is given below:

|Name|Type|Description
|---|---|---
|filePath|string|Path to document to append. Query parameter. Required.
|storageName|string|Storage name. Query parameter. Optional
|versionId|string|File version id. Query parameter. Optional

### Resource URI

```html

HTTP GET ~/password?filePath#{filePath}

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/CheckPassword) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example3">}} {{< tab "Request" >}}

```bash

* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password?filePath#%2Fwords%2Fpassword-protected.docx" \
-X GET
-H "Authorization: Bearer
<jwt token>"

```

{{< /tab >}} {{< tab "Response" >}}

```json

{
  "isPasswordSet": true
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example4">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_CheckDocumentPasswordProtection.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_CheckDocumentPasswordProtection.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_CheckDocumentPasswordProtection.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_CheckDocumentPasswordProtection.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_CheckDocumentPasswordProtection.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_CheckDocumentPasswordProtection.py >}}

{{< /tab >}} {{< /tabs >}}

## Remove Document Password

This REST API allows removing the password from a password-protected document. API endpoint accepts document storage path as input payload and returns the path to document without password-protection.
The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|Path to resultant document|Required

### Resource URI

```html

HTTP DELETE ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/RemovePassword) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password" \
-X DELETE
-H "Authorization: Bearer
<jwt token>"
-d "{
        'FileInfo': { 'FilePath': 'words/password-protected.docx'},
        'Password':  'Password',
        'OutputPath': 'output/remove-password.docx'
    }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

{
  "path": "output/remove-password.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example6">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_RemoveDocumentPassword.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_RemoveDocumentPassword.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_RemoveDocumentPassword.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_RemoveDocumentPassword.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_RemoveDocumentPassword.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_RemoveDocumentPassword.py >}}

{{< /tab >}} {{< /tabs >}}

## Update Document Password

This REST API allows updating the password for the password-protected document. The resultant document will have a new password. API endpoint accepts document storage path as input payload and returns path to document with a new password.

The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|File path in storage|Required property
|StorageName|Storage name|Could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Required
|NewPassword|New password|Required
|OutputPath|Path to resultant document|Required

### Resource URI

```html

HTTP POST ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/UpdatePassword) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password" \
-X POST
-H "Authorization: Bearer
<jwt token>"
-d "{
        'FileInfo':
     {
        'FilePath': '/words/password-protected.docx',
         'Password':  'Password',
     },
     'NewPassword':  'NewPassword',
     'OutputPath': 'output/update-password.docx'
    }"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "path": "output/update-password.docx"
}

```

{{< /tab >}} {{< /tabs >}}

Response

```html
{
  "path": "output/update-password.docx"
}
```

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example8">}} {{< tab "C#" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_UpdateDocumentPassword.cs >}}

{{< /tab >}} {{< tab "Java" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_UpdateDocumentPassword.java >}}

{{< /tab >}} {{< tab "PHP" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_UpdateDocumentPassword.php >}}

{{< /tab >}} {{< tab "Ruby" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_UpdateDocumentPassword.rb >}}

{{< /tab >}} {{< tab "Node.js" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_UpdateDocumentPassword.js >}}

{{< /tab >}} {{< tab "Python" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_UpdateDocumentPassword.py >}}

{{< /tab >}} {{< /tabs >}}
