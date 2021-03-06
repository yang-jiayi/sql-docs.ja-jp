---
title: テスト データのモデルへのフィルターの適用 |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d9254d42d61fdf6bf087d83d0ced4ff1761dd077
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539950"
---
# <a name="apply-filters-to-model-testing-data"></a>モデルのテスト データへのフィルターの適用
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  モデルのテストに使用する外部データ ソースを指定する場合に、入力データを制限するフィルターを必要に応じて適用できます。 たとえば、特定の所得範囲の顧客に関する予測についてのみモデルをテストできます。  
  
 たとえば、Adventure Works の絞り込みメール配信シナリオでは、テスト データを含み、所得範囲によってテスト ケースを制限する ProspectiveBuyer テーブルに対して、次のようなフィルター式を作成できます。  
  
 `[YearlyIncome] = '50000'`  
  
 フィルターの動作は、モデル トレーニング データとテスト データ セットのどちらをフィルター選択するかによって若干異なります。  
  
-   テスト データ セットに対するフィルターを定義する場合は、入力されるデータに対する WHERE 句を作成します。 モデルの評価に使用する入力データ セットに対するフィルター処理では、グラフの作成時にフィルター式が Transact-SQL ステートメントに変換され、入力テーブルに適用されます。 その結果として、テスト ケースの数を大幅に少なくすることができます。  
  
-   マイニング モデルに対してフィルターを適用する場合、作成したフィルター式はデータ マイニング拡張機能 (DMX) ステートメントに変換された後、個々のモデルに適用されます。 したがって、フィルターをモデルに適用すると、モデルをトレーニングするのに元のデータのサブセットのみが使用されます。 このオプションは、モデルが特定のデータ セットに対して調整されるようにトレーニング モデルを 1 つの条件セットでフィルター選択して、さらに別の条件セットでモデルをテストする場合に問題を引き起こすことがあります。  
  
-   構造を作成するときにテスト データ セットを定義した場合、トレーニングに使用されるモデル ケースには、マイニング構造のトレーニング セット内にあり、 **かつ** フィルターの条件を満たすケースのみが含まれます。 このため、モデルをテストするときに **[マイニング モデルのテスト ケースを使用する]** オプションを選択した場合、テスト用ケースには、マイニング構造のテスト セット内にあり、かつフィルターの条件を満たすケースのみが含まれます。 ただし、予約データセットを定義しなかった場合、テスト用のモデル ケースには、フィルター条件を満たすデータ セット内のすべてのケースが含まれます。  
  
-   モデルに適用するフィルター条件は、モデル ケースに対するドリルスルー クエリにも影響します。  
  
 要するに、複数のモデルをテストする場合は、すべてのモデルが同じマイニング構造に基づく場合でも、モデルがトレーニングとテストにデータの異なるサブセットを使用する可能性があることに注意する必要があります。 これは、精度チャートに対して次の影響を与えることがあります。  
  
-   テスト セット内のケースの総数が、テストされるモデル間で異なる場合があります。  
  
-   モデルでトレーニング データまたはテスト データの異なるサブセットが使用される場合、チャート内で各モデルの割合が揃わないことがあります。  
  
 結果に影響する可能性のある定義済みのフィルターがモデルに含まれるかどうかを確認するには、 **[プロパティ]** ペインで **Filter** プロパティを探すか、データ マイニング スキーマ行セットを使用してモデルをクエリします。 たとえば、次のクエリは指定したモデルのフィルター テキストを返します。  
  
 `SELECT [FILTER] FROM $system.DMSCHEMA_MINING_MODELS WHERE MODEL_NAME = 'name of model'`  
  
> [!WARNING]  
>  既存のマイニング モデルからフィルターを削除する場合や、フィルター条件を変更する場合は、マイニング モデルを再処理する必要があります。  
  
 適用できるフィルターの種類の詳細や、フィルター式がどのように評価されるかについては、「[モデル フィルターの構文と例 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)」を参照してください。  
  
### <a name="create-a-filter-on-external-testing-data"></a>外部テスト データに対するフィルターの作成  
  
1.  テストするモデルを含むマイニング構造をダブルクリックして、データ マイニング デザイナーを開きます。  
  
2.  **[マイニング精度チャート]** タブを選択し、次に **[入力の選択]** タブを選択します。  
  
3.  **[入力の選択]** タブの **[精度チャートに使用するデータセットの選択]** で、 **[別のデータセットを指定する]** を選択します。  
  
4.  [参照] ボタンをクリックします **([...])。** をダイアログ ボックスを開き、外部データ セットを選択します。  
  
5.  ケース テーブルを選択し、入れ子になったテーブルを必要に応じて追加します。 必要に応じてモデルの列を外部データ セットの列にマップします。 **[列マッピングの指定]** ダイアログ ボックスを閉じてソース テーブルの定義を保存します。  
  
6.  データセットのフィルターを定義するには、 **[フィルター エディターを開く]** をクリックします。  
  
     **[データセット フィルター]** ダイアログ ボックスが開きます。 入れ子になったテーブルが構造に含まれている場合は、2 つの部分から成るフィルターを作成できます。 まず、ケース テーブルの条件を **[データセット フィルター]** ダイアログ ボックスで設定し、次に、入れ子になった行の条件を **[フィルター]** ダイアログ ボックスで設定します。  
  
7.  **[データセット フィルター]** ダイアログ ボックスで、 **[マイニング構造列]** の下のグリッドの先頭行をクリックし、一覧からテーブルまたは列を選択します。  
  
     データ ソース ビューに複数のテーブルが含まれているか、入れ子になったテーブルが含まれている場合は、テーブル名を先に選択する必要があります。 それ以外の場合は、ケース テーブルから列を直接選択できます。  
  
     フィルター選択する各列に新しい行を追加します。  
  
8.  **[演算子]** 列と **[値]** 列を使用して、列をフィルター選択する方法を定義します。  
  
     **注** 値は、引用符を使用せずに入力してください。  
  
9. **[ルールの適用条件]** ボックスをクリックして論理演算子を選択し、複数の条件を結合する方法を定義します。  
  
10. 必要に応じて、参照 ボタンをクリックして **(...)** の右側にある、**値**テキスト ボックスを開く、**フィルター**  ダイアログ ボックスし、入れ子になったテーブルまたは個々 のケース テーブル列の条件を設定します。  
  
11. **[式]** ペインに表示されるテキストで、完成したフィルター条件が適切であることを確認します。  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     フィルター条件は、精度チャートの作成時にデータ ソースに適用されます。  
  
## <a name="see-also"></a>参照  
 [モデルのテスト データの選択およびマップ](../../analysis-services/data-mining/choose-and-map-model-testing-data.md)   
 [入れ子になったテーブルのデータを精度チャートの入力として使用する方法](../../analysis-services/data-mining/using-nested-table-data-as-an-input-for-an-accuracy-chart.md)   
 [精度チャートの種類の選択とグラフのオプションの設定](../../analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
