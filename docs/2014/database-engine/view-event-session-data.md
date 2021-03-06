---
title: イベント セッション データを表示 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ac742a01-2a95-42c7-b65e-ad565020dc49
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: befef498ab4cda12ce38a34678b78a2b5dcd278c
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120299"
---
# <a name="view-event-session-data"></a>イベント セッション データの表示
  このトピックでは、表示のユーザー インターフェイスを使用して、拡張イベント データを表示および分析する方法について説明します。  
  
-   [ターゲット データの表示]  
  
-   データの処理  
  
## <a name="view-target-data"></a>[ターゲット データの表示]  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]内で指定したターゲットに収集されたデータを表示することができます。  
  
### <a name="view-target-data"></a>ターゲット データの表示  
 ターゲット データを表示するには:  
  
1.  オブジェクト エクスプローラーで、 **[管理]**、 **[拡張イベント]**、 **[セッション]** の順に展開し、セッションを展開します。  
  
2.  ターゲット名を右クリックし、 **[ターゲット データの表示]** をクリックしてターゲット データを表示します。  
  
     既定のビューにターゲット データ ウィンドウが表示され、ターゲット データが表示されます。  
  
 ターゲット データを表示する際の注意事項:  
  
-   ETW ターゲットに対しては、ターゲット データを利用できません。  
  
-   ring_buffer データを XML 形式で表示するには、ターゲット データ ウィンドウで **[ring_buffer ターゲット データ]** リンクをクリックします。 XML エディターに ring_buffer.xml ファイルが表示されます。  
  
-   event_file ターゲットの場合、ファイル ターゲット データ (.XEL ファイル) を表示するには、次のいずれかの方法を使用します。  
  
    -   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] で [ファイル] -> [開く] を使用する。  
  
    -   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]にファイルをドラッグ アンド ドロップする。  
  
    -   .XEL ファイルをダブルクリックする。  
  
    -   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で、実行中の拡張イベント セッションを右クリックし、[ターゲット データの表示] をクリックする。  
  
    -   [fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)  
  
    -   1 つ以上を表示することができます。XEL ファイルを選択して**拡張イベント ファイルの結合**ファイルから、開く メニュー。  
  
### <a name="watching-live-data"></a>ライブ データの監視  
 キャプチャされているライブ データを監視することができます。  
  
-   オブジェクト エクスプローラーで **[管理]** ノード、 **[拡張イベント]** ノード、および **[セッション]** ノードの順に展開します。  
  
-   セッション名を右クリックし、 **[ライブ データの監視]** をクリックしてトレース データを表示します。  
  
     既定の表示列は、 **Event Name** と **TimeStamp**です。  
  
     トレース ウィンドウに列を追加するには、[拡張イベント] ツール バーで **[列の選択]** をクリックします。 **[詳細]** タブに選択したイベントのすべてのイベント情報が表示されます。  
  
     イベントは通常、約 30 秒間表示されます。 待機時間を変更するには、 **[新しいセッション]** ダイアログの **[詳細設定]** ページで **[ディスパッチの最大待機時間]** を変更します。  
  
### <a name="to-refresh-target-data"></a>ターゲット データを更新するには  
 event_files ターゲットでは、ターゲット データの更新はサポートされていません。  
  
1.  ターゲット データが自動的に更新されるようにするには、ターゲット データを右クリックして **[更新間隔]** をクリックし、更新間隔の一覧から更新間隔を選択します。  
  
2.  自動更新を一時停止または再開するには、ターゲット データを右クリックし、 **[一時停止]** または **[再開]** をクリックします。  
  
3.  ターゲット データを手動で更新するには、ターゲット データを右クリックし、 **[更新]** をクリックします。  
  
## <a name="working-with-data"></a>データの処理  
 拡張イベント ユーザー インターフェイスの分析機能を使用すると、問題を特定することができます。  
  
### <a name="details-pane"></a>[詳細] ペイン  
 **[詳細]** ペインには、フィールドとアクションを含め、選択したイベントのすべての列が表示されます。 ターゲット データ テーブルに列を追加するには、 **[詳細]** ペインで行を右クリックし、 **[テーブルの列を表示する]** をクリックします。  
  
