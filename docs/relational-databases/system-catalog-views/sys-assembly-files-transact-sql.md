---
title: sys.assembly_files (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.assembly_files
- assembly_files_TSQL
- assembly_files
- sys.assembly_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_files catalog view
ms.assetid: 1a384a2c-5556-4d12-a2ba-4da781363143
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0279d6c2850dff07b365e7543f387f6cf6e9f328
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810230"
---
# <a name="sysassemblyfiles-transact-sql"></a>sys.assembly_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アセンブリを構成するファイルごとに 1 行のデータを保持します。  
    
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|このファイルが所属するアセンブリの ID です。|  
|**name**|**nvarchar(260)**|アセンブリ ファイルの名前です。|  
|**file_id**|**int**|ファイルの ID です。 アセンブリ内で一意です。 ファイル ID 1 は、アセンブリ DLL を表します。|  
|**content**|**varbinary(max)**|ファイルのコンテンツです。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR アセンブリ カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;TRANSACT-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
