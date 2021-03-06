---
title: 画像デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: be32765c6d996bcc67580949176c2265a0741eed
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56039013"
---
# <a name="image-device-information-settings"></a>画像デバイス情報設定
  次の表は、IMAGE 形式で表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**[列]**|レポートに設定する列の数。 この値により、レポートの元の設定はオーバーライドされます。|  
|**ColumnSpacing**|レポートに設定する列の間隔。 この値により、レポートの元の設定はオーバーライドされます。|  
|`DpiX`|出力画像の水平方向の解像度。 既定値は **96**です。 適用対象`BMP`、 `GIF`、 `PNG`、および`TIFF`出力形式。|  
|`DpiY`|出力画像の垂直方向の解像度。 既定値は **96**です。 適用対象`BMP`、 `GIF`、 `PNG`、および`TIFF`出力形式。|  
|**EndPage**|表示するレポートの最後のページ。 既定値は `StartPage` の値です。|  
|**MarginBottom**|レポートに設定する下余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**MarginLeft**|レポートに設定する左余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**MarginRight**|レポートに設定する右余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**MarginTop**|レポートに設定する上余白の値 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`1in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**OutputFormat**|[!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) でサポートされるいずれかの出力形式。`BMP`、`EMF`、`GIF`、`JPEG`、`PNG`、または `TIFF` です。|  
|**PageHeight**|レポートに設定するページの高さ (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`11in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**PageWidth**|レポートに設定するページの幅 (インチ単位)。 整数または小数の値の後に "in" を付ける必要があります (たとえば、`8.5in`)。 この値により、レポートの元の設定はオーバーライドされます。|  
|**PrintDpiX**|出力画像の水平方向の解像度。 既定値は `300` です。 拡張メタファイルに適用されます (`EMF`) 出力形式。|  
|**PrintDpiY**|出力画像の垂直方向の解像度。 既定値は `300` です。 拡張メタファイルに適用されます (`EMF`) 出力形式。|  
|`StartPage`|表示するレポートの最初のページ。 値 `0` はすべてのページを表示することを示します。 既定値は `1` です。|  
  
## <a name="see-also"></a>参照  
 [表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
