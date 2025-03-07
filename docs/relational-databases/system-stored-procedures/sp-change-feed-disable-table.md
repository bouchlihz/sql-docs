---
description: "The sp_change_feed_disable_table system stored procedure disables a table in the change feed for Azure Synapse Link for SQL."
title: "sp_change_feed_disable_table (Transact-SQL)"
ms.custom:
- event-tier1-build-2022
ms.date: 11/09/2022
ms.service: synapse-analytics
ms.prod_service: "database-engine, sql-database, synapse-analytics"
ms.reviewer: ""
ms.topic: "reference"
f1_keywords: 
  - "sp_change_feed_disable_table_TSQL"
  - "sp_change_feed_disable_table"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_change_feed_disable_table"
author: WilliamDAssafMSFT
ms.author: wiassaf
monikerRange: ">=sql-server-ver16 || =azuresqldb-current"
---
# sp_change_feed_disable_table (Transact-SQL)
[!INCLUDE [sqlserver2022-asdb](../../includes/applies-to-version/sqlserver2022-asdb.md)]

Removes a table from the change feed for [Azure Synapse Link for SQL](/azure/synapse-analytics/synapse-link/sql-synapse-link-overview). For more information, see [Manage Azure Synapse Link for SQL Server and Azure SQL Database](../../sql-server/synapse-link/synapse-link-sql-server-change-feed-manage.md).

> [!NOTE]
> This stored procedure is used internally and is not recommended for direct administrative use. Use Synapse Studio instead. Using this procedure will introduce inconsistency with Synapse Workspace configuration.

## Syntax  
   
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
```syntaxsql  
EXECUTE sys.sp_change_feed_disable_table
    @table_group_id uniqueidentifier,
    @table_id uniqueidentifier
GO
```  

## Arguments  
#### @table_group_id

Required. Data type is uniqueidentifier. 

The unique identifier of the change feed table group that the table belongs to. It is a GUID generated by the initial setup.

#### @table_id

Required. Data type is uniqueidentifier.

The unique identifier of the link table. It is the GUID generated by the setup flow and passed to the source publisher during provision. 
 
## Remarks

The last changes published and synchronized to Azure Synapse cannot be guaranteed. To guarantee synchronization between source and target up to a certain time, verify the "last transaction commit time" on the target and then call this procedure.

## Permissions  

  Currently, only a member of the sysadmin server role or db_owner role, or a user with CONTROL database permissions can execute this procedure.

## See also  

- [What is Synapse Link for SQL?](/azure/synapse-analytics/synapse-link/sql-synapse-link-overview)
- [sp_change_feed_disable_db (Transact-SQL)](sp-change-feed-disable-db.md)
- [sp_change_feed_drop_table_group (Transact-SQL)](sp-change-feed-drop-table-group.md)

## Next steps

- [Manage Azure Synapse Link for SQL Server and Azure SQL Database](../../sql-server/synapse-link/synapse-link-sql-server-change-feed-manage.md)
- [Get started with Synapse Link for SQL Server 2022 (Preview)](/azure/synapse-analytics/synapse-link/connect-synapse-link-sql-server-2022)
