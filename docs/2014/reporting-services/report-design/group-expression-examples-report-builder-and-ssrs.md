---
title: グループ式の例 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 0ce66534d59d68118fcd66eaedc82ac57850750c
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56294750"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a>グループ式の例 (レポート ビルダーおよび SSRS)
  データ領域では、1 つのフィールドでデータをグループ化することも、グループ化の基準となるデータを識別する、より複雑な式を作成することもできます。 複合式には、複数のフィールドやパラメーター、条件ステートメント、またはカスタム コードなどへの参照が含まれます。 データ領域に対してグループを定義する場合、これらの式を **[グループ]** プロパティに追加します。 詳細については、「 [データ領域でのグループの追加または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。  
  
 簡単なフィールド式に基づく 2 つ以上のグループをマージするには、各フィールドをグループ定義のグループ式一覧に追加します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a>グループ式の例  
 次の表に、グループの定義に使用できるグループ式の例を挙げます。  
  
|説明|式|  
|-----------------|----------------|  
|`Region` フィールドでグループ化します。|`=Fields!Region.Value`|  
|姓と名でグループ化します。|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|姓の最初の文字でグループ化します。|`=Fields!LastName.Value.Substring(0,1)`|  
|ユーザー選択に基づいてパラメーターでグループ化します。<br /><br /> この例では `GroupBy` パラメーターは、グループ化に使用する有効な選択肢を提供する使用可能な値の一覧に基づいている必要があります。|`=Fields(Parameters!GroupBy.Value).Value`|  
|3 つの異なるの年齢範囲でグループ化します。<br /><br /> "21 未満"、"21 ～ 50"、および "51 以上"。|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|多数の年齢範囲でグループ化します。 次の例は、 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET で記述され、次の範囲に対して文字列を返すカスタム コードを示します。<br /><br /> 25 以下<br /><br /> 26 ～ 50<br /><br /> 51 ～ 75<br /><br /> 76 以上|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> カスタム コード :<br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a>参照  
 [データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式の例 (レポート ビルダーおよび SSRS)](expression-examples-report-builder-and-ssrs.md)   
 [レポート デザイナーでカスタム コードやアセンブリを式から参照する (SSRS)](custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  
