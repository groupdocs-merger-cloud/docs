---
id: "generate-document-pages-preview"
url: "merger/generate-document-pages-preview"
title: "Generate Document Pages Preview"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

This REST API provides an ability to generate document pages of image representations.
There are several ways to specify page numbers needed for preview:

* Provide exact page numbers via Pages collection;
* Specify pages range start/end page numbers. There is also an ability to get only even/odd pages from the specified page range by setting RangeMode property.

For protected documents, it is also required to provide a password.
The following properties of preview may be customized:

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
|Width|Image width in pixels|Optional
|Height|Image height in pixels|Optional
|Format|Image format - JPG, PNG, BMP|The default value is JPG
|OutputPath|Path format to resultant images|Required

## Resource URI

```html

HTTP POST ~/preview

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Preview) lets you call this REST API directly from the browser.

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
curl -v "https://api.groupdocs.cloud/v1.0/merger/preview" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
    'FileInfo': { 'FilePath': 'WordProcessing/four-pages.docx' },
  'OutputPath': '/Output/preview-page',
  'Pages': [1, 3],
  Format: 'Png'
 }"

```

{{< /tab >}} {{< tab "Response" >}}

```json
//Response will contain storage path to resultant documents
{
  'documents': [
    {
      'path': '\Output\page_1.png'
    },
    {
      'path': '\preview\page_3.png'
    }
  ]
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
    /// This example demonstrates how to generate document pages preview.
    /// </summary>
    public class PreviewDocument
	{
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new DocumentApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
						FilePath = "WordProcessing/four-pages.docx"
                };

                var options = new PreviewOptions()
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/preview-page",
                    Pages = new List<int?> { 1, 3 },
                    Format = PreviewOptions.FormatEnum.Png
                };

                var request = new PreviewRequest(options);
                var response = apiInstance.Preview(request);

                foreach (var document in response.Documents)
                {
                    Console.WriteLine("Output file path: " + document.Path);
                }
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
 * This example demonstrates how to generate document pages preview.
 */
public class Merger_Java_PreviewDocument {

	public static void main(String[] args) {		

		DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/four-pages.docx");

			PreviewOptions options = new PreviewOptions();
			options.setFileInfo(fileInfo);
			options.setPages(Arrays.asList(1, 3));
			options.setOutputPath("output/preview-page");
			options.setFormat(PreviewOptions.FormatEnum.PNG);

			PreviewRequest request = new PreviewRequest(options);

			MultiDocumentResult response = apiInstance.preview(request);

			for (DocumentResult documentResult : response.getDocuments()) {
				System.err.println("Output file path: " + documentResult.getPath());
			}			
		
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
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/four-pages.docx");         
 
$options = new Model\PreviewOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/preview-page");
$options->setPages([1, 3]);
$options->setFormat(Model\PreviewOptions::FORMAT_PNG);
 
$request = new Requests\previewRequest($options);       
$response = $documentApi->preview($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::PreviewOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/four-pages.docx'
options.output_path = "Output/preview-page"
options.pages = [1, 3]
options.format = "Png"
 
result = documentApi.preview(GroupDocsMergerCloud::PreviewRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.documentApi = merger_cloud.DocumentApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.PreviewOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/four-pages.docx";  
options.outputPath = "Output/preview-page";
options.pages = [1, 3];
options.format = merger_cloud.PreviewOptions.FormatEnum.Png;
 
let result = await documentApi.preview(new merger_cloud.PreviewRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.PreviewOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/four-pages.docx")
options.output_path = "Output/preview-page"
options.pages = [1, 3]
options.format = "Png"
 
result = documentApi.preview(groupdocs_merger_cloud.PreviewRequest(options))
```

{{< /tab >}} {{< /tabs >}}
