---
title: 円グラフへのパーセンテージの表示 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 724a4d423e0e2ed517467c7a2e710ce6138fc194
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56291300"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>円グラフへのパーセンテージの表示 (レポート ビルダーおよび SSRS)
  既定では、それぞれの値を識別するために、カテゴリが凡例に表示されます。 カテゴリ ラベルを使用して円グラフにラベルを付けた場合、凡例にパーセンテージを表示できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>円グラフにパーセンテージをラベルとして表示するには  
  
1.  レポートに円グラフを追加します。 詳細については、「[レポートへのグラフの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)」を参照してください。  
  
2.  デザイン画面で、円グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。 円グラフの各スライス内にデータ ラベルが表示されます。  
  
3.  デザイン画面で、ラベルを右クリックし、 **[系列ラベルのプロパティ]** をクリックします。 **[系列ラベルのプロパティ]** ダイアログ ボックスが表示されます。  
  
4.  型`#PERCENT`の**データ ラベル**オプション。  
  
5.  (省略可) ラベルに表示する小数点以下桁数を指定するには、「#PERCENT{P*n*}」と入力します。ここで、 *n* は、表示する小数点以下桁数を表します。 たとえば、小数点以下を表示しない場合は「#PERCENT{P0}」と入力します。  
  
### <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>円グラフの凡例にパーセンテージを表示するには  
  
1.  デザイン画面で、円グラフを右クリックし、 **[系列のプロパティ]** をクリックします。 **[系列のプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **凡例**、型`#PERCENT`の**カスタムの凡例テキスト**プロパティ。  
  
## <a name="see-also"></a>参照  
 [円グラフ &#40;レポート ビルダーおよび SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [グラフの凡例の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [円グラフの外側へのデータ ポイント ラベルの表示 (レポート ビルダーおよび SSRS)](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS)](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
