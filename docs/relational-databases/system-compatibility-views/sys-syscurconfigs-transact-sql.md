---
title: "sys.syscurconfigs (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.syscurconfigs
- sys.syscurconfigs_TSQL
- syscurconfigs
- syscurconfigs_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.syscurconfigs compatibility view
- syscurconfigs system table
ms.assetid: 454ab849-07a5-4b50-ba0a-6b1b14721f77
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ced0f1fa5237ecef93d61ea2049245f33bcca3cc
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="syssyscurconfigs-transact-sql"></a>sys.syscurconfigs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在の構成オプションごとに 1 つのエントリを保持します。 また、このビューには、構成構造を表す 4 つのエントリも登録されます。 **syscurconfigs**は、ユーザーが照会されたときに動的に構築します。 詳細については、次を参照してください。 [sys.sysconfigures &#40;です。TRANSACT-SQL と #41 です;](../../relational-databases/system-compatibility-views/sys-sysconfigures-transact-sql.md)。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**値**|**int**|ユーザーが変更可能な変数の値です。 これは、使用して、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] RECONFIGURE が実行された場合にのみです。|  
|**構成**|**smallint**|構成変数番号です。|  
|**コメント**|**nvarchar (255)**|この構成オプションの説明です。|  
|**ステータス**|**smallint**|このオプションの状態を表すビットマップです。 次の値があります。<br /><br /> 0 = 静的。 設定はサーバーの再起動時に反映されます。<br /><br /> 1 = 動的。 変数は RECONFIGURE ステートメントの実行時に反映されます。<br /><br /> 2 = 詳細。 変数が表示される場合にのみ、**オプションの詳細の表示**設定されています。<br /><br /> 3 = 動的および詳細。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  