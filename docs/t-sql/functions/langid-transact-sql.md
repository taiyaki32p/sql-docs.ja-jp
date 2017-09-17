---
title: "@@LANGID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LANGID'
- '@@LANGID_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- languages [SQL Server], current in use
- '@@LANGID function'
- current language in use
- ID for language in use
- local language IDs [SQL Server]
ms.assetid: 7a0fc089-2a48-4a81-9d78-2aaedb540d37
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4e27e2678cd5c54f44711ecd3d5d1d75a85f1a16
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="langid-transact-sql"></a>@@LANGID (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在使用している言語のローカル言語識別子 (ID) を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@LANGID  
```  
  
## <a name="return-types"></a>戻り値の型  
 **smallint**  
  
## <a name="remarks"></a>解説  
 言語 ID 番号を含めて、言語設定に関する情報を表示するには実行**sp_helplanguage**パラメーターを指定します。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のセッションの言語を設定`Italian`、しを使用して`@@LANGID`してイタリア語の ID を返します。  
  
```  
SET LANGUAGE 'Italian'  
SELECT @@LANGID AS 'Language ID'  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Changed language setting to Italiano.  
Language ID  
-----------  
6            
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [言語を設定する & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-language-transact-sql.md)   
 [sp_helplanguage & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)  
  
  