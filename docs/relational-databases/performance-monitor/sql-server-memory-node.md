---
title: SQL Server、Memory Node | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: ed5f54ae9e24574589f880f864645a634d78e177
ms.sourcegitcommit: 0c1d552b3256e1bd995e3c49e0561589c52c21bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2018
ms.locfileid: "53380010"
---
# <a name="sql-server-memory-node"></a>SQL Server、Memory Node
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Microsoft **の** Memory Node [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトには、NUMA ノードのサーバー メモリの使用状況を監視するためのカウンターが用意されています。  
  
## <a name="memory-node-counters"></a>Memory Node カウンター  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** カウンターについて説明します。  
  
|SQL Server Memory Manager カウンター|[説明]|  
|----------------------------------------|-----------------|  
|**Database Node Memory (KB)**|このノードでデータベース ページに現在使用しているメモリの量を指定します。|  
|**Free Node Memory (KB)**|このノードの未使用のメモリの量を指定します。|  
|**Foreign Node Memory (KB)**|このノードの NUMA ローカル メモリ以外のメモリの量を指定します。|  
|**Stolen Memory Node (KB)**|このノードでデータベース ページ以外に使用しているメモリの量を指定します。|  
|**Target Node Memory**|このノードの理想的なメモリの量を指定します。|  
|**Total Node Memory**|サーバーがこのノードでコミットしているメモリの総容量を示します。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server: Buffer Manager オブジェクト](../../relational-databases/performance-monitor/sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.md)  
  
  
