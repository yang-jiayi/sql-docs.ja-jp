---
title: データベース ミラーリング エンドポイント (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- database mirroring [SQL Server], endpoint
- endpoints [SQL Server], AlwaysOn Availability Groups
- endpoints [SQL Server], database mirroring
- Availability Groups [SQL Server], endpoint
ms.assetid: 39332dc5-678e-4650-9217-6aa3cdc41635
caps.latest.revision: 44
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e9250860dbdc750bda53e28e52a31bcbe0e038b9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185171"
---
# <a name="the-database-mirroring-endpoint-sql-server"></a>データベース ミラーリング エンドポイント (SQL Server)
  サーバー インスタンスが [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] またはデータベース ミラーリングに参加するには、専用の *データベース ミラーリング エンドポイント*が必要です。 このエンドポイントの用途は特殊で、他のサーバー インスタンスからの接続を受信するためにのみ使用されます。 特定のサーバー インスタンスでは、他のサーバー インスタンスに対するすべての [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] またはデータベース ミラーリング接続では、単一のデータベース ミラーリング エンドポイントが使用されます。  
  
 データベース ミラーリング エンドポイントでは、伝送制御プロトコル (TCP) を使用して、データベース ミラーリング セッションに参加するサーバー インスタンス間、または可用性レプリカをホストするサーバー インスタンス間でメッセージを送受信します。 データベース ミラーリング エンドポイントでは、一意な TCP ポート番号でリッスンします。  
  
> [!NOTE]  
>  プリンシパル サーバーまたはプライマリ レプリカとのクライアント接続では、データベース ミラーリング エンドポイントは使用されません。  
  
> [!NOTE]  
>  データベース ミラーリング機能は、将来のバージョンの Microsoft SQL Server では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在データベース ミラーリングを使用しているアプリケーションでは、代わりに [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] を使用するようにアプリケーションを修正することを計画してください。  
  
  
##  <a name="ServerNetworkAddress"></a> サーバー ネットワーク アドレス  
 サーバー インスタンスのネットワーク アドレス (サーバー インスタンスの *サーバー ネットワーク アドレス* または *エンドポイント URL*) には、そのサーバー インスタンスのホスト コンピューターのシステム名とドメイン名以外に、そのサーバー インスタンスのエンドポイントのポート番号も含まれています。 このポート番号は、特定のサーバー インスタンスを一意に識別します。  
  
 次の図に、同じサーバー上の 2 つのサーバー インスタンスを一意に識別するしくみを示します。 どちらのサーバー インスタンスのサーバー ネットワーク アドレスにも、同じシステム名 `MYSYSTEM`とドメイン名 `Adventure-Works.MyDomain.com`が含まれています。 システム側でサーバー インスタンスまでルーティングできるように、サーバー ネットワーク アドレスには、特定のサーバー インスタンスのミラーリング エンドポイントに関連付けられたポート番号が含まれています。  
  
 ![既定のインスタンスのサーバー ネットワーク アドレス](../media/dbm-2-instances-ports-1-system.gif "既定のインスタンスのサーバー ネットワーク アドレス")  
  
 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにはデータベース ミラーリング エンドポイントは含まれていません。 データベース ミラーリング エンドポイントは、データベース ミラーリング セッションの設定時に手動で作成する必要があります。 データベース ミラーリングにかかわる各サーバー インスタンスには、システム管理者が、別個のエンドポイントを作成する必要があります。 特定のコンピューターで複数のサーバー インスタンスがデータベース ミラーリング ポイントを必要とする場合は、エンドポイントごとに異なるポート番号を指定します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターでファイアウォールを使用している場合は、エンドポイントで指定されているポートを送信と受信の両方の接続で使用できるようにファイアウォールを構成する必要があります。  
  
 データベース ミラーリングと [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]では、認証と暗号化はエンドポイントで構成されます。 詳細については、次を参照してください。[データベース ミラーリングと AlwaysOn 可用性グループのトランスポート セキュリティ&#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)します。  
  
> [!IMPORTANT]  
>  使用中のデータベース ミラーリング エンドポイントは再構成しないでください。 サーバー インスタンスは、互いのエンドポイントを使用して、他のシステムの状態を調べます。 エンドポイントを再構成すると、そのエンドポイントは再起動されます。これにより、他のサーバー インスタンスではエラーが発生したように見えることがあります。 これは、自動フェールオーバー モードでは特に重要です。この場合、パートナーでエンドポイントを再構成すると、フェールオーバーが発生する可能性があります。  
  
  
##  <a name="EndpointAuthenticationTypes"></a> データベース ミラーリング エンドポイント用の Windows 認証の種類の決定  
 データベース ミラーリング エンドポイントに使用できる認証の種類は、サーバー インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントによって次のように決定されることを理解しておく必要があります。  
  
-   サーバー インスタンスがドメイン サービス アカウントで実行中の場合は、データベース ミラーリング エンドポイントで Windows 認証を使用できます。 同じドメイン ユーザー アカウントですべてのサーバー インスタンスを実行した場合は、自動的に両方の **マスター** データベースに正しいユーザー ログインが存在します。 可用性データベースのセキュリティ構成が単純化されるので、こちらの方法をお勧めします。  
  
     可用性グループの可用性レプリカをホストするサーバー インスタンスが異なるアカウントで実行される場合は、他のサーバー インスタンスの **マスター** 内にログイン アカウントを作成する必要があります。 その後、そのログインに対して、そのサーバー インスタンスのデータベース ミラーリング エンドポイントに接続するための CONNECT 権限を与える必要があります。 詳細については、[データベース ミラーリングまたは AlwaysOn 可用性グループには、ログイン アカウントを設定&#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)します。  
  
     サーバー インスタンスで Windows 認証を使用する場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、PowerShell、または新しい可用性グループ ウィザードを使用して、データベース ミラーリング エンドポイントを作成できます。  
  
    > [!NOTE]  
    >  可用性レプリカをホストするサーバー インスタンスにデータベース ミラーリング エンドポイントがない場合、新しい可用性グループ ウィザードは、Windows 認証を使用するデータベース ミラーリング エンドを自動的に作成できます。 詳細については、「[新しい可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](../availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)」を参照してください。  
  
-   サービス インスタンスがビルトイン アカウント (Local System、Local Service、Network Service など) で実行されている場合、または、非ドメイン アカウントで実行されている場合は、エンドポイント認証に証明書を使用する必要があります。 データベース ミラーリング エンドポイントに証明書を使用する場合、各サーバー インスタンスの発信接続と着信接続の両方に証明書を使用するための構成をシステム管理者が行う必要があります。  
  
     証明書を使用してデータベース ミラーリング セキュリティを自動的に構成する方法は用意されていません。 作成エンドポイントのどちらかを使用する必要があります[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントまたは`New-SqlHadrEndpoint`PowerShell コマンドレット。 詳細については、「[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)」を参照してください。 サーバー インスタンスの証明書認証を有効にする方法については、次を参照してください。[データベース ミラーリング エンドポイントの証明書を使用&#40;TRANSACT-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)します。  
  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **データベース ミラーリング エンドポイントを構成するには**  
  
-   [Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [データベース ミラーリング エンドポイントで着信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [サーバー ネットワーク アドレスの指定 &#40;データベース ミラーリング&#41;](specify-a-server-network-address-database-mirroring.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../ssms/sql-server-management-studio-ssms.md)  
  
 **データベース ミラーリング エンドポイントに関する情報を表示するには**  
  
-   [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリングと AlwaysOn 可用性グループのトランスポート セキュリティ&#40;SQL Server&#41;](transport-security-database-mirroring-always-on-availability.md)   
 [データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;](troubleshoot-database-mirroring-configuration-sql-server.md)   
 [sys.dm_hadr_availability_replica_states &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)   
 [sys.dm_db_mirroring_connections &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections)  
  
  