---
id: "mix-document-pages"
url: "merger/mix-document-pages"
title: "Mix Document Pages"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
toc: True
---

This REST API allows mixing specific pages from several source documents into a single resultant document. You can specify the exact order and selection of pages from each document, enabling advanced document composition scenarios.

To mix pages, provide:

* A list of source documents (`Files` collection).
* A list of page selections (`FilesPages` collection), where each item specifies which pages to take from which document and in what order.
* The output path for the resultant document.

For password-protected documents, supply the password in the `FileInfo` object.

The table below describes the main properties for the Mix operation:

| Name           | Description                                                         | Comment
|----------------|---------------------------------------------------------------------|---
| Files          | List of files to mix                                                | Required
| FilesPages     | List of page selections, each with file index and page numbers      | Required
| OutputPath     | Path to resultant document                                          | Required
| WordJoinMode   | Join mode for Word documents                                        | Optional, default is `Default`
| WordJoinCompliance | Compliance mode for Word OOXML format                        | Optional, default is `Auto`
| ImageJoinMode  | Join mode for images                                                | Optional

## Resource URI

```html
HTTP POST ~/mix
```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Document/Mix) lets you call this REST API directly from the browser.

## cURL example

{{< tabs "example1">}} {{< tab "Request" >}}

```bash
# First get JSON Web Token
# Please get your Client Id and Client Secret from https://dashboard.groupdocs.cloud/applications.
curl -v "https://api.groupdocs.cloud/connect/token" \
-X POST \
-d "grant_type=client_credentials&client_id=xxxx&client_secret=xxxx" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Accept: application/json"

# cURL example to mix pages from several documents into one document
curl -v "https://api.groupdocs.cloud/v1.0/merger/mix" \
-X POST \
-H "Content-Type: application/json" \
-H "Accept: application/json" \
-H "Authorization: Bearer <jwt token>" \
-d "{
    'Files': [
        { 'FilePath': 'WordProcessing/sample-10-pages.docx' },
        { 'FilePath': 'WordProcessing/four-pages.docx' }
    ],
    'FilesPages': [
        { 'FileIndex': 0, 'Pages': [1, 2] },
        { 'FileIndex': 1, 'Pages': [1, 2] },
        { 'FileIndex': 0, 'Pages': [3, 4] }
    ],
    'OutputPath': 'Output/mixed-pages.docx'
}"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "path": "Output/mixed-pages.docx"
}
```

{{< /tab >}} {{< /tabs >}}

## SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of making requests and handling responses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check the article to learn how to add an SDK to your project.

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
    /// This example demonstrates how to mix specific pages from several source documents.
    /// </summary>
    public class MixPages
    {
        public static void Run()
        {
            var configuration = Common.GetConfig();
            var apiInstance = new DocumentApi(configuration);

            var options = new MixPagesOptions
            {
                Files = new List<FileInfo> {
                    new() { FilePath = "WordProcessing/sample-10-pages.docx" },
                    new() { FilePath = "WordProcessing/four-pages.docx" }
                },
                FilesPages = new List<MixPagesItem>
                {
                    new() { FileIndex = 0, Pages = new List<int?> { 1, 2 } },
                    new() { FileIndex = 1, Pages = new List<int?> { 1, 2 } },
                    new() { FileIndex = 0, Pages = new List<int?> { 3, 4 } },
                },
                OutputPath = "Output/mixed-pages.docx"
            };

            var request = new MixRequest(options);
            var response = apiInstance.Mix(request);

            Console.WriteLine("Output file path: " + response.Path);
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
 * This example demonstrates how to mix specific pages from several source documents.
 */
public class Merger_Java_MixPages {

    public static void main(String[] args) {        

        DocumentApi apiInstance = new DocumentApi(Utils.GetConfiguration());

        MixPagesOptions options = new MixPagesOptions();
        options.setFiles(Arrays.asList(
            new FileInfo().setFilePath("WordProcessing/sample-10-pages.docx"),
            new FileInfo().setFilePath("WordProcessing/four-pages.docx")
        ));
        options.setFilesPages(Arrays.asList(
            new MixPagesItem().setFileIndex(0).setPages(Arrays.asList(1, 2)),
            new MixPagesItem().setFileIndex(1).setPages(Arrays.asList(1, 2)),
            new MixPagesItem().setFileIndex(0).setPages(Arrays.asList(3, 4))
        ));
        options.setOutputPath("Output/mixed-pages.docx");

        MixRequest request = new MixRequest(options);

        DocumentResult response = apiInstance.mix(request);

        System.out.println("Output file path: " + response.getPath());
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

$documentApi = new GroupDocs\Merger\DocumentApi($configuration);

$fileInfo1 = new Model\FileInfo();
$fileInfo1->setFilePath("WordProcessing/sample-10-pages.docx");
$fileInfo2 = new Model\FileInfo();
$fileInfo2->setFilePath("WordProcessing/four-pages.docx");

$item1 = new Model\MixPagesItem();
$item1->setFileIndex(0);
$item1->setPages([1, 2]);
$item2 = new Model\MixPagesItem();
$item2->setFileIndex(1);
$item2->setPages([1, 2]);
$item3 = new Model\MixPagesItem();
$item3->setFileIndex(0);
$item3->setPages([3, 4]);

$options = new Model\MixPagesOptions();
$options->setFiles([$fileInfo1, $fileInfo2]);
$options->setFilesPages([$item1, $item2, $item3]);
$options->setOutputPath("Output/mixed-pages.docx");

$request = new Requests\MixRequest($options);
$response = $documentApi->mix($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud

documentApi = GroupDocsMergerCloud::DocumentApi.from_keys($app_sid, $app_key)

file1 = GroupDocsMergerCloud::FileInfo.new
file1.file_path = 'WordProcessing/sample-10-pages.docx'
file2 = GroupDocsMergerCloud::FileInfo.new
file2.file_path = 'WordProcessing/four-pages.docx'

item1 = GroupDocsMergerCloud::MixPagesItem.new
item1.file_index = 0
item1.pages = [1, 2]
item2 = GroupDocsMergerCloud::MixPagesItem.new
item2.file_index = 1
item2.pages = [1, 2]
item3 = GroupDocsMergerCloud::MixPagesItem.new
item3.file_index = 0
item3.pages = [3, 4]

options = GroupDocsMergerCloud::MixPagesOptions.new
options.files = [file1, file2]
options.files_pages = [item1, item2, item3]
options.output_path = "Output/mixed-pages.docx"

result = documentApi.mix(GroupDocsMergerCloud::MixRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud

global.documentApi = merger_cloud.DocumentApi.fromKeys(appSid, appKey);

let file1 = new merger_cloud.FileInfo();
file1.filePath = "WordProcessing/sample-10-pages.docx";
let file2 = new merger_cloud.FileInfo();
file2.filePath = "WordProcessing/four-pages.docx";

let item1 = new merger_cloud.MixPagesItem();
item1.fileIndex = 0;
item1.pages = [1, 2];
let item2 = new merger_cloud.MixPagesItem();
item2.fileIndex = 1;
item2.pages = [1, 2];
let item3 = new merger_cloud.MixPagesItem();
item3.fileIndex = 0;
item3.pages = [3, 4];

let options = new merger_cloud.MixPagesOptions();
options.files = [file1, file2];
options.filesPages = [item1, item2, item3];
options.outputPath = "Output/mixed-pages.docx";

let result = await documentApi.mix(new merger_cloud.MixRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud

documentApi = groupdocs_merger_cloud.DocumentApi.from_keys(app_sid, app_key)

file1 = groupdocs_merger_cloud.FileInfo("WordProcessing/sample-10-pages.docx")
file2 = groupdocs_merger_cloud.FileInfo("WordProcessing/four-pages.docx")

item1 = groupdocs_merger_cloud.MixPagesItem()
item1.file_index = 0
item1.pages = [1, 2]
item2 = groupdocs_merger_cloud.MixPagesItem()
item2.file_index = 1
item2.pages = [1, 2]
item3 = groupdocs_merger_cloud.MixPagesItem()
item3.file_index = 0
item3.pages = [3, 4]

options = groupdocs_merger_cloud.MixPagesOptions()
options.files = [file1, file2]
options.files_pages = [item1, item2, item3]
options.output_path = "Output/mixed-pages.docx"

result = documentApi.mix(groupdocs_merger_cloud.MixRequest(options))
```

{{< /tab >}} {{< /tabs >}}