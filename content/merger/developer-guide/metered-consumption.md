---
id: "metered-consumption"
url: "merger/metered-consumption"
title: "Getting metered license consumption"
productName: "GroupDocs.Merger Cloud"
description: ""
keywords: ""
---
### Introduction ###

{{< alert style="info" >}}
This example related to Docker version of GroupDocs.Merger-Cloud only
{{< /alert >}}

The metered license can be used in Docker version of GroupDocs.Merger-Cloud.
Here is an example how to retrieve metered license consumption.

You can find more information about Docker version at [How to self-host GroupDocs.Merger Cloud with Docker]({{< ref "merger/getting-started/self-host-with-docker.md" >}})

## Note about credits consumption when using metered license in docker version ##

+ Storage calls are not charged
+ Merger API calls charge is based on document size: 1 credit per call per 20MB
+ Not about /join method: if page options, like page number, are set for first of joined documents, there may be extra credit consumed, because of internal implementation. If page number not provided for 1st document than it should consume as 1 operation.If you not provide page number for 1st document than it should consume as 1 operation.

## Resource URI ##

```HTTP GET ~/merger/consumption```

## cURL Example ##

{{< tabs tabTotal="2" tabID="1" tabName1="Request" tabName2="Response" >}} {{< tab tabNum="1" >}}

```html

* cURL example to get metered license consumption
curl -v "http://<base url>/v2.0/merger/consumption" \
-X GET \
-H "Accept: application/json" \
-H "Authorization: Bearer <jwt token>"
```

{{< /tab >}} {{< tab tabNum="2" >}}

```html
{
  "credit": 487848,
  "quantity": 6061570985.37938
}
{{< /tab >}} {{< /tabs >}}

## Response ##

The response structure contains metered license consumption information:

| Name | Type | Comment
|---|---|---
|Credit|decimal|Amount of used credits.
|Quantity|decimal|Amount of MBs processed.

## SDKs ##

Our API is completely independent of your operating system, database system or development language. You can use any language and platform that supports HTTP to interact with our API. However, manually writing client code can be difficult, error-prone and time-consuming. Therefore, we have provided and support API [SDKs](https://github.com/groupdocs-merger-cloud) in many development languages in order to make it easier to integrate with us.

### SDK Examples ###

{{< tabs tabTotal="6" tabID="10" tabName1="C#" tabName2="Java" tabName3="PHP" tabName4="Node.js" tabName5="Python" tabName6="Ruby" >}} {{< tab tabNum="1" >}}

```csharp
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-dotnet-samples
string MyClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
string MyClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
var configuration = new Configuration(MyClientId, MyClientSecret);
  
// Create necessary API instances
var apiInstance = new LicenseApi(configuration);

var response = apiInstance.GetConsumptionCredit();

Console.WriteLine($"Credits: {response.Credit}");
Console.WriteLine($"Quantity: {response.Quantity}");
```

{{< /tab >}} {{< tab tabNum="2" >}}

```java
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-java-samples
String MyClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
String MyClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
Configuration configuration = new Configuration(MyClientId, MyClientSecret);
  
// Create API instance
LicenseApi apiInstance = new LicenseApi(configuration);

ConsumptionResult response = apiInstance.getConsumptionCredit();
System.out.println("Credit: " + response.getCredit());
System.out.println("Quantity: " + response.getQuantity());
```

{{< /tab >}} {{< tab tabNum="3" >}}

```php
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-php-samples
use GroupDocs\Merger\Model;
use GroupDocs\Merger\Model\Requests;

$ClientId = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$ClientSecret = ""; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
$configuration = new GroupDocs\Merger\Configuration();
$configuration->setAppSid($ClientId);
$configuration->setAppKey($ClientSecret);

$apiInstance = new GroupDocs\Merger\LicenseApi($configuration);

// Prepare request
$filePath = dirname(realpath(__DIR__)) . '\Resources\WordProcessing\four-pages.docx';
$request = new Requests\ConvertDocumentDirectRequest("pdf", $filePath);

// Get consumption
$result = $apiInstance->getConsumptionCredit();

// Done
echo "Credit: " . $result->getCredit();
```

{{< /tab >}} {{< tab tabNum="4" >}}

```node
// For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-node-samples
global.merger_cloud = require("groupdocs-merger-cloud");

global.clientId = "XXXX-XXXX-XXXX-XXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
global.clientSecret = "XXXXXXXXXXXXXXXX"; // Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
global.licenseApi = merger_cloud.LicenseApi.fromKeys(clientId, clientSecret);

let response = await licenseApi.getConsumptionCredit();
console.log("GetLicenseConsumption: Credit = " + response.credit);
```

{{< /tab >}} {{< tab tabNum="5" >}}

```python
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-python-samples
import groupdocs_merger_cloud

client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
# Create necessary API instances
apiInstance = groupdocs_merger_cloud.LicenseApi.from_keys(Common.client_id, Common.client_secret)

# Get consumption
result = apiInstance.get_consumption_credit()

print("Credit: " + result.credit)
```

{{< /tab >}} {{< tab tabNum="6" >}}

```ruby
# For complete examples and data files, please go to https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-ruby-samples
require 'groupdocs_merger_cloud'

$client_id = "XXXX-XXXX-XXXX-XXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
$client_secret = "XXXXXXXXXXXXXXXX" # Get ClientId and ClientSecret from https://dashboard.groupdocs.cloud
  
# Create necessary API instances
apiInstance = GroupDocsMergerCloud::LicenseApi.from_keys($client_id, $client_secret)

# Get consumption
result = apiInstance.get_consumption_credit()

puts("Credit: " + result.credit)
```

{{< /tab >}} {{< /tabs >}}
