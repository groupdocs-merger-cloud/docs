---
id: "join-document-pages"
url: "merger/join-document-pages"
title: "Join Document Pages"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

This REST API allows merging the source document with specific document pages from joined documents into one resultant document by specifying desired page numbers or page ranges.
There are several ways to specify page numbers needed from each document:

* Provide exact page numbers via Pages collection;
* Specify pages range start/end page numbers. There is also an ability to get only even/odd pages from the specified page range by setting RangeMode property.

For protected documents, it is also required to provide a password.
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
                'FilePath': 'WordProcessing/sample-10-pages.docx'
            },
            'Pages':  [ 3, 6, 8 ],
        },
        {
            'FileInfo':
            {
                'FilePath': 'WordProcessing/four-pages.docx'
            },
            'StartPageNumber': 1,
            'EndPageNumber': 4,
            'RangeMode' : 1
        }
    ],
    'OutputPath': 'output/joined-pages.docx'
}"

```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant document
{
  "path": "output/joined-pages.docx"
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
    /// This example demonstrates how to join specific pages from several source documents.
    /// </summary>
    public class JoinPagesFromVariousDocuments
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
                        FilePath = "WordProcessing/sample-10-pages.docx"
                    },
                    Pages = new List<int?> {  3, 6, 8 }
                };

                var item2 = new JoinItem
                {
                    FileInfo = new FileInfo
                    {
                        FilePath = "WordProcessing/four-pages.docx"
                    },
                    StartPageNumber= 1,
                    EndPageNumber = 4,
                    RangeMode = JoinItem.RangeModeEnum.OddPages 
                };

                var options = new JoinOptions
                {
                    JoinItems = new List<JoinItem> { item1, item2 },
                    OutputPath = "Output/joined-pages.docx"
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
 * This example demonstrates how to join specific pages from several source documents.
 */
public class Merger_Java_JoinPagesFromVariousDocuments {

	public static void main(String[] args) {		

		DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo1 = new FileInfo();			
			fileInfo1.setFilePath("WordProcessing/sample-10-pages.docx");
			JoinItem item1 = new JoinItem();
			item1.setFileInfo(fileInfo1);
			item1.setPages(Arrays.asList(3, 6, 8));

			FileInfo fileInfo2 = new FileInfo();			
			fileInfo2.setFilePath("WordProcessing/four-pages.docx");
			JoinItem item2 = new JoinItem();
			item2.setFileInfo(fileInfo2);
			item2.setStartPageNumber(1);
			item2.setEndPageNumber(4);
			item2.setRangeMode(JoinItem.RangeModeEnum.ODDPAGES);

			JoinOptions options = new JoinOptions();
			options.setJoinItems(Arrays.asList(item1, item2));
			options.setOutputPath("output/joined-pages.docx");

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
$fileInfo1->setFilePath("WordProcessing/sample-10-pages.docx");         
$item1 = new Model\JoinItem();        
$item1->setFileInfo($fileInfo1);
$item1->setPages([3, 6, 8]);
 
$fileInfo2 = new Model\FileInfo();
$fileInfo2->setFilePath("WordProcessing/four-pages.docx");          
$item2 = new Model\JoinItem();
$item2->setFileInfo($fileInfo2); 
$item2->setStartPageNumber(1);               
$item2->setEndPageNumber(4);
$item2->setRangeMode(Model\JoinItem::RANGE_MODE_ODD_PAGES);
 
$options = new Model\JoinOptions();
$options->setJoinItems([$item1, $item2]);
$options->setOutputPath("Output/joined-pages.docx");
 
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
item1.file_info.file_path = 'WordProcessing/sample-10-pages.docx'
item1.pages = [3, 6, 8]
 
item2 = GroupDocsMergerCloud::JoinItem.new
item2.file_info = GroupDocsMergerCloud::FileInfo.new
item2.file_info.file_path = 'WordProcessing/four-pages.docx'       
item2.start_page_number = 1
item2.end_page_number = 4
item2.range_mode = "OddPages"
 
options = GroupDocsMergerCloud::JoinOptions.new
options.join_items = [item1, item2]
options.output_path = "Output/joined-pages.docx"
 
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
item1.fileInfo.filePath = "WordProcessing/sample-10-pages.docx";
item1.pages = [3, 6, 8];
 
let item2 = new merger_cloud.JoinItem();
item2.fileInfo = new merger_cloud.FileInfo();
item2.fileInfo.filePath = "WordProcessing/four-pages.docx";
item2.startPageNumber = 1
item2.endPageNumber = 4
item2.rangeMode = merger_cloud.JoinItem.RangeModeEnum.OddPages;
         
let options = new merger_cloud.JoinOptions();
options.joinItems = [item1, item2];
options.outputPath = "Output/joined-pages.docx";
 
let result = await documentApi.join(new merger_cloud.JoinRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)
 
item1 = groupdocs_merger_cloud.JoinItem()
item1.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
item1.pages = [3, 6, 8]
 
item2 = groupdocs_merger_cloud.JoinItem()
item2.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/four-pages.docx")
item2.start_page_number = 1
item2.end_page_number = 4
item2.range_mode = "OddPages"
 
options = groupdocs_merger_cloud.JoinOptions()
options.join_items = [item1, item2]
options.output_path = "Output/joined-pages.docx"
 
result = documentApi.join(groupdocs_merger_cloud.JoinRequest(options))
```

{{< /tab >}} {{< /tabs >}}
