---
title: 既定のテーブル名を変更する |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 40d580a79371cfb73dd38bc92a0dd69c50df1cd6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34015670"
---
# <a name="lesson-1-4---modifying-default-table-names"></a>レッスン 1 ~ 4 - 既定のテーブル名の変更
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

データ ソース ビューのオブジェクトの **FriendlyName** プロパティ値を変更することで、オブジェクトをわかりやすく、また使いやすくすることができます。  
  
この実習では、データ ソース ビューの各テーブルの表示名から "**Dim**" プレフィックスと "**Fact**" プレフィックスを削除して、わかりやすい名前にします。 これにより、次のレッスンで定義するキューブ オブジェクトとディメンション オブジェクトがわかりやすく (使いやすく) なります。  
  
> [!NOTE]  
> より簡単に使用できるようにするため、列の表示名を変更して、計算列を定義し、データ ソース ビューのテーブルやビューを結合します。  
  
### <a name="to-modify-the-default-name-of-a-table"></a>テーブルの既定の名前を変更するには  
  
1.  **データ ソース ビュー デザイナー** の **[テーブル]** ペインで **FactInternetSales** テーブルを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  Microsoft Visual Studio ウィンドウの右側の [プロパティ] ウィンドウが表示されていない場合は、[プロパティ] ウィンドウのタイトル バーにある **[自動的に隠す]** ボタンをクリックして、[プロパティ] ウィンドウが常に開いたままになるようにします。  
  
    データ ソース ビューの各テーブルのプロパティを変更するときは、[プロパティ] ウィンドウを開いたままにしておくと便利です。 **[自動的に隠す]** ボタンをクリックしてウィンドウを開いたまま固定しておかないと、 **ダイアグラム** ペイン内の別のオブジェクトをクリックしたときに [プロパティ] ウィンドウが閉じてしまいます。  
  
3.  **FactInternetSales** オブジェクトの **FriendlyName** プロパティをクリックして、「 ***InternetSales***」と入力します。  
  
    **FriendlyName** 以外のセルをクリックすると、変更が適用されます。 次のレッスンでは、このファクト テーブルを基にしてメジャー グループを定義します。 このレッスンで表示名を変更したので、次に作成するファクト テーブルの名前も FactInternetSales ではなく InternetSales になります。  
  
4.  **[テーブル]** ペインで **[DimProduct]** をクリックします。 [プロパティ] ウィンドウで、 **FriendlyName** プロパティを ***Product***に変更します。  
  
5.  データ ソース ビューの他のテーブルについても、同じ方法で **FriendlyName** プロパティを変更します。つまり、**Dim**プレフィックスを削除します。  
  
6.  操作が完了したら、 **[自動的に隠す]** ボタンをクリックして、[プロパティ] ウィンドウを再び非表示にします。  
  
7.  **[ファイル]** メニューまたは [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のツール バーで、 **[すべてを保存]** をクリックして、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトに対するこの時点までの変更を保存します。 ここでチュートリアルを終了しても、後でこの続きから再開できます。  
  
## <a name="next-lesson"></a>次のレッスン  
[レッスン 2: 定義して、キューブの展開](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>参照  
[多次元モデル内のデータ ソース ビュー](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
[データ ソース ビューのプロパティの変更 &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
  
