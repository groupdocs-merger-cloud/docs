---
id: "security-operations"
url: "merger/security-operations"
title: "Security Operations"
productName: "GroupDocs.Merger Cloud"
weight: 5
description: ""
keywords: ""
toc: True
---

## Add Document Password Protection

This REST API allows adding document password protection. API endpoint accepts document storage path as input payload and returns path to the created a password-protected document.

The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|Path to resultant document|Required

### Resource URI

```html

HTTP PUT ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/AddPassword) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password" \
-X PUT
-H "Authorization: Bearer
<jwt token>"
-d "{
        'FileInfo': { 'FilePath': 'words/four-pages.docx'},
        'Password':  'Password',
        'OutputPath': 'output/add-password.docx'
    }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

{
  "path": "output/add-password.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example2">}} {{< tab "C#" >}}

```csharp
using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using GroupDocs.Merger.Cloud.Sdk.Model;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to add password to document.
    /// </summary>
    public class AddDocumentPassword
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new SecurityApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
					FilePath = "WordProcessing/one-page.docx",
                    Password = "Password"
                };

                var options = new Options
                {
                    FileInfo = fileInfo,
                    OutputPath = "output/add-password.docx"
                };

                var request = new AddPasswordRequest(options);
                var response = apiInstance.AddPassword(request);

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
package examples.SecurityOperations;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to add password to document.
 */
public class Merger_Java_AddDocumentPassword {

