---
title: 'SQL Server: Buffer Manager オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Buffer Manager object
- SQLServer:Buffer Manager
ms.assetid: 9775ebde-111d-476c-9188-b77805f90e98
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ed9c8ff90798205f9db02ae4b4b47eb4310d4b06
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52777524"
---
# <a name="sql-server-buffer-manager-object"></a>SQL Server: Buffer Manager オブジェクト
  **Buffer Manager** オブジェクトには、次に示す項目の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] による使用状況を監視するためのカウンターが用意されています。  
  
-   データ ページを保存するメモリ。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によるデータベース ページの読み書きに伴う物理 I/O を監視するカウンター。  
  
-   ソリッドステート ドライブ (SSD) などの高速不揮発性記憶域を使用してバッファー キャッシュを拡張するバッファー プール拡張。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用されるメモリやカウンターを監視すると、次のことを確認できます。  
  
-   物理メモリが適切でないことによるボトルネックが存在するかどうか。 頻繁にアクセスするデータをキャッシュに格納できない場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はデータをディスクから取得する必要があります。  
  
-   メモリを増設したり、データ キャッシュや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の内部構造により多くのメモリを使用できるように設定することで、クエリのパフォーマンスを向上できるかどうか。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がディスクからデータをどの程度の頻度で読み取る必要があるか。 メモリ アクセスなどの他の操作に比べて、物理 I/O には多くの時間がかかります。 物理 I/O をできる限り少なくすると、クエリのパフォーマンスが向上します。  
  
## <a name="buffer-manager-performance-objects"></a>Buffer Manager パフォーマンス オブジェクト  
 次の表で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Buffer Manager** パフォーマンス オブジェクトについて説明します。  
  
|SQL Server Buffer Manager カウンター|説明|  
|----------------------------------------|-----------------|  
|**Buffer cache hit ratio**|バッファー キャッシュ内に存在し、ディスクから読み取る必要がないページの比率を示します。 この比率は、最近の数千のページ アクセスでのキャッシュ ヒットの総数を、キャッシュ参照の総数で割って算出します。 長い時間が経過すると、この比率はほとんど変化しなくなります。 キャッシュから読み取る方が、ディスクから読み取るよりもコストが低いので、この比率が高くなるようにします。 一般に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できるメモリの量を増やすか、バッファー プール拡張機能を使用することで、バッファー キャッシュ ヒット率を増加させることができます。|  
|**Checkpoint pages/sec**|チェックポイントにより、またはすべてのダーティ ページをフラッシュする必要があるその他の操作により、ディスクにフラッシュされた 1 秒あたりのページ数を示します。|  
|**Database pages**|データベースの内容が含まれたこのノード上のバッファー プール内のページの数を示します。|  
|**Extension allocated pages**|バッファー プール拡張ファイル内の非フリー キャッシュ ページの総数。|  
|**Extension free pages**|バッファー プール拡張ファイル内のフリー キャッシュ ページの総数。|  
|**Extension in use as percentage**|バッファー マネージャー ページによって占有されるバッファー プール拡張ページング ファイルの割合。|  
|**Extension outstanding IO counter**|バッファー プール拡張ファイルの I/O キューの長さ。|  
|**Extension page evictions/sec**|1 秒あたりにバッファー プール拡張ファイルから削除されるページ数。|  
|**Extension page reads/sec**|1 秒あたりにバッファー プール拡張ファイルから読み取られるページ数。|  
|**Extension page unreferenced time**|ページが参照されないままバッファー プール拡張に存在する平均秒数。|  
|**Extension pages writes/sec**|1 秒あたりにバッファー プール拡張ファイルに書き込まれるページ数。|  
|**Free list stalls/sec**|フリー ページを待機する必要があった要求の 1 秒あたりの数を示します。|  
|**Lazy writes/sec**|バッファー マネージャーのレイジー ライターにより書き込まれたバッファーの 1 秒あたりの数を示します。 *レイジー ライター* とは、古いダーティ バッファー (異なるページのためにバッファーを再利用する前にディスクに書き戻す必要がある変更を含んでいるバッファー) をまとめてフラッシュし、ユーザー プロセスで使用できるようにするシステム プロセスです。 レイジー ライターを使用することで、使用可能なバッファーを作成するために頻繁にチェックポイントを実行する必要がなくなります。|  
|**Page life expectancy**|ページが参照されないままバッファー プールに存在する秒数を示します。|  
|**Page lookups/sec**|バッファー プールのページを検索する要求の 1 秒あたりの数を示します。|  
|**Page reads/sec**|物理的なデータベース ページ読み取りが実行される 1 秒あたりの回数を示します。 すべてのデータベースのページの物理的な読み取りの総数が表示されます。 物理 I/O にはコストがかかるので、データ キャッシュを大きくしたり、高性能のインデックスや効率のよいクエリを使用したり、データベースのデザインを変更したりすることで、できる限りコストを抑えることができます。|  
|**Page writes/sec**|物理的なデータベース ページ書き込みが実行される 1 秒あたりの回数を示します。|  
|**Readahead pages/sec**|使用を見越して読み取られた 1 秒あたりのページ数を示します。|  
  
## <a name="see-also"></a>参照  
 [SQL Server: Buffer Node](sql-server-buffer-node.md)   
 [サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [SQL Server の Plan Cache オブジェクト](sql-server-plan-cache-object.md)   
 [リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)   
 [バッファー プール拡張](../../database-engine/configure-windows/buffer-pool-extension.md)  
  
  
