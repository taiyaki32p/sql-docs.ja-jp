---
title: スナップショットを使用しないトランザクション サブスクリプションの初期化 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, initializing
- replication [SQL Server], initializing
- initializing subscriptions [SQL Server replication], without snapshots
ms.assetid: 75c8c1f8-60bc-44a8-944b-d18d1f6bda11
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 03931adbcd8de462f9562cc35083f080aabd7e05
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719940"
---
# <a name="initialize-a-transactional-subscription-without-a-snapshot"></a>スナップショットを使用しないトランザクション サブスクリプションの初期化
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  トランザクション パブリケーションへのサブスクリプションは、既定ではスナップショットを使用して初期化されます。このスナップショットはスナップショット エージェントによって生成され、ディストリビューション エージェントによって適用されます。 初期データセットが大規模な場合など、状況によっては、別の方法でサブスクリプションを初期化するのが望ましい場合があります。 サブスクライバーを初期化する他の方法としては、以下のものがあります。  
  
-   バックアップを指定する方法。 サブスクライバー上でバックアップを復元してから、ディストリビューション エージェントにより、必要なレプリケーション メタデータとシステム プロシージャがコピーされます。 バックアップを使用した初期化は、サブスクライバーにデータを配信する最も高速な方法であり便利です。バックアップを使用した初期化をパブリケーションで有効にした後で取得したバックアップであれば、どのバックアップでも使用できます。  
  
-   データベースのインポートなど、他の手法で初期データセットをサブスクライバーにコピーする方法。 正しいデータとスキーマがサブスクライバーにあることを確認してから、ディストリビューション エージェントにより、必要なメタデータとシステム プロシージャがコピーされます。  
  
## <a name="initializing-a-subscription-with-a-backup"></a>バックアップを使用したサブスクリプションの初期化  
 バックアップにはデータベース全体が含まれるため、各サブスクリプション データベースを初期化した後は、パブリケーション データベースの完全なコピーが含まれます。  
  
-   バックアップには、パブリケーションでアーティクルとして指定されていないテーブルが含まれます。  
  
-   バックアップには、テーブルに対して行フィルターや列フィルターが指定してある場合でも、すべてのデータが含まれます。  
  
 バックアップを復元した後に不要なオブジェクトやデータを削除するのは、管理者またはアプリケーションの責任です。 以降の同期では、アーティクルとして指定されたテーブルに該当するデータの変更と、指定したフィルター条件に一致した変更だけがレプリケートされます。  
  
> [!NOTE]  
>  バックアップを復元する際、サブスクライバーを使用して自動的に同期させる場合には、そのバックアップがパブリッシャーのものであることを確認する必要があります。 同期を開始する位置の設定に使用する、バックアップ内のログ シーケンス番号 (LSN) の値は、パブリッシャーに固有です。  
  
 **バックアップを使用してサブスクリプションを初期化するには**  
  
 バックアップを使用してサブスクリプションを初期化するには、まずパブリケーションを作成する際にオプションを有効にし、さらにサブスクリプションを作成する際にいくつかのオプションに値を指定する必要があります。 パブリケーションは、パブリケーションの新規作成ウィザードかプログラムで有効にできます。 ただし、サブスクリプション オプションで必要な値は、プログラムでしか指定できません。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/enable-initialization-with-backup-for-transactional-publications.md)  
  
-   レプリケーション Transact-SQL プログラミング: [トランザクション サブスクリプションのバックアップからの初期化 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)  
  
> [!NOTE]  
>  スナップショットを使用せずにサブスクリプションを初期化する場合、パブリッシャーで SQL Server サービスを実行する際に使用されるアカウントには、ディストリビューターのスナップショット フォルダーに対する書き込み権限が必要です。 権限の詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
### <a name="ensuring-the-suitability-of-a-backup"></a>バックアップの適合性の確認  
 バックアップがサブスクライバーの初期化に適しているのは、バックアップの取得後に実行されたすべてのトランザクションがディストリビューターに保存されている場合です。 バックアップが適していない場合には、レプリケーションでエラー メッセージが表示されます。  
  
 バックアップが使用に適したものになるように、次のガイドラインに従ってください。  
  
-   利用できる最新のバックアップを使用してください。最新のバックアップがディストリビューションの最長保有期間より古い場合には、バックアップを使用してサブスクリプションを初期化する前に、新しいバックアップを作成してください。 保有期間の詳細については、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」を参照してください。  
  
-   既定では、ディストリビューション クリーンアップ ジョブにより、72 時間よりも古いトランザクションがディストリビューション データベースから削除されます。 クリーンアップは、パブリケーションで設定された保有期間に基づきます。 古いバックアップを使用して同期する場合は、バックアップを復元する前にジョブを一時的に無効にし、サブスクリプションが正常に作成された後で再度有効にすることを検討してください。 これにより、バックアップから正常に同期するために必要となるトランザクションが、ディストリビューション データベースから削除されることを防ぐことができます。 クリーンアップ ジョブの詳細については、「[Run Replication Maintenance Jobs &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)」(レプリケーション メンテナンス ジョブの実行 &#40;SQL Server Management Studio&#41;) を参照してください。  
  
 場合によっては、バックアップを使用してサブスクリプションを初期化した後で、復元したサブスクライバー データベースを手動でカスタマイズする必要があります。 一般に、復元したサブスクライバー データベースを手動で変更する必要があるのは、サブスクライバー データベースの内容がパブリッシャー データベースの内容と異なるようにパブリケーションが定義されている場合です。  
  
-   復元されたデータベースのインデックス付きビューが、ログに基づくテーブルへのインデックス付きビューのアーティクルとしてパブリッシュされている場合は、テーブルに変換する必要があります。  
  
-   復元したデータベースでサブスクライブされた timestamp 列は、 **binary(8)** 列に変換する必要があります。そのためにまず、timestamp 列を含むテーブルの内容を新しいテーブル (ほぼ同じスキーマで、timestamp 列の代わりに **binary(8)** 列を使用したテーブル) にコピーしてください。次に、元のテーブルを削除し、新しいテーブルを元のテーブルと同じ名前に変更してください。  
  
## <a name="initializing-a-subscription-with-an-alternative-method"></a>代替手段を使用したサブスクリプションの初期化  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のように、パブリケーション データベースのスキーマとデータをサブスクライバーにコピーできる方法であれば、任意の方法を使ってサブスクリプションを初期化することができます。 代替手段を使用してサブスクライバーを初期化すると、レプリケーション サポート オブジェクトはサブスクライバーにコピーされます。  
  
 バックアップを使用して初期化する場合と違い、サブスクリプションを追加した時点でデータとスキーマが正しく同期されていることを手動またはアプリケーションで確認する必要があります。 たとえば、データとスキーマをサブスクライバーにコピーしてからサブスクリプションを追加するまでの間にパブリッシャー上で処理が実行されると、この処理による変更がサブスクライバーにレプリケートされない場合があります。  
  
 代替手段を使用してサブスクリプションを初期化するには、「 [Initialize a Subscription Manually](../../relational-databases/replication/initialize-a-subscription-manually.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)  
  
  
