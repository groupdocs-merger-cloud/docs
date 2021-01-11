---
id: "self-host-with-docker"
url: "merger/self-host-with-docker"
title: "How to self-host GroupDocs.Merger Cloud with Docker"
productName: "GroupDocs.Merger Cloud"
weight: 11
description: ""
keywords: ""
---

[Docker](https://docs.docker.com/get-started/overview/) is an open platform that effectively solves three main tasks development, deployment, and running the applications. With Docker, you can isolate your applications from the infrastructure that simplifies software development and delivery. The main building blocs are images and containers. The image includes everything you need to run the application: code or binaries, runtime dependencies, file system. The container is an isolated process with additional features that you can interact with. The use of containers to deploy applications is called *containerization*.

[Docker Hub](https://hub.docker.com/) is a repository or library of the container images where you can share and find images.

## Self-hosting

The GroupDocs.Merger Cloud Container Image available at [https://hub.docker.com/r/groupdocs/merger-cloud](https://hub.docker.com/r/groupdocs/merger-cloud) and enables users to self-host GroupDocs.Merger Cloud.

To run the GroupDocs.Merger Cloud in Docker the Docker itself should be installed on your machine.

### Install Docker

Check [Get Started](https://www.docker.com/get-started) section for Docker installation for your platform. After you installed and started Docker on your local machine we can run the container.

{{< alert style="info" >}}
When running Docker on Windows make sure to switch to Linux containers by clicking on Docker icon in the tray and selecting "Switch to Linux containers..." (see [https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) for more details.)
{{< /alert >}}

### Run Container

Before running the container you can create two optional folders with files to process and custom fonts that we'll be mounted and available to GroupDocs.Merger Cloud service when we start the container.

To run GroupDocs.Merger Cloud in Docker type one of the following commands:

{{< alert style="info" >}}
In case you don't have license keys you can omit LICENSE_PUBLIC_KEY and LICENSE_PRIVATE_KEY parameters. Without license GroupDocs.Merger will work in evaluation mode.
{{< /alert >}}

{{< tabs tabTotal="2" tabID="1" tabName1="Windows (PowerShell)" tabName2="Linux (bash)" >}} {{< tab tabNum="1" >}}

```powershell

docker run `
В  В  -p 8080:80 `
В  В  -v "${pwd}/data:/data" `
В  В  -e "LICENSE_PUBLIC_KEY#public_key" `
В  В  -e "LICENSE_PRIVATE_KEY#private_key" `
В  В  --name merger_cloud `
В  В  groupdocs/merger-cloud

```

{{< /tab >}} {{< tab tabNum="2" >}}

```bash

docker run \
В В В В -p 8080:80 \
В В В В -v $(pwd)/data:/data \
В В В В -e LICENSE_PUBLIC_KEY#public_key \
В В В В -e LICENSE_PRIVATE_KEY#private_key \
В В В В --name merger_cloud \
В В В В groupdocs/merger-cloud

```

{{< /tab >}} {{< /tabs >}}

The Docker would download GroupDocs.Merger Cloud image from Docker Hub and start a container.

{{< alert style="info" >}}
I'm running Docker on Windows and will be using PowerShell to run the commands but the experience would be the same in case you're on Linux.
{{< /alert >}}

After the container is started you'll see the following messages that indicate that GroupDocs.Merger Cloud service up and running.

![Docker container started](merger/images/docker_run.png)

Now you can work with GroupDocs.Merger Cloud which is hosted on your machine.

### Health-check

When the container and GroupDocs.Merger Cloud started you can check service status by calling GET [http://localhost:8080/](http://localhost:8080/). The successful response status (200) will indicate that the service is up and running.

{{< tabs tabTotal="2" tabID="2" tabName1="Windows (PowerShell)" tabName2="Linux (bash)" >}} {{< tab tabNum="1" >}}

```powershell
Invoke-WebRequest -Uri http://localhost:8080/
```

{{< /tab >}} {{< tab tabNum="2" >}}

```bash
curl -i http://localhost:8080/
```

{{< /tab >}} {{< /tabs >}}

At the following screenshot, I'm calling [http://localhost:8080/](http://localhost:8080/) in a separate Powershell window and response indicates that service is alive:

![Health check](merger/images/docker_invoke.png)

### Using UI

After starting, you can use Swagger UI at [http://localhost:8080/swagger/](http://localhost:8080/swagger/) and explore the API. With Swagger UI you can call API methods in your browser.

![Swagger UI](merger/images/docker_ui.png)

### Using SDK

We generate our SDKs in different languages so you may check if yours is available at [GitHub](https://github.com/groupdocs-merger-cloud). SDKs require authentication, so predefined CLIENT_ID/CLIENT_SECRET parameters must be set.

{{< alert style="info" >}}
If you don't find your language in the SDK list, feel free to request for it on our [Support Forums](https://forum.groupdocs.cloud/c/merger), or use raw REST API requests as you can find it [here](https://products.groupdocs.cloud/merger/curl).
{{< /alert >}}

{{< tabs tabTotal="2" tabID="3" tabName1="Windows (PowerShell)" tabName2="Linux (bash)" >}} {{< tab tabNum="1" >}}

```powershell
docker run `
В В В В -p 8080:80 `
В В В В -v "${pwd}/data:/data" `
В В В В -e "LICENSE_PUBLIC_KEY#public_key" `
В В В В -e "LICENSE_PRIVATE_KEY#private_key" `
В В В В -e "client_id=client_id" `
В В В В -e "client_secret=client_secret" `
В В В В --name merger_cloud `
В В В В groupdocs/merger-cloud
```

{{< /tab >}} {{< tab tabNum="2" >}}

```bash
docker run \
В В В В -p 8080:80 \
В В В В -v $(pwd)/data:/data \
В В В В -e LICENSE_PUBLIC_KEY#public_key \
В В В В -e LICENSE_PRIVATE_KEY#private_key \
В В В В -e client_id=client_id \
В В В В -e client_secret=client_secret \
В В В В --name merger_cloud \
В В В В groupdocs/merger-cloud
```

{{< /tab >}} {{< /tabs >}}

### Stop Container

To stop the running Docker container, just use Ctrl+C in the same terminal where the container is running. Alternatively, you can stop the container by name.

```bash
docker stop merger_cloud
```

## Licensing

GroupDocs.Merger Cloud can be started in trial and licensed modes. When GroupDocs.Merger Cloud is working in trial mode the following limitations are applied:

* You can compare only two first pages of the document
* Evaluation watermarks added to the output

You can find more information about evaluation at [Evaluate GroupDocs.Merger]({{< ref "merger/getting-started/evaluate-groupdocs-merger.md" >}}).
