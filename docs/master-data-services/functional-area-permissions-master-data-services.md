---
title: 機能領域アクセス許可 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- functional area permissions [Master Data Services], about functional area permissions
- functional area permissions [Master Data Services]
- permissions [Master Data Services], functional areas
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b16b70e4956caa7a2f5bffbdc484a725cfee937d
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52773824"
---
# <a name="functional-area-permissions-master-data-services"></a>機能領域権限 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ユーザー インターフェイス (UI) の各機能領域に、権限を割り当てることができます。 機能領域を次に示します。  
  
-   **エクスプローラー**  
  
-   **バージョン管理**  
  
-   **統合管理**  
  
-   **システム管理**  
  
-   **ユーザー/グループの権限**  
  
-   **スーパー ユーザー**  
  
 機能領域に権限を割り当てると、UI のその領域がユーザーまたはグループに表示されます。  
  
 **[エクスプローラー]** 機能領域内でユーザーがアクセスできるデータは、モデル オブジェクトおよび階層メンバーに割り当てられた追加権限によって決定されます。 その他のすべての機能領域内でモデルを表示および操作するには、ユーザーはモデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
> [!IMPORTANT]  
>  スーパー ユーザー権限を持つユーザーは、実質的にすべてのモデルに対する管理者権限を持ち、その他のすべての機能権限を持ちます。  
  
 **にアクセスするには、ユーザーまたはグループが、少なくとも 1 つの機能領域および** [モデル] [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]タブに表示される少なくとも 1 つのモデルに対する権限を持っている必要があります。  
  
## <a name="see-also"></a>参照  
 [機能領域の権限を割り当てる (マスター データ サービス)](../master-data-services/assign-functional-area-permissions-master-data-services.md)   
 [モデル オブジェクト権限 (マスター データ サービス)](../master-data-services/model-object-permissions-master-data-services.md)   
 [階層メンバーの権限 (マスター データ サービス)](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [権限の決定方法 (マスター データ サービス)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
