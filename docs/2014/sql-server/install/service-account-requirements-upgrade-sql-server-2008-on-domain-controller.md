---
title: サービスのドメイン コント ローラー上の SQL Server 2008 にアップグレードするためのアカウントの要件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 640f0f30991307a56112270d0619f6ea0380021e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126811"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>ドメイン コントローラーで SQL Server 2008 へのアップグレードを実行するためのサービス アカウント要件
  アップグレード アドバイザーのインスタンスを検出する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で Network Service や Local Service アカウントで実行されている、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]ドメイン コント ローラー。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ドメイン コントローラーに [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] がインストールされている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを Local Service アカウントまたは Network Service アカウントの特権を使用して実行することはできません。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>修正措置  
 すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントが Domain アカウントまたは Local System アカウントに割り当てられていることを確認してください。 このように変更してからアップグレードしないと、セットアップがブロックされます。 サービス アカウントの SQL ライター、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、および Active Directory Helper サービスは、Network Service アカウントにハードコードされていて変更できないため例外となります。  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 アップグレード アドバイザー&#91;新規&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
