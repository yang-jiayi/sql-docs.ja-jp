---
title: sp_batch_params (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_batch_params
- sp_batch_params_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_batch_params
ms.assetid: 7b92fe9e-e755-4b7a-8a15-822c58a813d3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a759490fdd2306d7fecfd34484708e5c24970217
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126842"
---
# <a name="spbatchparams-transact-sql"></a>sp_batch_params (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  含まれているパラメーターに関する情報を含む行セットを返す、 [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチです。 **sp_batch_params**のみに指定されたバッチを解析し、埋め込みパラメーター値に関する情報を返します。 バッチの実行や、実行環境の変更は行いません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_batch_params [ [ @tsqlbatch = ] 'tsqlbatch' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@tsqlbatch =**] **'**_tsqlbatch_**'**  
 含む Unicode 文字列には、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはバッチのパラメーターの情報は、します。 *tsqlbatch*は**nvarchar (max)** に暗黙的に変換または**nvarchar (max)** します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**PARAMETER_NAME**|**sysname**|バッチ内で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が検出したパラメーターの名前です。|  
|**COLUMN_TYPE**|**smallint**|このフィールドは、次のいずれかの値を返します。<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE<br /><br /> この列は常に 0 です。|  
|**DATA_TYPE**|**smallint**|パラメーターのデータ型 (ODBC データ型の整数コード) です。 このデータ型が ISO 型にマップできない場合、値は NULL になります。 ネイティブ データ型の名前が返されます、 **TYPE_NAME**列。 この値は常に NULL です。|  
|**TYPE_NAME**|**sysname**|基になる DBMS によって表された、データ型を表す文字列です。 この値は NULL です。|  
|**PRECISION**|**int**|有効桁数です。 戻り値、**精度**列は 10 進数。|  
|**LENGTH**|**int**|データの転送サイズです。 この値は NULL です。|  
|**スケール**|**smallint**|小数点より右側の桁数です。 この値は NULL です。|  
|**RADIX**|**smallint**|数値型の基数です。 この値は NULL です。|  
|**NULLABLE**|**smallint**|NULL 値を許容するかどうかを指定します。<br /><br /> 1 = NULL 値を許容するパラメーターのデータ型が作成されます。<br /><br /> 0 = null 値は許可されません。<br /><br /> この値は NULL です。|  
|**SQL_DATA_TYPE**|**smallint**|記述子の TYPE フィールドでの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型の値です。 この列は、**datetime** データ型と ISO **interval** データ型以外は、**DATA_TYPE** 列と同じです。 この列は常に値が返されます。 この値は NULL です。|  
|**SQL_DATETIME_SUB**|**smallint**|**Datetime**または ISO**間隔**サブコードの場合、値の**SQL_DATA_TYPE**が SQL_DATETIME または SQL_INTERVAL します。 **datetime** および **ISO interval** 以外のデータ型の場合、この列は NULL です。 この値は NULL です。|  
|**CHAR_OCTET_LENGTH**|**int**|最大長のバイト単位、**文字**または**バイナリ**データ型のパラメーター。 他のすべてのデータ型の場合、この列は NULL を返します。 この値は常に NULL です。|  
|**ORDINAL_POSITION**|**int**|バッチ内でのパラメーターの序数です。 パラメーター名が複数回繰り返される場合は、この列には最初のオカレンスの序数が入ります。 最初のパラメーターには序数 1 が設定されます。 この列は常に値が返されます。|  
  
## <a name="permissions"></a>アクセス許可  
 実行する権限**sp_batch_params**に付与されます**パブリック**します。  
  
## <a name="examples"></a>使用例  
 この例では、クエリが `sp_batch_params` に渡されています。 結果セットは、埋め込みパラメーター値の一覧を列挙します。  
  
```  
DECLARE @SQLString nvarchar(500);  
/* Build the SQL string */  
SET @SQLString =  
     N'SELECT * FROM AdventureWorks2012.HumanResources.Employee   
     WHERE BusinessEntityID = @BusinessEntityID';  
EXECUTE sp_batch_params @SQLString;  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [ストアド プロシージャの操作方法に関するトピックを実行している&#40;ODBC&#41;](https://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)   
 [ストアド プロシージャの実行 &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/stored-procedures-running.md)  
  
  
