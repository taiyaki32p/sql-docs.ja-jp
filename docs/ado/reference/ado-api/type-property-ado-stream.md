---
title: Type プロパティ (ADO Stream) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e4df670c5fe6ca42015e7e85445dafde47738f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637040"
---
# <a name="type-property-ado-stream"></a>Type プロパティ (ADO Stream)
含まれるデータの型を示す、 [Stream](../../../ado/reference/ado-api/stream-object-ado.md) (バイナリまたはテキスト)。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 設定または取得を[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)に含まれるデータの種類を指定する値、 **Stream**オブジェクト。 既定値は**adTypeText**します。 ただし、新しいバイナリ データが書き込まれた最初に空にする**Stream**、**型**に変わります**adTypeBinary**します。  
  
## <a name="remarks"></a>コメント  
 **型**プロパティは読み取り/書き込みを現在の位置がの先頭にある場合にのみ、 **Stream** ([位置](../../../ado/reference/ado-api/position-property-ado.md)は 0 です)、およびその他の任意の位置に読み取り専用です。  
  
 **型**プロパティは、読み取りと書き込みに使用する方法を決定します。、 **Stream**します。 テキストの**ストリーム**を使用して、 [ReadText](../../../ado/reference/ado-api/readtext-method.md)と[WriteText](../../../ado/reference/ado-api/writetext-method.md)します。 バイナリの**ストリーム**を使用して、[読み取り](../../../ado/reference/ado-api/read-method.md)と[書き込み](../../../ado/reference/ado-api/write-method.md)します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [RecordType プロパティ (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Type プロパティ (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