### <a name="create-modify-or-delete-merged-columns"></a>結合列の作成、変更、および削除  
 結合列を使用すると、一連のフィールドを結合して、1 つの列に表示することができます。 結合列には、NULL 以外の最初のフィールドのデータが、フィールド リストに追加されたときの順序で表示されます。 これは、イベントに応じて異なるデータが特定の列に表示される [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler の表示に似ています (これの最も一般的な例は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler の TextData フィールドです)。 たとえば、sql_statement_completed イベントのステートメントと sql_batch_completed イベントの batch_text フィールドを myStatement という名前のフィールドに結合できます。 テーブルに myStatement 列を表示すると、関連付けられているイベントの適切なデータが表示されます。  
  
 結合列を作成、変更、または削除するには、次の手順を実行します。  
  
1.  .XEL ファイルを開いてトレース結果を表示します (セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません)。  
  
2.  トレース結果ウィンドウで、列見出しを右クリックして、 **[列の選択]** をクリックします。  
  
 結合列を作成するには、 **[列の選択]** ダイアログ ボックスで、 **[新規作成]** をクリックします。  **[新しい結合列]** ダイアログで、結合列の名前を付け、結合列に含める元の列を選択します。  
  
 結合列を編集するには、 **[列の選択]** ダイアログで、結合列を選択し、 **[編集]** をクリックします。 **[結合列の編集]** ダイアログで、結合列の名前や結合列に含める元の列を変更します。  
  
 結合列を削除するには、 **[列の選択]** ダイアログで、結合列を選択し、 **[削除]** をクリックします。  
  
### <a name="filter-results"></a>結果へのフィルターの適用  
 トレース結果を表示します。フィルターを適用することで、トレース ウィンドウに表示されるトレース結果を絞り込むことができます。 表示フィルターには、時間フィルターと高度なフィルターが含まれています。 時間フィルターではトレース結果をイベントのタイムスタンプでフィルター処理し、高度なフィルターではイベントのフィールドとアクションを使用してフィルター条件を作成します。 時間フィルターと高度なフィルターとの間には "and" 関係があります。  
  
 フィルターを作成するには:  
  
1.  .XEL ファイルを開いてトレース結果を表示します (セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません)。  
  
2.  トレース結果ウィンドウでフィルターを選択し、 **[拡張イベント]** ツール バーの **[フィルター]** をクリックします。  
  
3.  **[フィルター]** ダイアログ ボックスで **[時間フィルターの設定]** をクリックし、スライダー バーをドラッグするか、編集ボックスの時間を変更することにより時間フィルターを設定します。  
  
4.  **[追加のフィルター]** セクションでフィルター条件を適用し、 **[適用]** をクリックします。  
  
### <a name="sort-results"></a>結果の並べ替え  
 結果を昇順または降順に並べ替えるには:  
  
1.  .XEL ファイルを開いてトレース結果を表示します (セッション名を右クリックし、 **[ライブ データの監視]** をクリックして、ツール バーの **[データ フィードの停止]** をクリックします)。  
  
2.  トレース結果ウィンドウで、並べ替える列の見出しを右クリックし、 **[昇順で並べ替え]** または **[降順で並べ替え]** をクリックします。  
  
 また、列見出しをクリックして並べ替え順を切り替えることもできます。  
  
 列がグループ化されている場合、データはグループ内のみで並べ替えられます。  
  
### <a name="group-results"></a>結果のグループ化  
 結果のグループ化は、[!INCLUDE[tsql](../includes/tsql-md.md)] の `GROUP BY` 句と同等の機能です。 ターゲット データ テーブルにはグループ化されたデータが表示され、データの展開と折りたたみを行うことができます。  
  
 データは、集計する前にグループ化する必要があります。 たとえば、query_hash 値でグループ化し、実行時間を基準に降順に並べ替え、各グループの平均実行時間を取得した後、集計を基準に降順に並べ替えることができます。  これにより生成された一覧には、平均実行時間が長い方から順に並べ替えられた一意のステートメントの一覧が表示されます。 一番上のグループを展開すると、そのクエリの個々の実行時間が長い方から順に表示されます。  
  
 1 つの列または複数の列で結果をグループ化できます。  
  
 .XEL ファイルを開いてトレース結果を表示します (セッション名を右クリックし、 **[ライブ データの監視]** をクリックして、ツール バーの **[データ フィードの停止]** をクリックします)。  
  
 1 つの列で結果をグループ化するには、トレース結果ウィンドウで、列見出しを右クリックし、 **[この列でグループ化]** をクリックします。 グループ化を解除するには、行の 1 つを選択し、 **[すべてのグループを削除]** をクリックします。  
  
 複数の列で結果をグループ化するには、 **[拡張イベント]** ツール バーの **[グループ化]** をクリックします。 **[グループ化]** ダイアログの **[使用可能な列]** ボックスでグループ化する列を選択し、選択した列を **[次の条件でグループ化される列]** ボックスに移動します。 順序を変更するには、 **[次の条件でグループ化される列]** ボックスで上矢印または下矢印をクリックします。  
  
### <a name="aggregate-results"></a>結果の集計  
 トレース結果を表示できます。また、結果の列を集計することにより、イベント データをさらに詳細に分析できます。 拡張イベントは次の 5 つの集計関数をサポートします。  
  
-   sum  
  
-   min  
  
-   max  
  
-   平均  
  
-   count  
  
 sum、min、max、および average は、数値列のみで使用できます。 count は、グループ内の選択した列に存在する NULL 以外の値の数を表します。  
  
 集計はグループに対して実行されるため、集計を実行する前に結果をグループ化する必要があります。 結果を集計するには:  
  
1.  .XEL ファイルを開いてトレース結果を表示します (セッション名を右クリックし、 **[ライブ データの監視]** をクリックして、ツール バーの **[データ フィードの停止]** をクリックします)。  
  
2.  **[拡張イベント]** ツール バーの **[集計]** をクリックします。 集計に使用できる列が [集計] ダイアログ ボックスに表示されます。  
  
3.  **[集計の種類]** 列で、集計の種類を選択します。  
  
4.  **[集計の並べ替え]** ボックスで、並べ替え列を選択します。 次に、昇順または降順を選択します。  
  
### <a name="search-for-text-in-columns"></a>列のテキストの検索  
 列のテキストを検索するには、次の手順を実行します。  
  
1.  .XEL ファイルを開いてトレース結果を表示します (セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません)。  
  
2.  **[拡張イベント]** ツール バーの **[検索]** をクリックします。  
  
3.  **[拡張イベントで検索]** ダイアログ ボックスの **[検索する文字列]** ボックスに、検索テキストを入力します。 ドロップダウン リストから直前の 20 回の検索文字列の 1 つを選択することができます。  
  
4.  **[検索対象]** ボックスで、指定したテキストを検索する場所を選択します。 次の検索オプションを使用できます。  
  
    -   [テーブル列]。 トレース ウィンドウに表示されているすべての列を検索するには、このオプションを使用します。  
  
    -   [詳細]。 このオプションを使用して開始する前に選択されたトレース ウィンドウに (昇格および未昇格の) すべての列を検索、**拡張イベントで検索** ダイアログ ボックス。  
  
    -   *Event_column_name*。 ドロップダウン リストから特定のイベント列で検索するには、このオプションを使用します。  
  
5.  検索の定義方法を指定するには、次のオプションを使用します。  
  
    -   [大文字と小文字を区別する]。 [検索する文字列] で入力したテキストに大文字と小文字の違いを含めて完全に一致する検索結果を表示するには、このオプションを使用します。  
  
    -   [単語単位]。 入力したテキストに単語単位で一致する検索結果のみを表示するには、このオプションを使用します。  
  
    -   [上へ検索]。 カーソル位置から先頭までを検索するには、このオプションを使用します。  
  
    -   [使用]。 [検索する文字列] ボックスに入力された特殊文字および正規表現を解釈するには、このオプションを使用します。 特殊文字には 1 文字以上を表すワイルドカード文字 (*) および (?) が含まれます。 正規表現は、検索テキストのパターンを定義する特殊な表記です。  
  
    -   **[次を検索]** をクリックすると、 **[検索する文字列]** で入力したテキストの次の箇所が検索されます。  
  
### <a name="bookmarks"></a>ブックマーク  
 行に簡単に戻ることができるようにするには、ターゲット データの 1 つまたは複数の行にブックマークを付けます。 ブックマークを変更するには、行を右クリックします。 ブックマークが付いている行に移動するには、 **[拡張イベント]** ツール バーの [戻る] および [次へ] を使用します。  
  
### <a name="change-display-settings"></a>表示設定の変更  
 トレース結果の列情報 (列の順番、結合列、および列幅) とフィルター情報は、拡張イベント表示設定ファイル (.viewsetting ファイル) に保存することができます。 ファイルを保存した後、トレース結果に適用することによって、ビューを変更することができます。  
  
 表示設定を変更するには:  
  
1.  .XEL ファイルを開いてトレース結果を表示します (セッション名を右クリックして、 **[ライブ データの監視]** をクリックしてもかまいません)。  
  
2.  **[拡張イベント]** ツール バーで、 **[表示設定]** をクリックします。 ドロップダウン リストから次のいずれかのオプションを選択します。  
  
    -   [名前を付けて保存]。 トレース結果の列情報とフィルター情報を .viewsetting ファイルに保存します。  
  
    -   開く。 既存の .viewsetting ファイルを開きます。  
  
    -   [最近使用した項目を開く]。 最近保存した .viewsetting ファイルを開きます。  
  
### <a name="copy-or-export-trace-results"></a>トレース結果のコピーまたはエクスポート  
 トレース結果から選択した行にセル、行、および詳細をコピーできます。 トレース結果を次のものにエクスポートすることもできます。  
  
-   .XEL ファイル  
  
-   テーブル  
  
-   .CSV ファイル  
  
 トレース結果をコピーするには、セルまたは行 (行は複数可) を選択し、右クリックして、 **[コピー]** をクリックし、 **[セル]**、 **[行]**、または **[詳細]** をクリックします。 拡張イベントは、最大 1000 行のコピーをサポートしています。  
  
 トレース結果を .XEL ファイル、テーブル、または .CSV ファイルにエクスポートするには、 **で** [拡張イベント] **メニュー オプションの** [エクスポート先] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]をクリックします。  
  
