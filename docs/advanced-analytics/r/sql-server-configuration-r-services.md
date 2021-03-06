---
title: SQL Server の構成 (R Services) - SQL Server Machine Learning サービス
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 63ba1878317427b4274d894ae1b0c4237601f141
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645281"
---
# <a name="sql-server-configuration-for-use-with-r"></a>R で使用するための SQL Server の構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、2 つのケース スタディに基づく R Services のパフォーマンスの最適化を説明するシリーズの 2 つ目です。  この記事では、SQL Server R Services を実行するために使用するコンピューターのハードウェアおよびネットワークの構成に関するガイダンスを提供します。 SQL Server インスタンス、データベース、またはソリューションで使用されるテーブルを構成する方法に関する情報も含まれています。 SQL Server での NUMA の使用は、ハードウェアとデータベースの最適化の間の線をぼかします、ため、3 番目のセクションには CPU の結合とリソース ガバナンスの詳細について説明します。

> [!TIP]
> SQL Server に慣れていない場合、SQL Server のパフォーマンス チューニングのガイドを確認することを強くお勧めします。[パフォーマンスの監視し、チューニング](https://docs.microsoft.com/sql/relational-databases/performance/monitor-and-tune-for-performance)します。

## <a name="hardware-optimization"></a>ハードウェアの最適化

サーバー コンピューターの最適化が外部スクリプトを実行するためのリソースがあることを確認する場合に重要です。 リソースが、制限されている、次のよう現象が発生する可能性があります。

- ジョブの実行が遅延または他のデータベース操作の優先順位を設定するためにキャンセル
- 完了する前に終了する原因となる R スクリプトのエラー「クォータを超過しました」
- 不完全な結果の切り捨て、R のメモリに読み込まれるデータ

### <a name="memory"></a>Memory

コンピューター上で利用できるメモリの量は、高度な分析アルゴリズムのパフォーマンスに大きな影響を与える場合があります。 メモリが不足している可能性がありますに SQL 計算コンテキストを使用する場合、並列処理の次数に影響します。 また、処理可能なチャンク サイズ (読み取り操作あたりの行数) や、サポートできる同時セッション数にも影響する可能性があります。

32 GB の最小値は強くお勧めします。 ある場合は、32 GB 以上使用可能な場合は、読み取り操作あたりのパフォーマンスを向上させるために複数の行を使用する SQL データ ソースを構成できます。

インスタンスによって使用されるメモリを管理することもできます。 既定では、メモリを割り当てるときに、SQL Server は外部スクリプト プロセスよりも優先されます。 R. に R Services の既定のインストール、使用可能なメモリの 20% のみが割り当てられています。

通常これは十分でないデータ サイエンス タスクでは、SQL server のメモリがたいもです。 実験し、データベース エンジン、関連するサービス、および最適な構成の異なるケースで理解したうえで、外部スクリプトの間のメモリ割り当てを細かく調整する必要があります。

再開-一致するモデルの場合、外部スクリプトの使用状況が負荷の高いとが含まれていないその他のデータベース エンジン サービスが実行中です。そのため、スクリプトのパフォーマンスの最適な構成であった、70% に外部スクリプトに割り当てられたリソースが増加します。

### <a name="power-options"></a>電源オプション

Windows オペレーティング システムで、**高性能**電源オプションを使用する必要があります。 SQL Server を使用する場合、パフォーマンスが低下したり、一貫性のない結果異なる電源設定を使用します。

### <a name="disk-io"></a>ディスク IO

トレーニングと予測の R Services を使用して、ジョブは、本質的に IO バインドでありに、データベースが格納されているディスクの速度によって異なります。 ソリッド ステート ドライブ (SSD) などの高速のドライブが役立つ場合があります。

ディスク IO は、ディスクにアクセスする他のアプリケーションによっても影響を受けます (たとえば、データベースに対して読み取り操作を行う他のクライアントなど)。 またディスク IO のパフォーマンスは、使用されているファイル システムの設定によっても影響を受けることがあります (ファイル システムによって使用されるブロック サイズなど)。

複数のドライブが使用可能な場合は、データベースに格納されている SQL Server データベース エンジンを要求するため、別のドライブ上のデータベースと同じディスク達していないストアを要求します。

トレーニング時に RevoScaleR 分析関数を繰り返し実行する場合も、ディスク IO がパフォーマンスに大きな影響を与える可能性があります。 たとえば、 `rxLogit`、 `rxDTree`、`rxDForest`と`rxBTrees`すべて複数のイテレーションを使用します。 データ ソースが SQL サーバーの場合、これらのアルゴリズムは、データをキャプチャする最適化された一時ファイルを使用します。 これらのファイルは、セッションの完了後に自動的にクリーンアップされます。 読み取り/書き込み操作の高パフォーマンスのディスクを持つと、これらのアルゴリズムの全体的な経過時間を大幅に向上させることができます。

> [!NOTE]
> R Services の以前のバージョンでは、Windows オペレーティング システムの 8.3 ファイル名のサポートが必要です。 この制限は、Service Pack 1 の後に解除されました。 ただし、ドライブが 8.3 ファイル名をサポートするかどうかを確認するか、そうでない場合は、サポートを有効にする fsutil.exe を使用することができます。

### <a name="paging-file"></a>ページング ファイル

Windows オペレーティング システムでは、クラッシュ ダンプの管理や仮想メモリ ページの格納に、ページング ファイルが使用されます。 過度なページングに気付いた場合は、コンピューター上の物理メモリを増やすことを検討してください。 物理メモリを増やしてもページングがなくなるわけではありませんが、ページングの必要性が減ります。

ページ ファイルが格納されるディスクの速度も、パフォーマンスに影響する可能性があります。 ページ ファイルを SSD に格納したり、複数の SSD 間で複数のページ ファイルを使用すると、パフォーマンスを改善できる可能性があります。

ページファイルのサイズ調整方法の詳細については、次を参照してください。 [64 ビット バージョンの Windows の適切なページ ファイル サイズを決定する方法](https://support.microsoft.com/kb/2860880)します。

## <a name="optimizations-at-instance-or-database-level"></a>インスタンスまたはデータベース レベルでの最適化

SQL Server インスタンスの最適化は、外部スクリプトを効率的に実行するキーです。

> [!NOTE]
> 最適な設定は、スコア付けまたはモデルのトレーニングを使用している列の数、データの種類とサイズによって異なります。
> 
> 最終回で特定の最適化の結果を確認することができます。[パフォーマンス チューニング - 結果のケース スタディ](../../advanced-analytics/r/performance-case-study-r-services.md)
> 
> サンプル スクリプトは、個別を参照してください。 [GitHub リポジトリ](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/PerfTuning)します。

### <a name="table-compression"></a>テーブル圧縮

IO パフォーマンスは、圧縮、または列指向データ ストアを使用して多くの場合、改善できます。 一般に、データは多くの場合、繰り返され、テーブル内の複数の列で、データを圧縮するときに、これらの繰り返し利用列ストアを使用しています。

列ストアは、テーブルに多数の挿入がある場合を効率化できない可能性がありますが、データが静的またはのみ変更頻度が低い場合をお勧めします。 列ストアが適切でない場合は、行メジャー テーブルでの圧縮を有効にすることで、IO を改善できる可能性があります。

詳しくは、次の各ドキュメントをご覧ください。

+ [データの圧縮](../../relational-databases/data-compression/data-compression.md)

+ [テーブルまたはインデックスの圧縮を有効にします。](../../relational-databases/data-compression/enable-compression-on-a-table-or-index.md)

+ [列ストア インデックス ガイド](../../relational-databases/indexes/columnstore-indexes-overview.md)

### <a name="memory-optimized-tables"></a>メモリ最適化テーブル

今日では、メモリは、最新のコンピューターの問題ではなくなりました。 ハードウェアの仕様は引き続き向上させるためは、比較的簡単に良好な値に RAM を取得できます。 ただし、同時に、データは、今までよりも迅速に作成されていると、低待機時間でデータを処理する必要があります。

メモリ最適化テーブルでは、ビッグ データの問題に取り組むの高度なコンピューターで利用できる大容量のメモリを利用することで、1 つのソリューションを表します。 メモリ最適化テーブルでデータを読み取ったり、メモリに書き込まれるように、主にメモリに存在します。 耐久性に優れた、テーブルの 2 番目のコピーがディスクに保持され、データベースの復旧中にディスクからデータを読み取るだけです。

読み取りを頻繁にテーブルに書き込む必要がある場合、高いスケーラビリティ、低待機時間とメモリ最適化テーブルを引き起こすことができます。  再開の一致は、メモリ最適化テーブルでの使用は、データベースからすべての再開機能を読み込むし、新しい求人に一致するように、メイン メモリに格納することを許可しました。 これにより、ディスク IO が大幅に減少します。

複数の同時バッチから、データベースを戻す予測を作成中のメモリ最適化テーブルを使用して追加のパフォーマンスの向上を実現されました。 SQL Server でメモリ最適化テーブルの使用には、テーブルの読み取りと書き込みの低待機時間が有効にします。

その経験は開発時にもシームレスです。 持続性のあるメモリ最適化テーブルは、データベースが作成されたのと同時に作成されました。 そのため、開発は、データの保存場所にかかわらず、同じワークフローを使用します。

### <a name="processor"></a>プロセッサ

SQL Server は、マシンで使用可能なコアを使用して並列でタスクを実行することができます。多くのコア、使用可能なパフォーマンスが優れています。 コアの数を増やすことが問題が解決しないバインド IO 操作の中に、CPU は、多くのコアを備えた高速の Cpu からアルゴリズムの特典をバインドします。

サーバーが同時に使用して複数のユーザー通常ため、データベース管理者必要があります理想的なピーク ワークロード計算をサポートするために必要なコア数を決定します。

### <a name="resource-governance"></a>リソース ガバナンス

リソース ガバナーをサポートするエディションでは、特定のワークロードが Cpu の数はいくつかに割り当てられていることを指定するのにリソース プールを使用できます。 特定のワークロードに割り当てられたメモリの量を管理することもできます。

SQL Server でのリソース ガバナンス R. と SQL Server で使用されるさまざまなリソースを監視および管理を一元化できます。たとえば、サービスが一時的に重いワークロードもいつでも実行できますその中核となることを確認する、データベース エンジンの半分の使用可能なメモリを割り当てます。

外部スクリプトによるメモリ消費の既定値は、SQL Server 自体の使用可能なメモリの合計の 20% に制限されます。 この制限は、既定では、データベース サーバーに依存するすべてのタスクは深刻な影響を受けないこと実行時間の長い R ジョブを確実に適用されます。 ただし、これらの制限はデータベース管理者によって変更することもできます。 多くの場合では、20% の制限は深刻な機械学習のワークロードをサポートするのに十分ではありません。

サポートされる構成オプションは**MAX_CPU_PERCENT**、 **MAX_MEMORY_PERCENT**、および**MAX_PROCESSES**します。 現在の設定を表示するには、このステートメントを使用します。 `SELECT * FROM sys.resource_governor_external_resource_pools`

-  サーバーは、主に、R Services の使用に MAX_CPU_PERCENT を 40% や 60% に増やすことが考えられます。

-  多くの R セッションでは、同時に同じサーバーを使用する必要があります、3 つすべての設定を増やす必要があります。

割り当てられるリソースの値を変更するには、T-SQL ステートメントを使用します。

+ このステートメントでは、メモリ使用量を 40% に設定します。 `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_MEMORY_PERCENT = 40)`

+ このステートメントは、次の 3 つすべての構成可能な値を設定します。 `ALTER EXTERNAL RESOURCE POOL [default] WITH (MAX_CPU_PERCENT = 40, MAX_MEMORY_PERCENT = 50, MAX_PROCESSES = 20)`

+ メモリ、CPU、または最大プロセスの設定を変更し、設定をすぐに適用する場合は、このステートメントを実行します。 `ALTER RESOURCE GOVERNOR RECONFIGURE`

## <a name="soft-numa-hardware-numa-and-cpu-affinity"></a>ソフト NUMA、ハードウェア NUMA、CPU アフィニティ

を計算コンテキストとして SQL Server を使用する場合は、NUMA、プロセッサ アフィニティに関連する設定をチューニングすることによってパフォーマンスを向上させる場合があります実現できます。 

システムで_ハードウェア NUMA_プロセッサの小さなセットを提供している各 1 つ以上のシステム バスがあります。 各 CPU は、一貫した方法で他のグループに関連付けられているメモリにアクセスできます。 この CPU の各グループのことを NUMA ノードと呼びます。 ハードウェア NUMA を使用する場合は、NUMA ではなくインターリーブされたメモリを使用するように構成できます。 その場合は、Windows と SQL Server のためはいない NUMA として認識します。 

SQL Server で使用できるメモリ ノードの数を検索する次のクエリを実行することができます。

```sql
SELECT DISTINCT memory_node_id
FROM sys.dm_os_memory_clerks
```

クエリが 1 つのメモリ ノード (ノード 0) を返す場合は、ハードウェア NUMA がないか、またはハードウェアがインターリーブ (非 NUMA) として構成されています。 SQL Server では、ハードウェア NUMA も無視されますと 4 つ以下の Cpu が、少なくとも 1 つのノードに 1 つだけの CPU がある場合、または。

コンピューターが複数のプロセッサがハードウェア NUMA がない場合も使える[ソフト NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server) Cpu をより小さなグループに分割します。  SQL Server 2016 および SQL Server 2017 の両方でソフト NUMA 機能は、SQL Server サービスを開始するときに自動的に有効です。

ソフト NUMA を有効にすると、SQL Server は、ノードを自動的には管理します。ただし、特定のワークロード用の最適化を無効にできます_ソフト アフィニティ_し、ソフト NUMA ノードの CPU 関係を手動で構成します。 これは、ことができます、どのノードに割り当てられているワークロードの詳細に制御リソース管理をサポートする SQL Server のエディションを使用している場合に特に。 CPU 関係を指定して、Cpu のグループとリソース プールのアラインメント、によって、待機時間を短縮し、関連するプロセスが、同じ NUMA ノード内で実行されることを確認できます。

ソフト NUMA と R のワークロードをサポートするために CPU 関係を構成するための全体的なプロセスは次のとおりです。

1. 使用可能な場合に、ソフト NUMA を有効にします。
2. プロセッサのアフィニティを定義します。
3. リソース プールを使用して、外部のプロセスを作成する[リソース ガバナー](../r/resource-governance-for-r-services.md)
4. 割り当てる、[ワークロード グループ](../../relational-databases/resource-governor/resource-governor-workload-group.md)アフィニティ グループを特定する

サンプル コードを含む詳細については、このチュートリアルを参照してください。[SQL の最適化のヒントとテクニック (Ke Huang)](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

**その他のリソース:**

+ [SQL Server でのソフト NUMA](https://docs.microsoft.com/sql/database-engine/configure-windows/soft-numa-sql-server)
    
    Cpu をソフト NUMA ノードをマップする方法

+ [自動ソフト NUMA:高速化 (Bob Ward) を実行します。](https://blogs.msdn.microsoft.com/bobsql/2016/06/03/sql-2016-it-just-runs-faster-automatic-soft-numa/)

   履歴をについて説明します。 以降のマルチコア サーバーでパフォーマンスの実装の詳細とします。

## <a name="task-specific-optimizations"></a>タスク固有の最適化

このセクションでこれらのケース スタディ、および特定の機械学習のワークロードを最適化するための他のテストで採用しているメソッドをまとめたものです。 一般的なワークロードには、モデルのトレーニング、特徴を抽出し、特徴エンジニア リング、およびスコアリングのためのさまざまなシナリオが含まれます。 単一行、小さなバッチ、および大規模なバッチ。

### <a name="feature-engineering"></a>機能エンジニアリング

R の問題点の 1 つは、1 つの CPU の処理は通常です。 これは、多くのタスクの主要なパフォーマンスのボトルネック、特に特徴エンジニア リングします。 再開の一致のソリューションでは、だけで、特徴エンジニア リング タスクは、する最初の 100 の機能と組み合わせる必要があった 2,500 のクロス積の機能を作成します。 このタスクで、単一の CPU ですべてが完了した場合、かなりの時間がかかる場合があります。

特徴エンジニア リングのパフォーマンスを向上させるために複数の方法はあります。 R コードを最適化し、モデリング プロセス内での特徴の抽出を保持するか、機能エンジニア リング プロセスを SQL に移動します。

- R を使用関数を定義し、引数として渡します[rxTransform](https://docs.microsoft.com/r-server/r-reference/revoscaler/rxtransform)トレーニング中にします。 モデルでは、並列処理をサポートする場合、複数の Cpu を使用して特徴エンジニア リング タスクを処理できます。 このアプローチを使用して、データ サイエンス チームは時間をスコア付けの観点から 16% のパフォーマンスの向上を観察しました。 ただし、このアプローチでは、並列処理と並列プランを使用して実行できるクエリをサポートするモデルが必要です。

- R を使用して、sql では、コンテキストを計算します。 個別のバッチの実行で使用できるリソースの分離を使用するマルチプロセッサ環境では、バッチごとのテーブルからデータを抽出し、同じワークロード グループのデータを制限するために使用する SQL クエリを分離することで効率を実現できます。 バッチを分離するために使用メソッドは、パーティション分割を含めるし、分離したクエリを並列に実行する PowerShell の使用します。

- アドホックの並列実行します。SQL Server のコンピューティング コンテキストでは、並列実行可能であればより効率的なオプションが見つからないかどうかに適用する SQL データベース エンジンを利用できます。

- 独立した特徴の生成プロセスで T-SQL を使用します。 SQL を使用してデータを機能で一般に高速です。

### <a name="prediction-scoring-in-parallel"></a>並列 (スコア付け) 予測

SQL Server の利点の 1 つは、膨大な量の並列内の行を処理する機能です。 それに遠く及ばず、この利点マークされているスコアリングのようにします。 一般に、モデル必要はありませんすべてのデータへのアクセス、スコア付けため、各ワークロード グループを 1 つのタスクを処理すると、入力データをパーティション分割できます。

1 つのクエリとして、入力データを送信することもでき、SQL Server はクエリを分析します。 入力データの並列クエリ プランを作成する場合、ノードに割り当てられているデータをパーティション分割自動的にし並列も必要な結合と集計を実行します。

スコア付けで使用するためのストアド プロシージャを定義する方法の詳細に関心がある場合に、サンプル プロジェクトを参照してください[GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips/SQLR)し"step5_score_for_matching.sql"ファイルを探します。 サンプル スクリプトも追跡クエリの開始と終了時刻、および書き込み、SQL コンソールにかかる時間パフォーマンスを評価するようにします。

### <a name="concurrent-scoring-using-resource-groups"></a>リソース グループを使用して同時実行とスコア付け

スケール アップ、スコア付けの問題には、何百万もの項目が複数のバッチに分割する map-reduce アプローチを採用するを勧めします。 次に、複数のスコア付けジョブが同時に実行されます。 このフレームワークで、バッチは、異なる CPU で処理され、結果が収集され、データベースに書き戻す。

これは、再開-一致するシナリオで使用されるアプローチです。ただし、SQL Server でのリソース ガバナンスは、このアプローチの実装に不可欠です。 外部スクリプト ジョブのワークロード グループをセットアップして R ジョブを複数のプロセッサ グループにスコア付けをルーティングし、高速なスループットを実現できます。

リソース ガバナンスが割り当てることができます (CPU およびメモリ) ワークロードの競合を最小限に抑えるには、サーバーで使用可能なリソースを分割します。 分類子関数を設定するには、R ジョブの種類を区別するために: ことから、アプリケーションは常に呼び出されるスコア付け、優先、再トレーニング ジョブが優先度の低いなどあります。 このリソースの分離は、実行時間を向上させる可能性があるとより予測可能なパフォーマンスを提供します。

### <a name="concurrent-scoring-using-powershell"></a>PowerShell を使用して同時実行とスコア付け

自分でデータをパーティション分割する場合は、複数の同時実行のスコア付けタスクを実行する PowerShell スクリプトを使用できます。 これを行うには、Invoke-sqlcmd コマンドレットを使用し、スコア付けのタスクを並列を開始します。

再開の一致では、同時実行は、次のように設計されました。

- 20 のプロセッサは、5 つの Cpu の 4 つのグループに分かれています。 Cpu の各グループは、同じ NUMA ノードにあります。

- 同時実行のバッチの最大数は、8 に設定されました。

- 各ワークロード グループには、2 つのスコア付けタスクを処理する必要があります。 データとスコア付けの開始を読み取り中に 1 つのタスクが完了したら、すぐ、他のタスクは、データベースからデータの読み取りを開始できます。

このシナリオ用の PowerShell スクリプトを表示するでファイル experiment.ps1 を開き、 [Github プロジェクト](https://github.com/Microsoft/SQL-Server-R-Services-Samples/tree/master/SQLOptimizationTips)します。

### <a name="storing-models-for-prediction"></a>予測モデルを格納します。

最適なモデルを選択したは、トレーニングと評価が完了すると、予測で使用されるように、データベースにモデルを格納するをお勧めします。 予測のデータベースからの事前計算済みのモデルの読み込みは、SQL Server machine learning では、特別なシリアル化のアルゴリズムを使用して格納し、R とデータベースの間を移動するときに、モデルを読み込むために、効率的です。

> [!TIP]
> SQL Server 2017 では、R がサーバーにインストールされていない場合でもスコアリングを実行するのに、PREDICT 関数を使用できます。 RevoScaleR パッケージから、限られたモデルの種類がサポートされます。

ただし、に応じて、アルゴリズムを使用する、いくつかのモデルがあります非常に大きく、特に大規模なデータ セットでトレーニングする場合。 などのアルゴリズムなど**lm**または**glm**ルールと共に概要データの多くを生成します。 Varbinary 列に格納できるモデルのサイズに制限があるために、モデルを運用環境のデータベースに保存する前に、モデルから不要な成果物を除去することをお勧めします。

## <a name="articles-in-this-series"></a>このシリーズの記事

[パフォーマンス チューニング - R の概要](../r/sql-server-r-services-performance-tuning.md)

[R で SQL Server の構成のパフォーマンス チューニング](../r/sql-server-configuration-r-services.md)

[R の R のパフォーマンス チューニング コードとデータの最適化](../r/r-and-data-optimization-r-services.md)

[パフォーマンス チューニング - 結果のケース スタディ](../r/performance-case-study-r-services.md)
