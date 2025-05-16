---
id: "remove-pages"
url: "merger/remove-pages"
title: "Remove Pages"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

This REST API provides an ability to remove a single page or a collection of specific page numbers from the source document.
There are several ways to specify page numbers to be removed from a document:

* Provide exact page numbers via Pages collection;
* Specify pages range start/end page numbers. There is also an ability to get only even/odd pages from the specified page range by setting RangeMode property.

For protected documents, it is also required to provide a password.

The table below contains the full list of properties that can be specified when removing pages from a document:

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

HTTP POST ~/pages/remove

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Remove) lets you call this REST API directly from the browser.

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
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/remove" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
     'FileInfo': { 'FilePath': '/WordProcessing/four-pages.docx'},
     'Pages':  [ 2, 4 ],
     'OutputPath': 'output/remove-pages.docx'
 }"
```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant document
{
  "path": "output/remove-pages.docx"
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
    /// This example demonstrates how to remove document pages.
    /// </summary>
    public class RemovePages
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

                var options = new RemoveOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/remove-pages.docx",
                    Pages = new List<int?> { 2, 4 }
                };
                var request = new RemoveRequest(options);

                var response = apiInstance.Remove(request);

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

import java.util.Arrays;
import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to remove document pages.
 */
public class Merger_Java_RemovePages {

	public static void main(String[] args) {		

		PagesApi apiInstance = new PagesApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/four-pages.docx");

			RemoveOptions options = new RemoveOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/remove-pages.docx");
			options.setPages(Arrays.asList(2, 4));

			RemoveRequest request = new RemoveRequest(options);

			DocumentResult response = apiInstance.remove(request);

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
 
$options = new Model\RemoveOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/remove-pages.docx");
$options->setPages([2, 4]);        
 
$request = new Requests\removeRequest($options);       
$response = $pagesApi->remove($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
pagesApi = GroupDocsMergerCloud::PagesApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::RemoveOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/four-pages.docx'
options.output_path = "Output/remove-pages.docx"
options.pages = [2, 4]
 
result = pagesApi.remove(GroupDocsMergerCloud::RemoveRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.pagesApi = merger_cloud.PagesApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.RemoveOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/four-pages.docx";  
options.outputPath = "Output/remove-pages.docx";
options.pages = [2, 4];
 
let result = await pagesApi.remove(new merger_cloud.RemoveRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
pagesApi = groupdocs_merger_cloud.PagesApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.RemoveOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/four-pages.docx")
options.output_path = "Output/remove-pages.docx"
options.pages = [2, 4]
 
result = pagesApi.remove(groupdocs_merger_cloud.RemoveRequest(options))
```

{{< /tab >}} {{< /tabs >}}
