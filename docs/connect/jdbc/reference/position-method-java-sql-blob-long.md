---
title: position (java.sql.Blob, long) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.position (java.sql.Blob.long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebd005e5-f6c5-4789-87f9-d2fdacd35060
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f7d4ae8550d35b65589ba735765016df623fc7c3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830090"
---
# <a name="position-method-javasqlblob-long"></a>position (java.sql.Blob, long) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたパターンと開始インデックスに基づいて、BLOB 内の指定されたパターンの位置を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public long position(java.sql.Blob pattern,  
                     long start)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *pattern*  
  
 検索するパターンです。  
  
 *start*  
  
 検索の開始インデックスです。  
  
## <a name="return-value"></a>戻り値  
 パターンが見つかった場合は位置の **long** 値で、見つからなかった場合は -1 です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この位置のメソッドは、java.sql.Blob インターフェイスでの位置のメソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [position メソッド&#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/position-method-sqlserverblob.md)   
 [SQLServerBlob のメソッド](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob のメンバー](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob クラス](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
