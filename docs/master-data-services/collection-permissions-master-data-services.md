---
title: コレクション アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 8bb926515be3cd16a5ae1ce9dd1b2694f4bc55a7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759274"
---
# <a name="collection-permissions-master-data-services"></a>コレクション権限 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  コレクション権限は、エンティティのすべてのコレクションに適用されます。 特定のコレクションに権限を与えることはできません。つまり、権限はすべてのコレクションに適用されます。  
  
> [!NOTE]  
>  これらの権限は、ユーザー インターフェイスの **[エクスプローラー]** 機能領域にのみ適用されます。  
  
|権限|[説明]|  
|----------------|-----------------|  
|**読み取り**|ユーザーがコレクションのメンバーとメンバーの属性を読み取ることができます。|  
|**作成**|ユーザーがコレクションのメンバーを作成して属性値を割り当てることができます。|  
|**Update**|ユーザーがコレクションのメンバー、属性、リレーションシップを更新できます。|  
|**削除**|ユーザーがコレクションのメンバーを削除できます。|  
|**Deny**|コレクション メンバーに対するアクセスをすべて拒否します。|  
  
 読み取り、作成、更新、削除の各権限は組み合わせることができます。 作成、更新、削除が割り当てられると、読み取り権限が自動的に割り当てられます。  
  
## <a name="see-also"></a>参照  
 [モデル オブジェクト権限を割り当てる (マスター データ サービス)](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [コレクション (マスター データ サービス)](../master-data-services/collections-master-data-services.md)   
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
