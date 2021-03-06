---
title: クロス検証 (Analysis Services - データ マイニング) |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bf8960fb659611003325275b2cf86d9325351c29
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52540746"
---
# <a name="cross-validation-analysis-services---data-mining"></a>相互検証 (Analysis Services - データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  *クロス検証*は標準の分析ツールであり、データ マイニング モデルの開発と微調整に役立つ重要な機能です。 マイニング構造および関連マイニング モデルを作成した後に、相互検証を使用してモデルの有効性を確認します。  相互検証には次の用途があります。  
  
-   特定のマイニング モデルの堅牢性を検証します。  
  
-   1 つのステートメントから複数のモデルを評価します。  
  
-   複数のモデルを作成し、統計情報に基づいて最適なモデルを特定します。  
  
 ここでは、データ マイニング用のクロス検証機能の使用方法と、単一のモデルに関するクロス検証または単一のデータセットに基づく複数のモデルに関するクロス検証について、結果の解釈方法を説明します。  
  
## <a name="overview-of-cross-validation-process"></a>クロス検証プロセスの概要  
 クロス検証は、トレーニングと結果生成の 2 つのフェーズから構成されます。 これらのフェーズには、次の手順が含まれます。  
  
-   対象のマイニング構造を選択します。  
  
-   テストするモデルを指定します。 この手順は省略可能です。マイニング構造だけをテストすることもできます。  
  
-   トレーニング済みのモデルをテストするためのパラメーターを指定します。  
  
    -   予測可能な属性、予測値、および精度のしきい値。  
  
    -   構造データまたはモデル データをパーティション分割する際のフォールド数。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、フォールドと同数のモデルが作成されてトレーニングされます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] から、各モデルの各フォールド (またはデータセット全体) に対する一連の精度基準が返されます。  
  
## <a name="configuring-cross-validation"></a>クロス検証の構成  
 クロス検証の動作をカスタマイズして、セクション数、テストするモデル、および予測の精度バーを制御できます。 相互検証ストアド プロシージャを使用する場合、モデルの検証に使用するデータセットを指定することもできます。 このように選択肢が豊富なため、結果を比較して分析する必要がある多数のさまざまな結果セットを簡単に生成できます。  
  
 ここでは、相互検証を適切に構成するために役立つ情報を示します。  
  
### <a name="setting-the-number-of-partitions"></a>パーティション数の設定  
 パーティション数を指定すると、作成される一時的なモデルの数が決まります。 パーティションごとに、複数のセクションにわたるデータにテスト セットとして使用するためのフラグが設定され、パーティションに含まれない残りのデータをトレーニングすることによって新しいモデルが作成されます。 指定した数のモデルが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で作成およびテストされるまで、このプロセスが繰り返されます。 クロス検証で使用できるよう指定したデータは、すべてのパーティション間で均等に分散されます。  
  
 図の例は、3 つのフォールドを指定した場合のデータの使用方法を示しています。  
  
 ![クロス検証によるデータのセグメント](../../analysis-services/data-mining/media/xvoverviewmain.gif "クロス検証によるデータの分割方法")  
  
 図のシナリオでは、テスト用に使用される予約データセットがマイニング構造に含まれていますが、相互検証にはこのテスト データセットが含まれていません。 その結果、トレーニング データセット内のすべてのデータ、つまりマイニング構造内のデータの 70% が、相互検証に使用されます。 相互検証レポートには、各パーティションで使用されたケースの合計数が示されます。  
  
 使用するケースの合計数を指定することによって、クロス検証時に使用するデータ量を指定することもできます。 ケースは、すべてのフォールド間で均等に分散されます。  
  
 マイニング構造が SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに格納されている場合、フォールド数として設定できる最大値は、256 またはケース数のいずれか小さい方です。 セッションのマイニング構造を使用する場合、フォールドの最大数は 10 です。  
  
> [!NOTE]  
>  フォールド数を増やすと、それに応じて相互検証の所要時間も長くなります。フォールドごとにモデルを生成およびテストする必要があるためです。 フォールド数が多すぎると、パフォーマンス上の問題が発生することがあります。  
  
