---
title: データの結合 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 366f1f60f078334f1d0e6f25c8ad6b65443238d0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640796"
---
# <a name="combine-data-mds-add-in-for-excel"></a>データの結合 (Excel 用 MDS アドイン)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で、パブリッシュする前にデータを比較する場合は、2 つのワークシートのデータを結合します。 この手順では、2 つのワークシートのデータを 1 つに結合します。 これにより、さらに比較を実行して、MDS リポジトリにパブリッシュするデータを決定することができます。  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   MDS によって管理されるデータが含まれているワークシートが必要です。 詳細については、「 [マスター データ サービスからデータを Excel にエクスポート](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)」を参照してください。  
  
-   MDS によって管理されるデータに結合するデータが含まれているワークシートが必要です。 このシートには、ヘッダー行が必要です。  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>MDS によって管理されるシートに管理されないデータを結合するには  
  
1.  MDS によって管理されるデータを含むシートで、 **[パブリッシュと検証]** グループの **[データの結合]** をクリックします。  
  
2.  **[データの結合]** ダイアログ ボックスで、 **[MDS データと結合する範囲]** ボックスの横にあるアイコンをクリックします。 ダイアログ ボックスが縮小されます。  
  
3.  結合するデータを含むシートをクリックします。  
  
4.  シート上の結合するすべてのセル (ヘッダー行を含む) を強調表示します。  
  
5.  **[データの結合]** ダイアログ ボックスで、アイコンをクリックします。 ダイアログ ボックスが拡張されます。  
  
6.  MDS エンティティに一覧表示される列について、 **[対応する列]** の下にある列を選択します。 すべての MDS 列に対応する列が必要なわけではありません。  
  
7.  **[結合]** をクリックします。 MDS からのデータか外部ソースからのデータかを示す **[SOURCE]** 列が表示されます。  
  
## <a name="next-steps"></a>Next Steps  
  
-   MDS によって管理されるデータと外部データの類似性を見つける場合は、「[類似データの照合 &#40;Excel 用 MDS アドイン&#41;](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [概要: Excel へのデータのエクスポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Excel 用 MDS アドインでのデータ品質照合](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
