---
id: "get-document-information"
url: "merger/get-document-information"
title: "Get Document Information"
productName: "GroupDocs.Merger Cloud"
weight: 2
description: ""
keywords: ""
toc: True
---

This REST API allows us to obtain basic information about the document and it's pages properties. The endpoint accepts the document storage path as input payload.
Here is the list of properties that can be obtained for a document:

* Document file extension;
* Document size in bytes;
* Document file format.

Here is the list of properties that can be obtained for document pages:

* Page width in pixels (when converted to the image);
* Page height in pixels (when converted to image);
* Page number;
* Visible property that indicates whether the page is visible or not.

## Resource URI

```html

HTTP POST ~/info

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Info/GetInfo) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/info" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer
<jwt token>"
-d "{ FilePath: '/wordprocessing/four-pages.docx' }"

```

{{< /tab >}} {{< tab "Response" >}}

```json
 {
  "extension": ".docx",
  "pages": [
   {
    "width": 612,
   "height": 792,
   "pageNumber": 1,
   "visible": true
   },
   {
   "width": 612,
   "height": 792,
    "pageNumber": 2,
    "visible": true
   },
   {
    "width": 612,
   "height": 792,
   "pageNumber": 3,
   "visible": true
   },
   {
   "width": 612,
    "height": 792,
   "pageNumber": 4,
   "visible": true
   }],
 "size": 8651,
 "fileFormat": "Microsoft Word Open XML Document"
}
```

{{< /tab >}} {{< /tabs >}}

## SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the [Get Document Information](https://apireference.groupdocs.cloud/merger/#/Info/GetInfo) article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

```csharp
using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to get document info.
    /// </summary>
    public class GetDocumentInformation
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new InfoApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
						FilePath = "WordProcessing/password-protected.docx",
						Password = "password",
						StorageName = Common.MyStorage
					};

				var request = new GetInfoRequest(fileInfo);

				var response = apiInstance.GetInfo(request);
				Console.WriteLine("InfoResult.Pages.Count: " + response.Pages.Count);
			}
			catch (Exception e)
			{
				Console.WriteLine("Exception while calling InfoApi: " + e.Message);
			}
		}
	}
}
```

{{< /tab >}} {{< tab "Java" >}}

```java
package examples;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to get document info.
 */
public class Merger_Java_GetDocumentInformation {

	public static void main(String[] args) {

		InfoApi apiInstance = new InfoApi(Utils.GetConfiguration());
		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/password-protected.docx");
			fileInfo.setPassword("password");

			GetInfoRequest request = new GetInfoRequest(fileInfo);

			InfoResult response = apiInstance.getInfo(request);

			System.err.println("InfoResult.Pages.Count: " + response.getPages().size());
		} catch (ApiException e) {
			System.err.println("Exception while calling InfoApi:");
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
 
$infoApi = GroupDocs\Merger\InfoApi($configuration);
  
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/password-protected.docx");
$fileInfo->setPassword("password");
 
$response = $infoApi->getInfo(new Requests\getInfoRequest($fileInfo));
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
infoApi = GroupDocsMergerCloud::InfoApi.from_keys($app_sid, $app_key)
fileInfo = GroupDocsMergerCloud::FileInfo.new
fileInfo.file_path = 'WordProcessing/password-protected.docx'
fileInfo.password = 'password'
request = GroupDocsMergerCloud::GetInfoRequest.new(fileInfo)
response = infoApi.get_info(request)
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.infoApi = merger_cloud.InfoApi.fromKeys(appSid, appKey);
 
let fileInfo = new merger_cloud.FileInfo();
fileInfo.filePath = "WordProcessing/password-protected.docx";
fileInfo.password = "password";
fileInfo.storageName = myStorage;
let request = new merger_cloud.GetInfoRequest(fileInfo);
let response = await infoApi.getInfo(request);
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
infoApi = groupdocs_merger_cloud.InfoApi.from_keys(app_sid, app_key)
 
fileInfo = groupdocs_merger_cloud.FileInfo("WordProcessing/password-protected.docx", None, None, "password")
result = infoApi.get_info(groupdocs_merger_cloud.GetInfoRequest(fileInfo))
```

{{< /tab >}} {{< /tabs >}}
