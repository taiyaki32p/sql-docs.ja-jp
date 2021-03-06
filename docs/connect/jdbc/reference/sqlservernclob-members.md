---
title: SQLServerNClob のメンバー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81bcb5406a491d0e7b73ec098b160008c1a11c4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795540"
---
# <a name="sqlservernclob-members"></a>SQLServerNClob のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表は、[SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md) クラスによって公開されるメンバーを示しています。  
  
## <a name="constructors"></a>コンストラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
 [なし] :  
  
## <a name="methods"></a>メソッド  
  
|[オブジェクト名]|[説明]|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|このメソッドは、**NCLOB** オブジェクトと、それが占有していたリソースを解放します。|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|取得、 **NCLOB**によって指定された値、 **java.sql.NClob**を ASCII ストリームとしてのオブジェクト。|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|取得、 **NCLOB**によって指定された値、 **java.sql.NClob**オブジェクト。|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|指定された部分文字列のコピーを取得、 **NCLOB**によって指定された値、 **java.sql.NClob**オブジェクト。|  
|[length](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|内の文字数を取得、 **NCLOB**によって指定された値、 **java.sql.NClob**オブジェクト。|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|指定した文字位置を取得**java.sql.NClob**オブジェクトまたはサブスト リングので、 **java.sql.NClob**指定された開始位置に基づいて。|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|この **java.sql.NClob** オブジェクトが表す **NCLOB** 値の指定された位置から ASCII 文字を書き込むために使用するストリームを取得します。|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|この **java.sql.NClob** オブジェクトが表す **NCLOB** 値の指定された位置から Unicode 文字のストリームを書き込むために使用するストリームを取得します。|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|書き込み、指定した**文字列**を**NCLOB**の指定した位置から始まります。|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|**NCLOB** 値を指定された長さに切り捨てます。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|--------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Clob|free、getAsciiStream、getCharacterStream、getSubString、length、position、setAsciiStream、setCharacterStream、setString、truncate|  
  
## <a name="see-also"></a>参照  
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
