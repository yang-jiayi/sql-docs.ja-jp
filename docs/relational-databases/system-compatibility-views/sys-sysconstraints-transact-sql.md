---
title: sys.sysconstraints (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fce3ca4a2055d7f4eb10cfdcac7f09c7fd004282
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806880"
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  データベースにおける、制約を持つオブジェクトとその制約のマッピングを格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|制約番号。|  
|**id**|**int**|制約を持つテーブルの ID。|  
|**colid**|**smallint**|制約が定義されている列の ID。<br /><br /> 0 = テーブル制約|  
|**spare1**|**tinyint**|予約済み。|  
|**status**|**int**|状態を示す疑似ビットマスク。 次の値があります。<br /><br /> 1 = PRIMARY KEY 制約<br /><br /> 2 = UNIQUE KEY 制約<br /><br /> 3 = FOREIGN KEY 制約<br /><br /> 4 = CHECK 制約<br /><br /> 5 = DEFAULT 制約<br /><br /> 16 = 列レベル制約<br /><br /> 32 = テーブル レベル制約|  
|**アクション**|**int**|予約済み。|  
|**error**|**int**|予約済み。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
