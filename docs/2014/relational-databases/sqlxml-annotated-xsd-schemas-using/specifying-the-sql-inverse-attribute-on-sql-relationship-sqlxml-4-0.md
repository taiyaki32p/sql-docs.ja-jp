---
title: Sql:relationship (SQLXML 4.0) での sql:inverse 属性の指定 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf8d5dee0d72800c5b6250d83106cda552004536
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52800794"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>sql:relationship での sql:inverse 属性の指定 (SQLXML 4.0)
  `sql:inverse` 属性は、一括読み込みまたはアップデートグラムで XSD スキーマが使用される場合にのみ便利です。 `sql:inverse`で属性を指定することができます、  **\<sql:relationship >** 要素。 アップデートグラムでは、アップデートグラム ロジックによってスキーマが解釈され、アップデートグラム操作で更新されるテーブルと列が決定されます。 また、スキーマで指定される親子リレーションシップによって、レコードが変更、挿入、または削除される順序が決定されます。  
  
 XSD スキーマを使用しており、そこで指定されている親子リレーションシップが、対応するデータベース列間の主キー/外部キー リレーションシップの逆順である場合は、アップデートグラムで挿入または削除操作を実行すると、主キー/外部キー違反で失敗します。 このような場合は、`sql:inverse`属性が指定されて (`sql:inverse="true"`) で、  **\<sql:relationship >** 要素、および、アップデート グラム ロジックに逆に解釈指定された親/子リレーションシップスキーマです。  
  
 `sql:inverse` 属性はブール値 (0 = false、1=true) をとります。 指定できる値は 0、1、true、false です。  
  
 使用して作業用サンプルを`sql:inverse`注釈を参照してください[注釈付きマッピング スキーマを指定するアップデート グラムで](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)します。  
  
## <a name="see-also"></a>参照  
 [使用したリレーションシップ sql:relationship を指定する&#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
