---
title: sys.pdw_health_component_status_mappings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 4272cfad-5ad7-493d-9edd-d9111619bda0
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 02771656dfdb0b7396e62a5bde364b0eea324aa0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031193"
---
# <a name="syspdwhealthcomponentstatusmappings-transact-sql"></a>sys.pdw_health_component_status_mappings (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  間のマッピングを定義、[!INCLUDE[ssDW](../../includes/ssdw-md.md)]コンポーネントのステータスとコンポーネントの製造元定義名。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|property_id|**int**|プロパティの一意の識別子。<br /><br /> property_id、かを照会および physical_name は、このビューのキーを形成します。|NOT NULL|  
|component_id|**int**|コンポーネントの ID。 参照してください[sys.pdw_health_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md)します。<br /><br /> property_id、かを照会および physical_name は、このビューのキーを形成します。|NOT NULL|  
|physical_name|**nvarchar(32)**|プロパティ名、製造元によって定義されています。<br /><br /> property_id、かを照会および physical_name は、このビューのキーを形成します。|NOT NULL|  
|logical_name|**nvarchar (255)**|プロパティ名で定義されている[!INCLUDE[ssDW](../../includes/ssdw-md.md)]します。|NOT NULL<br /><br /> 0 - デバイスのインスタンスは一意です。<br /><br /> 1-デバイスのインスタンスは一意ではありません。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と Parallel Data Warehouse カタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
