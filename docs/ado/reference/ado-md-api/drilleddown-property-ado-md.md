---
title: DrilledDown プロパティ (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DrilledDown
- Member::DrilledDown
helpviewer_keywords:
- DrilledDown property [ADO MD]
ms.assetid: bf39dd36-fc7a-4f6e-86c0-fa71430c0d86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9021ce8b3ad4f7442650731cb60b70cd4376d78a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828210"
---
# <a name="drilleddown-property-ado-md"></a>DrilledDown プロパティ (ADO MD)
子の直後にあるかどうかを示す、[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)軸にします。  
  
## <a name="return-values"></a>戻り値  
 返します、**ブール**値し、は読み取り専用です。 **DrilledDown**返します**True**軸に現在のメンバーの子メンバーが存在しない場合。 **DrilledDown**返します**False**現在のメンバーに 1 つまたは複数の子メンバーがある場合は、軸上。  
  
## <a name="remarks"></a>コメント  
 使用して、 **DrilledDown**プロパティをこのメンバーの直後の軸では、このメンバーの少なくとも 1 つの子があるかどうかを判断します。 この情報は、メンバーを表示するときに役立ちます。  
  
 このプロパティでのみサポート[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)に属するオブジェクトを[位置](../../../ado/reference/ado-md-api/position-object-ado-md.md)オブジェクト。 このプロパティはから参照したときにエラーが発生した**メンバー**に属するオブジェクトを[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)オブジェクト。  
  
## <a name="applies-to"></a>適用対象  
 [Member オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/member-object-ado-md.md)  
  
## <a name="see-also"></a>参照  
 [ParentSameAsPrev プロパティ (ADO MD)](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md)
