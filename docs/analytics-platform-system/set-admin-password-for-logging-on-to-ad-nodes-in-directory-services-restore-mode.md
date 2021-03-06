---
title: Active Directory パスワード - Analytics Platform System の設定 |Microsoft Docs
description: ディレクトリ サービス復元モードでは、Analytics Platform System (APS) で Active Directory ノード管理者ログオン パスワードを設定します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3df6203a4d98bace5d23a92e70a596a34dedb60e
ms.sourcegitcommit: 170c275ece5969ff0c8c413987c4f2062459db21
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54226449"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>ディレクトリ サービスで AD ノードへのログオンの復元モード (DSRM) - Analytics Platform System の管理者パスワードの設定します。
ディレクトリ サービス復元モード (DSRM) では、修復、または Active Directory Domain Services (AD DS) の復元のブート モードです。 AD DS が失敗した後、または AD DS を復元する必要がある場合、アプライアンス AD ノードにログオンに使用されます。 DSRM のパスワードは、ハードウェア ベンダーのサイトのアプライアンスのセットアップ時に初期化されており、アプライアンス管理者によって変更する必要があります。 Analytics Platform System が 2 つの AD DS (ドメイン コント ローラー) **_appliance_domain_-AD01**と **_appliance_domain_-AD02**します。 各アプライアンス AD ノードには、次の手順を使用して、DSRM パスワードを変更します。  
  
## <a name="HowToDSRM"></a>管理者のパスワードをリセットするには  
  
1.  アプライアンス AD ノードでコマンド プロンプト ウィンドウを開きます <strong>_appliance_domain_-AD_xx_</strong>仮想マシン。  
  
2.  コマンド プロンプトで、「`ntdsutil`」と入力します。  
  
3.  **Ntdsutil**プロンプトで「`set dsrm password`します。  
  
4.  **管理者パスワードのリセット:** プロンプトで「`reset password on server null`します。  
  
5.  プロンプトで、新しいパスワードを入力します。  
  
6.  各アプライアンス AD 仮想マシン上の 1 ~ 5 の手順を繰り返します。  
  
    > [!WARNING]  
    > Analytics Platform System は、ドメイン管理者またはローカル管理者パスワードのドル記号 ($) をサポートしていません。 ドル記号を含むパスワードは検証し、する操作可能なアップグレード、およびメンテナンス アクティビティをブロックできます。  
  
> [!NOTE]  
> AD の仮想マシンを特定の Active Directory ドメイン サービスまたは仮想マシンが破損した場合に実行されている**ReplaceVM**影響を受けた AD 仮想マシンは、推奨される修正措置。 アシスタンスの css に問い合わせます。  
  
## <a name="see-also"></a>参照  
[パスワードのリセット&#40;Analytics Platform System&#41;](password-reset.md)  
  
