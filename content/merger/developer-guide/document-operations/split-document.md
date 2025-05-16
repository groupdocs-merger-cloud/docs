---
id: "split-document"
url: "merger/split-document"
title: "Split Document"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

## Split the Document Into Several One-Page Documents

GroupDocs.Merger Cloud REST API provides an ability to split the document into several one-page documents by providing exact page numbers.
The following example demonstrates how to split the document into three one-page documents with 3rd, 6th, and 8th pages. As a result, these documents will be produced:

|Document name|Page numbers
|---|---
|document_0|3
|document_1|6
|document_2|8

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

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

* Response will contain storage path to resultant document
{
  "path": "Output/joined.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

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
    /// This example demonstrates how to split the document to several one-page documents (by exact page numbers).
    /// </summary>
    public class SplitToSinglePages
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new DocumentApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
						FilePath = "WordProcessing/sample-10-pages.docx"
                };

                var options = new SplitOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/split-document",
                    Pages = new List<int?> { 1, 3 },
                    Mode = SplitOptions.ModeEnum.Pages
                };

                var request = new SplitRequest(options);
                var response = apiInstance.Split(request);

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
package examples.DocumentOperations.SplitDocument;

import java.util.Arrays;
import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to split the document to several one-page documents (by exact page numbers).
 */
public class Merger_Java_SplitToSinglePages {

