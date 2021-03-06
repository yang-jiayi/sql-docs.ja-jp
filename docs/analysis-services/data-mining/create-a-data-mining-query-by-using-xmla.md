---
title: XMLA を使用してデータ マイニング クエリの作成 |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d9741a81c10a71623f6e336795bb47ae199ee13d
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50146957"
---
# <a name="create-a-data-mining-query-by-using-xmla"></a>XMLA を使用したデータ マイニング クエリの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  AMO、DMX、または XML/A を使用すると、データ マイニング オブジェクトに対するさまざまなクエリを作成できます。  
  
 Analysis Services サーバーとすべてのクライアントの間の通信には、XML が使用されます。 したがって、一般には DMX を使用してコンテンツ クエリを作成する方がはるかに簡単ですが、SOAP プロトコルをサポートするクライアントを使用するか、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で XML/A クエリを作成することにより、XML/A で DISCOVER および COMMAND ステートメントを使用してクエリを作成できます。  
  
 このトピックでは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で利用できる XML/A テンプレートを使用して、現在のサーバーに格納されているマイニング モデルに対するモデル コンテンツ クエリを作成する方法について説明します。  
  
## <a name="querying-data-mining-schema-rowsets-by-using-xmla"></a>XML/A を使用したデータ マイニング スキーマ行セットのクエリ  
  
#### <a name="to-open-an-xmla-template"></a>XML/A テンプレートを開くには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  キューブ アイコンをクリックして、Analysis Services テンプレートの一覧を開きます。  
  
3.  テンプレート カテゴリの一覧で **[XMLA]**、 **[スキーマ行セット]** の順に展開し、 **[スキーマ行セットの発見]** をダブルクリックします。コード エディターにこのテンプレートが表示されます。  
  
4.  **[Analysis Services への接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]** をクリックします。 新しいクエリ エディター ウィンドウが開き、 **[スキーマ行セットの発見]** テンプレートの内容が表示されます。  
  
#### <a name="to-discover-column-names-from-the-mining-model-content-schema-rowset"></a>MINING MODEL CONTENT スキーマ行セットから列名を検出するには  
  
1.  **[スキーマ行セットの発見]** テンプレートを開き、 **[実行]** をクリックします。  
  
     **[結果]** ペインに返されるスキーマ行セットの一覧には、現在のインスタンスで入手できるすべての行セットの行セット名と行セット列が含まれます。  
  
2.  **クエリ**ウィンドウで、後にカーソルを置き **\<Restriction List >** し、enter キーを押して新しい行を追加します。  
  
3.  種類と空白行にカーソルを置き **\<SchemaName > DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName >**  
  
     制限のセクション全体は次のようになります。  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  **[実行]** をクリックします。  
  
     **[結果]** ペインに、指定したスキーマ行セットの列名の一覧が表示されます。  
  
#### <a name="to-create-a-content-query-using-the-mining-model-content-schema-rowset"></a>MINING MODEL CONTENT スキーマ行セットを使用してコンテンツ クエリを作成するには  
  
1.  **[スキーマ行セットの発見]** テンプレートで、"要求の種類" タグの内側のテキストを置き換えて、要求の種類を変更します。  
  
     次の行を置き換えます。  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     置き換えると、次のようになります。  
  
     **\<RequestType > DMSCHEMA_MINING_MODEL_CONTENT\</RequestType >**  
  
2.  制限リストに新しい条件を追加することで、名前でマイニング モデルを指定するように制限リストを変更します。  
  
3.  テンプレートで、`<Restriction List>` の後ろにカーソルを置き、Enter キーを押して新しい行を追加します。  
  
4.  空白行にカーソルを置き、「**<MODEL_NAME>My model name</MODEL_NAME>**」と入力します。  
  
     制限のセクション全体は次のようになります。  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  **[実行]** をクリックします。  
  
     [結果] ペインに、スキーマ定義および指定したモデルの値が表示されます。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)   
 [データ マイニング スキーマ行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets)  
  
  
