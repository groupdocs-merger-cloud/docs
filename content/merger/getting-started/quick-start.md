---
id: "quick-start"
url: "merger/quick-start"
title: "Quick Start"
productName: "GroupDocs.Merger Cloud"
weight: 2
description: ""
keywords: ""
toc: True
---

## Create an account

Creating an account is very simple. Go to [https://dashboard.groupdocs.cloud](https://dashboard.groupdocs.cloud/) to create a free account.

## Create an API client app

Before you can make any requests to GroupDocs Cloud API you need to get Client Id and Client Secret. That will be used to invoke the GroupDocs Cloud API.

You can get it from existing Application or create new Application from [Applications View of GroupDocs Cloud Dashboard]({{< ref "total/ui-topics/creating-and-managing-application.md" >}}).

## Install the SDK of your choice

Using an SDK (API client) is the quickest way for a developer to speed up the development. An SDK takes care of a lot of low-level details of makingRequests and handlingResponses and lets you focus on writing code specific to your particular project. Please check  article to learn how to add an SDK to your project.

## Make an APIRequest from the SDK of your choice

Use the **Client Id** and **Client Secret** from the API app client you created in step one and replace it in the corresponding code. Below is an example demonstrating how to get a list of all supported file formats in GroupDocs.Merger Cloud.

{{< alert style="info" >}}
The GitHub repository for [GroupDocs.Merger Cloud](https://github.com/groupdocs-merger-cloud) has a complete set of examples, demonstrating our API capabilities.
{{< /alert >}}

For complete examples and data files, please go to [https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-dotnet-samples](https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-dotnet-samples)

{{< tabs "example1">}} {{< tab "C#" >}}

```csharp
// Get Client Id and Client Secret from https://dashboard.groupdocs.cloud

var configuration = new Configuration(MyClientId, MyClientSecret);
var apiInstance = new InfoApi(configuration);
varResponse = apiInstance.GetSupportedFileFormats();
```

{{< /tab >}} {{< /tabs >}}
