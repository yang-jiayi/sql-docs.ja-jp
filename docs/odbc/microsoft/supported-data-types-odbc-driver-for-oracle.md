---
title: サポートされるデータ型 (ODBC Driver for Oracle) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], data types
ms.assetid: 21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 219a6d2e837280ca3220382bea56d2ab610ce87a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620460"
---
# <a name="supported-data-types-odbc-driver-for-oracle"></a>サポートされるデータ型 (ODBC Driver for Oracle)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 ODBC Driver for Oracle は Oracle 7.3 のすべてのデータ型をサポートしていますただし、ここに表示されている、新しい Oracle8 データ型のいずれかのこともできません。  
  
|データ型|Oracle 7.3|Oracle8|  
|---------------|----------------|-------------|  
|BFILE|n/a|サポートされていません|  
|BLOB|n/a|サポートされていません|  
|CHAR|Supported|Supported|  
|CLOB|n/a|サポートされていません|  
|[DATE]|Supported|Supported|  
|[FLOAT]|Supported|Supported|  
|INTEGER|Supported|Supported|  
|LONG|Supported|Supported|  
|LONG RAW|Supported|Supported|  
|NCHAR|n/a|サポートされていません|  
|NCLOB|n/a|サポートされていません|  
|NUMBER|Supported|Supported|  
|NVARCHAR2|n/a|サポートされていません|  
|RAW|Supported|Supported|  
|VARCHAR2|Supported|Supported|  
|MLSLABEL|サポートされていません。|サポートされていません。|  
  
> [!NOTE]  
>  VARCHAR 列の許容サイズの詳細については、次を参照してください。 [VARCHAR 列のサイズ](../../odbc/microsoft/varchar-column-size-odbc-driver-for-oracle.md)このガイドでします。
