---
title: 登录后应用程序的页面上有错误 | Microsoft Docs
description: 如何解决应用程序本身发出错误的 Azure AD 登录问题
services: active-directory
documentationcenter: ''
author: CelesteDG
manager: mtillman
ms.assetid: ''
ms.service: active-directory
ms.subservice: app-mgmt
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: conceptual
ms.date: 07/11/2017
ms.author: celested
ms.reviewer: asteen
ms.collection: M365-identity-device-management
ms.openlocfilehash: 438f4f60c80cb798c3c40f57e22c9194a9fd5f86
ms.sourcegitcommit: 3102f886aa962842303c8753fe8fa5324a52834a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60442805"
---
# <a name="error-on-an-applications-page-after-signing-in"></a>登录后应用程序的页面上出现错误

在这种情况下，用户已登录到 Azure AD，但应用程序显示错误，使得用户无法成功完成登录流。 在这种情况下，应用程序不接受 Azure AD 作出的响应。

应用程序不接受来自 Azure AD 的响应的原因可能有几个。 如果无法根据应用程序的错误清楚知道响应中缺少的内容，那么：

-   如果应用程序位于 Azure AD 库，请确认已遵循[如何在 Azure Active Directory 中调试对应用程序进行基于 SAML 的单一登录](https://azure.microsoft.com/documentation/articles/active-directory-saml-debugging)文章中的所有步骤。

-   使用 [Fiddler](https://www.telerik.com/fiddler) 之类的工具捕获 SAML 请求、SAML 响应和 SAML 令牌。

-   与应用程序供应商共享 SAML 响应以了解缺少的内容。

## <a name="missing-attributes-in-the-saml-response"></a>SAML 响应中缺少属性

若要在 Azure AD 配置中添加要在 Azure AD 响应中发送的属性，请执行以下步骤：

1. 打开 [**Azure 门户**](https://portal.azure.com/)，并以“全局管理员”或“共同管理员”身份登录。

2. 在左侧主导航菜单顶部单击“所有服务”，打开“Azure Active Directory 扩展”。

3. 在筛选器搜索框中键入“Azure Active Directory”，选择“Azure Active Directory”项。

4. 在 Azure Active Directory 的左侧导航菜单中，单击“企业应用程序”。

5. 单击“所有应用程序”，查看所有应用程序的列表。

   * 如果未看到想在此处显示的应用程序，请使用“所有应用程序列表”顶部的“筛选器”控件，并将“显示”选项设为“所有应用程序”。

6. 选择要配置单一登录的应用程序。

7. 在应用程序加载后，在应用程序的左侧导航菜单中单击“单一登录”。

8. 单击“用户属性”部分下的“查看和编辑所有其他用户属性”，以编辑在用户登录时要发送至应用程序（位于 SAML 令牌中）的属性。

   若要添加属性：

   * 单击“添加属性”。 输入“名称”，并从下拉列表中选择“值”。

   * 单击“保存”。 然后就能在表中看到新属性了。

9. 保存配置。

用户下次登录应用程序时，Azure AD 便会发送 SAML 响应中的新属性。

## <a name="the-application-expects-a-different-user-identifier-value-or-format"></a>应用程序需要不同的用户标识符值或格式

应用程序登录失败是因为 SAML 响应缺少属性（如角色），或因为应用程序需要不同格式的 EntityID 属性。

## <a name="add-an-attribute-in-the-azure-ad-application-configuration"></a>在 Azure AD 应用程序配置中添加属性:

若要更改用户标识符值，请执行以下步骤：

1. 打开 [**Azure 门户**](https://portal.azure.com/)，并以“全局管理员”或“共同管理员”身份登录。

2. 在左侧主导航菜单顶部单击“所有服务”，打开“Azure Active Directory 扩展”。

3. 在筛选器搜索框中键入“Azure Active Directory”，选择“Azure Active Directory”项。

4. 在 Azure Active Directory 的左侧导航菜单中，单击“企业应用程序”。

5. 单击“所有应用程序”，查看所有应用程序的列表。

   * 如果未看到想在此处显示的应用程序，请使用“所有应用程序列表”顶部的“筛选器”控件，并将“显示”选项设为“所有应用程序”。

6. 选择要配置单一登录的应用程序。

7. 在应用程序加载后，在应用程序的左侧导航菜单中单击“单一登录”。

8. 在“用户属性”下的“用户标识符”下拉列表中，为用户选择唯一标识符。

## <a name="change-entityid-user-identifier-format"></a>更改 EntityID（用户标识符）格式

如果应用程序需要其他格式的 EntityID 属性。 将无法选择在用户进行身份验证后，Azure AD 在响应中发送给应用程序的 EntityID（用户标识符）格式。

Azure AD 会根据所选值或 SAML AuthRequest 中应用程序要求的格式，为 NameID 属性（用户标识符）选择格式。 有关详细信息，请参阅 NameIDPolicy 部分下的[单一登录 SAML 协议](https://docs.microsoft.com/azure/active-directory/develop/active-directory-single-sign-on-protocol-reference#authnrequest)文章。

## <a name="the-application-expects-a-different-signature-method-for-the-saml-response"></a>应用程序对 SAML 响应要求其他签名方法

若要更改 SAML 令牌中由 Azure Active Directory 进行数字签名的部分。 执行以下步骤:

1. 打开 [**Azure 门户**](https://portal.azure.com/)，并以“全局管理员”或“共同管理员”身份登录。

2. 在左侧主导航菜单顶部单击“所有服务”，打开“Azure Active Directory 扩展”。

3. 在筛选器搜索框中键入“Azure Active Directory”，选择“Azure Active Directory”项。

4. 在 Azure Active Directory 的左侧导航菜单中，单击“企业应用程序”。

5. 单击“所有应用程序”，查看所有应用程序的列表。

   * 如果未看到想在此处显示的应用程序，请使用“所有应用程序列表”顶部的“筛选器”控件，并将“显示”选项设为“所有应用程序”。

6. 选择要配置单一登录的应用程序。

7. 在应用程序加载后，在应用程序的左侧导航菜单中单击“单一登录”。

8. 单击“SAML 签名证书”部分下的“显示高级证书签名设置”。

9. 选择应用程序要求的相应“签名选项”：

   * 对 SAML 响应进行签名

   * 对 SAML 响应和断言进行签名

   * 对 SAML 断言进行签名

用户下次登录应用程序时，Azure AD 会对所选择的 SAML 响应部分进行签名。

## <a name="the-application-expects-the-signing-algorithm-to-be-sha-1"></a>应用程序要求 SHA-1 签名算法

默认情况下，Azure AD 使用最安全的算法对 SAML 令牌进行签名。 除非应用程序要求，否则不建议将签名算法更改为 SHA-1。

若要更改签名算法，请执行以下步骤：

1. 打开 [**Azure 门户**](https://portal.azure.com/)，并以“全局管理员”或“共同管理员”身份登录。

2. 在左侧主导航菜单顶部单击“所有服务”，打开“Azure Active Directory 扩展”。

3. 在筛选器搜索框中键入“Azure Active Directory”，选择“Azure Active Directory”项。

4. 在 Azure Active Directory 的左侧导航菜单中，单击“企业应用程序”。

5. 单击“所有应用程序”，查看所有应用程序的列表。

   * 如果未看到想在此处显示的应用程序，请使用“所有应用程序列表”顶部的“筛选器”控件，并将“显示”选项设为“所有应用程序”。

6. 选择要配置单一登录的应用程序。

7. 在应用程序加载后，在应用程序的左侧导航菜单中单击“单一登录”。

8. 单击“SAML 签名证书”部分下的“显示高级证书签名设置”。

9. 在“签名算法”中选择“SHA-1”。

用户下次登录应用程序时，Azure AD 会使用 SHA-1 算法对 SAML 令牌进行签名。

## <a name="next-steps"></a>后续步骤
[如何在 Azure Active Directory 中调试对应用程序进行基于 SAML 的单一登录](https://azure.microsoft.com/documentation/articles/active-directory-saml-debugging)
