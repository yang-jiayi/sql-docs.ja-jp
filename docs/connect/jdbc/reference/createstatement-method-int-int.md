---
title: createStatement (int, int) メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.createStatement (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 90dbf639-c3d8-4519-9300-5447c79aec17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58390bfd2310b1cae9ce7427106c88a8e38915df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645370"
---
# <a name="createstatement-method-int-int"></a>createStatement (int, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された結果セットの種類およびコンカレンシーの [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを生成する [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Statement createStatement(int resultSetType,  
                                          int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *resultSetType*  
  
 結果セットの種類を表す **int** 値です。  
  
 *resultSetConcurrency*  
  
 **Int**結果セットの同時実行の種類を表す値。  
  
## <a name="return-value"></a>戻り値  
 ステートメントのオブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この createStatement メソッドは、java.sql.Connection インターフェイスの createStatement メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [createStatement メソッド &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
