---
title: SetSecureConnectionLevel メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b22e8d9e67e0c897aaab859dde097707d3272ec3
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029064"
---
# <a name="setsecureconnectionlevel-method-wmi-msreportserverconfigurationsetting"></a>SetSecureConnectionLevel メソッド (WMI MSReportServer_ConfigurationSetting)
  レポート サーバーのセキュリティで保護された接続レベルを設定します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *レベル*  
 セキュリティで保護された接続レベルを表す整数値。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>コメント  
 このメソッドを呼び出すと、レポート サーバーの SecureConnectionLevel プロパティ値が指定した値に設定されます。 値 0 は、SSL がオフであることを示します。 1 以上の値は、SSL がオンであることを示します。  
  
-   レポート サーバーの構成ファイルの SecureConnectionLevel 要素が変更された値が設定されている場合、`URLRoot`場合は、"https://"を使用する構成ファイル内の要素が設定されて、指定した*レベル*がより大きいまたは場合に、1、または"http://"と等しく、指定した*レベル*は 0 です。  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]で、SecureConnectionLevel がオン/オフのスイッチとして使用されます。既定値は 0 です。 SetSecureConnectionLevel メソッド API に渡された値が 1 以上である場合、SSL はオンであると見なされ、それに従って rsreportserver.config ファイルで構成プロパティ SecureConnectionLevel が設定されます。 値 2 と 3 は、旧バージョンとの互換性のために許可されています。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
