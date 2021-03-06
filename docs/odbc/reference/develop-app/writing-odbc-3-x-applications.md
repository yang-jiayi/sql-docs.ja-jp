---
title: ODBC 3.x アプリケーションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], about upgrading
- ODBC drivers [ODBC], backward compatibility
- upgrading applications [ODBC]
- compatibility [ODBC], upgrading applications
- application upgrades [ODBC]
- upgrading applications [ODBC], about upgrading
- backward compatibility [ODBC], upgrading applications
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93c8510bb23bb57244590a472073fc882f9fe64f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769150"
---
# <a name="writing-odbc-3x-applications"></a>ODBC 3.x アプリケーションの作成
ODBC 2 時にします。*x*アプリケーションは、ODBC 3 にアップグレードされます *。x*、両方 ODBC 2 で動作するように記述する必要があります *。x* 3 *。x*ドライバー。 アプリケーションでは、ODBC 3 のフル活用するために条件付きのコードを組み込む必要があります。*x*機能します。  
  
 SQL_OV_ODBC2 を SQL_ATTR_ODBC_VERSION 環境属性を設定する必要があります。 これにより、ODBC 2 のように、ドライバーが動作する *.x*セクションで説明されている変更に関するドライバー[動作が変更される](../../../odbc/reference/develop-app/behavioral-changes.md)します。  
  
 アプリケーションが、セクションで説明されている機能のいずれか使うかどうか[の新機能](../../../odbc/reference/develop-app/new-features.md)、条件付きのコードを使用して、ドライバーが、ODBC 3 であるかどうかを判断する必要があります *。x*または ODBC 2 *.x*ドライバー。 アプリケーションを使用して**SQLGetDiagField**と**SQLGetDiagRec** ODBC 3 を取得します *。x* SQLSTATEs これらの条件付きのコード フラグメントの処理中にエラーを実行中にします。 新しい機能については、次の点を考慮する必要があります。  
  
-   行セット サイズの動作の変更によって影響を受けるアプリケーションを呼び出すしないように注意する必要があります**SQLFetch**配列のサイズが 1 より大きい場合。 これらのアプリケーションへの呼び出しを置き換える必要があります**SQLExtendedFetch**への呼び出しに**SQLSetStmtAttr** SQL_ATTR_ARRAY_STATUS_PTR ステートメント属性を設定して**SQLFetchScroll**両方 ODBC 3 で動作する一般的なコードがあるため、します。*x*および ODBC 2 *。x*ドライバー。 **SQLSetStmtAttr** SQL_ATTR_ROW_ARRAY_SIZE にマップされる**SQLSetStmtAttr** ODBC 2 SQL_ROWSET_SIZE と *。x*ドライバー、その複数行のフェッチ操作、アプリケーションは SQL_ATTR_ROW_ARRAY_SIZE を設定できますだけです。  
  
-   アップグレードするほとんどのアプリケーションは、SQLSTATE コードの変更によって実際には影響ありません。 影響を受けるアプリケーションの機械的な検索を実行し、「SQLSTATE マッピング」のセクションではエラーの変換テーブルを使用して、ODBC 3 を変換するほとんどの場合を指定して置換できます。*x*エラー コードが ODBC 2 *.x*コード。 ODBC 3 以降 *.x*ドライバー マネージャーは ODBC 2 からマッピングを実行します *。x* odbc 3 SQLSTATEs *。x* SQLSTATEs、これらのアプリケーションの作成者に ODBC 3 のチェックだけが必要があります *。x* SQLSTATEs し、ODBC 2 を含む詳細については心配ありません *。x* SQLSTATEs で条件付きコード。  
  
-   アプリケーション日付、時刻、および timestamp データ型の場合は、アプリケーションは、ODBC 2 自体を宣言できます。*x*コスト コードを使用する代わりに、既存のコードをアプリケーションおよび使用します。  
  
 アップグレードでは、次の手順を含める必要があります。  
  
-   呼び出す**SQLSetEnvAttr** SQL_OV_ODBC2 を SQL_ATTR_ODBC_VERSION 環境属性を設定する接続を割り当てる前にします。  
  
-   すべての呼び出しを置き換える**SQLAllocEnv**、 **SQLAllocConnect**、または**SQLAllocStmt**への呼び出しに**SQLAllocHandle**と適切な*HandleType* sql_handle_env として、sql_handle_dbc として、または sql_handle_stmt としての引数。  
  
-   すべての呼び出しを置き換える**SQLFreeEnv**または**SQLFreeConnect**への呼び出しに**SQLFreeHandle**と適切な*HandleType*引数sql_handle_dbc としてまたは sql_handle_stmt として。  
  
-   すべての呼び出しを置き換える**SQLSetConnectOption**への呼び出しに**SQLSetConnectAttr**します。 属性の値の設定が文字列の場合、設定、 *StringLength*引数適切にします。 変更*属性*SQL_ATTR_XXXX SQL_XXXX から引数。  
  