### <a name="setting-the-accuracy-threshold"></a>精度のしきい値の設定  
 状態のしきい値を使用すると、予測の精度バーを設定できます。 モデルではケースごとに、予測された状態が正確である確率を意味する *予測確率*が計算されます。 予測確率が精度バーを超える場合は予測が正しいと見なされ、超えない場合は誤りと見なされます。 この値は、 **[状態のしきい値]** を 0.0 ～ 1.0 の数値に設定することによって制御します。この数値が 1 に近いほど予測の信頼性レベルが高く、0 に近いほど予測が正しい可能性が低くなります。 状態のしきい値の既定値は NULL です。これは、最も高い確率を持つ予測された状態が、対象の値と見なされることを意味します。  
  
 状態のしきい値の設定がモデルの精度の測定に影響を与えることに注意してください。 たとえば、テストするモデルが 3 つあるとします。 いずれも同じマイニング構造に基づき、[Bike Buyer] という列を予測するモデルです。 予測しようとする値は 1 ("はい、購入します" の意味) だとします。 3 つのモデルから、それぞれ 0.05、0.15、0.8 の予測確率を持つ予測が返されます。 状態のしきい値を 0.10 に設定すると、2 つの予測が正しいと見なされます。 状態のしきい値を 0.5 に設定すると、1 つのモデルだけが正しい予測を返したものと見なされます。 既定値の NULL を使用すると、最も確率の高い予測が正しいと見なされます。 この場合、3 つの予測すべてが正しいと見なされます。  
  
> [!NOTE]  
>  しきい値を 0.0 に設定することは可能ですが、確率が 0 の予測も正しいと見なされるようになるため、このような値は意味がありません。 **[状態のしきい値]** を誤って 0.0 に設定しないよう注意してください。  
  
### <a name="choosing-models-and-columns-to-validate"></a>検証するモデルおよび列の選択  
 データ マイニング デザイナーの **[クロス検証]** タブを使用する場合、最初に一覧から予測可能列を選択する必要があります。 通常、1 つのマイニング構造で複数のマイニング モデルをサポートできますが、すべてのマイニング モデルで同じ予測可能列が使用されるわけではありません。 クロス検証を実行した場合、レポートに含めることができるのは、同じ予測可能列を使用するモデルのみです。  
  
 予測可能な属性を選択するには、 **[対象の属性]** をクリックし、一覧から列を選択します。 対象の属性が入れ子になった列の場合、または入れ子になったテーブルの列の場合は、形式を使用して、入れ子になった列の名前を入力する必要があります\<入れ子になったテーブル名 > (キー).\<列を入れ子になった >。 使用することができます、入れ子になったテーブルから使用される唯一の列がキー列の場合は、\<入れ子になったテーブル名 > (キー)。  
  
 予測可能な属性を選択すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、同じ予測可能な属性を使用しているすべてのモデルが自動的にテストされます。 対象の属性に不連続値が含まれているときに特定の値を予測する場合は、予測可能列を選択した後で、必要に応じて対象の状態を入力することができます。  
  
 対象の状態の選択は、返されるメジャーに影響します。 対象の属性を指定する場合、列名は、- し、既定では、モデルが最も可能性の高い状態の予測に対して評価される、予測するモデルを特定の値を選択しないでください。  
  
 クラスター モデルに対してクロス検証を使用する場合、予測可能列は存在しません。この場合は、 **[対象の属性]** ボックスの一覧から **[#Cluster]** を選択します。 このオプションを選択すると、 **[対象の状態]** などの、クラスター モデルに関連しない他のオプションは無効になります。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] マイニング構造に関連付けられたすべてのクラスター モデルが によってテストされます。  
  
## <a name="tools-for-cross-validation"></a>クロス検証のためのツール  
 クロス検証は、データ マイニング デザイナーから使用できるほか、ストアド プロシージャを実行することによって行うこともできます。  
  
 データ マイニング デザイナーのツールを使用してクロス検証を実行する場合、トレーニングと精度の結果のパラメーターを 1 つのダイアログ ボックスで構成できます。 こちらの方が簡単に設定でき、結果も表示しやすくなります。 1 つのマイニング構造に関連するすべてのマイニング モデルの精度を測定し、その結果を HTML レポートですぐに表示することができます。 ただし、ストアド プロシージャは、追加のカスタマイズや、プロセスをスクリプト化する機能など、いくつかの利点を提供します。  
  
### <a name="cross-validation-in-data-mining-designer"></a>データ マイニング デザイナーでのクロス検証  
 **または SQL Server Development Studio では、マイニング精度チャート ビューの** [クロス検証] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] タブを使用してクロス検証を実行できます。  
  
 このユーザー インターフェイスからクロス検証レポートを作成する方法の例については、「 [クロス検証レポートの作成](../../analysis-services/data-mining/create-a-cross-validation-report.md)」を参照してください。  
  
