---
title: ファイルまたはレポートをアップロードする (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3c60005e798e2a942970d9fb7a8746256308c795
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023673"
---
# <a name="upload-a-file-or-report-report-manager"></a>ファイルまたはレポートをアップロードする (レポート マネージャー)
  レポート マネージャーには、レポート、モデル、およびその他のファイルをクライアント アプリケーションからパブリッシュしなくてもレポート サーバーに追加できるアップロード機能が備わっています。 ファイル システムからアップロードしたファイルは、レポート サーバー上のアイテムとして格納されます。 ファイルがどのように格納されるかは、アップロードするファイルの種類によって異なります。  
  
-   .rdl ファイルはレポートとして保存されます。  
  
-   .smdl ファイルはレポート モデルとして格納されます。  
  
-   共有データ ソース (.rds) ファイルなど、その他すべてのファイルはリソースとしてアップロードされます。 リソースはレポート サーバーでは処理されませんが、レポート サーバーが MIME タイプのファイルをサポートしていれば、レポート マネージャーで表示できます。  
  
### <a name="to-upload-a-file-or-report"></a>ファイルまたはレポートをアップロードするには  
  
1.  [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) を開始します。  
  
2.  レポート マネージャーで **[コンテンツ]** ページに移動します。 アイテムを追加するフォルダーに移動します。  
  
3.  **[ファイルのアップロード]** をクリックします。  
  
4.  **[参照]** をクリックして、アップロードするファイルを選択します。 レポート定義ファイル、画像、ドキュメント、またはレポート サーバーで利用できるようにする任意のファイルをアップロードできます。  
  
5.  新しいアイテムの名前を入力します。 アイテム名ではスペースを使用できます。ただし、予約文字 (; ? :) は使用できません : \@ & = + , $ / * \< > |.  
  
6.  既存のアイテムを新しいアイテムに置き換える場合は、 **[アイテムが存在する場合は上書きする]** をクリックします。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [共有データ ソースを作成、削除、または変更する (レポート マネージャー)](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [[コンテンツ] ページ (レポート マネージャー)](../contents-page-report-manager.md)   
 [[ファイルのアップロード] ページ (レポート マネージャー)](../upload-file-page-report-manager.md)   
 [フォルダーへのファイルのアップロード](../report-server/upload-files-to-a-folder.md)  
  
  
