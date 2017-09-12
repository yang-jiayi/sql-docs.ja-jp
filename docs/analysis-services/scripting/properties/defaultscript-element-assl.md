---
title: "DefaultScript 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DefaultScript Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DefaultScript
helpviewer_keywords:
- DefaultScript element
ms.assetid: 60716e63-2d64-4774-9ac9-253efe612fa5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 163c57ea60a832547a69d9e4c5ec1e6e21bb2f51
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="defaultscript-element-assl"></a>DefaultScript 要素 (ASSL)
  既定値を識別[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)内の要素、 [MdxScripts](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)コレクション。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MdxScript>  
   ...  
   <DefaultScript>...</DefaultScript>  
   ...  
</MdxScript>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|**True**|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値を設定**DefaultScript**に**True**スクリプトを 1 つの値の設定の**DefaultScript**に**False**の他のすべての**MdxScript**内の要素、 **MdxScripts**コレクション。  
  
 親に対応する要素**DefaultScript**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MdxScript>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  