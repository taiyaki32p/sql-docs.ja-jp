---
title: '*= (乗算代入) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '*=_TSQL'
- '*='
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, *=
- assignment operators, *=
- augmented operators, *=
- '*= (multiply equals)'
- '*= (multiplication assignment)'
ms.assetid: 816ff5dc-9a40-4c07-8351-39c194dbc079
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b88b98271d44039e70dfec3e47fa48099f3dd33
ms.sourcegitcommit: 01e17c5f1710e7058bad8227c8011985a9888d36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265239"
---
# <a name="-multiplication-assignment-transact-sql"></a>*= (乗算代入) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

2 つの数値を乗算し、値に演算の結果を設定します。 たとえば、変数 @x が 35 である場合、@x *= 2 は @x の元の値を取得し、2 を乗算して、@x にその新しい値 (70) を設定します。  
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression *= expression  
```  
  
## <a name="arguments"></a>引数  
_式 (expression)_  
数値型に分類される任意のデータ型を持つ有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。ただし、**bit** データ型は除きます。  
  
## <a name="result-types"></a>戻り値の型  
優先順位が高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
## <a name="remarks"></a>Remarks  
詳細については、「[&#42; &#40;乗算&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/multiply-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[複合演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
[演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
