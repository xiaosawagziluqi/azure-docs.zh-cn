---
title: 关于 v2.0 | Azure
description: 了解 v2.0 终结点和平台。
services: active-directory
documentationcenter: dev-center-name
author: CelesteDG
manager: mtillman
editor: ''
ms.service: active-directory
ms.subservice: develop
ms.devlang: na
ms.topic: overview
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 09/24/2018
ms.author: celested
ms.reviewer: saeeda
ms.custom: aaddev
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb269df035bcc11583ebb7cff7d1ee2c3f6d8bca
ms.sourcegitcommit: 301128ea7d883d432720c64238b0d28ebe9aed59
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56208291"
---
# <a name="about-v20"></a>关于 v2.0

v2.0 终结点和平台已处于预览状态并不断增强。 目前，JavaScript 单页应用程序 (SPA) 方案功能已完成，我们邀请你使用 MSAL.js 构建基于浏览器的应用程序并向我们提供反馈，以便我们可以将状态从“预览”更新为“正式发布”(GA)。

> [!NOTE]
> MSAL Android、iOS 和 .NET 的功能仍在开发中。 可以使用它们来构建应用程序并向我们发送反馈。

Azure 门户[应用注册（预览版）](quickstart-register-app.md)体验已经过重大更新，现在包括使用 ADAL 或 MSAL 构建的所有应用程序，并提高了可用性。

在过去，想要支持个人 Microsoft 帐户和 Azure Active Directory (Azure AD) 中的工作帐户的应用程序开发人员必须集成两个单独的系统。 v2.0 终结点和平台提供了一个简化此过程的身份验证 API 版本。 使用它可通过一次集成从这两种类型的帐户登录。 使用 v2.0 终结点的应用程序还可以通过其中一种帐户从 [Microsoft 图形 API](https://developer.microsoft.com/graph) 使用 REST API。

## <a name="getting-started"></a>入门

从下述列表中选择偏爱的平台，以使用 Microsoft 开源库与框架生成应用程序：

[!INCLUDE [v2.0 endpoint platforms](../../../includes/active-directory-v2-quickstart-table.md)]

## <a name="learn-more-about-the-v20-endpoint-and-platform"></a>详细了解 v2.0 终结点和平台

了解 Azure AD v2.0 终结点的作用：

* 探索[可以使用 Azure AD v2.0 终结点生成的应用程序类型](v2-app-types.md)。
* 了解 Azure AD v2.0 终结点的[限制、局限性和约束](active-directory-v2-limitations.md)。

## <a name="additional-resources"></a>其他资源

浏览有关 v2.0 的深入信息：

* [关于 Microsoft 标识平台](about-microsoft-identity-platform.md)
* [v2.0 协议参考](active-directory-v2-protocols.md)
* [访问令牌参考](access-tokens.md)
* [ID 令牌参考](id-tokens.md)
* [v2.0 身份验证库参考](reference-v2-libraries.md)
* [v2.0 中的权限和许可](v2-permissions-and-consent.md)
* [Microsoft 图形 API](https://developer.microsoft.com/graph)

> [!NOTE]
> 如果只需从 Azure Active Directory 登录到工作和学校帐户，请从 [Azure AD 开发人员指南](v1-overview.md)入手。 V2.0 终结点供显式需要登录 Microsoft 个人帐户的开发人员使用。

[!INCLUDE [Help and support](../../../includes/active-directory-develop-help-support-include.md)]