-   すべての呼び出しを置き換える**SQLGetConnectOption**への呼び出しに**SQLGetConnectAttr**します。 文字列またはバイナリ属性を取得する場合は、設定*BufferLength*に適切な値を渡します、 *StringLength*引数。 変更*属性*SQL_ATTR_XXXX SQL_XXXX から引数。  
  
-   すべての呼び出しを置き換える**SQLSetStmtOption**への呼び出しに**SQLSetStmtAttr**します。 属性の値の設定が文字列の場合、設定、 *StringLength*引数適切にします。 変更*属性*SQL_ATTR_XXXX SQL_XXXX から引数。  
  
-   すべての呼び出しを置き換える**SQLGetStmtOption**への呼び出しに**SQLGetStmtAttr**します。 文字列またはバイナリ属性を取得する場合は、設定*BufferLength*に適切な値を渡します、 *StringLength*引数。 変更*属性*SQL_ATTR_XXXX SQL_XXXX から引数。  
  
-   すべての呼び出しを置き換える**SQLTransact**への呼び出しに**SQLEndTran**します。 場合の最も右にある有効なハンドル、 **SQLTransact**呼び出しは、環境ハンドルを*HandleType* sql_handle_env としての引数を使用する必要があります、 **SQLEndTran**を呼び出す適切な*処理*引数。 場合の最も右にある有効なハンドル、 **SQLTransact**呼び出しは、接続ハンドルを*HandleType* sql_handle_dbc としての引数を使用する必要があります、 **SQLEndTran**を呼び出す適切な*処理*引数。  
  
-   すべての呼び出しを置き換える**SQLColAttributes**への呼び出しに**SQLColAttribute**します。 場合、 *FieldIdentifier* SQL_COLUMN_PRECISION、SQL_COLUMN_SCALE、または SQL_COLUMN_LENGTH のいずれかに引数がある関数の名前以外にも変更しないでください場合、。 そうでない場合は、変更*FieldIdentifier* SQL_COLUMN_XXXX SQL_DESC_XXXX するからです。 場合*FieldIdentifier* SQL_DESC_CONCISE_TYPE データ型が datetime データ型であり、対応する ODBC 3 に変更 *.x*データ型。  
  
-   ブロック カーソル、スクロール可能なカーソル、またはその両方を使用して、アプリケーションは次の。  
  
    -   行セットのサイズ、カーソルの種類、およびカーソルの同時実行制御を使用して設定**SQLSetStmtAttr**します。  
  
    -   呼び出し**SQLSetStmtAttr**状態レコードの配列を指すようにし、SQL_ATTR_ROW_STATUS_PTR を設定します。  
  
    -   呼び出し**SQLSetStmtAttr** SQLINTEGER を指す SQL_ATTR_ROWS_FETCHED_PTR を設定します。  
  
    -   必要なバインディングを実行し、SQL ステートメントを実行します。  
  
    -   呼び出し**SQLFetchScroll**で行をフェッチし、結果内を移動するループを設定します。  
  
    -   ブックマークによるをフェッチする必要がある場合、アプリケーションが呼び出す**SQLSetStmtAttr** SQL_ATTR_FETCH_BOOKMARK_PTR を呼び出し、フェッチする行のブックマークを含む変数を設定する**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_BOOKMARK の引数。  
  
-   パラメーターの配列を使用する場合、アプリケーションは、次の。  
  
    -   呼び出し**SQLSetStmtAttr** SQL_ATTR_PARAMSET_SIZE 属性パラメーターの配列のサイズを設定します。  
  
    -   呼び出し**SQLSetStmtAttr**内部 UDWORD 変数を指す SQL_ATTR_ROWS_PROCESSED_PTR を設定します。  
  
    -   実行の準備、バインド、および適切な操作を実行します。  
  
    -   何らかの理由 (SQL_NEED_DATA) などの実行が停止し場合、は、SQL_ATTR_ROWS_PROCESSED_PTR によって示される場所を調べることによってパラメーターの「現在」の行を検索ができます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [アプリケーションの旧バージョンとの互換性のためのマッピング置換関数](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)  
  
-   [SQLCloseCursor の呼び出し](../../../odbc/reference/develop-app/calling-sqlclosecursor.md)  
  
-   [SQLGetDiagField の呼び出し](../../../odbc/reference/develop-app/calling-sqlgetdiagfield.md)  
  
-   [SQLSetPos の呼び出し](../../../odbc/reference/develop-app/calling-sqlsetpos.md)  
  
-   [カーソル ライブラリの操作](../../../odbc/reference/develop-app/cursor-library-operations.md)  
  
-   [Cursor Attributes1 の情報の種類のマッピング](../../../odbc/reference/develop-app/mapping-the-cursor-attributes1-information-types.md)  
  
-   [SQL_NO_DATA](../../../odbc/reference/develop-app/sql-no-data.md)
