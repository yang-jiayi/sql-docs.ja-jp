---
title: Reporting Services スクリプト ファイルを実行する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f7db9d1ec95e384cc2756b43518e7e85242005b4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013573"
---
# <a name="run-a-reporting-services-script-file"></a>Reporting Services スクリプト ファイルを実行する
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト ファイルは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スクリプト環境 (RS.exe) を使用してコマンド プロンプトから実行します。 RS.exe には、ユーザーが使用できるコマンド プロンプト引数が多数用意されています。 コマンド プロンプト オプションの詳細については、「[RS.exe ユーティリティ &#40;SSRS&#41;](rs-exe-utility-ssrs.md)」を参照してください。 他のスクリプトのサンプルについては、「 [SQL Server Reporting Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。  
  
## <a name="sample-command-lines"></a>コマンド ラインでの実行例  
  
-   スクリプト環境で Script.rss を次のように実行すると、ターゲット レポート サーバーが指定されます。 既定では、Windows 認証が適用されます。  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、Web サービスの呼び出しを認証するためのユーザー名とパスワードが指定されます。  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、30 秒のサーバー タイムアウトが指定されます。  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、 *report*と呼ばれるグローバル スクリプト変数が指定されます。  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   スクリプト環境で Script.rss を次のように実行すると、スクリプト ファイルの Web サービス操作がバッチとして実行するように指定されます。  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a>参照  
 [テクニカル リファレンス (SSRS)](../technical-reference-ssrs.md)  
  
  
