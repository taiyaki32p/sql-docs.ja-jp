---
title: SQL Server テーブルに列の追加 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32e78feae791788e0aad87079546ea8c7d49e734
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48214242"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>SQL Server テーブルへの列の追加
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **itabledefinition::addcolumn**関数。 これにより、コンシューマーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに列を追加できます。  
  
 列を追加すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、テーブル、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーは次の制約します。  
  
-   DBPROP_COL_AUTOINCREMENT が VARIANT_TRUE の場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **timestamp** データ型を使用して列を定義している場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。  
  
-   それ以外の列定義の場合、DBPROP_COL_NULLABLE は VARIANT_TRUE にする必要があります。  
  
 コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。 *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
 新しい列名は、DBCOLUMNDESC パラメーター *pColumnDesc* の *dbcid* メンバー内にある、*uName* 共用体の *pwszName* メンバーに Unicode 文字列として指定されます。 *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
