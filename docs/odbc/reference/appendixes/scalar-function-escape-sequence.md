---
title: スカラー関数エスケープ シーケンス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0913458d683d7641145b262552e147033dbfc054
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660790"
---
# <a name="scalar-function-escape-sequence"></a>スカラー関数のエスケープ シーケンス
ODBC スカラー関数のエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Remarks  
 BNF 表記では、構文がとおりです。  
  
 *ODBC スカラー関数エスケープ*:: =  
  
 *ODBC のイニシエーター esc* fn*スカラー関数 ODBC esc 終端*  
  
 *スカラー関数*:: =*関数名*(*引数リスト*)  
  
 (、非終端要素の定義*関数名*と*関数名*(*引数リスト*) は、スカラー関数の一覧から派生[付録 e: スカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md))。  
  
 *ODBC のイニシエーター esc* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 データ ソースには、プロシージャがサポートされ、ドライバーは ODBC プロシージャの呼び出し構文をサポートしているかどうかを調べるにアプリケーションを呼び出すことができます**SQLGetInfo**します。 詳細については、次を参照してください。[付録 e: スカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)します。
