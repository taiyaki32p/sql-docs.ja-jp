---
title: NumRings (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6a553dc687ec9f1aef15e1455e80106f3612dd9b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750570"
---
# <a name="numrings-geography-data-type"></a>NumRings (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **Polygon** インスタンス内のリングの合計数を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **geography** 型では、すべてのリングが外部リングとして扱われるため、外部リングと内部リングは区別されません。  
  
## <a name="syntax"></a>構文  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の戻り値の型: **int**  
  
 CLR の戻り値の型: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、対象となるインスタンスが **Polygon** インスタンスではない場合に NULL を返し、空のインスタンスの場合に 0 を返します。 このメソッドは正確です。  
  
## <a name="examples"></a>使用例  
 2 つのリングを含む `Polygon` インスタンスを作成し、リングが 2 つあることを確認する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
