---
title: データベース エンジンがインストールされ開始されているかどうかの確認 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bed1ec3eeb3dffe1ff1174d83050cd2e09af4caf
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2018
ms.locfileid: "52639268"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a>データベース エンジンがインストールされ開始されているかどうかの確認
  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインストールが成功すると、ファイルがファイル システムにインストールされ、レジストリのエントリが作成されて、ツールがいくつかインストールされます。 このトピックでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 構成マネージャーを使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされて起動されているかどうかを確認する方法について説明します。  
  
##  <a name="SSMSProcedure"></a> SQL Server 構成マネージャーの使用  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a>SQL Server 構成マネージャーを使用してデータベース エンジンを表示および開始する方法  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**、 **[構成ツール]** の順にポイントし、 **[SQL Server 構成マネージャー]** をクリックします。  
  
     **[スタート]** メニューにこれらのエントリがない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が正しくインストールされていません。 セットアップを実行して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]をインストールします。  
  
2.  **[SQL Server 構成マネージャー]** の左側のペインで、 **[SQL Server のサービス]** をクリックします。 右側のペインには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に関連するサービスがいくつか表示されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] がインストールされると、既定のインスタンスの場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] サービスは **[SQL Server (MSSQLSERVER)]** と表示され、 **が名前付きインスタンスとしてインストールされている場合は、**\<*[SQL Server (*>**instance_name**)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] と表示されます。 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] はインスタンス名が変更されない限り、 **SQLEXPRESS**という名前の名前付きインスタンスとしてインストールされます。 緑の三角形のアイコンは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が実行中であることを示します。 赤い四角形のアイコンは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] が停止していることを示します。  
  
3.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]を開始するには、右側のペインで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]を右クリックして、 **[開始]** をクリックします。  
  
> [!NOTE]  
>  ユーザーは、セットアップ時に、プログラム ファイルとデータベース ファイルをインストールする場所を選択できます。 ユーザーが既定の場所をそのまま使用すると、ファイルは [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] および C:\Program Files\Microsoft SQL Server\MSSQL.*x*( *x* は番号) にインストールされます。  
  
  
