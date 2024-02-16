---
id: "join-images"
url: "merger/join-images"
title: "Join Images"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

There is an additional option for Image joining.

|Name|Description|Comment
|---|---|---|
|JoinItem.ImageJoinMode|Possible modes for the image joining|Values: Horizontal, Vertical

## Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

## cURL example

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
                'FilePath': 'Img/task1.jpg'
            }
        },
        {
            'FileInfo':
            {
                'FilePath': 'Img/task2.jpg'
            },
            'ImageJoinMode': 'Vertical'
        }
    ],
    'OutputPath': 'Output/joined.jpg'
}"

```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant document
{
  "path": "Output/joined.jpg"
}

```

{{< /tab >}} {{< /tabs >}}

## SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

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
            FilePath = "Img/task1.jpg"
        }
    };

    var item2 = new JoinItem
    {
        FileInfo = new FileInfo
        {
            FilePath = "Img/task2.jpg"
        },
        ImageJoinMode = JoinItem.ImageJoinModeEnum.Vertical
    };

    var options = new JoinOptions
    {
        JoinItems = new List<JoinItem> { item1, item2 },
        OutputPath = "Output/joined.jpg",
                    
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

{{< /tab >}} {{< tab "Java & Android" >}}

```java
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-java-samples
String MyClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
String MyClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

Configuration configuration = new Configuration(MyClientId, MyClientSecret);
DocumentApi apiInstance = new DocumentApi(configuration);

try {
    FileInfo fileInfo1 = new FileInfo();
    fileInfo1.setFilePath("Img/task1.jpg");
    JoinItem item1 = new JoinItem();
    item1.setFileInfo(fileInfo1);

    FileInfo fileInfo2 = new FileInfo();
    fileInfo2.setFilePath("Img/task2.jpg");
    JoinItem item2 = new JoinItem();
    item2.setFileInfo(fileInfo2);
    item2.setImageJoinMode(ImageJoinModeEnum.VERTICAL);

    JoinOptions options = new JoinOptions();
    options.setJoinItems(Arrays.asList(item1, item2));
    options.setOutputPath("Output/joined.jpg");

    JoinRequest request = new JoinRequest(options);

    DocumentResult response = apiInstance.join(request);

    System.err.println("Output file path: " + response.getPath());

} catch (ApiException e) {

    System.err.println("Exception while calling api:");
    e.printStackTrace();
}

```

{{< /tab >}} {{< tab "PHP" >}}

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
$fileInfo1->setFilePath("Img/task1.jpg");         
$item1 = new Model\JoinItem();        
$item1->setFileInfo($fileInfo1);

$fileInfo2 = new Model\FileInfo();
$fileInfo2->setFilePath("Img/task2.jpg");          
$item2 = new Model\JoinItem();
$item2->setFileInfo($fileInfo2);
$шеуь2->setImageJoinMode(Model\JoinItem::IMAGE_JOIN_MODE_VERTICAL);

$options = new Model\JoinOptions();
$options->setJoinItems([$item1, $item2]);
$options->setOutputPath("Output/joined.jpg");

$request = new Requests\joinRequest($options);       
$response = $documentApi->join($request);

echo "Output file path: " . $response->getPath();    
echo "\n";                  

```

{{< /tab >}} {{< tab "Node.js" >}}

```JavaScript

// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.merger_cloud = require("groupdocs-merger-cloud");

global.clientId = "XXXX-XXXX-XXXX-XXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
global.clientSecret = "XXXXXXXXXXXXXXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

global.documentApi = merger_cloud.DocumentApi.fromKeys(clientId, clientSecret);

let item1 = new merger_cloud.JoinItem();
item1.fileInfo = new merger_cloud.FileInfo();
item1.fileInfo.filePath = "Img/task1.jpg";

let item2 = new merger_cloud.JoinItem();
item2.fileInfo = new merger_cloud.FileInfo();
item2.fileInfo.filePath = "Img/task2.jpg";    
item2.imageJoinMode = merger_cloud.JoinItem.ImageJoinModeEnum.Vertical;

let options = new merger_cloud.JoinOptions();
options.joinItems = [item1, item2];
options.outputPath = "Output/joined_continous.docx";

let result = await documentApi.join(new merger_cloud.JoinRequest(options));

console.log("Output file path: " + result.path);

```

{{< /tab >}} {{< tab "Python" >}}

```python

# For complete examples and data files, please go to https://github.com/groupdocs-merger_cloud-cloud/groupdocs-merger_cloud-cloud-python-samples
from groupdocs_merger_cloud import *
import groupdocs_merger_cloud

client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(client_id, client_secret)

item1 = groupdocs_merger_cloud.JoinItem()
item1.file_info = groupdocs_merger_cloud.FileInfo("Img/task1.jpg")
item2 = groupdocs_merger_cloud.JoinItem()
item2.file_info = groupdocs_merger_cloud.FileInfo("Img/task2.jpg")
item2.image_join_mode = "Vertical"

options = groupdocs_merger_cloud.JoinOptions()
options.join_items = [item1, item2]
options.output_path = "Output/joined.jpg"

result = documentApi.join(groupdocs_merger_cloud.JoinRequest(options))        

print("Output file path = " + result.path)

```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby

# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
require 'groupdocs_merger_cloud'

$client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud

documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($client_id, $client_secret)

item1 = GroupDocsMergerCloud::JoinItem.new
item1.file_info = GroupDocsMergerCloud::FileInfo.new
item1.file_info.file_path = 'Img/task1.jpg'

item2 = GroupDocsMergerCloud::JoinItem.new
item2.file_info = GroupDocsMergerCloud::FileInfo.new
item2.file_info.file_path = 'Img/task2.jpg'        
item2.image_join_mode = 'Vertical'

options = GroupDocsMergerCloud::JoinOptions.new
options.join_items = [item1, item2]
options.output_path = "Output/joined.jpg"

result = documentApi.join(GroupDocsMergerCloud::JoinRequest.new(options))

puts("Output file path: " + result.path)

```

{{< /tab >}} {{< /tabs >}}
