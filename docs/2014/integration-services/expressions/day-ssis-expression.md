---
title: DAY (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8d530819e235efd233df3247d2e85d7da8c2cf1d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805134"
---
# <a name="day-ssis-expression"></a>DAY (SSIS 式)
  ある日付の、日の日付要素を表す整数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a>引数  
 *date*  
 有効な日付または日付形式の文字列を返す式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_I4  
  
## <a name="remarks"></a>コメント  
 引数が NULL の場合、DAY は NULL を返します。  
  
 日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
> [!NOTE]  
>  式は、リテラルの日付が日付データ型のいずれかに明示的にキャストするときに検証に失敗します。DT_DBTIMESTAMPOFFSET と DT_DBTIMESTAMP2 します。  
  
 DAY 関数を使用すると、DATEPART("DAY", date) 関数を使用する場合と同じ結果を、より簡単に取得できます。  
  
## <a name="expression-examples"></a>式の例  
 この例は、日付リテラルの日数を返します。 データ形式が "mm/dd/yyyy" 形式の場合、この例は 23 を返します。  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 この例は、 **ModifiedDate** 列内の日を表す整数を返します。  
  
```  
DAY(ModifiedDate)  
```  
  
 この例は、現在の日付の日を表す整数を返します。  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a>参照  
 [DATEADD &#40;SSIS 式&#41;](dateadd-ssis-expression.md)   
 [DATEDIFF &#40;SSIS 式&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS 式&#41;](datepart-ssis-expression.md)   
 [MONTH &#40;SSIS 式&#41;](month-ssis-expression.md)   
 [YEAR &#40;SSIS 式&#41;](year-ssis-expression.md)   
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
