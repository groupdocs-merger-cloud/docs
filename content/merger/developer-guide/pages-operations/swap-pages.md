---
id: "swap-pages"
url: "merger/swap-pages"
title: "Swap Pages"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

This REST API allows swapping two pages of positions within the source document. The result is a new document where two pages have their positions exchanged.
For swapping pages positions it's needed to specify page numbers along with a path to document in storage. For protected documents, it is also required to provide a password.

The table below contains the full list of properties that can be specified while swapping document pages.

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|FirstPageNumber|First-page number to swap|Required
|SecondPageNumber|Second-page number to swap|Required

## Resource URI

```html

HTTP POST ~/pages/swap

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Swap) lets you call this REST API directly from the browser.
|---|---

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
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/swap" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
  'FileInfo': { 'FilePath': 'words/four-pages.docx'},
     'FirstPageNumber':  2,
     'SecondPageNumber':  4,
     'OutputPath': 'output/swap-pages.docx'
 }"
```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant document
{
  "path": "output/swap-pages.docx"
}
```

{{< /tab >}} {{< /tabs >}}

## SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

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
    /// This example demonstrates how to swap document pages.
    /// </summary>
    public class SwapPages
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new PagesApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
						FilePath = "WordProcessing/four-pages.docx"
                };

                var options = new SwapOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/swap-pages.docx",
                    FirstPageNumber = 2,
                    SecondPageNumber = 4
                };
                var request = new SwapRequest(options);

                var response = apiInstance.Swap(request);

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
package examples.PagesOperations;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to swap document pages.
 */
public class Merger_Java_SwapPages {

	public static void main(String[] args) {		

		PagesApi apiInstance = new PagesApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/four-pages.docx");

			SwapOptions options = new SwapOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/swap-pages.docx");
			options.setFirstPageNumber(2);
			options.setSecondPageNumber(4);

			SwapRequest request = new SwapRequest(options);

			DocumentResult response = apiInstance.swap(request);

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
 
$pagesApi = GroupDocs\Merger\PagesApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/four-pages.docx");         
 
$options = new Model\SwapOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/swap-pages.docx");
$options->setFirstPageNumber(2);
$options->setSecondPageNumber(4);
 
$request = new Requests\swapRequest($options);       
$response = $pagesApi->swap($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
pagesApi = GroupDocsMergerCloud::PagesApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::SwapOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/four-pages.docx'
options.output_path = "Output/swap-pages.docx"
options.first_page_number = 2
options.second_page_number = 4
 
result = pagesApi.swap(GroupDocsMergerCloud::SwapRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.pagesApi = merger_cloud.PagesApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.SwapOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/four-pages.docx";  
options.outputPath = "Output/swap-pages.docx";
options.firstPageNumber = 2;
options.secondPageNumber = 4;
 
let result = await pagesApi.swap(new merger_cloud.SwapRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
pagesApi = groupdocs_merger_cloud.PagesApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.SwapOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/four-pages.docx")
options.output_path = "Output/swap-pages.docx"
options.first_page_number = 2
options.second_page_number = 4
 
result = pagesApi.swap(groupdocs_merger_cloud.SwapRequest(options))
```

{{< /tab >}} {{< /tabs >}}
