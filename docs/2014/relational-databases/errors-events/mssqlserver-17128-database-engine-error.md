---
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a73f2469c38d611b95e3446e80755687f40346e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52507045"
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17128|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|INIT_NOBUFSPACE|  
|メッセージ テキスト|initdata:カーネル バッファー用のメモリがありません。|  
  
## <a name="explanation"></a>説明  
 バッファー プールの初回メモリ割り当てまたは予約に失敗しており、SQL Server が終了します。  
  
## <a name="user-action"></a>ユーザーの操作  
 通常、最小システム要件を大きく下回るような非常に小規模なコンピューターで SQL Server を起動した場合に発生します。  
  
  
