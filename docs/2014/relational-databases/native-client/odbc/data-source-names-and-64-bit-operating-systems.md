---
title: データ ソース名と 64 ビット オペレーティング システム。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: c2f86810-2775-4ddd-8df7-e8373785a7fc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4007543cbe06b8b80c28a3a2a35c1a3c3fdbb525
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190592"
---
# <a name="data-source-names-and-64-bit-operating-systems"></a>データ ソース名と 64 ビット オペレーティング システム
  アプリケーションを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドして実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。  
  
## <a name="remarks"></a>Remarks  
 64 ビットの Windows オペレーティング システムには、2 つの odbcad32.exe ファイルがあります。  
  
-   %SystemRoot%\system32\odbcad32.exe は、64 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
-   %SystemRoot%\SysWOW64\odbcad32.exe は、64 ビット オペレーティング システムで実行される 32 ビット アプリケーションなど、32 ビット アプリケーションのデータ ソース名の作成と保持に使用されます。  
  
## <a name="see-also"></a>関連項目  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
