---
id: "move-pages"
url: "merger/move-pages"
title: "Move Pages"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

This REST API provides a move page feature that allows you to manipulate page ordering by moving any page(s) to a new position within a document.
For moving page to a new position, it's needed to specify current and new page numbers along with the path to document in storage. For protected documents, it is also required to provide a password.
The table below contains the full list of properties that can be specified while moving document pages.

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|PageNumber|Page number to move|Required
|NewPageNumber|New page number|Required
|OutputPath|Path to resultant document|Required

## Resource URI

```html

HTTP GET ~/Pages/Move

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Move) lets you call this REST API directly from the browser.

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
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/move" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
  'FileInfo': { 'FilePath': 'words/four-pages.docx'},
     'PageNumber':  1,
     'NewPageNumber':  2,
     'OutputPath': 'output/move-page.docx'
 }"
```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant document
{
  "path": "output/move-page.docx"
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
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to move document page to a new position.
    /// </summary>
    public class MovePage
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

                var options = new MoveOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/move-pages.docx",
                    PageNumber = 1,
                    NewPageNumber = 2
                };
                var request = new MoveRequest(options);

                var response = apiInstance.Move(request);

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
 * This example demonstrates how to move document page to a new position.
 */
public class Merger_Java_MovePage {

	public static void main(String[] args) {		

		PagesApi apiInstance = new PagesApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/four-pages.docx");

			MoveOptions options = new MoveOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/move-pages.docx");
			options.setPageNumber(1);
			options.setNewPageNumber(2);

			MoveRequest request = new MoveRequest(options);

			DocumentResult response = apiInstance.move(request);

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
 
$options = new Model\MoveOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/move-pages.docx");
$options->setPageNumber(1);
$options->setNewPageNumber(2);        
 
$request = new Requests\moveRequest($options);       
$response = $pagesApi->move($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to move document page to a new position.
    /// </summary>
    public class MovePage
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

                var options = new MoveOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/move-pages.docx",
                    PageNumber = 1,
                    NewPageNumber = 2
                };
                var request = new MoveRequest(options);

                var response = apiInstance.Move(request);

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

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.pagesApi = merger_cloud.PagesApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.MoveOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/four-pages.docx";  
options.outputPath = "Output/move-pages.docx";
options.pageNumber = 1;
options.newPageNumber = 2;
 
let result = await pagesApi.move(new merger_cloud.MoveRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
pagesApi = groupdocs_merger_cloud.PagesApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.MoveOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/four-pages.docx")
options.output_path = "Output/move-pages.docx"
options.page_number = 1
options.new_page_number = 2       
 
result = pagesApi.move(groupdocs_merger_cloud.MoveRequest(options))
```

{{< /tab >}} {{< /tabs >}}
