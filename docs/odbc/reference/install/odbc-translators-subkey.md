---
title: "ODBC トランスレーター サブキー |Microsoft ドキュメント"
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
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dfc34daa6236fa7187c27a204ee16cc47a0de7b0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-translators-subkey"></a>ODBC 変換者のサブキー
ODBC 変換器サブキーの下の値には、インストールされているトランスレーターが一覧表示します。 これらの値の形式は次の表に示します。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|*トランスレーター desc*|REG_SZ|**インストールされています。**|  
  
 *トランスレーター desc*名は変換プログラムの開発者によって定義されます。  
  
 たとえば、ユーザーがインストールされている、Microsoft® コード ページ変換プログラムとカスタム ASCII EBCDIC トランスレーターとします。 ODBC 変換器サブキーの下の値は次のあります。  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```