### <a name="cross-validation-stored-procedures"></a>クロス検証ストアド プロシージャ  
 上級ユーザーは、完全にパラメーター化されたシステム ストアド プロシージャの形式でクロス検証を使用することもできます。 ストアド プロシージャを実行するにはからインスタンスに接続して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、またはいずれかからマネージ コード アプリケーション。  
  
 ストアド プロシージャは、マイニング モデルの種類別にグループ化されています。 そのうちの 1 つは、クラスタリング モデルのみを扱うストアド プロシージャのグループです。 それ以外のマイニング モデルを扱うストアド プロシージャは、他のグループに含まれています。  
  
 どちらの種類のマイニング モデル (クラスタリング モデルとそれ以外のモデル) も、ストアド プロシージャは、2 つの独立したフェーズでクロス検証を実行します。  
  
 **データのパーティション分割とパーティションの基準の生成**  
  
 最初のフェーズでは、指定した数のパーティションをデータセット内に作成し、各パーティションに対して精度の結果を返すシステム ストアド プロシージャを呼び出します。 それぞれの基準について、パーティションの平均と標準偏差が Analysis Services によって計算されます。  
  
-   [SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)  
  
 **データセット全体の基準の生成**  
  
 2 番目のフェーズでは、先ほどとは異なる一連のストアド プロシージャを呼び出します。 これらのストアド プロシージャは、データセットのパーティション分割を行わずに、指定したデータセット全体の精度の結果を生成します。 マイニング構造のパーティション分割と処理を既に終えている場合は、この 2 つ目の一連のストアド プロシージャを呼び出すだけで結果を得ることができます。  
  
-   [SystemGetAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)  
  
