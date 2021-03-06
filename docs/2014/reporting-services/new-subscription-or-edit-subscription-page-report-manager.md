---
title: 新しいサブスクリプションまたは編集のサブスクリプション ページ (レポート マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: e02d6529-ce67-4305-b7f0-433997e99c21
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a6194516bfc230c73df928bda5095c106776beff
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030133"
---
# <a name="new-subscription-or-edit-subscription-page-report-manager"></a>[新しいサブスクリプション] ページまたは [サブスクリプションの編集] ページ (レポート マネージャー)
  [新しいサブスクリプション] ページまたは [サブスクリプションの編集] ページでは、レポートに新しいサブスクリプションを作成したり、既存のサブスクリプションを変更したりできます。 このページに表示されるオプションは、ロールの割り当てによって異なります。 高度な権限を持つユーザーは、追加のオプションを使用して作業できます。  
  
 サブスクリプションは、自動的に実行できるレポートでサポートされています。 少なくとも、レポートでは、格納された資格情報を使用するか、資格情報を使用しないようにする必要があります。 レポートでパラメーターを使用する場合、既定値を指定する必要があります。 レポート実行の設定を変更したり、パラメーター プロパティで使用される既定値を削除したりすると、サブスクリプションが非アクティブになることがあります。 詳細については、「 [ネイティブ モード レポート サーバーのサブスクリプションの作成と管理](../../2014/reporting-services/create-manage-subscriptions-native-mode-report-servers.md)」を参照してください。  
  
> [!NOTE]  
>  この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 エディションでサポートされている機能の一覧については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を参照してください[機能は、SQL Server 2014 の各エディションでサポートされている](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)します。  
  
## <a name="navigation"></a>ナビゲーション  
 ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。  
  
### <a name="to-open-the-new-subscription-or-edit-subscription-page"></a>新しいサブスクリプション ページまたはサブスクリプションの編集ページを開くには  
  
1.  レポート マネージャーを開き、サブスクリプションを追加するレポートを探します。  
  
2.  レポートの上にマウス ポインターを移動し、下矢印をクリックします。  
  
3.  ドロップダウン メニューで次のいずれかの操作を行います。  
  
    -   **[管理]** をクリックします。 この操作により、レポートの [全般] プロパティ ページが開きます。 **[サブスクリプション]** タブをクリックします。ツール バーで、 **[新しいサブスクリプション]** をクリックするか、既存のサブスクリプションを選択して **[編集]** をクリックします。  
  
    -   **[サブスクライブ]** をクリックします。 この操作により、レポートの **[新しいサブスクリプション]** ページが開きます。  
  
## <a name="options"></a>および  
 **によって提供されます。**  
 レポートの配信に使用する配信拡張機能を選択します。 選択した配信拡張機能に応じて、次の設定が表示されます。  
  
-   電子メール サブスクリプションによって、電子メール ユーザーがよく使用するフィールド ( **[宛先]** フィールド、 **[件名]** フィールド、 **[優先度]** フィールドなど) が表示されます。 レポートを埋め込むか添付するには、 **[レポートを含める]** を指定します。レポートに URL を含めるには、 **[リンクを含める]** を指定します。 添付または埋め込みをするレポートの表示形式を選択するには、 **[表示形式]** を指定します。  
  
-   ファイル共有サブスクリプションには、配信先の場所を指定できるフィールドがあります。 ファイル共有には任意のレポートを配信できます。 ただし、対話機能をサポートするレポート (たとえば、対応する行と列へのドリル ダウンをサポートするマトリックス形式のレポート) は、静的ファイルとして表示されます。 静的ファイルに行と列のドリル ダウンを表示することはできません。 汎用名前付け規則 (UNC) 形式でファイル共有名を指定する必要があります (たとえば、 \\\mycomputer\public\myreportfiles)。 パス名の末尾に円記号を含めないでください。 レポート ファイルは、表示形式に基づくファイル形式で配信されます (たとえば、 **[Excel]** を選択した場合、レポートは .xls ファイルとして配信されます)。  
  
 配信拡張機能を使用できるかどうかは、配信拡張機能がレポート サーバーにインストールおよび構成されているかどうかによって決まります。 レポート サーバーの電子メールは、既定の配信拡張機能ですが、使用する前に構成する必要があります。 ファイル共有配信は構成の必要はありませんが、共有フォルダーは使用前に定義が必要です。  
  
## <a name="subscription-processing-options"></a>サブスクリプション処理のオプション  
 これらの設定を使用して、サブスクリプションが処理される条件を定義します。 一部のオプションは、パラメーターを使用するレポートまたはレポート実行スナップショットとして実行するレポートのみに利用できます。  
  
 **レポート コンテンツの更新時**  
 スケジュールどおりに更新されるレポート スナップショットをサブスクライブするには、このオプションを選択します。 このオプションは、レポート実行スナップショットとして実行するレポートをサブスクライブしているときにのみ表示されます。 通常、レポート実行スナップショットの内容はスケジュールどおりに更新されます。 このモードで実行するレポートは、スナップショットの更新時にサブスクリプションを実行するように定義できます。  
  
 **スケジュールされたレポートの実行が完了したとき**  
 サブスクリプションの処理日時を決定するスケジュールを作成します。  
  
 **共有スケジュールで実行**  
 定義済みスケジュールを選択して、サブスクリプションを処理します。  
  
 **パラメーターの値を入力します**  
 パラメーターを使用するレポートをサブスクライブしている場合にこのオプションを使用します。 このオプションは、パラメーター化されたレポートにのみ使用できます。 パラメーター化されたレポートをサブスクライブしている場合、サブスクリプションを使用して配信されるバージョンのレポートを作成するときに使用するパラメーター値を指定できます。 たとえば、地域コードを指定して特定の地域の売上データを選択できます。 値を指定しない場合は、既定値が使用されます。  
  
## <a name="see-also"></a>参照  
 [レポート サーバー電子メール配信用に構成&#40;SSRS 構成マネージャー&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)   
 [レポート マネージャー F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
