---
title: "sqlsrv_commit |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- sqlsrv_commit
apitype: NA
helpviewer_keywords:
- transaction support
- API Reference, sqlsrv_commit
- sqlsrv_commit
ms.assetid: bad67571-61ad-45b5-b4ff-677e3544f809
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1461edf0b99631e04fabc0dd91442dd88ad98504
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvcommit"></a>sqlsrv_commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

指定した接続で現在のトランザクションをコミットし、接続を自動コミット モードに戻します。 現在のトランザクションには、 [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md) の呼び出しの後、 [sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md) または **sqlsrv_commit**の呼び出しの前に指定した接続で実行されたすべてのステートメントが含まれています。  
  
> [!NOTE]  
> [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]既定で自動コミット モードにします。 これは、すべてのクエリは、 **sqlsrv_begin_transaction**を使用してトランザクションを開始します。  
  
> [!NOTE]  
> 場合**sqlsrv_commit**で開始され、アクティブなトランザクションの外にある接続で呼び出される**sqlsrv_begin_transaction**、呼び出しから戻る**false**および*Not in Transaction*エラーがエラー コレクションに追加します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_commit( resource $conn )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$conn*: トランザクションがアクティブな接続です。  
  
## <a name="return-value"></a>戻り値  
ブール値: トランザクションが正常にコミットされた場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="example"></a>例  
次の例では、トランザクションの一部として 2 つのクエリを実行します。 両方のクエリが成功すると、トランザクションはコミットされます。 いずれか (または両方) のクエリが失敗した場合、トランザクションはロールバックされます。  
  
この例の最初のクエリは、新しい販売注文を AdventureWorks データベースの *Sales.SalesOrderDetail* テーブルに挿入します。 これは、製品 ID 709 の製品 5 つに対する注文です。 2 番目のクエリは、製品 ID 709 の在庫量を 5 つ分減らします。 これらのクエリはどちらも、データベースに注文および製品の可用性の状態を正確に反映する目的で成功する必要があるため、トランザクションに含まれています。  
  
この例では、SQL Server および [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースはローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initiate transaction. */  
/* Exit script if transaction cannot be initiated. */  
if (sqlsrv_begin_transaction( $conn) === false)  
{  
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initialize parameter values. */  
$orderId = 43659; $qty = 5; $productId = 709;  
$offerId = 1; $price = 5.70;  
  
/* Set up and execute the first query. */  
$tsql1 = "INSERT INTO Sales.SalesOrderDetail   
                     (SalesOrderID,   
                      OrderQty,   
                      ProductID,   
                      SpecialOfferID,   
                      UnitPrice)  
          VALUES (?, ?, ?, ?, ?)";  
$params1 = array( $orderId, $qty, $productId, $offerId, $price);  
$stmt1 = sqlsrv_query( $conn, $tsql1, $params1 );  
  
/* Set up and execute the second query. */  
$tsql2 = "UPDATE Production.ProductInventory   
          SET Quantity = (Quantity - ?)   
          WHERE ProductID = ?";  
$params2 = array($qty, $productId);  
$stmt2 = sqlsrv_query( $conn, $tsql2, $params2 );  
  
/* If both queries were successful, commit the transaction. */  
/* Otherwise, rollback the transaction. */  
if( $stmt1 && $stmt2 )  
{  
     sqlsrv_commit( $conn );  
     echo "Transaction was committed.\n";  
}  
else  
{  
     sqlsrv_rollback( $conn );  
     echo "Transaction was rolled back.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
トランザクションの動作を重視するため、いくつかの推奨されるエラー処理は前の例には含まれていません。 実稼働アプリケーションでは、 **sqlsrv** 関数のすべての呼び出しは、エラーを確認し、それに応じて処理することをお勧めします。  
  
> [!NOTE]  
> トランザクションの実行に、埋め込みの Transact SQL を使用しないでください。 たとえば、トランザクションを開始するために、"BEGIN TRANSACTION" を Transact-SQL クエリとして使用してステートメントを実行しないでください。 埋め込みの Transact SQL を使用してトランザクションを実行するときに、必要なトランザクションの動作は保証できません。  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[方法: トランザクションを実行する](../../connect/php/how-to-perform-transactions.md)  
[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/overview-of-the-php-sql-driver.md)
  
