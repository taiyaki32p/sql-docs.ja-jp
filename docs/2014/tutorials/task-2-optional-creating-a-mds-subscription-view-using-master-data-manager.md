---
title: 'タスク 2 (オプション): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f3da8219-e0cb-4848-95ca-285a76ec1ba9
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4596485b4eebeba66028d03f5a54b3ee2461205b
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015283"
---
# <a name="task-2-optional-creating-a-mds-subscription-view-using-master-data-manager"></a>タスク 2 (オプション): マスター データ マネージャーを使用して MDS サブスクリプション ビューを作成する
  このタスクで公開するサブスクリプション ビューを作成する、 **Supplier**内のエンティティ、 **Suppliers**モデルを他のアプリケーション。 現在のバージョンのチュートリアルでは、このビューを使用しません。  
  
1.  メイン ページに切り替えます**マスター データ マネージャー** ([http://localhost/MDS](http://localhost/MDS)) をクリックして**SQL Server 2012 マスター データ サービス**上部にあります。  
  
2.  クリックして**統合管理**します。  
  
3.  クリックして**ビューの作成**メニュー バーでします。  
  
     ![新しいサブスクリプションの表示 ボタンを追加](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-01.jpg "新しいサブスクリプションの表示 ボタンの追加")  
  
4.  クリックして **+ (正符号 +)** サブスクリプション ビューを作成するには、ツールバーのアイコン。  
  
5.  **サブスクリプション ビューの作成** ウィンドウで「 **Suppliers**の**サブスクリプション ビュー名**します。  
  
6.  選択**Suppliers**の**モデル**します。  
  
7.  選択**VERSION_1**の**バージョン**します。  
  
8.  選択**Supplier**の**エンティティ**します。  
  
9. 選択**リーフ メンバー**の**形式**します。  
  
     ![サブスクリプションの表示 ボタンを保存](../../2014/tutorials/media/et-creatingamdssubscriptionviewusingmdm-02.jpg "サブスクリプションの表示 ボタンの保存")  
  
10. クリックして**保存**サブスクリプション ビューを保存するには、ツールバー上。 このアクションは、SQL Server の名前にビューを作成**Suppliers**します。 SQL Server Management Studio (SSMS) を使用してこれを確認できます。  
  
## <a name="next-step"></a>次の手順  
 [タスク 3&#40;省略可能な&#41;:サブスクリプション ビューを確認](task-3-optional-reviewing-the-subscription-views.md)  
  
  
