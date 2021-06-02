---
id: "join-document-cross-format"
url: "merger/join-document-cross-format"
title: "Join Documents of different formats"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
---

## Introduction ##

This REST API allows merging the document of different formats into one pdf or word processing document.

The table below contains the full list of properties that can be specified for each joined document.

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|Could be omitted for default storage
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|Pages|Collection of page numbers to use in a Join operation|The first page should have number 1
|StartPageNumber|Start page number|Ignored if Pages collection is not empty
|EndPageNumber|End page number|Ignored if Pages collection is not empty
|RangeMode|Page range mode: Even, Odd, All. The default value is All|Ignored if Pages collection is not empty
|OutputPath|Path to resultant document|Required

## Resource URI ##

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

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
                'FilePath': 'Pdf/one-page-password.pdf',
                'Password': 'password'
            }
        },
        {
            'FileInfo':
            {
                'FilePath': 'WordProcessing/one-page.docx'
            }
        }
    ],
    'OutputPath': 'Output/joined.pdf'
}"

```

{{< /tab >}} {{< tab tabNum="2" >}}

```html

*Response will contain storage path to resultant document
{
  "path": "Output/joined.pdf"
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
    var item1 = new JoinItem
    {
        FileInfo = new FileInfo
        {
            FilePath = "Pdf/one-page-password.pdf",
            Password = "password"
        }
    };

    var item2 = new JoinItem
    {
        FileInfo = new FileInfo
        {
            FilePath = "WordProcessing/one-page.docx"
        }
    };

    var options = new JoinOptions
    {
        JoinItems = new List<JoinItem> { item1, item2 },
        OutputPath = "Output/joined.pdf"
    };

    var request = new JoinRequest(options);
    var response = apiInstance.Join(request);

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
    FileInfo fileInfo1 = new FileInfo();   
    fileInfo1.setFilePath("Pdf/one-page-password.pdf");
    fileInfo1.setPassword("password");
    JoinItem item1 = new JoinItem();
    item1.setFileInfo(fileInfo1);

    FileInfo fileInfo2 = new FileInfo();   
    fileInfo2.setFilePath("WordProcessing/one-page.docx");
    JoinItem item2 = new JoinItem();
    item2.setFileInfo(fileInfo2);

    JoinOptions options = new JoinOptions();
    options.setJoinItems(Arrays.asList(item1, item2));
    options.setOutputPath("output/joined.pdf");

    JoinRequest request = new JoinRequest(options);

    DocumentResult response = apiInstance.join(request);

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

$fileInfo1 = new Model\FileInfo();
$fileInfo1->setFilePath("Pdf/one-page-password.pdf");         
$fileInfo1->setPassword("password");
$item1 = new Model\JoinItem();        
$item1->setFileInfo($fileInfo1);

$fileInfo2 = new Model\FileInfo();
$fileInfo2->setFilePath("WordProcessing/one-page.docx");          
$item2 = new Model\JoinItem();
$item2->setFileInfo($fileInfo2);                

$options = new Model\JoinOptions();
$options->setJoinItems([$item1, $item2]);
$options->setOutputPath("Output/joined.pdf");

$request = new Requests\joinRequest($options);       
$response = $documentApi->join($request);

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

let item1 = new merger_cloud.JoinItem();
item1.fileInfo = new merger_cloud.FileInfo();
item1.fileInfo.filePath = "Pdf/one-page-password.pdf";
item1.fileInfo.password = "password";

let item2 = new merger_cloud.JoinItem();
item2.fileInfo = new merger_cloud.FileInfo();
item2.fileInfo.filePath = "WordProcessing/one-page.docx";    

let options = new merger_cloud.JoinOptions();
options.joinItems = [item1, item2];
options.outputPath = "Output/joined.pdf";

let result = await documentApi.join(new merger_cloud.JoinRequest(options));

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

item1 = groupdocs_merger_cloud.JoinItem()
item1.file_info = groupdocs_merger_cloud.FileInfo("Pdf/one-page-password.pdf", None, None, "password")
item2 = groupdocs_merger_cloud.JoinItem()
item2.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/one-page.docx")

options = groupdocs_merger_cloud.JoinOptions()
options.join_items = [item1, item2]
options.output_path = "Output/joined.pdf"

result = documentApi.join(groupdocs_merger_cloud.JoinRequest(options))        

print("Output file path = " + result.path)

```

{{< /tab >}} {{< tab tabNum="6" >}}

```ruby

# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
require 'groupdocs_merger_cloud'

$client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($client_id, $client_secret)

item1 = GroupDocsMergerCloud::JoinItem.new
item1.file_info = GroupDocsMergerCloud::FileInfo.new
item1.file_info.file_path = 'Pdf/one-page-password.pdf'
item1.file_info.password = 'password'

item2 = GroupDocsMergerCloud::JoinItem.new
item2.file_info = GroupDocsMergerCloud::FileInfo.new
item2.file_info.file_path = 'WordProcessing/one-page.docx'        

options = GroupDocsMergerCloud::JoinOptions.new
options.join_items = [item1, item2]
options.output_path = "Output/joined.pdf"

result = documentApi.join(GroupDocsMergerCloud::JoinRequest.new(options))

puts("Output file path: " + result.path)

```

{{< /tab >}} {{< /tabs >}}
