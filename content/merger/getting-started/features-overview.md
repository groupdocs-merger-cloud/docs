---
id: "features-overview"
url: "merger/features-overview"
title: "Features Overview"
productName: "GroupDocs.Merger Cloud"
weight: 1
description: ""
keywords: ""
---

# Overview #

GroupDocs.Merger Cloud is a REST API that allows you to join multiple documents and manipulate single document structure across a wide range of . Below, the shortlist of possible actions:

## Document operations ##

### Join Documents ###

This feature lets you merge two or more documents into one document, join specific pages or page ranges from several source documents into a single resultant document.
Joined documents should be of the same format.

### Split Document ###

The** split** operation allows dividing a source document to several resultant documents.

### Document Preview  ###

The document preview feature allows generating image representations of document pages. This may be helpful for a better understanding of document content and its structure. Preview can be generated for all document pages (by default) or for specific page numbers or page range.

Supported image formats for document preview are:

* PNG
* JPG
* BMP

## Document pages operations ##

### Move Page ###

**MovePage** operation allows the moving page to another position within a document.

### Remove Pages ###

**RemovePages **operation feature provides an ability to remove a single page or a collection of specific page numbers from the source document.

### Rotate Pages ###

**The RotatePages** operation lets you rotate pages within the document. You can rotate pages by setting rotation angle to 90,180 or 270 degrees.

### Swap Page ###

**SwapPages **operation allows swapping two pages of positions within the source document. The result is a new document where two pages have their positions exchanged.

### Extract Pages ###

**ExtractPages** feature allows extracting a specified page or page ranges from the source document. The result is a new document that contains only specified pages from the source document.

### Change Pages Orientation ###

**ChangeOrientation **operation lets you set page orientation (portrait, landscape) for specific or all pages of the document.

## Document security operations ##

GroupDocs.Merger API allows to manage document password-protection through the following security operations:

* Check for password-protection;
* Set document password if document is not protected with password;
* Update password if the document is password-protected already;
* Remove the password if the document is password-protected.

## Document information extraction ##

GroupDocs.Merger Cloud allows obtaining basic information about source document - file type, size, pages count, page height and width, etc.
This may be quite useful for generating document previews.

# API Endpoint Groups Overview #

|Endpoint Group|Description
|---|---
|Info|It contains endpoints for obtaining a list of formats supported by GroupDocs.Merger Cloud, and getting basic information about the document and its pages
|Document|Contains endpoints for manipulating with documents - join, split, preview
|Pages|Contains endpoints for manipulating with document pages - move, remove, rotate, swap pages, etc.
|Security|Contains endpoints for working with document protection - check, add, update remove document password protection
|File|Contains endpoints for upload, download, copy, move, delete files in the storage
|Folder|Contains endpoints for creating, copy, move, delete folders in the storage
|Storage|Contains endpoints for obtaining storage information and file information

# Security and Authentication #

The GroupDocs.Merger Cloud API is secured and requires authentication. Two keys AppSID and AppKey are required for Authentication which can be created at the [Dashboard](http://dashboard.groupdocs.cloud/). Check [Authenticating API Requests]({{< ref "merger/getting-started/json-web-token-authentication.md" >}})) article for the complete example.
|---|---|---|---

# SDKs #

Check out our GitHub [repository](https://github.com/groupdocs-merger-cloud) for a complete list of GroupDocs.Merger SDKs along with working examples, to get you started in no time.
|---|---

At the moment following SDKs are provided:

* .NET ([Sources](https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-dotnet), [NuGet Package](https://www.nuget.org/packages/GroupDocs.Merger-Cloud))
|---|---|---|---
* Java ([Sources](https://github.com/groupdocs-merger-cloud/groupdocs-merger-cloud-java), [Jar](https://repository.groupdocs.cloud/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-merger-cloud))

# API Explorer #

The easiest way to try out our API right away in your browser! With the [GroupDocs Cloud API explorer](https://apireference.groupdocs.cloud/merger/). This is a collection of Swagger documentation for the GroupDocs Cloud APIs. You can get information about all the resources in the API. It also provides testing and interactivity to our API endpoint documentation.
|---|---
