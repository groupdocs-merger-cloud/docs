---
id: "security-operations"
url: "merger/security-operations"
title: "Security Operations"
productName: "GroupDocs.Merger Cloud"
weight: 5
description: ""
keywords: ""
---

## Add Document Password Protection ##

This REST API allows adding document password protection. API endpoint accepts document storage path as input payload and returns path to the created a password-protected document.

The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|Path to resultant document|Required

## Resource URI ##

```html

HTTP PUT ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/AddPassword) lets you call this REST API directly from the browser.

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

{{< /tab >}} {{< tab tabNum="2" >}}

```html

{
  "path": "output/add-password.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

### Add Document Password Protection ###

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_AddDocumentPassword.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_AddDocumentPassword.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_AddDocumentPassword.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_AddDocumentPassword.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_AddDocumentPassword.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_AddDocumentPassword.py >}}

{{< /tab >}} {{< /tabs >}}

## Check the Document for Password Protection ##

This REST API allows checking the document for password-protection. The result will be **true** if the document has a password for the opening set, in another case **false** will be returned. The endpoint accepts the file path as a query string parameter and returns the IsPasswordSet flag.

The description of the important API parameters is given below:

|Name|Type|Description
|---|---|---
|filePath|string|Path to document to append. Query parameter. Required.
|storageName|string|Storage name. Query parameter. Optional
|versionId|string|File version id. Query parameter. Optional

## Resource URI ##

```html

HTTP GET ~/password?filePath#{filePath}

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/CheckPassword) lets you call this REST API directly from the browser.

### cURL Example ###

{{< tabs tabTotal="2" tabID="2" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html

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

{{< /tab >}} {{< tab tabNum="2" >}}

```html

{
  "isPasswordSet": true
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

### Check the Document for Password Protection ###

{{< tabs tabTotal="6" tabID="11" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_CheckDocumentPasswordProtection.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_CheckDocumentPasswordProtection.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_CheckDocumentPasswordProtection.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_CheckDocumentPasswordProtection.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_CheckDocumentPasswordProtection.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_CheckDocumentPasswordProtection.py >}}

{{< /tab >}} {{< /tabs >}}

## Remove Document Password ##

This REST API allows removing the password from a password-protected document. API endpoint accepts document storage path as input payload and returns the path to document without password-protection.
The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|Path to resultant document|Required

## Resource URI ##

```html

HTTP DELETE ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/RemovePassword) lets you call this REST API directly from the browser.

### cURL Example ###

{{< tabs tabTotal="2" tabID="3" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html

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

{{< /tab >}} {{< tab tabNum="2" >}}

```html

{
  "path": "output/remove-password.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDKs ###

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

### Remove Document Password ###

{{< tabs tabTotal="6" tabID="12" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_RemoveDocumentPassword.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_RemoveDocumentPassword.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_RemoveDocumentPassword.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_RemoveDocumentPassword.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_RemoveDocumentPassword.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_RemoveDocumentPassword.py >}}

{{< /tab >}} {{< /tabs >}}

## Update Document Password ##

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

## Resource URI ##

```html

HTTP POST ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/UpdatePassword) lets you call this REST API directly from the browser.

### cURL Example ###

{{< tabs tabTotal="2" tabID="4" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html

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

{{< /tab >}} {{< tab tabNum="2" >}}

```html
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

### SDKs ###

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

### Update Document Password ###

{{< tabs tabTotal="6" tabID="13" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

{{< gist groupdocscloud b7a9ad2a32b358e32583134d20c4a384 Merger_CSharp_UpdateDocumentPassword.cs >}}

{{< /tab >}} {{< tab tabNum="2" >}}

{{< gist groupdocscloud a22ef5f91f7f8565fee2bac658674b49 Merger_Java_UpdateDocumentPassword.java >}}

{{< /tab >}} {{< tab tabNum="3" >}}

{{< gist groupdocscloud 48648ca8f7d3bfedb079a7d7e3af9e0e Merger_Php_UpdateDocumentPassword.php >}}

{{< /tab >}} {{< tab tabNum="6" >}}

{{< gist groupdocscloud 61d2eea73f56f457c060b2894d545d23 Merger_Ruby_UpdateDocumentPassword.rb >}}

{{< /tab >}} {{< tab tabNum="4" >}}

{{< gist groupdocscloud 45a085bb4520da51407ee295a67b4021 Merger_Node_UpdateDocumentPassword.js >}}

{{< /tab >}} {{< tab tabNum="5" >}}

{{< gist groupdocscloud ca731968d52778c9e2b0fc5d82d044d0 Merger_Python_UpdateDocumentPassword.py >}}

{{< /tab >}} {{< /tabs >}}
