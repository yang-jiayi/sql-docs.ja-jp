---
title: "setClob (java.lang.String, java.io.Reader) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7457b8a-df31-4999-883e-8cc386a48ceb
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee2f6f5d5e6217c93f4ac0398361f88a68a5441e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setclob-method-javalangstring-javaioreader"></a>setClob (java.lang.String, java.io.Reader) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された Reader オブジェクトを指定されたパラメーターを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setClob(java.lang.String parameterName,  
            java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *パラメーター名*  
  
 A**文字列**パラメーター名を格納しています。  
  
 *リーダー*  
  
 リーダー オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setClob メソッドは、java.sql.CallableStatement インターフェイスの setClob メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setClob メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  