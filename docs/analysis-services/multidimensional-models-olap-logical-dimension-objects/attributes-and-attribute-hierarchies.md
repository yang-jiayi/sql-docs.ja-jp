---
title: 属性と属性階層 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e30f3be6270cdc62b4b17048f9032a7c5587557
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027329"
---
# <a name="attributes-and-attribute-hierarchies"></a>属性と属性階層
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ディメンションとは属性のコレクションで、これらの属性はデータ ソース ビュー内のテーブルまたはビューの 1 つ以上の列にバインドされています。  
  
## <a name="key-attribute"></a>キー属性  
 各ディメンションにはキー属性が含まれています。 各属性は、ディメンション テーブル内の 1 つ以上の列にバインドされています。 キー属性は、各ディメンションに含まれている属性で、ファクト テーブルとの外部キー リレーションシップで使用されるディメンション メイン テーブル内の列を識別します。 通常、キー属性は、ディメンション テーブルに含まれている 1 つまたは複数の主キー列を表します。 基になるデータ ソースに物理主キーがないテーブルには、データ ソース ビューで論理主キーを定義できます。 **詳細については**を参照してください[を定義する論理主キー データ ソース ビューで&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-logical-primary-keys-in-a-data-source-view-analysis-services.md)です。 キー属性を定義する場合、キューブ ウィザードとディメンション ウィザードは、データ ソース ビューでディメンション テーブルの主キー列を使用しようとします。 ディメンション テーブルに論理主キーまたは物理主キーが定義されていない場合、これらのウィザードでは、ディメンションのキー属性を正しく定義できない可能性があります。  
  
## <a name="binding-an-attribute-to-columns-in-data-source-view-tables-or-views"></a>データ ソース ビュー テーブルまたはビュー内の列への属性のバインド  
 属性は、1 つ以上のデータ ソース ビュー テーブルまたはビュー内の列にバインドされています。 属性は常に 1 つ以上のキー列にバインドされており、これによって属性に含まれるメンバーが決定されます。 既定では、これは属性のバインド先の唯一の列になります。 1 つの属性を、特定の目的で 1 つ以上の列にバインドすることもできます。 たとえば、属性の**NameColumn**プロパティは、各属性メンバーをユーザーに表示される名前を決定 - 属性には、このプロパティがデータ ソース ビューから特定のディメンション列にバインドすることができますかを指定できますデータ ソース ビューの計算列にバインドします。 詳細については、次を参照してください。 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)です。  
  
## <a name="attribute-hierarchies"></a>属性階層  
 属性メンバーは、既定でリーフ レベルと All レベルから成る 2 つのレベルの階層に編成されます。 All レベルの内容は、属性が関連付けられているディメンションが属する各メジャー グループにおける、メジャー全体の属性のメンバーの集計値です。 ただし場合、 **IsAggregatable**プロパティが False に設定されて、すべてのレベルは作成されません。 詳細については、次を参照してください。 [Dimension Attribute Properties Reference](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)です。  
  
 属性はユーザー定義階層に配置することができ、そのようにするのが一般的です。ユーザー定義階層では、属性が関連付けられているメジャー グループ内のデータをユーザーが参照できるようにするためのドリル ダウン パスが提供されます。 クライアント アプリケーションでは、属性はグループ化と制約に関する情報を提供するために使用できます。 レベルが多対一で関連付けられている場合、階層レベル間のリレーションシップを定義する属性はユーザー定義階層に配置され、ときに、または一対一のリレーションシップ (と呼ばれる、*自然*リレーションシップ)。 たとえば、Calendar Time 階層では、日レベルは月レベルに関連付けられており、月レベルは四半期レベルに関連付けられている必要があります。 ユーザー定義階層内のレベル間のリレーションシップを定義すると、Analysis Services では、さらに便利な集計を定義して、クエリのパフォーマンスを改善し、同時に処理パフォーマンス中のメモリを節約できます。これは大規模なキューブまたは複雑なキューブでは重要になります。 詳細については、次を参照してください。[ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)、 [Create User-Defined 階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)、および[属性リレーションシップの定義](../../analysis-services/multidimensional-models/attribute-relationships-define.md)です。  
  
## <a name="attribute-relationships-star-schemas-and-snowflake-schemas"></a>属性リレーションシップ、スター スキーマ、およびスノーフレーク スキーマ  
 スター スキーマでは既定ですべての属性がキー属性に直接関連付けられます。したがってユーザーはディメンション内の任意の属性階層に基づいてキューブ内のファクトを参照できます。 スノーフレーク スキーマでは、基になるテーブルをファクト テーブルに直接リンクしている場合、属性はキー属性に直接リンクされます。または、直接リンクしているテーブルにスノーフレーク テーブルをリンクする、基になるテーブルのキーにバインドされた属性によって間接的にリンクされます。  
  
## <a name="see-also"></a>参照  
 [ユーザー定義階層を作成します。](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)   
 [属性リレーションシップを定義します。](../../analysis-services/multidimensional-models/attribute-relationships-define.md)   
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
