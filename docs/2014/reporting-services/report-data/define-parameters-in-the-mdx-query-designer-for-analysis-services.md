---
title: Analysis Services (レポート ビルダーおよび SSRS) の MDX クエリ デザイナーでパラメーターの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], MDX
- Multidimensional Expressions [Reporting Services]
- Data Mining Prediction [Reporting Services]
- MDX [Reporting Services], defining parameters
- DMX [Reporting Services]
ms.assetid: 4ad1e5bc-f510-4752-b4f6-589e55317a90
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bbd72a6eadac5f65d292b742885c1af957a637e1
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039683"
---
# <a name="define-parameters-in-the-mdx-query-designer-for-analysis-services-report-builder-and-ssrs"></a>Analysis Services の MDX クエリ デザイナーでのパラメーターの定義 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースに対する MDX クエリをパラメーター化するには、そのクエリにクエリ パラメーターを追加する必要があります。 MDX クエリ デザイナーでは、デザイン モードとクエリ モードの両方で、フィルターを指定することによって、クエリ パラメーターを追加できます。 クエリ パラメーターを使用してクエリを定義すると、Reporting Services によってレポート パラメーターとデータセットが自動的に作成され、有効な値の一覧が示されます。 これにより、クエリに直接渡される値を指定できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-define-a-query-parameter-in-mdx-in-design-mode"></a>MDX のデザイン モードでクエリ パラメーターを定義するには  
  
1.  レポート データ ペインで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースの種類から作成されたデータセットを右クリックし、 **[クエリ]** をクリックします。 MDX クエリ デザイナーがデザイン モードで開きます。  
  
2.  ディメンションをフィルター領域にドラッグし、 **[ディメンション]** 列の最初のセルにドロップします。  
  
3.  **[階層]** 列のボックスの一覧から値を選択します。  
  
4.  **[演算子]** 列のボックスの一覧から演算子を選択します。  
  
5.  **[フィルター式]** 列のボックスの一覧から個々の値を選択するか、 **[すべて]** メンバーをクリックしてすべての値を選択します。  
  
6.  **[パラメーター]** 列で、チェック ボックスをオンにしてレポート パラメーターを作成します。  
  
7.  **[実行]** をクリックします。  
  
     クエリを実行したら、ツール バーの **[デザイン]** をクリックしてクエリ モードに切り替え、作成した MDX クエリを表示します。 引き続きデザイン モードを使用してクエリを作成する場合は、クエリ モードでクエリ テキストを変更しないでください。 デザイン モードに戻るには、 **[デザイン]** をクリックします。  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     レポート データ ペインで [パラメーター] ノードを展開して、フィルター用に自動的に作成されたレポート パラメーターを表示します。  
  
     レポート パラメーターで使用可能な値を示すデータセットを確認するには、レポート データ ペインの空白部分を右クリックし、 **[非表示のデータセットの表示]** をクリックします。 レポート データ ペインに、レポート内のすべてのデータセットが表示されます。  
  
### <a name="to-define-a-query-parameter-in-mdx-in-query-mode"></a>MDX のクエリ モードでクエリ パラメーターを定義するには  
  
1.  レポート データ ペインで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データ ソースの種類から作成されたデータセットを右クリックし、 **[クエリ]** をクリックします。 MDX クエリ デザイナーがデザイン モードで開きます。  
  
2.  ツール バーの **[デザイン]** をクリックして、クエリ モードに切り替えます。  
  
3.  MDX クエリ デザイナー ツール バーで **[クエリ パラメーター]** (![[クエリ パラメーター] ダイアログ ボックスのアイコン](../../analysis-services/media/iconqueryparameter.gif "[クエリ パラメーター] ダイアログ ボックスのアイコン")) をクリックします。 [クエリ パラメーター] ダイアログ ボックスが表示されます。  
  
4.  **[パラメーター]** 列で **[\<パラメーターの入力>]** をクリックし、パラメーター名を入力します。  
  
5.  **[ディメンション]** 列のボックスの一覧から値を選択します。  
  
6.  **[階層]** 列のボックスの一覧から値を選択します。  
  
7.  **[複数値]** 列で、チェック ボックスをオンにして複数値パラメーターを作成します。  
  
8.  手順 5. の選択に応じて、 **[既定]** 列のボックスの一覧から 1 つまたは複数の値を選択します。  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
10. クエリ デザイナーのツール バーで、 **[実行]** をクリックします。  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     レポート データ ペインで [パラメーター] ノードを展開して、フィルター用に自動的に作成されたレポート パラメーターを表示します。  
  
     レポート パラメーターで使用可能な値を示すデータセットを確認するには、レポート データ ペインの空白部分を右クリックし、 **[非表示のデータセットの表示]** をクリックします。 レポート データ ペインに、レポート内のすべてのデータセットが表示されます。  
  
## <a name="see-also"></a>参照  
 [MDX のための Analysis Services の接続の種類 &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md)   
 [Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス](analysis-services-mdx-query-designer-user-interface.md)  
  
  
