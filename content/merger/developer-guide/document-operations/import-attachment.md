---
id: "import-attachment"
url: "merger/import-attachment"
title: "Import attachment into pdf document"
productName: "GroupDocs.Merger Cloud"
weight: 2
description: ""
keywords: ""
---

## Introduction ##

This REST API allows add attachments into pdf documents. Attachments should be uploaded into cloud storage before importing.

The table below contains the full list of properties that can be specified.

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|Could be omitted for default storage
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|Attachments|Collection of attachments files paths
|OutputPath|Path to resultant document|Required

## Resource URI ##

```html

HTTP POST ~/import

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Import) lets you call this REST API directly from the browser.

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

* cURL example to join pages from several documents into one document
curl -v "https://api.groupdocs.cloud/v1.0/merger/import" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
    'FileInfo':
    {
        'FilePath': 'Pdf/one-page-password.pdf',
        'Password': 'password'
    },    
    'Attachments': [ "Txt/document.txt" ],
    'OutputPath': 'Output/with-attachment.pdf'
}"

```

{{< /tab >}} {{< tab tabNum="2" >}}

```html

*Response will contain storage path to resultant document
{
  "path": "Output/with-attachment.pdf"
}
```

{{< /tab >}} {{< /tabs >}}

## SDKs ##

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

### SDK Examples ###

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java & Android" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

```csharp

// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-dotnet-samples
string MyClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
string MyClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

var configuration = new Configuration(MyClientId, MyClientSecret);
var apiInstance = new DocumentApi(configuration);

try
{
    var options = new ImportOptions
    {
        FileInfo = new FileInfo
        {
            FilePath = "Pdf/one-page-password.pdf",
            Password = "password"
        },
        Attachments = new List<string> { "Txt/document.txt" },
        OutputPath = "Output/with-attachment.pdf"
    };

    var request = new ImportRequest(options);
    var response = apiInstance.Import(request);

    Console.WriteLine("Output file path: " + response.Path);
}
catch (Exception e)
{
    Console.WriteLine("Exception while calling api: " + e.Message);
}
```

{{< /tab >}} {{< tab tabNum="2" >}}

```java
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-java-samples
String MyClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
String MyClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

Configuration configuration = new Configuration(MyClientId, MyClientSecret);
DocumentApi apiInstance = new DocumentApi(configuration);

try {
    ImportOptions options = new ImportOptions();
    FileInfo fileInfo = new FileInfo();   
    fileInfo.setFilePath("Pdf/one-page-password.pdf");
    fileInfo.setPassword("password");   
    options.setFileInfo(fileInfo);   
    options.addAttachmentsItem("Txt/document.txt");
    options.setOutputPath("output/with-attachment.pdf");

    CallImportRequest request = new CallImportRequest(options);

    DocumentResult response = apiInstance.callImport(request);

    System.err.println("Output file path: " + response.getPath());

    } catch (ApiException e) {

    System.err.println("Exception while calling api:");
    e.printStackTrace();
}

```

{{< /tab >}} {{< tab tabNum="3" >}}

```php

// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-php-samples
use GroupDocs\Merger\Model;
use GroupDocs\Merger\Model\Requests;

$ClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$ClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

$configuration = new GroupDocs\Merger\Configuration();
$configuration->setAppSid($ClientId);
$configuration->setAppKey($ClientSecret);

$documentApi = new GroupDocs\Merger\DocumentApi($configuration);

$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("Pdf/one-page-password.pdf");         
$fileInfo->setPassword("password");

$options = new Model\ImportOptions();
$options->setFileInfo($fileInfo);
$options->setAttachments(["Txt/document.txt"]);
$options->setOutputPath("Output/with-attachment.pdf");

$request = new Requests\importRequest($options);       
$response = $documentApi->import($request);

echo "Output file path: " . $response->getPath();    
echo "\n";                  

```

{{< /tab >}} {{< tab tabNum="4" >}}

```JavaScript

// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.merger_cloud = require("groupdocs-merger-cloud");

global.clientId = "XXXX-XXXX-XXXX-XXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
global.clientSecret = "XXXXXXXXXXXXXXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

global.documentApi = merger_cloud.DocumentApi.fromKeys(clientId, clientSecret);

let options = new merger_cloud.ImportOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "Pdf/one-page-password.pdf";
options.fileInfo.password = "password";
options.attachments = ["Txt/document.txt"];
options.outputPath = "Output/with-attachment.pdf";

let result = await documentApi._import(new merger_cloud.ImportRequest(options));

console.log("Output file path: " + result.path);

```

{{< /tab >}} {{< tab tabNum="5" >}}

```python

# For complete examples and data files, please go to https://github.com/groupdocs-merger_cloud-cloud/groupdocs-merger_cloud-cloud-python-samples
from groupdocs_merger_cloud import *
import groupdocs_merger_cloud

client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(client_id, client_secret)

options = groupdocs_merger_cloud.ImportOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("Pdf/one-page-password.pdf", None, None, "password")
options.attachments = ["Txt/document.txt"]
options.output_path = "Output/with-attachment.pdf"

result = documentApi.call_import(groupdocs_merger_cloud.CallImportRequest(options))

print("Output file path = " + result.path)

```

{{< /tab >}} {{< tab tabNum="6" >}}

```ruby

# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
require 'groupdocs_merger_cloud'

$client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($client_id, $client_secret)

options = GroupDocsMergerCloud::ImportOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'Pdf/one-page-password.pdf'
options.file_info.password = 'password'        
options.attachments = ["Txt/document.txt"]
options.output_path = "Output/with-attachment.pdf"

result = documentApi.import(GroupDocsMergerCloud::ImportRequest.new(options))

puts("Output file path: " + result.path)

```

{{< /tab >}} {{< /tabs >}}
