---
title: 英語以外の言語バージョン の SQL Server Management Studio (SSMS) をインストールする | Microsoft Docs
description: 英語以外の言語バージョン の SQL Server Management Studio (SSMS) をインストールする
ms.custom: ''
ms.date: 12/08/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7baf327182cec41ffbd20e75517cc9b944226140
ms.sourcegitcommit: 9e722cc8d10ecbdb93efc2fc1886fe7b20dbc13c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2018
ms.locfileid: "52282044"
---
# <a name="install-non-english-language-versions-of-sql-server-management-studio-ssms"></a>英語以外の言語バージョン の SQL Server Management Studio (SSMS) をインストールする 

[SSMS は複数の言語で利用可能です](download-sql-server-management-studio-ssms.md#available-languages-ssms-1791)が、コンピューターのシステム ロケールが SSMS の言語と一致しない場合は、SSMS のインストーラーによってコンピューターへのインストールがブロックされます。 

以下の手順は、Windows のバージョンによって異なります。 以下は、Windows 10 向けのものです。

## <a name="install-non-english-ssms-on-a-computer-running-an-english-operating-system-os"></a>英語版のオペレーティング システム (OS) を実行しているコンピューターで、英語版以外の SSMS をインストールする

1. 次の手順で、SSMS で使用する言語の Windows 言語パックをインストールします。 
   - **[設定]** > **[時刻と言語]** > **[地域と言語]** > **[言語を追加する]** 
2. インストールした言語をクリックし、前の手順でインストールした言語パックを使用するようにシステム ロケールを設定します。次に、**[既定として設定する]** を選択します。 (システム ロケールの設定は、SSMS のインストール後に英語に戻せます。)
3. ご利用のオペレーティング システムが目的の言語で実行されると、[SSMS は複数の言語で利用できます](download-sql-server-management-studio-ssms.md#available-languages-ssms-1791)。 新しい言語の SSMS を初めてインストールする場合は、フル パッケージを使用します。 以降のインストールでは、アップグレード パッケージを使用できます。
4. SSMS を実行すると、前の手順でインストールした言語で表示されます。
5. コンピューターのシステム ロケールの設定を英語に戻します。

## <a name="install-ssms-in-a-language-other-than-the-language-of-the-installed-os"></a>インストールされている OS の言語以外の言語で SSMS をインストールする

1. 次の手順で、SSMS で使用する言語の Windows 言語パックをインストールします。 
   - **[設定]** > **[時刻と言語]** > **[地域と言語]** > **[言語を追加する]** 
2. インストールした言語をクリックし、前の手順でインストールした言語パックを使用するようにシステム ロケールを設定します。次に、**[既定として設定する]** を選択します。 
3. ご利用のオペレーティング システムが目的の言語で実行されると、[SSMS は複数の言語で利用できます](download-sql-server-management-studio-ssms.md#available-languages-ssms-1791)。 新しい言語の SSMS を初めてインストールする場合は、フル パッケージを使用します。 以降のインストールでは、アップグレード パッケージを使用できます。
4. インストールする各言語が、最初にインストールした SSMS のバージョンの言語と一致しない場合は、次の手順で対応する Visual Studio 2015 Shell (Isolated) Language Pack をインストールします。
   - [https://connect.microsoft.com/VisualStudio/ExtendVS](https://connect.microsoft.com/VisualStudio/ExtendVS) にアクセスしてください (サインインして *接続登録*プロセスを完了することが必要な場合があります)。
   - 目的の Visual Studio 2015 Shell (Isolated) Language Pack をダウンロードしてインストールします。

   > [!IMPORTANT]
   > Visual Studio 2015 Shell (Isolated) Language Pack のインストールは、必ず上記手順で実行してください。**[ツール]** | **[オプション]** | **[国際対応の設定]** の **[追加の言語を取得する]** リンクは使用しないでください。 

5. SSMS を実行して、次の設定から使用する言語を選択します。
   - **[ツール]** | **[オプション]** | **[国際対応の設定]**
1. SSMS を閉じて再起動します。

## <a name="next-steps"></a>次の手順

- [チュートリアル: SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/tutorials/tutorial-sql-server-management-studio)
