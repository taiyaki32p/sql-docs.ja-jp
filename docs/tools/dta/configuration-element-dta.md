---
title: Configuration 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Configuration element
ms.assetid: 1478e56f-57c4-4441-bac9-1ac91453839b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9a0e0bbcc65dd3b9cb1d6fd53f3d296f995f0527
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291318"
---
# <a name="configuration-element-dta"></a>Configuration 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ワークロードのチューニング時にデータベース エンジン チューニング アドバイザーが分析する、既存の仮想物理設計構造から成るユーザー指定の構成を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
    <Server>...</Server>  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions  
    <Configuration [SpecificationMode="Relative" | "Absolute"]>  
    ...code removed here...  
    </Configuration>  
</DTAInput>  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|Configuration の属性|[説明]|  
|-----------------------------|-----------------|  
|**SpecificationMode**|省略可。 データベース エンジン チューニング アドバイザーが、指定された構成を既存の構成との関連で分析を行うか、それともまったく新しい独立した構成として分析を行うかを指定します。 この属性を指定するには **string** データ型を使用します。指定できる値は次のいずれかです。<br /><br /> **Relative**:<br />                  指定された構成を、チューニングしているデータベースにある物理設計構造の現在の既存構成 (インデックス、インデックス付きビュー、パーティション) との関連で評価します。 例 :<br /><br /> `<Configuration SpecificationMode="Relative">`<br /><br /> **Absolute**:<br />                  指定された構成を、独立した構成として評価します。 Absolute が指定されると、データベース エンジン チューニング アドバイザーは既存の構成を考慮しません。 例 :<br /><br /> `<Configuration SpecificationMode="Absolute">`|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|[説明]|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|省略可。 **DTAInput** 要素につき 1 回使用できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DTAInput 要素 &#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**子要素**|[Configuration の Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md)|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
