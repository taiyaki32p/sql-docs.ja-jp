---
title: setClientInfo (java.lang.String, java.lang.String) メソッド | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ad28a2c578a4026d4152bb7056b00e8d3a05afd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47667326"
---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>setClientInfo (java.lang.String, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたクライアント情報のプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *name*  
  
 設定するクライアント情報のプロパティの名前を含む String です。  
  
 *value*  
  
 クライアント情報のプロパティに設定する値を含む String です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setClientInfo メソッドは、java.sql.Connection インターフェイスの setClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ではクライアント情報のプロパティをサポートしていません。 JDBC Driver 2.0 では、このメソッドはプロパティの警告を生成します。 アプリケーションは、[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) メソッドを使用して警告を取得する必要があります。  
  
## <a name="see-also"></a>参照  
 [setClientInfo メソッド &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