	public static void main(String[] args) {		

		DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/sample-10-pages.docx");

			SplitOptions options = new SplitOptions();
			options.setFileInfo(fileInfo);
			options.setPages(Arrays.asList(1, 3));
			options.setOutputPath("output/split-document");
			options.setMode(SplitOptions.ModeEnum.PAGES);

			SplitRequest request = new SplitRequest(options);

			MultiDocumentResult response = apiInstance.split(request);

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
$fileInfo->setFilePath("WordProcessing/sample-10-pages.docx");         
 
$options = new Model\SplitOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/split-document");
$options->setPages([1, 3]);
$options->setMode(Model\SplitOptions::MODE_PAGES);
 
$request = new Requests\splitRequest($options);       
$response = $documentApi->split($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::SplitOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/sample-10-pages.docx'
options.output_path = "Output/split-document"
options.pages = [1, 3]
options.mode = "Pages"
 
result = documentApi.split(GroupDocsMergerCloud::SplitRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.documentApi = merger_cloud.DocumentApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.SplitOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/sample-10-pages.docx";  
options.outputPath = "Output/split-document";
options.pages = [1, 3];
options.mode = merger_cloud.SplitOptions.ModeEnum.Pages;
 
let result = await documentApi.split(new merger_cloud.SplitRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.SplitOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
options.output_path = "Output/split-document"
options.pages = [1, 3]
options.mode = "Pages"
 
result = documentApi.split(groupdocs_merger_cloud.SplitRequest(options))
```

{{< /tab >}} {{< /tabs >}}

## Split the Document Into Several One-Page Documents by Providing Exact Page Numbers

GroupDocs.Merger Cloud REST API provides an ability to split the document into several one-page documents by specifying only start/end page numbers.
The following example demonstrates how to split the document into several one-page documents starting from 3rd and ending at 7th-page number. As a result, these documents will be produced:

|Document name|Page numbers
|---|---
|document_0|3
|document_1|4
|document_2|5
|document_3|6
|document_4|7

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example3">}} {{< tab "Request" >}}

```bash

*Response will contain storage path to resultant documents
{
  "documents": [
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_0.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_1.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_2.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_3.docx"
    },
    {
      "path": "output/split-by-start-end-numbers\sample-10-pages_4.docx"
    }
  ]
}

```

{{< /tab >}} {{< tab "Response" >}}

```json
*Response will contain storage path to resultant document
{
  "path": "Output/joined.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check article to learn how to add an SDK to your project.

{{< tabs "example4">}} {{< tab "C#" >}}

```csharp
﻿using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to split the document to several one-page documents (by start/end page numbers).
    /// </summary>
    public class SplitToSinglePagesByRange
    {
            public static void Run()
            {
                var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
                var apiInstance = new DocumentApi(configuration);

                try
                {
                    var fileInfo = new FileInfo
                    {
                        FilePath = "WordProcessing/sample-10-pages.docx"
                    };

                    var options = new SplitOptions
                    {
                        FileInfo = fileInfo,
                        OutputPath = "Output/split-by-start-end-numbers",
                        StartPageNumber = 3,
                        EndPageNumber = 7,
                        Mode = SplitOptions.ModeEnum.Pages
                    };

                    var request = new SplitRequest(options);
                    var response = apiInstance.Split(request);

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
package examples.DocumentOperations.SplitDocument;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to split the document to several one-page documents (by start/end page numbers).
 */
public class Merger_Java_SplitToSinglePagesByRange {

	public static void main(String[] args) {		

		DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/sample-10-pages.docx");

			SplitOptions options = new SplitOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/split-by-start-end-numbers");
			options.setStartPageNumber(3);
			options.setEndPageNumber(7);
			options.setMode(SplitOptions.ModeEnum.PAGES);

			SplitRequest request = new SplitRequest(options);

			MultiDocumentResult response = apiInstance.split(request);

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
﻿// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-php-samples
$AppSid = 'XXXX-XXXX-XXXX-XXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$AppKey = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
$configuration = new GroupDocs\Merger\Configuration();
$configuration->setAppSid(CommonUtils::$AppSid);
$configuration->setAppKey(CommonUtils::$AppKey);
 
$documentApi = GroupDocs\Merger\DocumentApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/sample-10-pages.docx");         
 
$options = new Model\SplitOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/split-by-start-end-numbers");
$options->setStartPageNumber(3);
$options->setEndPageNumber(7);
$options->setMode(Model\SplitOptions::MODE_PAGES);
 
$request = new Requests\splitRequest($options);       
$response = $documentApi->split($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
﻿# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::SplitOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/sample-10-pages.docx'
options.output_path = "Output/split-by-start-end-numbers"
options.start_page_number = 3
options.end_page_number = 7
options.mode = "Pages"
 
result = documentApi.split(GroupDocsMergerCloud::SplitRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
﻿// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.documentApi = merger_cloud.DocumentApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.SplitOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/sample-10-pages.docx";  
options.outputPath = "Output/split-by-start-end-numbers";
options.startPageNumber = 3;
options.endPageNumber = 7;
options.mode = merger_cloud.SplitOptions.ModeEnum.Pages;
 
let result = await documentApi.split(new merger_cloud.SplitRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
﻿# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.SplitOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
options.output_path = "Output/split-by-start-end-numbers"
options.start_page_number = 3
options.end_page_number = 7
options.mode = "Pages"
 
result = documentApi.split(groupdocs_merger_cloud.SplitRequest(options))
```

{{< /tab >}} {{< /tabs >}}

## Split the Document Into Several One-Page Documents by Applying Filter

GroupDocs.Merger Cloud REST API provides an ability to filter even/odd pages while splitting the document into several one-page documents by specifying only start/end page numbers
The following example demonstrates how to document several one-page documents for odd pages starting from 3rd and ending at 7th-page number. As a result, these documents will be produced:

|Document name
|---
|Page numbers
|document_0|3
|document_1|5
|document_2|7

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example5">}} {{< tab "Request" >}}

```bash

* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join pages from several documents into one document
curl -v "https://api.groupdocs.cloud/v1.0/merger/split" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
   'FileInfo': { 'FilePath': 'WordProcessing/sample-10-pages.docx' },
   'StartPageNumber':  3,
   'EndPageNumber' : 7,
   'RangeMode' : 1,
      'Mode': 'Pages',
      'OutputPath': 'output/split-by-start-end-numbers-with-filter'
 }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant documents
{
  "documents": [
    {
      "path": "output/split-by-start-end-numbers-with-filter\sample-10-pages_0.docx"
    },
    {
      "path": "output/split-by-start-end-numbers-with-filter\sample-10-pages_1.docx"
    },
    {
      "path": "output/split-by-start-end-numbers-with-filter\sample-10-pages_2.docx"
    }
  ]
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

{{< tabs "example6">}} {{< tab "C#" >}}

```csharp
﻿using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to split the document to several one-page documents (by start/end page numbers and even/odd filter).
    /// </summary>
    public class SplitToSinglePagesByRangeWithFilter
    {
            public static void Run()
            {
                var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
                var apiInstance = new DocumentApi(configuration);

                try
                {
                    var fileInfo = new FileInfo
                    {
                        FilePath = "WordProcessing/sample-10-pages.docx"
                    };

                    var options = new SplitOptions
                    {
                        FileInfo = fileInfo,
                        OutputPath = "Output/split-by-start-end-numbers-with-filter",
                        StartPageNumber = 3,
                        EndPageNumber = 7,
                        RangeMode = PageOptions.RangeModeEnum.OddPages,
                        Mode = SplitOptions.ModeEnum.Pages
                    };

                    var request = new SplitRequest(options);
                    var response = apiInstance.Split(request);

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
package examples.DocumentOperations.SplitDocument;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to split the document to several one-page documents (by start/end page numbers and even/odd filter).
 */
public class Merger_Java_SplitToSinglePagesByRangeWithFilter {

	public static void main(String[] args) {		

		DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/sample-10-pages.docx");

			SplitOptions options = new SplitOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/split-by-start-end-numbers-with-filter");
			options.setStartPageNumber(3);
			options.setEndPageNumber(7);
			options.setRangeMode(PageOptions.RangeModeEnum.ODDPAGES);
			options.setMode(SplitOptions.ModeEnum.PAGES);

			SplitRequest request = new SplitRequest(options);

			MultiDocumentResult response = apiInstance.split(request);

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
﻿// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-php-samples
$AppSid = 'XXXX-XXXX-XXXX-XXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$AppKey = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
$configuration = new GroupDocs\Merger\Configuration();
$configuration->setAppSid(CommonUtils::$AppSid);
$configuration->setAppKey(CommonUtils::$AppKey);
 
$documentApi = GroupDocs\Merger\DocumentApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/sample-10-pages.docx");         
 
$options = new Model\SplitOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/split-by-start-end-numbers-with-filter");
$options->setStartPageNumber(3);
$options->setEndPageNumber(7);
$options->setRangeMode(Model\SplitOptions::RANGE_MODE_ODD_PAGES);
$options->setMode(Model\SplitOptions::MODE_PAGES);
 
$request = new Requests\splitRequest($options);       
$response = $documentApi->split($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
﻿# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::SplitOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/sample-10-pages.docx'
options.output_path = "Output/split-by-start-end-numbers-with-filter"
options.start_page_number = 3
options.end_page_number = 7
options.range_mode = "OddPages"
options.mode = "Intervals"
 
result = documentApi.split(GroupDocsMergerCloud::SplitRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
﻿// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.documentApi = merger_cloud.DocumentApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.SplitOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/sample-10-pages.docx";  
options.outputPath = "Output/split-by-start-end-numbers-with-filter";
options.startPageNumber = 3;
options.endPageNumber = 7;
options.rangeMode = merger_cloud.SplitOptions.RangeModeEnum.OddPages;
options.mode = merger_cloud.SplitOptions.ModeEnum.Pages;
 
let result = await documentApi.split(new merger_cloud.SplitRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
﻿# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.SplitOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
options.output_path = "Output/split-by-start-end-numbers-with-filter"
options.start_page_number = 3
options.end_page_number = 7
options.range_mode = "OddPages"
options.mode = "Pages"
 
result = documentApi.split(groupdocs_merger_cloud.SplitRequest(options))
```

{{< /tab >}} {{< /tabs >}}

## Split the Document to Several Multi-Page Documents

GroupDocs.Merger Cloud REST API provides an ability to split the document into several one-page documents by providing exact page numbers.
The following example demonstrates how to split the document into three one-page documents with 3rd, 6th, and 8th pages. As a result, these documents will be produced:

|Document name|Page numbers
|---|---
|document_0|1, 2
|document_1|3, 4, 5
|document_2|6, 7
|document_3|8, 9, 10

### Resource URI

```html

HTTP POST ~/join

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Join) lets you call this REST API directly from the browser.

### cURL example

{{< tabs "example7">}} {{< tab "Request" >}}

```bash

* First get JSON Web Token
* Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications. Kindly place Client Id in "client_id" and Client Secret in "client_secret" argument.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

* cURL example to join pages from several documents into one document
curl -v "https://api.groupdocs.cloud/v1.0/merger/split" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{
   'FileInfo': { 'FilePath': 'WordProcessing/sample-10-pages.docx' },
    'Pages': [ 3, 6, 8 ],
    'Mode': 1,
    'OutputPath': '/output/split-to-multipage-document'
 }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

*Response will contain storage path to resultant documents

{
  "documents": [
    {
      "path": "output/split-to-multipage-document\sample-10-pages_0.docx"
    },
    {
      "path": "output/split-to-multipage-document\sample-10-pages_1.docx"
    },
    {
      "path": "output/split-to-multipage-document\sample-10-pages_2.docx"
    },
 {
      "path": "output/split-to-multipage-document\sample-10-pages_3.docx"
    }
  ]
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check  article to learn how to add an SDK to your project.

{{< tabs "example8">}} {{< tab "C#" >}}

```csharp
﻿using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using System.Collections.Generic;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to split the document to several multi-page documents by specified page ranges.
    /// </summary>
    public class SplitToMultiPageDocuments
    {
        public static void Run()
        {
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new DocumentApi(configuration);

            try
            {
                var fileInfo = new FileInfo
                {
                    FilePath = "WordProcessing/sample-10-pages.docx"
                };

                var options = new SplitOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "Output/split-to-multipage-document",
                    Pages = new List<int?> { 3, 6, 8 },
                    Mode = SplitOptions.ModeEnum.Intervals
                };

                var request = new SplitRequest(options);
                var response = apiInstance.Split(request);

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
package examples.DocumentOperations.SplitDocument;

import java.util.Arrays;
import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to split the document to several multi-page documents by specified page ranges.
 */
public class Merger_Java_SplitToMultiPageDocuments {

	public static void main(String[] args) {		

		DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/sample-10-pages.docx");

			SplitOptions options = new SplitOptions();
			options.setFileInfo(fileInfo);
			options.setPages(Arrays.asList(3, 6, 8));
			options.setOutputPath("output/split-to-multipage-document");
			options.setMode(SplitOptions.ModeEnum.INTERVALS);

			SplitRequest request = new SplitRequest(options);

			MultiDocumentResult response = apiInstance.split(request);

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
﻿// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-php-samples
$AppSid = 'XXXX-XXXX-XXXX-XXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$AppKey = 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
$configuration = new GroupDocs\Merger\Configuration();
$configuration->setAppSid(CommonUtils::$AppSid);
$configuration->setAppKey(CommonUtils::$AppKey);
 
$documentApi = GroupDocs\Merger\DocumentApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/sample-10-pages.docx");         
 
$options = new Model\SplitOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/split-to-multipage-document");
$options->setPages([3, 6, 8]);
$options->setMode(Model\SplitOptions::MODE_INTERVALS);
 
$request = new Requests\splitRequest($options);       
$response = $documentApi->split($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
﻿# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::SplitOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/sample-10-pages.docx'
options.output_path = "Output/split-to-multipage-document"
options.pages = [3, 6, 8]
options.mode = "Intervals"
 
result = documentApi.split(GroupDocsMergerCloud::SplitRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
﻿// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.documentApi = merger_cloud.DocumentApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.SplitOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/sample-10-pages.docx";  
options.outputPath = "Output/split-to-multipage-document";
options.pages = [3, 6, 8];
options.mode = merger_cloud.SplitOptions.ModeEnum.Intervals;
 
let result = await documentApi.split(new merger_cloud.SplitRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
﻿# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.SplitOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
options.output_path = "Output/split-to-multipage-document"
options.pages = [3, 6, 8]
options.mode = "Intervals"
 
result = documentApi.split(groupdocs_merger_cloud.SplitRequest(options))
```

{{< /tab >}} {{< /tabs >}}
