---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 23dc13b8dac23914cc4f337e4b39fbf84ee4b782
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700980"
---
# <a name="mssqlserver1401"></a>MSSQLSERVER_1401
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1401|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBM_MASTERSTARTUP|  
|メッセージ テキスト|データベース ミラーリングのマスター スレッド ルーチンのスタートアップが次の理由により失敗しました: %ls。 このエラーの原因を解決して SQL Server サービスを再開してください。|  
  
## <a name="explanation"></a>説明  
ミラーリングを制御するスレッドのスタートアップに失敗しました。  
  
## <a name="user-action"></a>ユーザーの操作  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを調べ、このメッセージの前に関連するエラーが記録されているかどうかを確認します。 このエラーの原因を解決したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス (MSSQLSERVER) を再開します。  
  
## <a name="see-also"></a>参照  
[データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](~/database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
