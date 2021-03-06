---
title: Excel 用マスター データ サービス アドインのプロパティの設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cab1c662-5d40-4c16-9f5c-36ff9608810b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f5743f528e7b356611258da598edfa7b205971f3
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793044"
---
# <a name="setting-properties-for-master-data-services-add-in-for-excel"></a>Excel 用マスター データ サービス アドインのプロパティの設定
  Excel 用マスター データ サービス アドインの設定では、MDS から Excel アドインにデータを読み込む方法と Excel アドインから MDS にデータをパブリッシュする方法を指定します。  
  
 Excel アドインの設定を行うには、 **Excel**を開き、 **[マスター データ]** メニューをクリックして **[設定]** をクリックします。 Excel にアクセスできるユーザーならだれでもこれらの設定を変更できます。 この設定は、Excel が開いているコンピューターに適用されます。  
  
## <a name="excel-add-in-settings"></a>Excel アドインの設定  
  
||||  
|-|-|-|  
|タブとセクション|設定|説明|  
|設定：発行|[パブリッシュ時に **[パブリッシュと注釈設定]** ダイアログ ボックスを表示する]|**[パブリッシュ]** をクリックした後に **[パブリッシュと注釈設定]** ダイアログ ボックスが表示されるようにする場合はオンにします。こうすると、すべての変更についての単一の注釈を入力したり、各変更の注釈を個別に入力することができます。<br /><br /> **[パブリッシュと注釈設定]** ダイアログ ボックスを表示せずにパブリッシュ プロセスが開始されるようにする場合はオフにします。 注釈を入力する機会はありません。|  
|設定：バージョン|[バージョンの選択]|Excel アドインに読み込まれるマスター データのバージョンを選択します。 次の値をとります。<br /><br /> **[なし]** : どのバージョンも既定のバージョンにしない場合に選択します。<br /><br /> **[最も古い]** : 最も古いバージョンを既定のバージョンにする場合に選択します。 **[最も新しい]** : 最も新しいバージョンを既定のバージョンにする場合に選択します。|  
|設定：ログの記録|[詳細なログ記録を有効にする]|サービスのすべてのコマンドの結果をログに記録されるようにマスター データを MDS から Excel アドインを読み込むプロセスのログ記録を有効にします。|  
|設定：バッチ処理サイズ|[読み込むセルの数]|MDS サーバーから Excel に読み込まれるバッチで読み込まれるセルの数を示す数値を選択します。 既定値は 50,000 セルです。|  
|設定：バッチ処理サイズ|[パブリッシュするセルの数]|Excel から MDS サーバーに返されるバッチでパブリッシュされるセルの数を示す数値を選択します。 既定値は 50,000 セルです。|  
|設定：セーフ リストに追加されたサーバー|[すべてクリア]|関連するショートカット クエリ ファイルを開いたときに安全と見なされた接続の一覧をクリアします。|  
|データ: フィルター|[大きなデータ セットの場合にフィルター警告を表示する]|MDS から Excel に読み込まれるデータ セットが行または列の最大数を超えている場合に警告を表示します。|  
|データ: フィルター|[最大行数]|読み込まれる行の数のしきい値を選択します。この値を超えると、フィルター警告が通知されます。|  
|データ: フィルター|[最大列数]|読み込まれる列の数のしきい値を選択します。この値を超えると、フィルター警告が通知されます。|  
|データ: セルの書式|色を変更する場合。属性の値の変更|Excel アドイン テーブルを MDS リポジトリからの新しいデータで更新したときにセルの属性値が変更された場合は、そのセルの色を変更するように指定します。|  
|データ: セルの書式|色を変更する場合。メンバーを追加します。|Excel アドイン テーブルを MDS リポジトリからの新しいデータで更新したときに新しいメンバーが行に追加された場合は、その行のセルの色を変更するように指定します。|  
  
  
