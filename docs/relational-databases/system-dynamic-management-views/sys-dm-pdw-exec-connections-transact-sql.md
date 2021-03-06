---
title: sys.dm_pdw_exec_connections (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e93d397d10a99f844454494c4bf0d82b7fe6d660
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030683"
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>sys.dm_pdw_exec_connections (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  このインスタンスの [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] との間に確立された接続に関する情報と各接続の詳細を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|session_id|**int**|この接続に関連付けられたセッションの識別子。 使用して `SESSION_ID()` を返す、 `session_id` の現在の接続。|  
|connect_time|**datetime**|接続が確立されたタイムスタンプ。 NULL 値は許可されません。|  
|encrypt_option|**nvarchar(40)**|TRUE のことを示します (接続が暗号化される) または FALSE (接続は enctypred ではありません)。|  
|auth_scheme|**nvarchar(40)**|この接続で使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows 認証方法を指定します。 NULL 値は許可されません。|  
|client_id|**varchar(48)**|このサーバーに接続するクライアントの IP アドレス。 NULL 値が許可されます。|  
|sql_spid|**int**|接続のサーバー プロセス ID。 使用して `@@SPID` を返す、 `sql_spid` の現在の接続。最も終えたら、使用、 `session_id` 代わりにします。|  
  
## <a name="permissions"></a>アクセス許可  
 必要があります**VIEW SERVER STATE**サーバーに対する権限。  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions.session_id|dm_pdw_exec_connections.session_id|一対一|  
|dm_pdw_exec_requests.connection_id|dm_pdw_exec_connections.connection_id|多対一|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 クエリ専用接続についての情報を収集する典型的なクエリ。  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

