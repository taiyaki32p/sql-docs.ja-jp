---
title: STSrid (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STSrid (geography Data Type)
- STSrid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STSrid method
ms.assetid: 6b04f5a7-2e69-4d34-901e-b61ba6ca9c14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 20c59a05c19d55406e27043602d979b2db681729
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712140"
---
# <a name="stsrid-geography-data-type"></a>STSrid (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  **STSrid** はインスタンスの SRID (spatial reference identifier) を表す整数です。  
  
## <a name="syntax"></a>構文  
  
```  
  
.STSrid  
```  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型: **int**  
  
 CLR 型: **SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 このプロパティは変更できます。  
  
## <a name="examples"></a>使用例  
 最初に、SRID 値 4326 (WGS84) の `geography` インスタンスを作成し、`STSrid` を使用して SRID を確認する例を示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STSrid;  
```  
  
 次に、`STSrid` を使用してそのインスタンスの SRID 値を 4267 (NAD27) に変更し、変更された SRID 値を確認する例を示します。  
  
```  
SET @g.STSrid = 4267;  
SELECT @g.STSrid;  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの OGC メソッド](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)   
 [&#40;SRIDs&#41; Spatial Reference Identifiers](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
  
