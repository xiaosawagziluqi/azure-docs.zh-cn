---
title: 在 SQL 数据仓库中使用用户定义架构 | Microsoft Docs
description: 有关在 Azure SQL 数据仓库中使用 T-SQL 用户定义架构开发解决方案的技巧。
services: sql-data-warehouse
author: WenJason
manager: digimobile
ms.service: sql-data-warehouse
ms.topic: conceptual
ms.component: implement
origin.date: 04/17/2018
ms.date: 10/15/2018
ms.author: v-jay
ms.reviewer: igorstan
ms.openlocfilehash: ae017461767a207deae1d990980258a1f661df3d
ms.sourcegitcommit: 3102f886aa962842303c8753fe8fa5324a52834a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61439139"
---
# <a name="using-user-defined-schemas-in-sql-data-warehouse"></a>在 SQL 数据仓库中使用用户定义架构
有关在 Azure SQL 数据仓库中使用 T-SQL 用户定义架构开发解决方案的技巧。

## <a name="schemas-for-application-boundaries"></a>应用程序边界的架构

传统数据仓库通常使用不同的数据库，根据工作负荷、域或安全性来创建应用程序边界。 例如，传统 SQL Server 数据仓库可能包含过渡数据库、数据仓库数据库和某些数据集市数据库。 在此拓扑中，每个数据库均作为体系结构中的工作负荷和安全边界来运行。

相比之下，SQL 数据仓库在一个数据库中运行整个数据仓库工作负荷。 不允许跨数据库联接。 因此，SQL 数据仓库预期仓库使用的所有表都存储在一个数据库中。

> [!NOTE]
> SQL 数据仓库不支持任何种类的跨数据库查询。 因此，需要修改利用此模式的数据仓库实现。
> 
> 

## <a name="recommendations"></a>建议
以下是针对使用用户定义的架构合并工作负荷、安全性、域和功能边界的一些建议

1. 使用一个 SQL 数据仓库数据库来运行整个数据仓库工作负荷
2. 合并现有的数据仓库环境，以使用一个 SQL 数据仓库数据库
3. 利用**用户定义架构**可以提供以前使用数据库实现的边界。

如果以前尚未使用用户定义的架构，则就不会存在任何记录。 只需使用旧数据库名称作为 SQL 数据仓库数据库中用户定义架构的基础。

如果已使用架构，则可以采用以下几个选项：

1. 删除旧架构名称并重新开始
2. 在表名称前面附加旧架构名称，以保留旧架构名称。
3. 在额外架构中的表上实现视图来重建旧架构结构，以保留旧架构名称。

> [!NOTE]
> 在首次检查时，选项 3 似乎像是最吸引人的选项。 但是，细节决定成败。 SQL 数据仓库中的视图为只读状态。 任何表修改或数据修改只能针对基础表执行。 选项 3 还在系统中引入了一个视图层。 如果已在体系结构中使用视图，可以再三考虑一下此选项。
> 
> 

### <a name="examples"></a>示例：
基于数据库名称实现用户定义的架构

```sql
CREATE SCHEMA [stg]; -- stg previously database name for staging database
GO
CREATE SCHEMA [edw]; -- edw previously database name for the data warehouse
GO
CREATE TABLE [stg].[customer] -- create staging tables in the stg schema
(       CustKey BIGINT NOT NULL
,       ...
);
GO
CREATE TABLE [edw].[customer] -- create data warehouse tables in the edw schema
(       CustKey BIGINT NOT NULL
,       ...
);
```

在表名称前面附加旧架构名称，以保留旧架构名称。 使用工作负荷边界的架构。

```sql
CREATE SCHEMA [stg]; -- stg defines the staging boundary
GO
CREATE SCHEMA [edw]; -- edw defines the data warehouse boundary
GO
CREATE TABLE [stg].[dim_customer] --pre-pend the old schema name to the table and create in the staging boundary
(       CustKey BIGINT NOT NULL
,       ...
);
GO
CREATE TABLE [edw].[dim_customer] --pre-pend the old schema name to the table and create in the data warehouse boundary
(       CustKey BIGINT NOT NULL
,       ...
);
```

使用视图保留旧架构名称

```sql
CREATE SCHEMA [stg]; -- stg defines the staging boundary
GO
CREATE SCHEMA [edw]; -- stg defines the data warehouse boundary
GO
CREATE SCHEMA [dim]; -- edw defines the legacy schema name boundary
GO
CREATE TABLE [stg].[customer] -- create the base staging tables in the staging boundary
(       CustKey    BIGINT NOT NULL
,       ...
)
GO
CREATE TABLE [edw].[customer] -- create the base data warehouse tables in the data warehouse boundary
(       CustKey    BIGINT NOT NULL
,       ...
)
GO
CREATE VIEW [dim].[customer] -- create a view in the legacy schema name boundary for presentation consistency purposes only
AS
SELECT  CustKey
,       ...
FROM    [edw].customer
;
```

> [!NOTE]
> 如果架构策略发生任何更改，则需要检查数据库的安全模型。 在许多情况下，可以在架构级别分配权限，以简化安全模型。 如果需要更高粒度的权限，可以使用数据库角色。
> 
> 

## <a name="next-steps"></a>后续步骤
有关更多开发技巧，请参阅[开发概述](sql-data-warehouse-overview-develop.md)。

