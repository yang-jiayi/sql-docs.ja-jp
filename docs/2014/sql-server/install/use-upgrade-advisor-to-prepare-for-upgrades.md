---
title: アップグレード アドバイザーを使用したアップグレードの準備 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server]
- upgrading SQL Server, Upgrade Advisor
- upgrading SQL Server, preparing to upgrade
- SQL Server Upgrade Advisor
- analyzing installations for upgrading [SQL Server]
ms.assetid: d85b0833-ddeb-42e3-9397-97ea60d521b7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8b12b22af124250fe05baab5d08a6585de061b56
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53368074"
---
# <a name="use-upgrade-advisor-to-prepare-for-upgrades"></a>アップグレード アドバイザーを使用したアップグレードの準備
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アップグレード アドバイザーは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] へのアップグレードの準備に役立ちます。 アップグレード アドバイザーでは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でインストールされたコンポーネントが分析され、アップグレードの前または後に修正する必要がある問題を示すレポートが生成されます。  
  
## <a name="how-upgrade-advisor-works"></a>アップグレード アドバイザーの機能  
 アップグレード アドバイザーを実行すると、アップグレード アドバイザーのホーム ページが表示されます。 ホーム ページからは、次のツールを起動できます。  
  
-   アップグレード アドバイザー分析ウィザード  
  
-   アップグレード アドバイザー レポート ビューアー  
  
-   アップグレード アドバイザーのヘルプ  
  
 最初にアップグレード アドバイザーを使用するときに、アップグレード アドバイザーの分析ウィザードを実行して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンポーネントを分析します。 ウィザードによる分析が完了したら、アップグレード アドバイザー レポート ビューアーで結果のレポートを表示します。 各レポートにはアップグレード アドバイザーのヘルプへのリンクが示されており、既知の問題の修正または影響の軽減に役立つ情報を参照できるようになっています。  
  
## <a name="upgrade-advisor-analysis"></a>アップグレード アドバイザーの分析  
 アップグレード アドバイザーでは、次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントを分析します。  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
 分析では、スクリプト、ストアド プロシージャ、トリガー、トレース ファイルなどのアクセス可能なオブジェクトが調べられます。 デスクトップ アプリケーションや暗号化されたストアド プロシージャは、アップグレード アドバイザーで分析できません。  
  
 出力は XML レポートの形式で行われます。 XML レポートを表示するには、アップグレード アドバイザー レポート ビューアーを使用します。  
  
> [!NOTE]  
>  レポートに "アップグレードに関するその他の問題" という項目が示される場合があります。 この項目は、サーバーやアプリケーションに存在する可能性があってもアップグレード アドバイザーでは検出されない問題の一覧にリンクされています。 この検出できない問題の一覧を確認し、これらの問題のためにサーバーやアプリケーションを変更する必要があるかどうかを判断してください。  
  
## <a name="how-to-install-and-run-upgrade-advisor"></a>アップグレード アドバイザーのインストールおよび実行方法  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アップグレード アドバイザーのインストール先は、分析対象のコンポーネントによって異なります。 アップグレード アドバイザーでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以外のサポートされているすべてのコンポーネントをリモートで分析できます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンしない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続でき、かつアップグレード アドバイザーの前提条件を満たす任意のコンピューターにアップグレード アドバイザーをインストールできます。 詳細については、「 [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」をご覧ください。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。  
  
 アップグレード アドバイザーは機能パックで提供されています。  
  
 アップグレード アドバイザーをインストールして実行するための前提条件は、次のとおりです。  
  
-   [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2、Windows 7 SP1、および [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] SP1。  
  
-   Windows インストーラー 4.5 以降のバージョン。 Windows インストーラーをインストールすることができます、 [Windows インストーラー Web サイト](https://go.microsoft.com/fwlink/?LinkId=49112)します。  
  
-   Microsoft .NET Framework 4。 .NET framework 4 がで使用できる、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、製品メディアとの間、 [.NET Framework 4 ダウンロード ページ](https://go.microsoft.com/fwlink/?LinkId=209895)します。  
  
    -   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] メディアから .NET Framework 4 をインストールするには、ディスク ドライブのルートに移動します。 \Redist フォルダーをダブルクリック、DotNetFrameworks フォルダーをダブルクリックし、dotNetFx40_Full_x86_x64.exe (32 ビット オペレーティング システムまたは 64 ビットのオペレーティング システム用) を実行します。  
  
 アップグレード アドバイザーを Web からインストールするには、ダウンロード ページのダウンロード ボタンをクリックします。 その後すぐにインストールを実行するか、または SQLUA.msi ファイルを保存して後から実行できます。 製品ディスクからインストールする場合は、製品ディスクから直接 SQLUA.msi を実行します。  
  
 アップグレード アドバイザーをインストールした後からを開くことができます、**開始**メニュー。  
  
-   クリックして**開始**、 をポイント**すべてのプログラム**、 をポイント[!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]、順にクリックします**[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]アップグレード アドバイザー**します。  
  
 詳細については、アップグレード アドバイザーのダウンロードおよび [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のリリース ノートに収録されているアップグレード アドバイザーのドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [複数のバージョンおよび SQL Server のインスタンスを使用します。](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)   
 [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [旧バージョンとの互換性](../../../2014/getting-started/backward-compatibility.md)  
  
  
