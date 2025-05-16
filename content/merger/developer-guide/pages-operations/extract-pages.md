---
id: "extract-pages"
url: "merger/extract-pages"
title: "Extract Pages"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

## Extract Pages by Exact Page Numbers

This REST API allows extracting pages from source documents by providing exact page numbers via Pages collection. The result is a new document that contains only specified pages from a source document. For protected documents, it is also required to provide a password.

The following example demonstrates how to extract pages 2,4,7 from a source document into a new document.

### Resource URI

```html

HTTP POST ~/Pages/Extract

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Extract) lets you call this REST API directly from the browser.

### cURL example

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
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/extract" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
     'FileInfo': { 'FilePath': '/WordProcessing/sample-10-pages.docx'},
     'Pages':  [ 2, 4, 7 ],
     'OutputPath': 'output/extract-pages-by-numbers.docx'
 }"
```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant document
{
  "path": "output/extract-pages-by-numbers.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

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
    /// This example demonstrates how to extract document pages by specifying their numbers.
    /// </summary>
    public class ExtractPagesByNumbers
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new PagesApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
						FilePath = "WordProcessing/sample-10-pages.docx"
                };

                var options = new ExtractOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/extract-pages-by-numbers.docx",
                    Pages = new List<int?> { 2, 4, 7 }
                };
                var request = new ExtractRequest(options);

                var response = apiInstance.Extract(request);

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
package examples.PagesOperations.ExtractPages;

import java.util.Arrays;
import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to extract document pages by specifying their numbers.
 */
public class Merger_Java_ExtractPagesByNumbers {

	public static void main(String[] args) {		

		PagesApi apiInstance = new PagesApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/sample-10-pages.docx");

			ExtractOptions options = new ExtractOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/extract-pages-by-numbers.docx");
			options.setPages(Arrays.asList(2, 4, 7));			

			ExtractRequest request = new ExtractRequest(options);

			DocumentResult response = apiInstance.extract(request);

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
$fileInfo->setFilePath("WordProcessing/sample-10-pages.docx");         
 
$options = new Model\ExtractOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/extract-pages-by-numbers.docx");
$options->setPages([2, 4, 7]);
 
$request = new Requests\extractRequest($options);       
$response = $pagesApi->extract($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
pagesApi = GroupDocsMergerCloud::PagesApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::ExtractOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/sample-10-pages.docx'
options.output_path = "Output/extract-pages-by-numbers.docx"
options.pages = [2, 4, 7]
 
result = pagesApi.extract(GroupDocsMergerCloud::ExtractRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.pagesApi = merger_cloud.PagesApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.ExtractOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/sample-10-pages.docx";  
options.outputPath = "Output/extract-pages-by-numbers.docx";
options.pages = [2, 4, 7];
 
let result = await pagesApi.extract(new merger_cloud.ExtractRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
pagesApi = groupdocs_merger_cloud.PagesApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.ExtractOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
options.output_path = "Output/extract-pages-by-numbers.docx"
options.pages = [2, 4, 7]        
 
result = pagesApi.extract(groupdocs_merger_cloud.ExtractRequest(options))
```

{{< /tab >}} {{< /tabs >}}

## Extract Pages by Exact Page Number Range

This REST API allows extracting pages from source documents by providing only start/end page numbers of the desired page range. There is also an ability to get only even/odd pages from the specified page range by setting RangeMode property.
The result is a new document that contains only specified pages from a source document. For protected documents, it is also required to provide a password.
The following example demonstrates how to extract even pages from a document in a range from 1st to 10th page.
The resultant document will contain pages 2, 4, 6, 8, 10 from the source document.

### Resource URI

```html

HTTP POST ~/Pages/Extract

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Pages/Extract) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example3">}} {{< tab "Request" >}}

```bash

* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join several documents into one
curl -v "https://api.groupdocs.cloud/v1.0/merger/pages/extract" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>" \
-d "{
     'FileInfo': { 'FilePath': '/WordProcessing/sample-10-pages.docx'},
  'StartPageNumber': 1,
  'EndPageNumber': 10,
        'RangeMode': 'EvenPages',
     'OutputPath': 'output/extract-pages-by-range.docx'
 }"
```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant document
{
  "path": "output/extract-pages-by-range.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example4">}} {{< tab "C#" >}}

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
    /// This example demonstrates how to extract document pages by specifying page numbers range.
    /// </summary>
    public class ExtractPagesByRange
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new PagesApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
						FilePath = "WordProcessing/sample-10-pages.docx"
                };

                var options = new ExtractOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/extract-pages-by-range.docx",
                    StartPageNumber = 1,
                    EndPageNumber = 10,
                    RangeMode = PageOptions.RangeModeEnum.EvenPages 
                };
                var request = new ExtractRequest(options);

                var response = apiInstance.Extract(request);

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
package examples.PagesOperations.ExtractPages;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to extract document pages by specifying page numbers range.
 */
public class Merger_Java_ExtractPagesByRange {

	public static void main(String[] args) {		

		PagesApi apiInstance = new PagesApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/sample-10-pages.docx");

			ExtractOptions options = new ExtractOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/extract-pages-by-range.docx");
			options.setStartPageNumber(1);
			options.setEndPageNumber(10);
			options.setRangeMode(PageOptions.RangeModeEnum.EVENPAGES);

			ExtractRequest request = new ExtractRequest(options);

			DocumentResult response = apiInstance.extract(request);

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
$fileInfo->setFilePath("WordProcessing/sample-10-pages.docx");         
 
$options = new Model\ExtractOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/extract-pages-by-range.docx");
$options->setStartPageNumber(1);
$options->setEndPageNumber(10);
$options->setRangeMode(Model\ExtractOptions::RANGE_MODE_EVEN_PAGES);
 
$request = new Requests\extractRequest($options);       
$response = $pagesApi->extract($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
pagesApi = GroupDocsMergerCloud::PagesApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::ExtractOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/sample-10-pages.docx'
options.output_path = "Output/extract-pages-by-range.docx"
options.start_page_number = 1
options.end_page_number = 10
options.range_mode = "EvenPages"
 
result = pagesApi.extract(GroupDocsMergerCloud::ExtractRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.pagesApi = merger_cloud.PagesApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.ExtractOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/sample-10-pages.docx";  
options.outputPath = "Output/extract-pages-by-range.docx";
options.startPageNumber = 1;
options.endPageNumber = 10;
options.rangeMode = merger_cloud.ExtractOptions.RangeModeEnum.EvenPages;
 
let result = await pagesApi.extract(new merger_cloud.ExtractRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
pagesApi = groupdocs_merger_cloud.PagesApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.ExtractOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
options.output_path = "Output/extract-pages-by-range.docx"
options.start_page_number = 1
options.end_page_number = 10
options.range_mode = "EvenPages"     
 
result = pagesApi.extract(groupdocs_merger_cloud.ExtractRequest(options))
```

{{< /tab >}} {{< /tabs >}}
