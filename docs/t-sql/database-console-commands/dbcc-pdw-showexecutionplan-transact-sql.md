---
title: DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.technology: data-warehouse
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: f83aeec8ca81dd819e466f0e5017fb2e13514b61
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57684957"
---
# <a name="dbcc-pdwshowexecutionplan-transact-sql"></a>DBCC PDW_SHOWEXECUTIONPLAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

特定の [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] または [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] 計算ノードまたは制御ノードで実行されているクエリの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 実行プランを表示します。 クエリの計算ノードと制御ノードでの実行中に、クエリ パフォーマンスの問題のトラブルシューティングを行うにはこれを使用します。
  
計算ノードで実行されている SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリについて、クエリのパフォーマンスに問題があることがわかった場合、パフォーマンスを向上する方法がいくつかあります。 計算ノードでのクエリのパフォーマンスを向上させる方法として、複数列統計の作成、非クラスター化インデックスの作成、クエリ ヒントの使用が考えられます。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
Azure SQL Data Warehouse の構文:

```sql
DBCC PDW_SHOWEXECUTIONPLAN ( distribution_id, spid )  
[;]  
```  
Azure 並列データ ウェアハウスの構文:
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( pdw_node_id, spid )  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *distribution_id*  
 クエリ プランを実行しているディストリビューションの識別子です。 これは整数であり、NULL にすることはできません。 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] をターゲットとする場合に使用されます。  
  
 *pdw_node_id*  
 クエリ プランを実行しているノードの識別子です。 これは整数であり、NULL にすることはできません。 アプライアンスをターゲットとする場合に使用されます。  
  
 *spid*  
 クエリ プランを実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セッションの識別子です。 これは整数であり、NULL にすることはできません。  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] に対する CONTROL アクセス許可が必要です。  
  
アプライアンスに対する VIEW-SERVER-STATE アクセス許可が必要です。
  
## <a name="examples-includesssdwincludessssdw-mdmd"></a>例: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]  
  
### <a name="a-dbcc-pdwshowexecutionplan-basic-syntax"></a>A. DBCC PDW_SHOWEXECUTIONPLAN の基本的な構文  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] インスタンスで実行している場合は、上記のクエリを変更して distribution_id も選択します。  
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status], [distribution_id]  
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
order by request_id, [dms_step_index];  
```  
  
その結果、アクティブに実行されている各ディストリビューションの spid が返されます。 セッション 375 で 1 が実行していたディストリビューションを確認するには、次のコマンドを実行します。
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 1, 375 );  
```  

## <a name="examples-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="b-dbcc-pdwshowexecutionplan-basic-syntax"></a>B. DBCC PDW_SHOWEXECUTIONPLAN の基本的な構文  
 実行時間が長すぎるクエリでは、DMS クエリプラン操作または SQL クエリ プラン操作が実行されています。  
  
クエリで DMS クエリ プラン操作が実行されている場合は、次のクエリを使用して、不完全な手順のノード ID とセッション ID のリストを取得できます。
  
```sql
SELECT [sql_spid], [pdw_node_id], [request_id], [dms_step_index], [type], [start_time], [end_time], [status]   
FROM sys.dm_pdw_dms_workers   
WHERE [status] <> 'StepComplete' and [status] <> 'StepError'  
AND pdw_node_id = 201001   
order by request_id, [dms_step_index], [distribution_id];  
```  
  
上記のクエリの結果に基づき、DBCC PDW_SHOWEXECUTIONPLAN へのパラメーターとして、sql_spid と pdw_node_id を使用します。 たとえば、次のコマンドでは、pdw_node_id 201001 と sql_spid 375 の実行プランが表示されます。
  
```sql
DBCC PDW_SHOWEXECUTIONPLAN ( 201001, 375 );  
```  

## <a name="see-also"></a>参照
[DBCC PDW_SHOWPARTITIONSTATS &#40;Transact-SQL&#41;](dbcc-pdw-showpartitionstats-transact-sql.md)  
[DBCC PDW_SHOWSPACEUSED &#40;Transact-SQL&#41;](dbcc-pdw-showspaceused-transact-sql.md)
