---
title: MSpub_identity_range (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpub_identity_range_TSQL
- MSpub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSpub_identity_range system table
ms.assetid: 68746eef-32e1-42bc-aff0-9798cd0e88b8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a60ae0e3cd8fb4a07ac9a947a8e4a7ea692d9b26
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821846"
---
# <a name="mspubidentityrange-transact-sql"></a>MSpub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpub_identity_range**テーブル id 範囲管理サポートを提供します。 このテーブルは、パブリケーションおよびサブスクリプション データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|レプリケーションで管理される ID 列を持つテーブルの ID です。|  
|**range**|**bigint**|サブスクリプションで調整の際に割り当てられる連続する ID 値の範囲の大きさを制御します。|  
|**pub_range**|**bigint**|パブリケーションで調整の際に割り当てられる連続する ID 値の範囲の大きさを制御します。|  
|**current_pub_range**|**bigint**|パブリケーションが使用している現在の範囲です。 これは異なっていてもかまいません*pub_range*による変更の後に表示した場合**sp_changearticle**と [次へ] の範囲調整の前にします。|  
|**threshold**|**int**|ディストリビューション エージェントがどの時点で新しい ID 範囲を割り当てるかを制御するパーセンテージの値です。 値の比率が指定されている場合*しきい値*はディストリビューション エージェント、新しい id 範囲を作成します。|  
|**last_seed**|**bigint**|現在の範囲の下限です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
