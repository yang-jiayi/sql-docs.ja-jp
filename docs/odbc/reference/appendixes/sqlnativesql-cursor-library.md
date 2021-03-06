---
title: SQLNativeSql (カーソル ライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5b87f64963e7b0ad45fbec33e410165cd0c9723
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656712"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLNativeSql**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLNativeSql**を参照してください[SQLNativeSql 関数](../../../odbc/reference/syntax/sqlnativesql-function.md)します。  
  
 ドライバーは、この関数をサポートする場合、カーソル ライブラリを呼び出す**SQLNativeSql**ドライバーで SQL ステートメントに渡します。 位置指定の update、delete、配置と**選択更新**ステートメント、カーソル ライブラリは、ドライバーに渡す前にステートメントを変更します。  
  
> [!NOTE]  
>  カーソル ライブラリを正しく返していない SQLSTATE 34000 (無効なカーソル名)、カーソル名が位置指定の update または delete ステートメントで渡されるは有効ではない場合、 *InStatementText*の引数**SQLNativeSql**. **SQLNativeSql**ステートメントの準備または実行時にのみ返される構文エラーを返すものではありません。
