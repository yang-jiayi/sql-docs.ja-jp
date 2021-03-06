---
title: sys.procedures (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- procedures
- sys.procedures_TSQL
- sys.procedures
- procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.procedures catalog view
ms.assetid: d17af274-b2dd-464e-9523-ee1f43e1455b
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69a3fec4f785477a9ea4982a51a6ac84c9712971
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705480"
---
# <a name="sysprocedures-transact-sql"></a>sys.procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  何らかのプロシージャである各オブジェクトの行を格納**sys.objects.type** = P、X、RF、および PC です。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**\<Sys.objects から継承された列 >**||このビューが継承する列の一覧は、次を参照してください[sys.objects &#40;TRANSACT-SQL。&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)|  
|**is_auto_executed**|**bit**|プロシージャをサーバー起動時に自動実行する場合は 1、それ以外の場合は 0。 master データベースのプロシージャに対してのみ設定できます。|  
|**is_execution_replicated**|**bit**|プロシージャの実行をレプリケートします。|  
|**is_repl_serializable_only**|**bit**|プロシージャ実行のレプリケーションを、トランザクションがシリアル化される場合にのみ実行します。|  
|**skips_repl_constraints**|**bit**|プロシージャの実行中、NOT FOR REPLICATION としてマークされた制約をスキップします。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
