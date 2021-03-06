---
title: Reporting Services でのファイル共有の配信 | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], file share delivery
- file share delivery [Reporting Services]
ms.assetid: 9f338dd3-f68a-4355-b9d7-9b25dacf3b5e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9630c2ce992ae6e0ce2e662b32755a201d3f0ec4
ms.sourcegitcommit: afc0c3e46a5fec6759fe3616e2d4ba10196c06d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "55889993"
---
# <a name="file-share-delivery-in-reporting-services"></a>Reporting Services でのファイル共有の配信
  SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、フォルダーへのレポートの配信を可能にするファイル共有配信拡張機能が用意されています。 ファイル共有配信拡張機能は既定で使用できるため、追加で構成する必要はありません。 ファイルの配信を正常に実行するためには、共有フォルダーに書き込みアクセス権を設定する必要があります。 ライター権限を必要とするアカウントには、サブスクリプションに構成された資格情報またはレポート サーバー用に構成された **ファイル共有アカウント** を使用できます。 ファイル共有アカウントの詳細については、「 [サブスクリプション設定とファイル共有アカウント &#40;構成マネージャー&#41;](../../reporting-services/install-windows/subscription-settings-and-a-file-share-account-configuration-manager.md)」を参照してください。 また、レポートへのアクセスを要求するユーザーは、共有フォルダーの読み取り権限を持っている必要があります。  
  
 ファイル共有にレポートを配信するには、標準のサブスクリプションまたはデータ ドリブン サブスクリプションを定義します。 データ ドリブン サブスクリプションでファイル共有配信を使用する方法については、「[データ ドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md)」を参照してください。 また、リモート ファイル共有サブスクリプションを実行するアカウントには、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンピューターに対するローカル ログオン権限が必要です。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード|  
  
 **このトピックの内容:**  
  
-   [共有フォルダーに配信されるレポートの特性](#bkmk_Characteristics)  
  
-   [対象フォルダー](#bkmk_target_folders)  
  
-   [ファイル形式](#bkmk_file_formats)  
  
-   [ファイル オプション](#bkmk_file_options)  
  
##  <a name="bkmk_Characteristics"></a> 共有フォルダーに配信されるレポートの特性  
  
-   レポート サーバーによってホストおよび管理されるレポートとは異なり、共有フォルダーに配信されるレポートは静的なファイルです。  
  
-   レポート用に定義されている対話機能は、ファイル システムにファイルとして保存されているレポートには **使用できません** 。 対話機能は、静的要素として表現されます。 たとえば、マトリックス形式のレポートを配信する場合は、レポートのトップレベルのビューが表示されます。行および列を拡張して、サポートしているデータを表示することはできません。  
  
-   レポートにグラフが含まれている場合は、既定の表示方法が使用されます。 レポートが別のレポートへリンクしている場合は、リンクは静的なテキストとして表示されます。  
  
-   配信したレポートで対話機能を保持するには、代わりに電子メール配信を使用します。 電子メールには、レポート サーバー上のレポートへのリンクが含まれます。これにより、ユーザーは、対話機能を使用できます。 詳細については、「 [Reporting Services の電子メール配信](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)」を参照してください。  
  
##  <a name="bkmk_target_folders"></a> 対象フォルダー  
 ファイル共有の配信を使用するサブスクリプションを定義する場合には、対象フォルダーとして既存のフォルダーを指定する必要があります。 レポート サーバーでは、ファイル システムにフォルダーを作成しません。 指定するフォルダーは、ネットワーク接続を使用してアクセス可能である必要があります。  
  
 共有フォルダーでレポートを **表示** するユーザーに読み取り権限があることを確認します。  
  
 サブスクリプションで対象フォルダーを指定する場合、コンピューターのネットワーク名を含む汎用名前付け規則 (UNC) 形式を使用してください。 フォルダー パスの末尾には円記号 (バックスラッシュ) を含めないでください。 以下に、UNC パスの例を示します。  
  
```  
\\<servername>\reportarchive\operations\2014  
```  
  
 フォルダーを作成するときに、必要な接続の上限を検討します。 レポート サーバーに必要な接続数は 2 つですが、共有フォルダーでレポートを開く追加のユーザーに対応できるように、十分な接続数を指定する必要があります。  
  
##  <a name="bkmk_file_formats"></a> ファイル形式  
 レポートは、HTML、DOCX、Excel などさまざまなファイル形式で表示されます。 レポートを特定の形式で保存するには、サブスクリプションの作成時に表示形式を選択します。 たとえば **Excel** を選択すると、レポートは [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ファイルとして保存されます。 サポートされている任意の表示形式を選択できますが、一部の形式はファイルの生成で他の形式より優れています。  
  
 ファイル共有配信を使用する場合は、すべての画像および関連するコンテンツが含まれているレポートを、単一のファイルで配信する形式を選択します。 適切な形式は、Web アーカイブ、PDF、TIFF、Excel などです。 HTML4.0 は避けてください。 レポートに画像が含まれている場合、HTML 4.0 形式のファイルにその画像が含まれるようには処理されません。  
  
##  <a name="bkmk_file_options"></a> ファイル オプション  
 ファイル共有サブスクリプションを作成するときに、ファイル名の作成方法と、レポートの以前のバージョンをファイルで上書きするかどうかを構成できます。 完全修飾ファイル名は、名前、拡張子、およびファイルに付加されるテキストや数値という 3 つの要素で構成されて一意のファイル名が形成されます。  
  
 **ファイル名:** 既定のファイル名はソース レポート名に基づいて生成されますが、サブスクリプションでは独自の名前を指定することもできます。 拡張子は省略可能です。拡張子を使用する場合は、表示形式に対応する拡張子がレポート サーバーによって生成されます。  
  
 **上書き:** 上書きオプションを指定すると、毎回のレポート配信または新規ファイルの作成時に同じファイル名を再利用できます。 ファイルを上書きするには、同じファイル名と拡張子を使用する必要があります。  
  
 配信ごとに一意のファイルを作成するための別の方法として、ファイル名にタイムスタンプを含める方法があります。 これを行うには、 **@timestamp** 変数をファイル名に追加します (例 : *CompanySales@timestamp*)。 この方法を使用すると、一意のファイル名が生成されるので、上書きされることはありません。  
  
 ファイル共有配信用に構成されたサブスクリプションの設定の例を次の図に示します。  
  
 ![ファイル共有サブスクリプション](../../reporting-services/subscriptions/media/ssrs-file-share-subscription.png "ファイル共有サブスクリプション")  
  
## <a name="see-also"></a>参照  
 [ネイティブ モード レポート サーバーのサブスクリプションの作成と管理](../../reporting-services/subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)   
 [サブスクリプション設定とファイル共有アカウント &#40;構成マネージャー&#41;](../../reporting-services/install-windows/subscription-settings-and-a-file-share-account-configuration-manager.md)  
  
  
