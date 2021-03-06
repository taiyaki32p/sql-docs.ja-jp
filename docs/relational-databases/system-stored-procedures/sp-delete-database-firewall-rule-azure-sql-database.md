---
title: sp_delete_database_firewall_rule (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 08/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_database_firewall_rule
- sp_delete_database_firewall_rule_TSQL
- sys.sp_delete_database_firewall_rule
- sys.sp_delete_database_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_database_firewall_rule procedure
ms.assetid: ed295312-e586-4fc2-9e80-806b490ee7bd
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: eb8ee3482868f64765e7bf90e962c9756eadbdbc
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015103"
---
# <a name="spdeletedatabasefirewallrule-azure-sql-database"></a>sp_delete_database_firewall_rule (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  データベース レベルのファイアウォール設定を削除します、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。 データベースのファイアウォール規則を構成および master のデータベースとユーザー データベースを削除できる[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]します。   
  
 
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_database_firewall_rule [@name =] [N]'name'
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [**@name =**] **'**_name_**'**  
 削除するデータベース レベルのファイアウォール設定の名前。 *名前*は**nvarchar (128)** で既定値はありません。 Unicode 識別子`N`は省略可能です[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]します。 
  
## <a name="permissions"></a>アクセス許可  
 サーバー レベル プリンシパル ログインだけプロビジョニング プロセスまたはデータベース レベルのファイアウォール ルールを削除できるの管理者として割り当てられている、Azure Active Directory プリンシパルによって作成します。  
  
## <a name="example"></a>例  
 次の例では、データベース レベルのファイアウォール設定の名前付き`Example DB Setting 1`します。
  
```  
-- Remove database-level firewall setting  
EXECUTE sp_delete_database_firewall_rule N'Example DB Setting 1';  
  
```  
  
## <a name="see-also"></a>参照  
 [Azure SQL Database ファイアウォール](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [方法: ファイアウォールの設定 (Azure SQL データベース) を構成します。](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [sp_set_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)   
 [sp_set_database_firewall_rule &#40;Azure SQL Database&#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)   
 [sys.database_firewall_rules &#40;Azure SQL Database&#41;](../../relational-databases/system-catalog-views/sys-database-firewall-rules-azure-sql-database.md)  
  
  


