---
title: "setClientInfo (java.util.Properties) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d3484e23a4f7e8997d1bfa21a34a4cdf6f6dee71
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setclientinfo-method-javautilproperties"></a>setClientInfo (java.util.Properties) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  接続のクライアント情報のプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *プロパティ*  
  
 設定するクライアント情報のプロパティの一覧を含むプロパティ オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setClientInfo メソッドは、java.sql.Connection インターフェイスの setClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]クライアント情報のプロパティをサポートしていません。 このメソッドは、場合に警告を生成、*プロパティ*入力パラメーターは空のプロパティ セットを参照していません。 つまり、このメソッドはアプリケーションが設定しようとするプロパティへの警告を生成します。 アプリケーションを使用する必要があります[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)それぞれの警告を取得するクラス。  
  
## <a name="see-also"></a>参照  
 [setClientInfo メソッド & #40 です。SQLServerConnection &#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  