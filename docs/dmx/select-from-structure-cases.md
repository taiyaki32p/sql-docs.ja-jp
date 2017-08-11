---
title: "SELECT FROM&lt;構造&gt;です。ケース |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SELECT
- CASES
- FROM
dev_langs:
- DMX
helpviewer_keywords:
- SELECT FROM <structure> statements
ms.assetid: 36f50213-14dc-42da-b899-20240b781e1a
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8af8e861c74c92be83e8ed61893d9a02587aa9a3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="select-from-ltstructuregtcases"></a>SELECT FROM&lt;構造&gt;です。場合
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マイニング構造の作成に使用されたケースを返します。  
  
 ドリルスルーが構造で使用可能でない場合、ステートメントは失敗します。 また、マイニング構造に対するドリルスルー権限がユーザーに与えられていない場合も、ステートメントは失敗します。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、新しいマイニング構造でドリルスルーが既定で有効にします。 特定の構造に対してドリルスルーが有効にするかどうかを確認するには、確認するかどうかの値、 **CacheMode**プロパティに設定されている**KeepTrainingCases**です。  
  
 場合の値**CacheMode**に変更が**ClearAfterProcessing**構造ケースがキャッシュから消去、および、ドリルスルーを使用することはできません。  
  
> [!NOTE]  
>  データ マイニング拡張機能 (DMX) を使用してマイニング構造のドリルスルーを有効または無効にすることはできません。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT [TOP n] <expression list> FROM <structure>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>引数  
 *n*  
 省略可。 返す行数を指定する整数値です。  
  
 *式の一覧*  
 式のコンマ区切りのリストです。  
  
 式には、列識別子、ユーザー定義関数、および VBA 関数を含めることができます。  
  
 *構造体*  
 構造の名前です。  
  
 *条件式*  
 列のリストから返される値を制限する条件です。  
  
 *式 (expression)*  
 省略可。 スカラー値を返す式。  
  
## <a name="remarks"></a>解説  
 モデルと構造の両方についてドリルスルーを有効にした場合、そのマイニング構造とマイニング モデルに対するドリルスルー権限を持つロールのすべてのメンバーは、次の構文を使用して、モデルに含まれていない構造列を返すことができます。  
  
```  
SELECT StructureColumn('<column name>') FROM <model>.CASES  
```  
  
 したがって、機密データまたは個人情報を保護する必要がありますを構築、個人情報をマスクし、付与、するデータ ソース ビュー **AllowDrillthrough**マイニング構造またはマイニング モデルに必要な場合にのみに対する権限。  
  
## <a name="examples"></a>使用例  
 次の例は、マイニング構造に基づく Targeted Mailing に基づく、[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]データベース、および関連するマイニング モデルです。 詳細については、次を参照してください。 [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)です。  
  
### <a name="example-1-drill-through-to-structure-cases"></a>例 1 : 構造ケースにドリルスルーする  
 次の例では、マイニング構造 Targeted Mailing で最も古い 500 人の顧客のリストが返されます。 このクエリではマイニング モデル内のすべての列が返されますが、行は自転車を購入した顧客に制限され、年齢順に並べ替えられます。 必要な列のみを返すように式のリストを編集することもできます。  
  
```  
SELECT TOP 500 *  
FROM [Targeted Mailing].Cases  
WHERE [Bike Buyer] = 1  
ORDER BY Age DESC;  
```  
  
### <a name="example-2-drillthrough-to-test-or-training-cases-only"></a>例 2 : テスト ケースまたはトレーニング ケースのみにドリルスルーする  
 次の例では、テスト用に予約されている Targeted Mailing の構造ケースのリストが返されます。 マイニング構造に、提示されたテスト セットが含まれていない場合、既定ではすべてのケースがトレーニング ケースとして扱われ、このクエリはケースを返しません。  
  
```  
SELECT [Customer Key], Gender, Age  
FROM [Targeted Mailing].Cases  
WHERE IsTestCase();  
```  
  
 トレーニング ケースを返すには、するには、関数を置き換える`IsTrainingCase()`です。  
  
## <a name="see-also"></a>参照  
 [選択 (&) #40";"DMX"&"#41;](../dmx/select-dmx.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
