---
title: 相互運用可能なアプリケーションのテスト |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 509dd17efeeb982c51938d7a18fad99a2e84ba5b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794180"
---
# <a name="testing-interoperable-applications"></a>相互運用可能なアプリケーションのテスト
相互運用可能なアプリケーションのテストは、時間がかかりせいぜいビジネスや市場で新しいドライバーが継続的に表示されるため、最悪の不可能です。 ただし、適度なテストが可能です。 制限付きまたは低の相互運用性とアプリケーションは、それらのドライバーをサポートすることが保証されますに対してのみテストが必要です。 ただし、その必要があります完全テスト行われるこれらのドライバーに対して。  
  
 高い相互運用可能なアプリケーションは、すべてのドライバーに対して実質的にテストできません。 ほとんどのアプリケーション開発者はそれが重要に完全にドライバーの数が少ないと cursorily に対してさらにいくつかをテストします。 テスト済みのドライバーは、アプリケーションの市場で最も人気のある Dbms の最も人気のあるドライバーを含める必要があります。市場には、Dbms のすべてがカバーしている場合は、デスクトップとサーバーの両方の Dbms 用のドライバーをテストしてください。  
  
 ODBC アプリケーションのテストの問題の 1 つは、関連するコンポーネントの数: アプリケーション自体、ドライバー マネージャー、ドライバー、DBMS、場合によってネットワーク ソフトウェアやゲートウェイ。 アプリケーションやすくを使用して ODBC 関数から返されたエラー メッセージを投稿することでエラーを追跡するために**SQLGetDiagField**と**SQLGetDiagRec**します。 これらのメッセージは、製造元とエラーが発生したコンポーネントを確認します。 詳細については、次を参照してください。[診断](../../../odbc/reference/develop-app/diagnostics.md)します。