	public static void main(String[] args) {		

		SecurityApi apiInstance = new SecurityApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/one-page.docx");
			fileInfo.setPassword("password");

			Options options = new Options();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/add-password.docx");

			AddPasswordRequest request = new AddPasswordRequest(options);

			DocumentResult response = apiInstance.addPassword(request);

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
 
$securityApi = GroupDocs\Merger\SecurityApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/one-page.docx");         
$fileInfo->setPassword("Password");
 
$options = new Model\Options();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/add-password.docx");
 
$request = new Requests\addPasswordRequest($options);       
$response = $securityApi->addPassword($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
securityApi = GroupDocsMergerCloud::SecurityApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::Options.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/one-page.docx'
options.file_info.password = 'password'
options.output_path = "Output/add-password.docx"
 
result = securityApi.add_password(GroupDocsMergerCloud::AddPasswordRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.securityApi = merger_cloud.SecurityApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.Options();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/one-page.docx";  
options.fileInfo.password = "Password";  
options.outputPath = "Output/add-password.docx";
 
let result = await securityApi.addPassword(new merger_cloud.AddPasswordRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
securityApi = groupdocs_merger_cloud.SecurityApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.Options()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/one-page.docx", None, None, "password")
options.output_path = "Output/add-password.docx"
 
result = securityApi.add_password(groupdocs_merger_cloud.AddPasswordRequest(options))
```

{{< /tab >}} {{< /tabs >}}

## Check the Document for Password Protection

This REST API allows checking the document for password-protection. The result will be **true** if the document has a password for the opening set, in another case **false** will be returned. The endpoint accepts the file path as a query string parameter and returns the IsPasswordSet flag.

The description of the important API parameters is given below:

|Name|Type|Description
|---|---|---
|filePath|string|Path to document to append. Query parameter. Required.
|storageName|string|Storage name. Query parameter. Optional
|versionId|string|File version id. Query parameter. Optional

### Resource URI

```html

HTTP GET ~/password?filePath#{filePath}

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/CheckPassword) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password?filePath#%2Fwords%2Fpassword-protected.docx" \
-X GET
-H "Authorization: Bearer
<jwt token>"

```

{{< /tab >}} {{< tab "Response" >}}

```json

{
  "isPasswordSet": true
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example4">}} {{< tab "C#" >}}

```csharp
using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to check document password.
    /// </summary>
    public class CheckDocumentPasswordProtection
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new SecurityApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
						FilePath = "WordProcessing/password-protected.docx"
                };

                var request = new CheckPasswordRequest(fileInfo.FilePath);
                var response = apiInstance.CheckPassword(request);

				Console.WriteLine("Check password: " + response.IsPasswordSet);
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
package examples.SecurityOperations;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to check document password.
 */
public class Merger_Java_CheckDocumentPasswordProtection {

	public static void main(String[] args) {		

		SecurityApi apiInstance = new SecurityApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/password-protected.docx");			

			CheckPasswordRequest request = new CheckPasswordRequest(fileInfo.getFilePath(), Utils.MYStorage, null);

			PasswordResult response = apiInstance.checkPassword(request);

			System.err.println("checkPassword: " + response.getIsPasswordSet());
		
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
 
$securityApi = GroupDocs\Merger\SecurityApi($configuration);
 
$request = new Requests\checkPasswordRequest("WordProcessing/password-protected.docx");       
$response = $securityApi->checkPassword($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
securityApi = GroupDocsMergerCloud::SecurityApi.from_keys($app_sid, $app_key)
 
result = securityApi.check_password(GroupDocsMergerCloud::CheckPasswordRequest.new("WordProcessing/password-protected.docx"))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.securityApi = merger_cloud.SecurityApi.fromKeys(appSid, appKey);
 
let result = await securityApi.checkPassword(new merger_cloud.CheckPasswordRequest("WordProcessing/password-protected.docx"));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
securityApi = groupdocs_merger_cloud.SecurityApi.from_keys(app_sid, app_key)
 
result = securityApi.check_password(groupdocs_merger_cloud.CheckPasswordRequest("WordProcessing/password-protected.docx"))
```

{{< /tab >}} {{< /tabs >}}

## Remove Document Password

This REST API allows removing the password from a password-protected document. API endpoint accepts document storage path as input payload and returns the path to document without password-protection.
The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|The file path in the storage|Required property
|StorageName|Storage name|It could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Should be specified only for password-protected documents
|OutputPath|Path to resultant document|Required

### Resource URI

```html

HTTP DELETE ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/RemovePassword) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password" \
-X DELETE
-H "Authorization: Bearer
<jwt token>"
-d "{
        'FileInfo': { 'FilePath': 'words/password-protected.docx'},
        'Password':  'Password',
        'OutputPath': 'output/remove-password.docx'
    }"

```

{{< /tab >}} {{< tab "Response" >}}

```json

{
  "path": "output/remove-password.docx"
}
```

{{< /tab >}} {{< /tabs >}}

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example6">}} {{< tab "C#" >}}

```csharp
using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using GroupDocs.Merger.Cloud.Sdk.Model;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to remove document password.
    /// </summary>
    public class RemoveDocumentPassword
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);
            var apiInstance = new SecurityApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
					FilePath = "WordProcessing/password-protected.docx",
                    Password = "password"
                };

                var options = new Options
                {
                    FileInfo = fileInfo,
                    OutputPath = "output/remove-password.docx"
                };

                var request = new RemovePasswordRequest(options);
                var response = apiInstance.RemovePassword(request);

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
package examples.SecurityOperations;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to remove document password.
 */
public class Merger_Java_RemoveDocumentPassword {

	public static void main(String[] args) {		

		SecurityApi apiInstance = new SecurityApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/password-protected.docx");
			fileInfo.setPassword("password");

			Options options = new Options();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/remove-password.docx");

			RemovePasswordRequest request = new RemovePasswordRequest(options);

			DocumentResult response = apiInstance.removePassword(request);

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
 
$securityApi = GroupDocs\Merger\SecurityApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/password-protected.docx");         
$fileInfo->setPassword("password");
 
$options = new Model\Options();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/remove-password.docx");
 
$request = new Requests\removePasswordRequest($options);       
$response = $securityApi->removePassword($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
securityApi = GroupDocsMergerCloud::SecurityApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::Options.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/password-protected.docx'
options.file_info.password = 'password'
options.output_path = "Output/remove-password.docx"
 
result = securityApi.remove_password(GroupDocsMergerCloud::RemovePasswordRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.securityApi = merger_cloud.SecurityApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.Options();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/password-protected.docx";  
options.fileInfo.password = "password";  
options.outputPath = "Output/remove-password.docx";
 
let result = await securityApi.removePassword(new merger_cloud.RemovePasswordRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
securityApi = groupdocs_merger_cloud.SecurityApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.Options()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/password-protected.docx", None, None, "password")
options.output_path = "Output/remove-password.docx"
 
result = securityApi.remove_password(groupdocs_merger_cloud.RemovePasswordRequest(options))
```

{{< /tab >}} {{< /tabs >}}

## Update Document Password

This REST API allows updating the password for the password-protected document. The resultant document will have a new password. API endpoint accepts document storage path as input payload and returns path to document with a new password.

The description of the important API parameters is given below:

|Name|Description|Comment
|---|---|---
|FilePath|File path in storage|Required property
|StorageName|Storage name|Could be omitted for default storage.
|VersionId|File version Id|Useful for storages that support file versioning
|Password|The password to open file|Required
|NewPassword|New password|Required
|OutputPath|Path to resultant document|Required

### Resource URI

```html

HTTP POST ~/password

```

[Swagger UI](https://apireference.groupdocs.cloud/merger/#/Security/UpdatePassword) lets you call this REST API directly from the browser.

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

* cURL example to get document information
curl -v "https://api.groupdocs.cloud/v1.0/merger/password" \
-X POST
-H "Authorization: Bearer
<jwt token>"
-d "{
        'FileInfo':
     {
        'FilePath': '/words/password-protected.docx',
         'Password':  'Password',
     },
     'NewPassword':  'NewPassword',
     'OutputPath': 'output/update-password.docx'
    }"
```

{{< /tab >}} {{< tab "Response" >}}

```json
{
  "path": "output/update-password.docx"
}

```

{{< /tab >}} {{< /tabs >}}

Response

```html
{
  "path": "output/update-password.docx"
}
```

### SDK examples

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Check out our [GitHub repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger Cloud SDKs along with working examples, to get you started in no time. Please check to [Get Supported File Formats]({{< ref "merger/getting-started/supported-document-formats.md" >}}) article to learn how to add an SDK to your project.

{{< tabs "example8">}} {{< tab "C#" >}}

```csharp
using GroupDocs.Merger.Cloud.Sdk.Api;
using GroupDocs.Merger.Cloud.Sdk.Client;
using GroupDocs.Merger.Cloud.Sdk.Model.Requests;
using System;
using GroupDocs.Merger.Cloud.Sdk.Model;
using FileInfo = GroupDocs.Merger.Cloud.Sdk.Model.FileInfo;

namespace GroupDocs.Merger.Cloud.Examples.CSharp
{
    /// <summary>
    /// This example demonstrates how to update document password.
    /// </summary>
    public class UpdateDocumentPassword
    {
		public static void Run()
		{
            var configuration = new Configuration(Common.MyAppSid, Common.MyAppKey);           
            var apiInstance = new SecurityApi(configuration);

			try
			{
				var fileInfo = new FileInfo
                {
					FilePath = "WordProcessing/password-protected.docx",
                    Password = "password"
                };

                var options = new UpdatePasswordOptions
                {
                    FileInfo = fileInfo,
                    OutputPath = "output/update-password.docx",
                    NewPassword = "NewPassword"
                };

                var request = new UpdatePasswordRequest(options);
                var response = apiInstance.UpdatePassword(request);

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
package examples.SecurityOperations;

import com.groupdocs.cloud.merger.client.*;
import com.groupdocs.cloud.merger.model.*;
import com.groupdocs.cloud.merger.model.requests.*;
import com.groupdocs.cloud.merger.api.*;
import examples.Utils;

/**
 * This example demonstrates how to update document password.
 */
public class Merger_Java_UpdateDocumentPassword {

	public static void main(String[] args) {		

		SecurityApi apiInstance = new SecurityApi(Utils.GetConfiguration());

		try {
			FileInfo fileInfo = new FileInfo();			
			fileInfo.setFilePath("WordProcessing/password-protected.docx");
			fileInfo.setPassword("password");

			UpdatePasswordOptions options = new UpdatePasswordOptions();
			options.setFileInfo(fileInfo);
			options.setOutputPath("output/update-password.docx");
			options.setNewPassword("newPassword");

			UpdatePasswordRequest request = new UpdatePasswordRequest(options);

			DocumentResult response = apiInstance.updatePassword(request);

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
 
$securityApi = GroupDocs\Merger\SecurityApi($configuration);
 
$fileInfo = new Model\FileInfo();
$fileInfo->setFilePath("WordProcessing/password-protected.docx");         
$fileInfo->setPassword("password");
 
$options = new Model\UpdatePasswordOptions();
$options->setFileInfo($fileInfo);
$options->setOutputPath("Output/update-password.docx");
$options->setNewPassword("NewPassword");
 
$request = new Requests\updatePasswordRequest($options);       
$response = $securityApi->updatePassword($request);
```

{{< /tab >}} {{< tab "Ruby" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
$app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
$app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
 
 
securityApi = GroupDocsMergerCloud::SecurityApi.from_keys($app_sid, $app_key)
 
options = GroupDocsMergerCloud::UpdatePasswordOptions.new
options.file_info = GroupDocsMergerCloud::FileInfo.new
options.file_info.file_path = 'WordProcessing/password-protected.docx'
options.file_info.password = 'password'
options.output_path = "Output/update-password.docx"
options.new_password = "NewPassword"
 
result = securityApi.update_password(GroupDocsMergerCloud::UpdatePasswordRequest.new(options))
```

{{< /tab >}} {{< tab "Node.js" >}}

```js
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.appSid = "XXXX-XXXX-XXXX-XXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
global.appKey = "XXXXXXXXXXXXXXXX"; // Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
global.securityApi = merger_cloud.SecurityApi.fromKeys(appSid, appKey);
 
let options = new merger_cloud.UpdatePasswordOptions();
options.fileInfo = new merger_cloud.FileInfo();
options.fileInfo.filePath = "WordProcessing/password-protected.docx";  
options.fileInfo.password = "password";  
options.outputPath = "Output/update-password.docx";
options.newPassword = "NewPassword";
 
let result = await securityApi.updatePassword(new merger_cloud.UpdatePasswordRequest(options));
```

{{< /tab >}} {{< tab "Python" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
app_sid = "XXXX-XXXX-XXXX-XXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
app_key = "XXXXXXXXXXXXXXXX" # Get AppKey and AppSID from https://dashboard.groupdocs.cloud
  
securityApi = groupdocs_merger_cloud.SecurityApi.from_keys(app_sid, app_key)
 
options = groupdocs_merger_cloud.UpdatePasswordOptions()
options.file_info = groupdocs_merger_cloud.FileInfo("WordProcessing/password-protected.docx", None, None, "password")
options.output_path = "Output/update-password.docx"
options.new_password = "NewPassword"
 
result = securityApi.update_password(groupdocs_merger_cloud.UpdatePasswordRequest(options))
```

{{< /tab >}} {{< /tabs >}}
