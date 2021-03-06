---
title: IsEmpty (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dbed0eba3fec73d7134b1ce21275c28dbd387fcd
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740171"
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)


  評価した式が空のセル値かどうかを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Value_Expression*  
 有効な多次元式 (MDX) 式です。通常は、メンバーまたは組のセル座標を返します。  
  
## <a name="remarks"></a>コメント  
 **IsEmpty**関数が返される**true**式の評価結果が空のセル値の場合。 この関数を返しますそれ以外の場合、 **false**です。  
  
> [!NOTE]  
>  メンバーの既定のプロパティは、そのメンバーの値です。  
  
 **IsEmpty**関数は、空のセル値に特別な意味があるため、空のセルを確実にテストする唯一の方法[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
> [!IMPORTANT]  
>  値式の評価エラーが返されます、この関数を返します**false**です。 値式がエラーを返すのは、たとえば、プロパティ参照によって、無効なプロパティまたは存在しないプロパティが参照されているような場合です。  
  
 空のセルの詳細については、OLE DB のドキュメントを参照してください。  
  
## <a name="example"></a>例  
 次の例では、Date ディメンションの Fiscal 階層にある現在のメンバーの Internet Sales Amount が空のセルを返す場合、TRUE を返します。  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [空の値の扱い](../mdx/working-with-empty-values.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
