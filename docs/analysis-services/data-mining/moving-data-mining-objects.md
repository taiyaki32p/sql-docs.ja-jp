---
title: データ マイニング オブジェクトの移動 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: edbceb50dd1532e427c3bf5738dfe183223afc2d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34016629"
---
# <a name="moving-data-mining-objects"></a>データ マイニング オブジェクトの移動
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング オブジェクトを移動する最も一般的なシナリオは、テスト環境または分析環境から運用環境にモデルを配置する方法、または他のユーザーとモデルを共有する方法です。  
  
 このトピックでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で用意されている、データ マイニング オブジェクトを移動するためのツールおよびスクリプト言語の使用方法について説明します。  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a>データベース間またはサーバー間でのデータ マイニング オブジェクトの移動  
 次の方法で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース間または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス間でデータ マイニング オブジェクトを移動できます。  
  
-   別のデータベースにソリューションを配置し直します。  
  
-   個々のオブジェクトのスクリプトを作成します。  
  
-   データベースをバックアップしてからそのコピーを復元します。  
  
-   構造とモデルをエクスポートおよびインポートします。  
  
 次のセクションでは、これらのオプションについて詳しく説明します。  
  
### <a name="deploying"></a>配置  
 ソリューションを別のサーバーまたはデータベースに配置するには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して作成されたソリューション ファイルが必要です。  
  
 Analysis Services ソリューションの配置の詳細については、「[Analysis Services プロジェクトの配置 &#40;SSDT&#41;](../../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)」を参照してください。  
  
### <a name="scripting"></a>スクリプトの作成  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]スクリプト オブジェクトに使用できるいくつかの言語を提供します。  
  
-   **XMLA:** [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクトを右クリックして、XMLA を使用してオブジェクトのスクリプトを作成することができます。 作成したスクリプトを実行するには、ターゲット サーバーの **XMLA クエリ** ウィンドウでスクリプトを開きます。  
  
-   **DMX:** [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で用意されているテンプレートまたはいずれかのクエリ ビルダーを使用して、スクリプトを作成できます。  
  
 ただし、スクリプト言語によって、実行できるタスクはそれぞれ異なります。  
  
-   オブジェクトの説明やデータ バインドなどのプロパティは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 言語を使用した場合のみ作成または変更できます。DMX を使用した場合は作成および変更できません。  
  
-   マイニング オブジェクトのインポートおよびエクスポートは、DMX でのみサポートされています。  
  
-   PMML の生成または PMML からのモデル定義のインポートは、DMX でのみサポートされています。  
  
-   アプリケーション データを使用したモデルのトレーニングは、DMX でのみサポートされています。 さらに、DMX INSERT INTO ステートメントでは、キー列の値を指定せずにモデルをトレーニングすることができます。  
  
 詳細については、「[Analysis Services スクリプト言語 &#40;ASSL&#41; での開発](../../analysis-services/multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。  
  
### <a name="backup-and-restore"></a>バックアップと復元  
 Analysis Services データベース全体のバックアップおよび復元は、データ マイニング ソリューションが OLAP オブジェクトに依存している場合に適しています。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]データベースのバックアップを迅速かつ容易には、バックアップと復元の機能を提供します。  
  
 詳細については、「 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」を参照してください。  
  
### <a name="exporting-and-importing"></a>エクスポートとインポート  
 DMX ステートメントを使用してマイニング モデルとマイニング構造をエクスポートし、インポートし直す方法は、リレーショナル データ マイニング オブジェクトを個別に移動したりバックアップしたりする場合に最も簡単です。 これらの操作の DMX 構文の詳細については、次のトピックを参照してください。  
  
-   [エクスポート (&) #40";"DMX"&"#41;](../../dmx/export-dmx.md)  
  
-   [インポート (&) #40";"DMX"&"#41;](../../dmx/import-dmx.md)  
  
 INCLUDE DEPENDENCIES オプションを指定すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって必要なデータ ソース ビューの定義もエクスポートされます。この場合、モデルや構造をインポートすると、ターゲット サーバーにデータ ソース ビューが再作成されます。 モデルのインポートが完了したら、オブジェクトに対して必要なマイニング権限を設定する必要があります。  
  
> [!NOTE]  
>  DMX を使用して OLAP モデルをエクスポートおよびインポートすることはできません。 マイニング モデルが OLAP キューブに基づいている場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で用意されている、データベース全体をバックアップおよび復元する機能を使用するか、キューブとモデルを配置し直す必要があります。  
  
## <a name="see-also"></a>参照  
 [オブジェクトとデータ マイニング ソリューションの管理](../../analysis-services/data-mining/management-of-data-mining-solutions-and-objects.md)  
  
  
