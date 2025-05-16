---
id: "join-multiple-documents"
url: "merger/join-multiple-documents"
title: "Join Multiple Documents"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

This REST API allows merging two or more documents into a single resultant document.
For the simplest scenario of combining several documents together it's only needed to provide storage path for each file. For protected documents, it is also required to provide a password.
The table below contains the full list of properties that can be specified for each joined document.

|Name|Description|Comment
|---|---|---|
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|Path to resultant document|Required

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

*Response will contain storage path to resultant document
{
  "path": "Output/joined.docx"
}

```

{{< /tab >}} {{< /tabs >}}

## SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

```csharp
using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using System.Collections.Generic;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to join multiple documents into one document.
    /// </summary>
    public class JoinMultipleDocuments
    {
		public static void Run()
		{
			var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new DocumentApi(configuration);

			try
			{
                var item1 = new JoinItem
                {
                    FileInfo = new FileInfo
                    {
                        FilePath = "WordProcessing/four-pages.docx"
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
                    OutputPath = "Output/joined.docx"
                };

                var request = new JoinRequest(options);
                var response = apiInstance.Join(request);

                Console.WriteLine("Output file path: " + response.Path);
            }
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling api: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples.DocumentOperations;

import java.util.Arrays;
import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to join multiple documents into one document.
 */
public class Merger_Java_JoinMultipleDocuments {

	public static void main(String[] args) {		

		DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo1 = new FileInfo();			
			fileInfo1.setFilePath("WordProcessing/four-pages.docx");
			JoinItem item1 = new JoinItem();
			item1.setFileInfo(fileInfo1);

			FileInfo fileInfo2 = new FileInfo();			
			fileInfo2.setFilePath("WordProcessing/one-page.docx");
			JoinItem item2 = new JoinItem();
			item2.setFileInfo(fileInfo2);

			JoinOptions options = new JoinOptions();
			options.setJoinItems(Arrays.asList(item1, item2));
			options.setOutputPath("output/joined.docx");

			JoinRequest request = new JoinRequest(options);

			DocumentResult response = apiInstance.join(request);

			System.err.println("Output file path: " + response.getPath());
		
		} catch (ApiException e) {

			System.err.println("Exception while calling api:");
			e.printStackTrace();
		}
	}
}
```

{{< /tab >}} {{< tab "PHP" >}}

```php
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-php-samples
$AppSid = 'XXXX-XXXX-XXXX-XXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$AppKey = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
$configuration = new GroupDocs\Merger\Configuration();
$configuration->setAppSid(CommonUtils::$AppSid);
$configuration->setAppKey(CommonUtils::$AppKey);
 
$documentApi = GroupDocs\Merger\DocumentApi($configuration);
  
$fileInfo1 = new Model\FileInfo();
$fileInfo1->setFilePath("WordProcessing/four-pages.docx");         
$item1 = new Model\JoinItem();        
$item1->setFileInfo($fileInfo1);
 
$fileInfo2 = new Model\FileInfo();
$fileInfo2->setFilePath("WordProcessing/one-page.docx");          
$item2 = new Model\JoinItem();
$item2->setFileInfo($fileInfo2);                
 
$options = new Model\JoinOptions();
$options->setJoinItems([$item1, $item2]);
$options->setOutputPath("Output/joined.docx");
 
$request = new Requests\joinRequest($options);       
$response = $documentApi->join($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($app_sid, $app_key)
 
item1 = GroupDocsMergerCloud::JoinItem.new
item1.file_info = GroupDocsMergerCloud::FileInfo.new
item1.file_info.file_path = 'WordProcessing/four-pages.docx'
 
item2 = GroupDocsMergerCloud::JoinItem.new
item2.file_info = GroupDocsMergerCloud::FileInfo.new
item2.file_info.file_path = 'WordProcessing/one-page.docx'       
 
options = GroupDocsMergerCloud::JoinOptions.new
options.join_items = [item1, item2]
options.output_path = "Output/joined.docx"
 
result = documentApi.join(GroupDocsMergerCloud::JoinRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.documentApi = merger_cloud.DocumentApi.fromKeys(appSid, appKey);
 
let item1 = new merger_cloud.JoinItem();
item1.fileInfo = new merger_cloud.FileInfo();
item1.fileInfo.filePath = "WordProcessing/four-pages.docx";
 
let item2 = new merger_cloud.JoinItem();
item2.fileInfo = new merger_cloud.FileInfo();
item2.fileInfo.filePath = "WordProcessing/one-page.docx";    
 
let options = new merger_cloud.JoinOptions();
options.joinItems = [item1, item2];
options.outputPath = "Output/joined.docx";
 
let result = await documentApi.join(new merger_cloud.JoinRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)
 
item1 = groupdocs_merger_cloud.JoinItem()
item1.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/four-pages.docx")
item2 = groupdocs_merger_cloud.JoinItem()
item2.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/one-page.docx")
 
options = groupdocs_merger_cloud.JoinOptions()
options.join_items = [item1, item2]
options.output_path = "Output/joined.docx"
 
result = documentApi.join(groupdocs_merger_cloud.JoinRequest(options))
```

{{< /tab >}} {{< /tabs >}}
