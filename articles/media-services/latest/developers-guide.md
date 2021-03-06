---
title: Azure 媒体服务 v3 SDK - Azure
description: 本文概述了如何使用 SDK 通过媒体服务 v3 API 开始进行开发。
services: media-services
documentationcenter: na
author: Juliako
manager: femila
editor: ''
tags: ''
keywords: ''
ms.service: media-services
ms.devlang: multiple
ms.topic: overview
ms.tgt_pltfrm: multiple
ms.workload: media
ms.date: 04/11/2019
ms.author: juliako
ms.custom: ''
ms.openlocfilehash: 9fb4d1561a661387f759aada9e776d43a95aa5c7
ms.sourcegitcommit: b8a8d29fdf199158d96736fbbb0c3773502a092d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2019
ms.locfileid: "59564502"
---
# <a name="develop-against-media-services-v3-api-using-sdks"></a>使用 SDK 针对媒体服务 v3 API 进行开发

作为开发者，可以利用媒体服务 [REST API](https://aka.ms/ams-v3-rest-ref) 或客户端库，与 REST API 交互，以轻松创建、管理和维护自定义媒体工作流。 [媒体服务 v3](https://aka.ms/ams-v3-rest-sdk) API 基于 OpenAPI 规范（以前称为 Swagger）。

> [!NOTE]
> Azure 媒体服务 v3 SDK 不保证是线程安全的。 在开发多线程应用程序时，应添加自己的线程同步逻辑以保护客户端，或对每个线程使用新的 AzureMediaServicesClient 对象。 你还应该注意由代码提供给客户端的可选对象引入的多线程问题（如 .NET 中的 HttpClient 实例）。

本主题提供 SDK、工具和操作指南的链接。

## <a name="prerequisites"></a>先决条件

若要开始针对媒体服务进行开发，你需要满足以下条件：

- 一个有效的 Azure 订阅。 如果没有 Azure 订阅，请在开始之前创建一个[免费帐户](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio)。
- [了解基本概念](concepts-overview.md)
- 查看[使用媒体服务 v3 API 进行开发](media-services-apis-overview.md)
- [创建媒体服务帐户 - CLI](create-account-cli-how-to.md)

## <a name="start-developing-with-sdks"></a>开始使用 SDK 进行开发

### <a name="net"></a>.NET

使用 [.NET SDK](https://aka.ms/ams-v3-dotnet-sdk) [连接到媒体服务](configure-connect-dotnet-howto.md)。

浏览媒体服务 [.NET 参考](https://aka.ms/ams-v3-dotnet-ref)文档。

### <a name="java"></a>Java

使用 [Java SDK](https://aka.ms/ams-v3-java-sdk) [连接到媒体服务](configure-connect-java-howto.md)。

查看媒体服务 [Java 参考](https://aka.ms/ams-v3-java-ref)文档。

### <a name="nodejs"></a>Node.js

使用 [Node.js SDK](https://aka.ms/ams-v3-nodejs-sdk) [连接到媒体服务](configure-connect-nodejs-howto.md)。

浏览媒体服务 [Node.js 参考](https://aka.ms/ams-v3-nodejs-ref)文档并查看[示例](https://github.com/Azure-Samples/media-services-v3-node-tutorials)，了解如何将媒体服务 API 与 Node.js 配合使用。

### <a name="python"></a>Python

使用 [Python SDK](https://aka.ms/ams-v3-python-sdk)。

查看媒体服务 [Python 参考](https://aka.ms/ams-v3-python-ref)文档。

### <a name="go"></a>Go

使用 [Go SDK](https://aka.ms/ams-v3-go-sdk)。

查看媒体服务 [Go 参考](https://aka.ms/ams-v3-go-ref)文档。

### <a name="ruby"></a>Ruby

使用 [Ruby SDK](https://aka.ms/ams-v3-ruby-sdk)。

## <a name="azure-media-services-explorer"></a>Azure 媒体服务浏览器

[Azure 媒体服务浏览器](https://github.com/Azure/Azure-Media-Services-Explorer) (AMSE) 是可供希望了解媒体服务的 Windows 客户使用的工具。 AMSE 是一个 Winforms/C# 应用程序，用于通过媒体服务对 VOD 和实时内容进行上传、下载、编码和流式传输。 AMSE 工具适用于希望在不编写任何代码的情况下测试媒体服务的客户。 对于希望使用媒体服务进行开发的客户，可以为其提供 AMSE 代码作为资源。

AMSE 是一个开源项目，由社区提供支持（可以将问题报告给 https://github.com/Azure/Azure-Media-Services-Explorer/issues)）。 本项目采用 [Microsoft 开源行为准则](https://opensource.microsoft.com/codeofconduct/)。 有关详细信息，请参阅[行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)；若有其他任何问题或意见，请联系 opencode@microsoft.com。

## <a name="next-steps"></a>后续步骤

[概述](media-services-overview.md)
