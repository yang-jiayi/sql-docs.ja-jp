---
title: 日付と時刻、およびスキーマ行セットの |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], schema rowsets
ms.assetid: 8c35e86f-0597-4ef4-b2b8-f643e53ed4c2
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 213c86a7f7b81a997082aa5653e00a830197f9d8
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52415579"
---
# <a name="metadata---date-and-time-and-schema-rowsets"></a>メタデータ - 日付、時刻、スキーマ行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックでは、COLUMNS 行セットおよび PROCEDURE_PARAMETERS 行セットについて説明します。 この情報は、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] で導入された OLE DB の日付と時刻の機能強化に関連しています。  
  
## <a name="columns-rowset"></a>COLUMNS 行セット  
 日付型または時刻型に対して返される列の値を次に示します。  
  
|列の型|DATA_TYPE|COLUMN_FLAGS、DBCOLUMFLAGS_SS_ISVARIABLESCALE|DATETIME_PRECISION|  
|-----------------|----------------|------------------------------------------------------|-------------------------|  
|日付|DBTYPE_DBDATE|Clear|0|  
|time|DBTYPE_DBTIME2|Set|0..7|  
|smalldatetime|DBTYPE_DBTIMESTAMP|Clear|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|Clear|3|  
|datetime2|DBTYPE_DBTIMESTAMP|Set|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|Set|0..7|  
  
 COLUMN_FLAG では、DBCOLUMNFLAGS_ISFIXEDLENGTH は日付/時刻型に対して常に true になり、次のフラグは常に false になります。  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 その他のフラグ (DBCOLUMNFLAGS_ISNULLABLE、DBCOLUMNFLAGS_MAYBENULL、DBCOLUMNFLAGS_WRITE、および DBCOLUMNFLAGS_WRITEUNKNOWN) は、列の定義方法に応じて設定されることがあります。  
  
 COLUMN_FLAGS に用意されている新しいフラグ DBCOLUMNFLAGS_SS_ISVARIABLESCALE を使用すると、アプリケーションは、DATA_TYPE が DBTYPE_DBTIMESTAMP である列のサーバーの種類を判断できます。 サーバーの種類を識別するには、DATETIME_PRECISION も使用する必要があります。  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE は [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のサーバーに接続されている場合にのみ有効です。 下位レベルのサーバーに接続されている場合、DBCOLUMNFLAGS_SS_ISFIXEDSCALE は未定義となります。  
  
## <a name="procedureparameters-rowset"></a>PROCEDURE_PARAMETERS 行セット  
 DATA_TYPE には COLUMNS スキーマ行セットと同じ値が格納され、TYPE_NAME にはサーバーの種類が格納されます。  
  
 COLUMNS 行セットと同様に、新しい列として SS_DATETIME_PRECISION が追加されました。この列は、DATETIME_PRECISION 列のように型の有効桁数を返します。  
  
## <a name="providertypes-rowset"></a>PROVIDER_TYPES 行セット  
 日付/時刻型に対して返される行を次に示します。  
  
|型 -><br /><br /> [列]|日付|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|日付|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_DBDATE|DBTYPE_DBTIME2|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMPOFFSET|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|scale|NULL|NULL|scale|scale|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|日付|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|0|NULL|NULL|0|0|  
|MAXIMUM_SCALE|NULL|7|NULL|NULL|7|7|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE (ただし、次のいずれかが当てはまる場合を除く)<br /><br /> 下位レベルのサーバーに接続されているクライアントの場合。<br /><br /> データ型の互換性の接続プロパティで、互換性レベルを 80 に指定している場合。|VARIANT_TRUE (ただし、次のいずれかが当てはまる場合を除く)<br /><br /> 下位レベルのサーバーに接続されているクライアントの場合。<br /><br /> データ型の互換性の接続プロパティで、互換性レベルを 80 に指定している場合。|VARIANT_TRUE|  
|IS_FIXEDLENGTH|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
  
 OLE DB では、MINIMUM_SCALE と MAXIMUM_SCALE が numeric 型および decimal 型用にしか定義されないため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client でこれらの列を time、datetime2、および datetimeoffset で使用することは標準的ではありません。  
  
## <a name="see-also"></a>参照  
 [メタデータ&#40;OLE DB&#41;](https://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
  
  
