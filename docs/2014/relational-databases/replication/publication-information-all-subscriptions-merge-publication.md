---
title: パブリケーション情報、[すべてのサブスクリプション] (マージ パブリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.merge.f1
ms.assetid: 0f4fa946-a0d9-4d3b-b90b-53503c40fba2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 13c1acf24212a236eae5e377a7febfd398e579c3
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54135922"
---
# <a name="publication-information-all-subscriptions-merge-publication"></a>パブリケーション情報、[すべてのサブスクリプション] (マージ パブリケーション)
  **[すべてのサブスクリプション]** タブには、選択したマージ パブリケーションに対するすべてのサブスクリプションの情報が表示されます。  
  
## <a name="options"></a>および  
 サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **並べ替え**:1 つ以上の列で並べ替え、**列の並べ替え** ダイアログ ボックス。  
  
-   **表示する列を選択**:列の表示とその表示順序を選択、**列の選択** ダイアログ ボックス。  
  
-   **フィルター**:列の値に基づいてグリッドの行をフィルター選択、**フィルター設定** ダイアログ ボックス。  
  
-   **フィルターのクリア**:グリッドのすべてのフィルター設定をオフにします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 **[表示]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。 サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。 たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。  
  
 **ステータス**  
 各サブスクリプションの状態です。これは、マージ エージェントの状態により決定されます。  
  
 既定では、サブスクリプションの情報を表示するグリッドは **[状態]** 列の順序で並べられています (同じ状態のサブスクリプションは、 **[パフォーマンス]** 列の順序で並べられています)。 表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。  
  
-   [エラー]  
  
-   [パフォーマンス クリティカル] \([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [長期マージ] \([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [まもなく期限切れ/期限切れ] \([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [初期化されていないサブスクリプション] \([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ)  
  
-   [失敗したコマンドの再試行]  
  
-   [同期中]  
  
-   [同期されていません]  
  
 特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。 たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。  
  
 状態値 **[パフォーマンス クリティカル]**、 **[長期マージ]**、 **[まもなく期限切れ/期限切れ]**、および **[初期化されていないサブスクリプション]** は警告です。 警告が表示される場合、 **[状態]** 列にはエージェントが同期中かどうかも表示されます。 たとえば、 **[同期中]、[パフォーマンス クリティカル]** という形で状態が表示されます。  
  
 状態値 **[まもなく期限切れ/期限切れ]** および **[長期マージ]** は、しきい値が設定されている場合のみ表示されます。 **[パフォーマンス クリティカル]** の状態の値は、同じ種類の接続 (ダイヤルアップまたは LAN) によるサブスクリプションの同期が 5 回行われた後にのみ表示されます。 パフォーマンスの測定としきい値の設定については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) と「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。  
  
 **サブスクリプション**  
 サブスクリプションごとに、フォームでの名前:*SubscriberName:SubscriptionDatabaseName*します。  
  
 **表示名**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。 各サブスクリプションの説明です。 この説明は、 **[サブスクリプションのプロパティ]** ダイアログ ボックスで入力するか、 **@description** または [sp_addmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql) の [@description](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql)と表示されます。 多くの場合、この説明は "表示名"、つまりサブスクリプションの通称として使用されます。  
  
 **[パフォーマンス]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。 各サブスクリプションのパフォーマンス評価です。これはレプリケーション モニターにより取得された、最新の配信率の計測結果に基づいています。 パフォーマンス評価は、接続の種類が同じ (ダイヤルアップまたは LAN) パブリケーションに対するサブスクリプションの履歴の平均パフォーマンスと、個々のサブスクリプションのパフォーマンスを比較することで決定されます。 レプリケーション モニターには、50 以上の変更を伴う同期がそれぞれ同じ種類の接続により 5 回行われた後で、値が表示されます。 50 以上の変更を伴う同期が 5 回未満の場合、または最新の同期における変更が 50 未満の場合には、この列は空白になります。  
  
> [!NOTE]  
>  パフォーマンスは、 **[接続]** 列に表示される接続の種類に基づいて決まります。したがって、配信率が低いサブスクリプションが低速の接続で同期されている場合、配信率が高いサブスクリプションよりも高いパフォーマンスが表示される可能性があります。  
  
 パフォーマンス評価は、次のいずれかの値になります。  
  
-   [非常に良い]  
  
-   [良い]  
  
-   [普通]  
  
-   悪い  
  
 パフォーマンス評価の定義方法とパフォーマンスしきい値の設定方法については、「[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md)」 (レプリケーション モニターを使用したパフォーマンスの監視) を参照してください。  
  
 **[配信率]**  
 マージ エージェントにより 1 秒間に処理される行数です。  
  
 **[最後の同期]**  
 マージ エージェントが最後に実行された時刻です。 この同期では変更が処理されていることも、処理されていないこともあります。 同期が進行中の場合、進行状況を示すパーセント値が表示されます。  
  
 **Duration**  
 最後の同期中におけるマージ エージェントの実行時間です。 マージ エージェントが現在同期中の場合、これは経過時間を表します。マージ エージェントが以前に同期された場合、これは合計時間を表します。  
  
 **[接続]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみです。 サブスクライバーとパブリッシャーの接続の種類です。 **[LAN]**、 **[ダイヤルアップ]**、 **[インターネット]** のいずれかの値になります。 サブスクリプションで Web 同期が使用されている場合、 **[インターネット]** が表示されます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](monitor/start-the-replication-monitor.md)   
 [表示情報とレプリケーション モニターを使用してタスクを実行します。](monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [レプリケーションの監視](monitoring-replication.md)   
 [マージ レプリケーションの Web 同期](web-synchronization-for-merge-replication.md)  
  
  
