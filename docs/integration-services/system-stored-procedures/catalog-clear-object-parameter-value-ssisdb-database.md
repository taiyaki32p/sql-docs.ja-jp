---
title: catalog.clear_object_parameter_value (SSISDB データベース) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: dcbbb714-a051-4805-9e2b-2c2fb647c890
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 54c0b537541db593f8c7053f0b66cf6bb4f109ae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47602730"
---
# <a name="catalogclearobjectparametervalue-ssisdb-database"></a>catalog.clear_object_parameter_value (SSISDB データベース)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  サーバーに格納されている既存の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトまたはパッケージのパラメーターの値をクリアします。  
  
## <a name="syntax"></a>構文  
  
```sql  
catalog.clear_object_parameter [ @folder_name = ] folder_name   
    , [ @project_name = ] project_name   
    , [ @object_type = ] object_type   
    , [ @object_name = ] object_name   
    , [ @parameter_ name = ] parameter_name  
```  
  
## <a name="arguments"></a>引数  
 [ \@folder_name = ] *folder_name*  
 プロジェクトを含むフォルダーの名前。 *folder_name* は **nvarchar(128)** です。  
  
 [ \@project_name = ] *project_name*  
 プロジェクトの名前。 *project_name* は **nvarchar(128)** です。  
  
 [ \@object_type = ] *object_type*  
 オブジェクトの種類。 有効な値は、プロジェクトでは `20`、パッケージでは `30` です。 *object_type* は **smallInt** です。  
  
 [ \@ object _name = ] *object _name*  
 パッケージの名前です。 *object _name* は **nvarchar(260)** です。  
  
 [ \@parameter_ name = ] *parameter_name*  
 パラメーターの名前。 *parameter_ name* は **nvarchar(128)** です。  
  
## <a name="return-code-value"></a>リターン コード値  
 成功した場合は 0 を返します。  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>アクセス許可  
 このストアド プロシージャには、次の権限のいずれかが必要です。  
  
-   プロジェクトの READ および MODIFY 権限  
  
-   **ssis_admin** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
  
## <a name="errors-and-warnings"></a>エラーおよび警告  
 clear_object_parameter ストアド プロシージャがエラーを発生させる可能性がある条件を以下に示します。  
  
-   無効なオブジェクトの種類が指定されているか、またはオブジェクト名がプロジェクトで見つからない  
  
-   プロジェクトが存在しない、プロジェクトにアクセスできない、またはプロジェクト名が無効  
  
-   無効なパラメーター値が指定されている  
  
-   ユーザーに適切なアクセス許可がない。  
  
  
