---
title: データベースの整合性確認タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.checkdatabaseintegritytask.f1
helpviewer_keywords:
- data integrity [Integration Services]
- Check Database Integrity task [Integration Services]
- checking database consistency
- database consistency checks [Integration Services]
- verifying database consistency
- integrity checking [Integration Services]
ms.assetid: 5a82fe99-4503-429f-9337-e6bac7649fe4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b2d438577187c7f1754d358cb1e92220bf2ba105
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52801684"
---
# <a name="check-database-integrity-task"></a>データベースの整合性確認タスク
  データベースの整合性確認タスクは、指定されたデータベース内のすべてのオブジェクトの割り当てと構造上の整合性をチェックします。 このタスクは、単一のデータベースまたは複数のデータベースをチェックできます。また、データベースのインデックスもチェックするかどうかを選択できます。  
  
 データベースの整合性確認タスクは、DBCC CHECKDB ステートメントをカプセル化します。 詳細については、「[DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)」を参照してください。  
  
## <a name="configuration-of-the-check-database-integrity-task"></a>データベースの整合性確認タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[データベースの整合性確認タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/check-database-integrity-task-maintenance-plan.md)  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)  
  
  
