---
title: 发布区域和终结点
titleSuffix: Azure Cognitive Services
description: 3 个创作区域和它们的门户网站支持所有多个发布的区域。 发布 LUIS 应用的区域对应于创建 Azure LUIS 终结点密钥时在 Azure 门户中指定的区域或位置。 发布应用时，LUIS 会自动为与密钥关联的区域生成终结点 URL。
services: cognitive-services
author: diberry
manager: nitinme
ms.custom: seodec18
ms.service: cognitive-services
ms.subservice: language-understanding
ms.topic: article
ms.date: 04/02/2019
ms.author: diberry
ms.openlocfilehash: 20ea2eb632a6d685351178691cc3d0f58a567902
ms.sourcegitcommit: 3102f886aa962842303c8753fe8fa5324a52834a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60599263"
---
# <a name="authoring-and-publishing-regions-and-the-associated-keys"></a>创作和发布区域及关联的密钥

三个创作区域支持相应 LUIS 门户。 若要将 LUIS 应用发布到多个区域，每个区域至少需要一个密钥。 

<a name="luis-website"></a>

## <a name="luis-authoring-regions"></a>LUIS 创作区域
有三个 LUIS 创作门户，基于区域。 必须在同一区域中创建和发布应用。 

|LUIS|创作区域|Azure 区域名称|
|--|--|--|
|[www.luis.ai][www.luis.ai]|美国<br>非欧洲<br>非澳大利亚| `westus`|
|[au.luis.ai][au.luis.ai]|澳大利亚| `australiaeast`|
|[eu.luis.ai][eu.luis.ai]|欧洲|`westeurope`|