### <a name="view-a-deadlock-graph-and-query-plans"></a>Deadlock Graph とクエリ プランの表示  
 [詳細] ペインで **xml_deadlock_report** のデッドロック グラフを表示して、デッドロックのトラブルシューティングを行うことができます。 次のイベントのクエリ プラン グラフを表示することもできます。  
  
-   query_post_compilation_showplan  
  
-   query_pre_execution_showplan  
  
-   query_post_execution_showplan  
  
 デッドロック グラフを表示するには:  
  
-   オブジェクト エクスプローラーで **[管理]** ノード、 **[拡張イベント]** ノード、および **[セッション]** ノードの順に展開します。  
  
-   表示する構成されたデッドロック イベントが含まれているセッションを右クリックして、 **[ライブ データの監視]** をクリックします。  
  
-   デッドロック イベントを選択して、[詳細] ペインの **[デッドロック]** タブでグラフを表示します。  
  
 クエリ プラン グラフを表示するには:  
  
1.  オブジェクト エクスプローラーで **[管理]** ノード、 **[拡張イベント]** ノード、および **[セッション]** ノードの順に展開します。  
  
2.  表示する構成されたクエリ プラン グラフ (query_post_compilation_showplan など) が含まれているセッションを右クリックして、 **[ライブ データの監視]** をクリックします。  
  
3.  クエリ プラン グラフ イベント (query_post_compilation_showplan など) を選択して、[詳細] ペインの **[クエリ プラン]** タブでグラフを表示します。  
  
  
