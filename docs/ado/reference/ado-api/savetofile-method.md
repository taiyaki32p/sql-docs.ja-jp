---
title: SaveToFile メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SaveToFile
- _Stream::SaveToFile
helpviewer_keywords:
- SaveToFile method [ADO]
ms.assetid: 8a8594f2-422b-4d2e-94f8-7fe337445900
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6afe36c7b3923c9ebf33fd615a1c21e34955e62d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827600"
---
# <a name="savetofile-method"></a>SaveToFile メソッド
バイナリ コンテンツを保存、 [Stream](../../../ado/reference/ado-api/stream-object-ado.md)ファイル。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stream.SaveToFile FileName, SaveOptions  
```  
  
#### <a name="parameters"></a>パラメーター  
 *FileName*  
 A**文字列**先ファイルの完全修飾名を含む値の内容、 **Stream**が保存されます。 有効なローカルの場所に保存できますか、任意の場所に UNC の値を使用してアクセスが。  
  
 *SaveOptions*  
 A [SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)によって新しいファイルを作成するかどうかを指定する値**SaveToFile**が既に存在しない場合、します。 既定値は**adSaveCreateNotExists**します。 これらのオプションでは、指定したファイルが存在しない場合にエラーが発生したことを指定できます。 指定することもできます**SaveToFile**既存のファイルの現在の内容が上書きされます。  
  
> [!NOTE]
>  既存のファイルを上書きする場合 (と**adSaveCreateOverwrite**設定されている)、 **SaveToFile**新しいに続く元の既存のファイルからバイトを切り捨てます[EOS](../../../ado/reference/ado-api/eos-property.md)します。  
  
## <a name="remarks"></a>コメント  
 **SaveToFile**の内容のコピーに使用できる、 **Stream**オブジェクトをローカル ファイルにします。 内容、またはプロパティの変更はありません、 **Stream**オブジェクト。 **Stream**オブジェクトが呼び出す前に開く必要があります**SaveToFile**します。  
  
 このメソッドの関連付けを変更していない、 **Stream**基になるソース オブジェクト。 **Stream**オブジェクトは元の URL に関連付けされますまたは**レコード**開かれたときにそのソースでした。  
  
 後に、 **SaveToFile**操作、現在の位置 ([位置](../../../ado/reference/ado-api/position-property-ado.md))、ストリームでは (0) のストリームの先頭に設定します。  
  
## <a name="applies-to"></a>適用対象  
 [Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
