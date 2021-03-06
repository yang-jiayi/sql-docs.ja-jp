---
title: sys.dm_hadr_cluster (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/31/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster
- dm_hadr_cluster_HADR
- sys.dm_hadr_cluster_TSQL
- dm_hadr_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: 13ce70e4-9d43-4a80-a826-099e6213bf85
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 58450f8e43c5f1f736fb4388008f7af3325e430d
ms.sourcegitcommit: 7c052fc969d0f2c99ad574f99076dc1200d118c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "55570735"
---
# <a name="sysdmhadrcluster-transact-sql"></a>sys.dm_hadr_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  かどうか、Windows Server フェールオーバー クラスタ リング (WSFC) ノード インスタンスをホストするの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を有効になっている[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]WSFC のクォーラムが存在**sys.dm_hadr_cluster**クラスター名と情報を公開する行を返しますクォーラムについて。 WSFC ノードがクォーラムを持たない場合、行は返されません。  
 > [!TIP]
 > 以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、この動的管理ビューは、Always On フェールオーバー クラスター インスタンスだけでなく Always On 可用性グループをサポートしています。

|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**cluster_name**|**nvarchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に対応した [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] のインスタンスをホストする WSFC クラスターの名前。|  
|**quorum_type**|**tinyint**|この WSFC クラスターで使用されているクォーラムの種類。次のいずれかになります。<br /><br /> 0 = ノード マジョリティ。 このクォーラム構成では、クラスター内の半数のノード (切り上げ) より 1 つ少ない数のノードの障害に耐えることができます。 たとえば、7 つのノードから成るクラスターの場合、このクォーラム構成では 3 つのノードの障害に対する耐性があります。<br /><br /> 1 = ノードおよびディスク マジョリティ。 ディスク監視がオンラインのままの場合、このクォーラム構成では、クラスター内の半数のノード (切り上げ) の障害に耐えることができます。 たとえば、6 つのノードから成るクラスターの場合、ディスク監視がオンラインのときは 3 つのノードの障害に対する耐性があります。 ディスク監視がオフラインになった場合、またはディスク監視で障害が発生している場合、半数のノード (切り上げ) より 1 つ少ない数のノードの障害に耐えることができます。 たとえば、6 つのノードから成るクラスターの場合、ディスク監視で障害が発生しているときは 2 つのノード (3-1=2) の障害に対する耐性があります。<br /><br /> 2 = ノードおよびファイル共有マジョリティ。 このクォーラム構成は "ノードおよびディスク マジョリティ" と同じように動作しますが、ディスク監視の代わりにファイル共有監視を使用します。<br /><br /> 3 = マジョリティなし。ディスクのみ。 クォーラム ディスクがオンラインの場合、このクォーラム構成では、1 つを除くすべてのノードの障害に耐えることができます。<br /><br /> 4 = 不明なクォーラム。 クラスターの不明なクォーラム。<br /><br /> 5 = クラウド ミラーリング監視サーバー。 クラスターは、クォーラムの調停の Microsoft Azure を利用します。 クラウド監視を使用できる場合、クラスターは半数のノード (切り上げ) の障害を維持できます。|  
|**quorum_type_desc**|**varchar (50)**|説明**quorum_type**、1 つの。<br /><br /> NODE_MAJORITY<br /><br /> NODE_AND_DISK_MAJORITY<br /><br /> NODE_AND_FILE_SHARE_MAJORITY<br /><br /> NO_MAJORITY:_DISK_ONLY <br /><br /> UNKNOWN_QUORUM <br /><br /> CLOUD_WITNESS|  
|**quorum_state**|**tinyint**|WSFC クォーラムの状態。次のいずれかになります。<br /><br /> 0 = クォーラム状態不明<br /><br /> 1 = 通常のクォーラム<br /><br /> 2 = 強制クォーラム|  
|**quorum_state_desc**|**varchar (50)**|説明**quorum_state**、1 つの。<br /><br /> UNKNOWN_QUORUM_STATE<br /><br /> NORMAL_QUORUM<br /><br /> FORCED_QUORUM|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [AlwaysOn 可用性グループのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql.md)  
  
  
