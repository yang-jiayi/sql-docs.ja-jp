---
title: sys.dm_exec_external_work (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DM_EXEC_EXTERNAL_WORK
- DM_EXEC_EXTERNAL_WORK_TSQL
- SYS.DM_EXEC_EXTERNAL_WORK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_external_work management view
- dm_exec_external_work management view
- PolyBase,views
- PolyBase
ms.assetid: 7597d97b-1fde-4135-ac35-4af12968f300
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a53a32f01dcf4646ee0bc12843c188b9b0e8e4c0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52418626"
---
# <a name="sysdmexecexternalwork-transact-sql"></a>sys.dm_exec_external_work (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  すべての計算ノード上のワーカーごとのワークロードに関する情報を返します。  
  
 (例: Hadoop または外部の SQL Server) は、外部データ ソースとの通信に作業を識別するために sys.dm_exec_external_work をクエリします。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|execution_id|**nvarchar(32)**|関連付けられている PolyBase クエリの一意の識別子。|参照してください*request_ID*で[sys.dm_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)します。|  
|step_index|**int**|このワーカーは、要求を実行します。|参照してください*step_index*で[sys.dm_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)します。|  
|dms_step_index|**int**|このワーカーを実行している DMS プランのステップします。|参照してください[sys.dm_exec_dms_workers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)します。|  
|compute_node_id|**int**|ノードの作業者が行われています。|参照してください[sys.dm_exec_compute_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)します。|  
|type|**nvarchar(60)**|外部の作業の種類。|ファイルの分割 '|  
|work_id|**int**|実際の分割の ID です。|以上の値を 0 にします。|  
|input_name|**nvarchar (4000)**|読み取るへの入力の名前|Hadoop を使用する場合は、ファイル名です。|  
|read_location|**bigint**|オフセット、または場所を読み取る。|読み取るファイルのオフセットです。|  
|bytes_processed|**bigint**|このワーカーによって処理された合計バイト数。|以上の値を 0 にします。|  
|length|**bigint**|Split または Hadoop が発生した場合、HDFS ブロックの長さ|ユーザーが定義可能です。 既定では 64 M です。|  
|status|**nvarchar(32)**|ワーカーの状態|保留中で、処理、完了、失敗した、中止されました|  
|start_time|**datetime**|作業の開始||  
|end_time|**datetime**|作業の終了||  
|total_elapsed_time|**int**|合計時間 (ミリ秒)||  
  
## <a name="see-also"></a>参照  
 [PolyBase 動的管理ビューでのトラブルシューティング](https://msdn.microsoft.com/library/ce9078b7-a750-4f47-b23e-90b83b783d80)   
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  
  
  
