---
title: IDBProperties (OLE DB) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 2e5a4fd8-5164-495a-9986-3477aef8d8a5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b6dada26e15fc83d890b270ad553eb051bb08fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135872"
---
# <a name="idbproperties-ole-db"></a>IDBProperties (OLE DB)
  OLE DB 標準仕様では、プロバイダーが `DBPROPINFO::vValues` に VT_EMPTY を指定することを認めています。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB は、呼び出すときに常に VT_EMPTY を返します`IDBProperties::GetPropertyInfo`で`DBPROPSET_ROWSETALL`行セット プロパティを取得します。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
