---
title: ConfigTranslator 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: edcffe36c0185276fae89f800e1bbcfc5bc33b33
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53214523"
---
# <a name="configtranslator-function"></a>ConfigTranslator 関数
**準拠**  
 バージョンが導入されました。ODBC 2.0  
  
 **まとめ**  
 **ConfigTranslator**トランスレーターの翻訳の既定のオプションを返します。 これは、トランスレーター DLL または別のセットアップ DLL に存在できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>引数  
 *hwndParent*  
 [入力]親ウィンドウ ハンドル。 関数では、ハンドルが null の場合、ダイアログ ボックスは表示されません。  
  
 *pvOption*  
 [出力]32 ビットの変換オプション。  
  
## <a name="returns"></a>戻り値  
 関数は、成功した場合、FALSE が失敗した場合に TRUE を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**ConfigTranslator** 、関連付けられている FALSE が返されます *\*pfErrorCode*インストーラー エラー バッファーへの呼び出しで値が投稿された**SQLPostInstallerError**呼び出すことによって取得できる**SQLInstallerError**します。 次の表、  *\*pfErrorCode*によって返される値**SQLInstallerError**とこの関数のコンテキストでそれぞれについて説明します。  
  
|*\*pfErrorCode*|[エラー]|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|無効なウィンドウ ハンドル|*HwndParent*引数が無効または NULL。|  
|ODBC_ERROR_DRIVER_SPECIFIC|ドライバーに translator 固有のエラー|定義された ODBC インストーラーのエラーがないドライバー固有のエラーです。 *SzError*への呼び出しの引数、 **SQLPostInstallerError**関数は、ドライバー固有のエラー メッセージを含める必要があります。|  
|ODBC_ERROR_INVALID_OPTION|無効な変換オプション|*PvOption*引数に無効な値が含まれています。|  
  
## <a name="comments"></a>コメント  
 翻訳者が 1 つの翻訳オプションのみをサポートしている場合**ConfigTranslator** TRUE を返し、設定*pvOption*オプションの 32 ビットにします。 それ以外の場合、使用する既定の変換オプションを決定します。 **ConfigTranslator**ユーザーが既定の変換オプションを選択 ダイアログ ボックスを表示できます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|翻訳オプション|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|トランスレーターの選択|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|翻訳オプションの設定|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
