---
title: アラートのプロパティ:新しい警告 (オプション ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69f467af1c797b9bf1cfa55c7def8456ad4a32bd
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52772814"
---
# <a name="alert-properties-new-alert-options-page"></a>アラートのプロパティ:新しい警告 (オプション ページ)
  このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告のオプションを表示および変更できます。  
  
## <a name="options"></a>および  
 **電子メール**  
 イベントからのエラー テキストがある場合は、それを電子メール通知に含めます。  
  
 **ポケットベル**  
 イベントからのエラー テキストがある場合は、それをポケットベル通知に含めます。  
  
 **Net send**  
 イベントからのエラー テキストがある場合は、それを Net Send 通知に含めます。  
  
 **[送信する付加通知メッセージ]**  
 通知メッセージに含める追加のテキストを入力します。  
  
 **[応答の遅延]**  
 反復的に発生するイベントの遅延を指定します。 イベントの中には、短時間に頻繁に発生するものがあります。 そのようなイベントに対しては、その発生を認識するだけで、すべてのイベントについて応答を返さないようにする場合があります。 このオプションは、タイムアウトを指定するために使用します。遅延を指定した場合、イベントに対して警告が返された後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、イベントが遅延中に発生するかどうかに関係なく、再び応答するまでに指定の遅延を待ちます。  
  
 **Minutes**  
 遅延を分単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
 **Seconds**  
 遅延を秒単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
## <a name="see-also"></a>参照  
 [警告](alerts.md)  
  
  
