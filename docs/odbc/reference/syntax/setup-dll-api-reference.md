---
title: "セットアップの DLL の API リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1bd84a225c94c4141cb9c7f6a897731926384ea6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setup-dll-api-reference"></a>セットアップ DLL の API リファレンス
このセクションでは、ドライバーのセットアップ DLL の API は、2 つの関数で構成の構文を説明 (**ConfigDriver**と**ConfigDSN**)。 **ConfigDriver**と**ConfigDSN**ドライバ DLL のいずれかまたは別個の DLL をセットアップできます。  
  
 このセクションの内容が、変換プログラムのセットアップ DLL の API は、1 つの関数から成るの構文を説明するさらに、(**ConfigTranslator**)。 **ConfigTranslator**トランスレーター DLL のいずれかまたは別個の DLL をセットアップできます。  
  
 各関数には、導入された ODBC のバージョンが付いています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ConfigDriver 関数](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN 関数](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator 関数](../../../odbc/reference/syntax/configtranslator-function.md)