-   [SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
#### <a name="defining-the-testing-data"></a>テスト データの定義  
 精度を計算するクロス検証ストアド プロシージャ (SystemGetAccuracyResults または SystemGetClusterAccuracyResults) を実行する際、クロス検証時のテストに使用するデータのソースを指定できます。 このオプションは、ユーザー インターフェイスでは使用できません。  
  
 テスト データ ソースの指定には、次のオプションがあります。  
  
-   トレーニング データのみを使用する。  
  
-   既存のテスト データセットを含める。  
  
-   テスト データセットのみを使用する。  
  
-   既存のフィルターをそれぞれのモデルに適用する。  
  
-   トレーニング セット、テスト セット、およびモデル フィルターを任意に組み合わせる。  
  
 テスト データ ソースを指定するには、ストアド プロシージャの **DataSet** パラメーターに整数値を指定します。 引数値の一覧については、関連するストアド プロシージャのリファレンス トピックの「解説」を参照してください。  
  
 データ マイニング デザイナーの **[クロス検証]** レポートを使用してクロス検証を実行する場合は、使用するデータ セットを変更できません。 既定で、各モデルのトレーニング ケースが使用されます。 フィルターがモデルに関連付けられている場合、そのフィルターが適用されます。  
  
## <a name="results-of-cross-validation"></a>クロス検証の結果  
 データ マイニング デザイナーを使用した場合、これらの結果がグリッド式の Web ビューアーに表示されます。 クロス検証ストアド プロシージャを使用した場合は、同じ結果がテーブルとして返されます。  
  
 レポートには 2 種類のメジャーが存在します。フォールドに分割したときのデータセットのばらつきを示す集計と、各フォールドの精度に対するモデル固有のメジャーです。 これらの基準について、以降のトピックで詳しく説明します。  
  
 [クロス検証の式](../../analysis-services/data-mining/cross-validation-formulas.md)  
  
 すべてのメジャーをテストの種類ごとに掲載しています。 メジャーの解釈について簡単に説明します。  
  
 [相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)  
  
 各メジャーを計算する数式について説明し、適用先となる属性の種類をメジャーごとに示します。  
  
## <a name="restrictions-on-cross-validation"></a>クロス検証の制限  
 SQL Server Development Studio のクロス検証レポートを使用してクロス検証を行う場合、テストできるモデルと設定できるパラメーターに関していくつかの制限事項があります。  
  
-   既定では、選択したマイニング構造に関連付けられているすべてのモデルがクロス検証されます。 対象のモデルまたはモデルの一覧を指定することはできません。  
  
-   Microsoft タイム シリーズ アルゴリズムまたは Microsoft シーケンス クラスター アルゴリズムに基づいているモデルの場合、クロス検証はサポートされません。  
  
-   クロス検証によってテストできるモデルがマイニング構造に含まれていない場合は、レポートを作成できません。  
  
-   マイニング構造にクラスター モデルと非クラスター モデルの両方が含まれているときに **[#Cluster]** オプションを選択しなかった場合、属性、状態、およびしきい値の設定がクラスター モデルに対して適切でない場合でも、同じレポートに両方の種類のモデルに関する結果が表示されます。  
  
-   一部のパラメーター値は制限されます。 たとえば、フォールドの数が 10 を超えていると警告が表示されます。これは、多数のモデルを生成した場合にレポートの表示が遅くなる可能性があるからです。  
  
 複数のマイニング モデルをテストする場合、モデルにフィルターがあると、各モデルが個別にフィルター処理されます。 相互検証中は、モデルにフィルターを追加したり、モデルのフィルターを変更したりすることができません。  
  
 既定の相互検証では、構造に関連付けられているすべてのマイニング モデルがテストされるため、フィルターを持つモデルと持たないモデルがあると、返される結果に一貫性がなくなることがあります。 同一のフィルターを持つモデルだけが比較されるようにするには、ストアド プロシージャを使用してマイニング モデルの一覧を指定します。 また、すべてのモデルに対して同一のデータセットが使用されるようにするには、フィルターがないマイニング構造テスト セットだけを使用します。  
  
 ストアド プロシージャを使用してクロス検証を実行する場合、テスト データのソースを選択する際のオプションが充実しています。 データ マイニング デザイナーを使用してクロス検証を実行する場合は、モデルまたは構造に関連付けられているテスト データ セットを使用する必要があります (存在する場合)。 一般に、高度な設定を指定する場合は、クロス検証ストアド プロシージャを使用するようにします。  
  
 クロス検証は、タイム シリーズまたはシーケンス クラスタリング モデルでは使用できません。 たとえば、KEY TIME 列または KEY SEQUENCE 列が含まれているモデルをクロス検証に含めることはできません。  
  
## <a name="related-content"></a>関連コンテンツ  
 クロス検証の詳細や、マイニング モデルのテストに関連した手法 (精度チャートなど) については、以下のトピックを参照してください。  
  
|トピック|リンク|  
|------------|-----------|  
|SQL Server Development Studio でクロス検証のパラメーターを設定する方法について説明します。|[[相互検証] タブ ([マイニング精度チャート] ビュー)](http://msdn.microsoft.com/library/bd215a68-1ad7-4046-9c44-ec8e2be13a64)|  
|クロス検証によって得られるメトリックについて説明します。|[クロス検証の式](../../analysis-services/data-mining/cross-validation-formulas.md)|  
|クロス検証レポートの形式について説明し、モデルの種類ごとに用意されている統計的尺度を明らかにします。|[相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)|  
|クロス検証の統計値を計算するためのストアド プロシージャを一覧にしています。|[データ マイニングのストアド プロシージャ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining.md)|  
|||  
|マイニング構造および関連するモデルのテスト データセットの作成方法について説明します。|[トレーニング データ セットとテスト データ セット](../../analysis-services/data-mining/training-and-testing-data-sets.md)|  
|他の種類の精度チャートの例を紹介します。|[分類マトリックス &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)<br /><br /> [リフト チャート (Analysis Services - データ マイニング)](../../analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)<br /><br /> [利益チャート (Analysis Services - データ マイニング)](../../analysis-services/data-mining/profit-chart-analysis-services-data-mining.md)<br /><br /> [散布図 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/scatter-plot-analysis-services-data-mining.md)|  
|各種の精度チャートを作成する手順について説明します。|[テストおよび検証タスク、および操作方法 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a>参照  
 [テストおよび検証 &#40;データ マイニング&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)  
  
  
