---
title: sys.server_triggers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_triggers
- sys.server_triggers_TSQL
- server_triggers_TSQL
- sys.server_triggers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_triggers catalog view
ms.assetid: 25926ff4-9271-45bf-bc32-d5d3344bd47a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b13aeed62a84258fcfbf5820c17dca59f4b5852
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731240"
---
# <a name="sysservertriggers-transact-sql"></a>sys.server_triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  TR または TA の object_type を持つすべてのサーバーレベル DDL トリガーのセットを含みます。 CLR トリガーの場合、アセンブリが、読み込む必要がある、**マスター**データベース。 すべてのサーバーレベル DDL トリガー名は、単一のグローバル スコープ内に存在します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|トリガーの名前。|  
|**object_id**|**int**|オブジェクトの ID。|  
|**parent_class**|**tinyint**|親のクラスです。 常に次の値をとります。<br /><br /> 100 = サーバー|  
|**parent_class_desc**|**nvarchar(60)**|親のクラスの説明です。 常に次の値をとります。<br /><br /> サーバー。|  
|**parent_id**|**int**|SERVER 上のトリガーに対しては常に 0 です。|  
|**type**|**char(2)**|オブジェクトの種類:<br /><br /> TA = アセンブリ (CLR) トリガー<br /><br /> TR = SQL トリガー|  
|**type_desc**|**nvarchar(60)**|オブジェクトの種類のクラスの説明です。<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|トリガーが作成された日付。|  
|**modify_date**|**datetime**|トリガーが ALTER ステートメントを使用して最後に変更された日付です。|  
|**is_ms_shipped**|**bit**|ユーザーの代理として内部で作成されたトリガー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンポーネント。|  
|**is_disabled**|**bit**|1 = トリガーが無効です。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
