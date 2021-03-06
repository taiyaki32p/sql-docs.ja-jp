---
title: ReserveURL メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2b771042ca00c9a9a80d7ffa035b100e2c4a6dc0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020513"
---
# <a name="reserveurl-method-wmi-msreportserverconfigurationsetting"></a>ReserveURL メソッド (WMI MSReportServer_ConfigurationSetting)
  指定したアプリケーションの URL 予約を追加します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *アプリケーション*  
 URL の予約対象となるアプリケーションの名前。  
  
 *URLString*  
 予約する URL。  
  
 *lcid*  
 返されるエラー メッセージに使用するロケール。  
  
 *Error*  
 [out] 発生したエラーの説明。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。  
  
## <a name="remarks"></a>コメント  
 *UrlString* には仮想ディレクトリ名は含まれません。 仮想ディレクトリ名の設定用に、 [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) メソッドが用意されています。  
  
 現在の Windows サービス アカウントに対して URL 予約が作成されます。 Windows サービス アカウントを変更するには、すべての URL 予約を手動で更新する必要があります。  
  
 このメソッドを実行すると、すべてのアプリケーション ドメインで強制力の高いリサイクル処理が実行されます。 この処理が完了した後に、アプリケーション ドメインが再起動されます。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
