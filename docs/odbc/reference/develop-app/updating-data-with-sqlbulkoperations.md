---
title: "SQLBulkOperations によるデータの更新 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75e5f954065c0b41935aa231c85c093d5ee10226
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updating-data-with-sqlbulkoperations"></a>SQLBulkOperations によるデータの更新
アプリケーションは、データ ソースへの呼び出しと基になるテーブルでの一括更新、削除、fetch、または挿入操作を実行できる**SQLBulkOperations**です。 呼び出す**SQLBulkOperations**便利な代替手段を作成して SQL ステートメントを実行します。 これにより、odbc データ ソースが配置されている SQL ステートメントをサポートしていない場合でも、位置指定更新をサポートできます。 関数呼び出しを使用してデータベースの完全なアクセスを実現するためのパラダイムの一部です。  
  
 **SQLBulkOperations**現在の行セットに対して演算を行いへの呼び出し後にのみ使用できます**SQLFetch**または**SQLFetchScroll**です。 アプリケーションでは、更新、削除、またはそのブックマークをキャッシュして、更新する行を指定します。 ドライバーは、新しい行のデータを更新するか、行セットのバッファーから、基になるテーブルに挿入する新しいデータを取得します。  
  
 によって使用される行セット サイズ**SQLBulkOperations**への呼び出しで設定されている**SQLSetStmtAttr**で、*属性*引数 sql_attr_row_array_size を指定します。 異なり**SQLSetPos**、のみ呼び出しの後に新しい行セットのサイズを使用する**SQLFetch**または**SQLFetchScroll**、 **SQLBulkOperations**を使用して、呼び出しの後に新しい行セット サイズ**SQLSetStmtAttr**です。  
  
 Sql、リレーショナル データベースとほとんどの対話が行われるため**SQLBulkOperations**広くサポートされていません。 ただし、ドライバー簡単にエミュレートできますそれを作成して実行して、**更新**、**削除**、または**挿入**ステートメントです。  
  
 どのような操作を決定する**SQLBulkOperation**サポートされており、アプリケーションが呼び出す**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_CURSOR_ATTRIBUTES1 情報オプション (カーソルの種類) によって異なります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLBulkOperations とブックマークによる行の更新](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [SQLBulkOperations とブックマークによる行の削除](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [SQLBulkOperations で行を挿入します。](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [SQLBulkOperations を持つ行のフェッチ](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)