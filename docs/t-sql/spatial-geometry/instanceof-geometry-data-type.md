---
title: InstanceOf (geometry データ型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d093331425443a0879d5f59f5a2d03fdebcb2abd
ms.sourcegitcommit: ad3b2133585bc14fc6ef8be91f8b74ee2f498b64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2019
ms.locfileid: "56425757"
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf (geometry データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** インスタンスが指定の型と同じであるかどうかをテストするメソッド。 **geometry** インスタンスの型が指定された型と同じである場合は、1 を返します。 このメソッドは、指定された型がインスタンスの型の先祖である場合も、1 を返します。 それ以外の場合、このメソッドは 0 を返します。
  
## <a name="syntax"></a>構文  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>引数  
*geometry_type*  
**geometry** 型の階層で公開されている 15 種類の型のうちの 1 つを指定する **nvarchar(4000)** 文字列。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **bit**  
  
 CLR の戻り値の型:**SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 メソッドへの入力は、次のいずれかの型である必要があります: **Geometry**、**Point**、**Curve**、**LineString**、**CircularString**、**CompoundCurve**、**Surface**、**Polygon**、**CurvePolygon**、**GeometryCollection**、**MultiSurface**、**MultiPolygon**、**MultiCurve**、**MultiLineString**、**MultiPoint**。 このメソッドは、上記以外の文字列が入力に使用された場合、**ArgumentException** をスローします。  
  
## <a name="examples"></a>使用例  
 `MultiPoint` インスタンスを作成し、`InstanceOf()` を使用して、このインスタンスが `GeometryCollection` であるかどうかを判定する例を次に示します。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>参照  
 [Geometry インスタンスの拡張メソッド](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