创作区域具有[配对故障转移区域](https://docs.microsoft.com/azure/best-practices-availability-paired-regions)。 

<a name="regions-and-azure-resources"></a>

## <a name="publishing-regions-and-azure-resources"></a>发布区域和 Azure 资源
该应用将发布到与 LUIS 门户中添加的 LUIS 资源关联的所有区域。 例如，对于上创建的应用[www.luis.ai][www.luis.ai]，如果创建中的 LUIS 或认知服务资源**westus**和[将其添加到作为资源应用程序](luis-how-to-azure-subscription.md)，在该区域中发布该应用。 

## <a name="public-apps"></a>公共应用
公共应用在所有区域中发布，以便有基于区域的 LUIS 资源密钥的用户可以在与其资源密钥关联的任何区域中访问该应用。

<a name="publishing-regions"></a>

## <a name="publishing-regions-are-tied-to-authoring-regions"></a>发布区域绑定到创作区域

创作区域中的应用仅可发布到对应的发布区域。 如果应用目前位于错误的创作区域中，请导出应用，然后将其导入发布区域对应的正确创作区域。 

https://www.luis.ai 上创建的 LUIS 应用可以发布到除[欧洲](#publishing-to-europe)和[澳大利亚](#publishing-to-australia)区域之外的所有终结点。 

## <a name="publishing-to-europe"></a>发布到欧洲

若要发布到欧洲区域，请仅在 https://eu.luis.ai 创建 LUIS 应用。 如果尝试使用欧洲区域中的密钥将应用发布到其他区域，LUIS 会显示警告消息。 请改用 https://eu.luis.ai。 在 [https://eu.luis.ai][eu.luis.ai] 中创建的 LUIS 应用不会自动迁移到其他区域。 要实现迁移，请导出然后再导入 LUIS 应用。

## <a name="europe-publishing-regions"></a>欧洲发布区域

 全球区域 | 创作 API 区域和创作网站| 发布和查询区域<br>`API region name`   |  终结点 URL 格式   |
|-----|------|------|------|
| [欧洲](#publishing-to-europe)| `westeurope`<br>[eu.luis.ai][eu.luis.ai]| 法国中部<br>`francecentral`     | https://francecentral.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   | 
| [欧洲](#publishing-to-europe)| `westeurope`<br>[eu.luis.ai][eu.luis.ai]| 北欧<br>`northeurope`     | https://northeurope.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   | 
| [欧洲](#publishing-to-europe) | `westeurope`<br>[eu.luis.ai][eu.luis.ai]| 西欧<br>`westeurope`    |  https://westeurope.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   | 
| [欧洲](#publishing-to-europe) | `westeurope`<br>[eu.luis.ai][eu.luis.ai]| 英国南部<br>`uksouth`    |  https://uksouth.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |

## <a name="publishing-to-australia"></a>发布到澳大利亚

若要发布到澳大利亚区域，请仅在 https://au.luis.ai 创建 LUIS 应用。 如果尝试使用澳大利亚区域中的密钥将应用发布到其他区域，LUIS 会显示警告消息。 请改用 https://au.luis.ai。 在 [https://au.luis.ai][au.luis.ai] 中创建的 LUIS 应用不会自动迁移到其他区域。 要实现迁移，请导出然后再导入 LUIS 应用。

## <a name="australia-publishing-regions"></a>澳大利亚发布区域

 全球区域 | 创作 API 区域和创作网站| 发布和查询区域<br>`API region name`   |  终结点 URL 格式   |
|-----|------|------|------|
| [澳大利亚](#publishing-to-australia) | `australiaeast`<br>[au.luis.ai][au.luis.ai]| 澳大利亚东部<br>`australiaeast`     |  https://australiaeast.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |

## <a name="publishing-to-other-regions"></a>发布到其他区域

若要发布到其他区域，您创建 LUIS 应用，价格[ https://www.luis.ai ](https://www.luis.ai)仅。 

## <a name="other-publishing-regions"></a>其他发布区域

 全球区域 | 创作 API 区域和创作网站| 发布和查询区域<br>`API region name`   |  终结点 URL 格式   |
|-----|------|------|------|
| 亚洲 | `westus`<br>[www.luis.ai][www.luis.ai]| 印度中部<br>`centralindia` |  https://centralindia.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 亚洲 | `westus`<br>[www.luis.ai][www.luis.ai]| 东亚<br>`eastasia`     |  https://eastasia.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 亚洲 | `westus`<br>[www.luis.ai][www.luis.ai]| 日本东部<br>`japaneast`     |   https://japaneast.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 亚洲 | `westus`<br>[www.luis.ai][www.luis.ai]| 日本西部<br>`japanwest`     |   https://japanwest.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 亚洲 | `westus`<br>[www.luis.ai][www.luis.ai]| 韩国中部<br>`koreacentral`     |   https://koreacentral.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 亚洲 | `westus`<br>[www.luis.ai][www.luis.ai]| 东南亚<br>`southeastasia`     |   https://southeastasia.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 北美 |`westus`<br>[www.luis.ai][www.luis.ai] | 加拿大中部<br>`canadacentral`     |   https://canadacentral.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 北美 |`westus`<br>[www.luis.ai][www.luis.ai] | 美国中部<br>`centralus`     |   https://centralus.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 北美 |`westus`<br>[www.luis.ai][www.luis.ai] | 美国东部<br>`eastus`      |  https://eastus.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 北美 | `westus`<br>[www.luis.ai][www.luis.ai] | 美国东部 2<br>`eastus2`     |  https://eastus2.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 北美 | `westus`<br>[www.luis.ai][www.luis.ai] | 美国中北部<br>`northcentralus`  |  https://northcentralus.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   | 
| 北美 | `westus`<br>[www.luis.ai][www.luis.ai] | 美国中南部<br>`southcentralus`  |  https://southcentralus.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   | 
| 北美 |`westus`<br>[www.luis.ai][www.luis.ai] | 美国中西部<br>`westcentralus`    |  https://westcentralus.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |
| 北美 | `westus`<br>[www.luis.ai][www.luis.ai] | 美国西部<br>`westus`  |   https://westus.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY  |
| 北美 |`westus`<br>[www.luis.ai][www.luis.ai] | 美国西部 2<br>`westus2`    |  https://westus2.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY  |
| 南美洲 | `westus`<br>[www.luis.ai][www.luis.ai] | 巴西南部<br>`brazilsouth`    |  https://brazilsouth.api.cognitive.microsoft.com/luis/v2.0/apps/YOUR-APP-ID?subscription-key=YOUR-SUBSCRIPTION-KEY   |

## <a name="endpoints"></a>终结点

LUIS 当前具有 2 个终结点： 一个用于创作，一个用于查询预测分析。

|目的|代码|
|--|--|
|创作|`https://{region}.api.cognitive.microsoft.com/luis/api/v2.0/apps/{appID}/`|
|文本分析（查询预测）|`https://{region}.api.cognitive.microsoft.com/luis/v2.0/apps/{appId}?q={q}[&timezoneOffset][&verbose][&spellCheck][&staging][&bing-spell-check-subscription-key][&log]`|

下表说明了上表中用大括号 `{}` 表示的参数。

|参数|目的|
|--|--|
|region|Azure 区域 - 创作和发布具有不同的区域|
|appID|在 URL 路由中使用的 LUIS 应用 ID，可在应用仪表板上找到|
|q|从客户端应用程序（如聊天机器人）发送的话语文本|

## <a name="failover-regions"></a>故障转移区域

每个区域的故障转移到次要区域。 在欧洲和澳大利亚的转移故障转移的欧洲失败在澳大利亚。

创作区域具有[配对故障转移区域](https://docs.microsoft.com/azure/best-practices-availability-paired-regions)。 

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [预生成实体参考](./luis-reference-prebuilt-entities.md)

 [www.luis.ai]: https://www.luis.ai
 [au.luis.ai]: https://au.luis.ai
 [eu.luis.ai]: https://eu.luis.ai
