---
title: 既存のテーブルを使用してディメンションを作成 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ebf7fb99def766b3635743a31fa2cfa37fcbc228
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-dimension-by-using-an-existing-table"></a>既存のテーブルを使用したディメンションの作成
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でディメンション ウィザードを使用して、既存のテーブルからディメンションを作成できます。 この操作を行うには、ウィザードの **[作成方法の選択]** ページで **[既存のテーブルの使用]** を選択します。 このオプションを選択すると、ディメンション構造は、ディメンション テーブル、その列、および既存のデータ ソース ビュー内の列間のリレーションシップに基づいて作成されます。 ウィザードでは、ソース テーブルと関連テーブル内のデータが抽出されます。 その後、このデータを使用して、ディメンション テーブル内の列に基づいて属性列を定義したり、属性階層 ( *ユーザー定義* 階層) を定義したりします。 ディメンション ウィザードを使用してディメンションを作成した後、ディメンション デザイナーを使用して、ディメンションの属性と階層を追加、削除、および構成できます。  
  
 既存のテーブルを使用してディメンションを作成する場合、ディメンション ウィザードでは次の手順が示されます。  
  
-   基になる情報の指定  
  
-   関連テーブルの選択  
  
-   ディメンション属性の選択  
  
-   勘定科目インテリジェンスの定義  
  
> [!NOTE]  
>  このトピックで説明する情報に対応する手順については、「 [ディメンション ウィザードを使用したディメンションの作成](../../analysis-services/multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)」を参照してください。  
  
## <a name="specifying-the-source-information"></a>基になる情報の指定  
 基になる情報は、 **[基になる情報の指定]** ページで指定します。 このプロセスでは、まず、作成するディメンションの基になるテーブルを含むデータ ソース ビューを選択します。 次に、定義するディメンションのメイン ディメンション テーブルを指定します。 メイン ディメンション テーブルとは、ファクト テーブルに直接リンクされるテーブルです。 たとえば、Products ディメンションには Product テーブルをメイン テーブルとして指定し、Employees ディメンションには Employee テーブルを指定します。 ウィザードでは、データ ソース ビューの主キーに基づいたキー列が自動的に選択されます。 ただし、キー列は、必要に応じて変更できます。 キー列によってディメンションのメンバーが決まります。 たとえば、Product ディメンションのキー列として ProductKey を定義します。  
  
 必要に応じて、メンバー名を含む列を定義できます。 既定では、ユーザーに表示されるメンバー名がキー列の値です。 多くの場合、ProductID や EmployeeID などのキー列の値は、ユーザーにとって意味のない、システムで生成される一意のキーです。 多くの場合、ユーザーに表示される名前を、ディメンションの他の列の対応する値に変更すると、ユーザーに意味のある情報を提供できます。 たとえば、製品名や従業員名を含むメンバー名列を定義できます。 メンバー名を変更すると、わかりやすい名前が表示されますが、クエリでは、同じ名前を共有するメンバーを正しく区別するために、引き続きキー列の値が使用されます。 キー列に複合キーを指定する場合は、キー属性のメンバーの値を提供する列も指定する必要があります。 属性のプロパティを構成する方法の詳細については、「 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)」を参照してください。  
  
## <a name="selecting-related-tables"></a>関連テーブルの選択  
  
> [!NOTE]  
>  メイン ディメンション テーブルに他のディメンション テーブルとのリレーションシップがデータ ソース ビューで定義されていない場合は、ウィザードでこの手順が省略されます。  
  
 スノーフレーク ディメンションを構築している場合は、 **[関連テーブルの選択]** ページで追加属性の定義に使用する関連テーブルを指定します。 たとえば、顧客の地理テーブルを作成する Customer ディメンションを構築しているとします。 この場合、地理テーブルを関連テーブルとして定義します。  
  
## <a name="selecting-dimension-attributes"></a>ディメンション属性の選択  
 ディメンション テーブルを選択したら、 **[ディメンション属性の選択]** ページを使用して、ディメンションに含める属性をこれらのテーブルから選択します。 これらすべてのテーブルの基になるすべての列は、ディメンションの属性として使用できる可能性があります。 ディメンション キー属性を選択して、参照を有効にする必要があります。  
  
 既定では、ウィザードによって属性の型が **標準**に設定されます。 ただし、特定の属性を、データをより適切に表す別の属性型にマップする場合があります。 たとえば、 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] DW サンプル データベースの dbo.DimAccount テーブルには、勘定科目番号を示す AccountCodeAlternateKey 列があります。 この属性の型を **標準** に設定するのではなく、この属性を **アカウント番号** 型にマップする場合があります。  
  
> [!NOTE]  
>  ディメンションの作成時にディメンションの種類と標準的な属性の型が設定されていない場合は、ディメンションの作成後に、ビジネス インテリジェンス ウィザードを使用して、これらの値を設定します。 詳しくは、「 [ディメンションへのディメンション インテリジェンスの追加](../../analysis-services/multidimensional-models/bi-wizard-add-dimension-intelligence-to-a-dimension.md) 」または (種類が勘定科目ディメンションの場合は)「 [ディメンションへの勘定科目インテリジェンスの追加](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md)」をご覧ください。  
  
 ウィザードでは、指定されている属性の型に基づいて、ディメンションの種類が自動的に設定されます。 ウィザードで指定された属性の型によって、属性の **Type** プロパティが設定されます。 ディメンションとその属性の **Type** プロパティの設定により、ディメンションのコンテンツに関する情報が、サーバーおよびクライアント アプリケーションに提供されます。 場合によっては、このような **Type** プロパティの設定は、クライアント アプリケーションに情報を提供するだけなので、省略できます。 また、Accounts ディメンション、Time ディメンション、または Currency ディメンションでは、これらの **Type** プロパティの設定によって、サーバーベースの具体的な動作が決まるため、特定のキューブの動作を実装する際に、この設定が必要になる場合もあります。  
  
 ディメンションの種類と属性の型の詳細については、「 [ディメンションの種類](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)」および「 [属性の種類の構成](../../analysis-services/multidimensional-models/attribute-properties-configure-attribute-types.md)」を参照してください。  
  
## <a name="defining-account-intelligence"></a>勘定科目インテリジェンスの定義  
  
> [!NOTE]  
>  ディメンション ウィザードでは、ウィザードの **[ディメンション属性の選択]** ページで **[勘定科目の種類]** ディメンション属性を定義した場合のみ、この手順が表示されます。  
  
 **[勘定科目インテリジェンスの定義]** ページを使用して、勘定科目の種類のディメンションを作成します。 勘定科目の種類のディメンションを作成する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でサポートしている標準的な勘定科目の種類を、ディメンションの勘定科目の種類の属性のメンバーにマップする必要があります。 サーバーではこれらのマッピングを使用して、勘定科目データの種類ごとに個別の集計関数と別名を指定します。  
  
 ウィザードでは、このような勘定科目の種類をマップするために、次の列を含むテーブルが用意されています。  
  
-   **[基になるテーブルの勘定科目の種類]** 列。データ ソース テーブルの勘定科目の種類が表示されます。  
  
-   **[ビルトイン勘定科目の種類]** 列。サーバーがサポートしている対応する標準的な勘定科目の種類が表示されます。 ソース データで標準的な名前を使用すると、ウィザードによって、自動的に、ソースの種類がサーバーの種類にマップされ、この情報が **[ビルトイン勘定科目の種類]** 列に表示されます。 サーバーで勘定科目の種類をマップしない場合またはマッピングを変更する場合は、 **[ビルトイン勘定科目の種類]** 列の一覧から異なる種類を選択します。  
  
> [!NOTE]  
>  ウィザードで Accounts ディメンションを作成する際に、勘定科目の種類がマップされていない場合は、ディメンションの作成後、ビジネス インテリジェンス ウィザードを使用して、これらのマッピングを構成します。 詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](../../analysis-services/multidimensional-models/bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。  
  
## <a name="completing-the-wizard"></a>ウィザードの完了  
 ウィザードで、ディメンション テーブルがスキャンされ、リレーションシップが検出されます。 ウィザードによって、スノーフレーク ディメンションのキー属性間の属性リレーションシップが自動的に作成されます。  
  
 また、親子リレーションシップがディメンションに存在するかどうかも自動的に検出されます。 親属性がディメンションのキー属性のメンバーを参照するときには、親子リレーションシップが存在します。 このリレーションシップでは、ディメンションのリーフ メンバー間の階層リレーションシップおよび集計パスが定義されます。 親子階層の詳細については、「 [親子階層の属性](../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。  
  
 **[ウィザードの完了]** ページで、新しいディメンションの名前を入力し、ディメンション構造を確認して、ウィザードを完了します。  
  
## <a name="see-also"></a>参照  
 [データ ソースのない時間テーブルを生成することによって、ディメンションを作成します。](../../analysis-services/multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)   
 [時間テーブルを生成することによって時間ディメンションを作成します。](../../analysis-services/multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)   
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)   
 [時間テーブルを生成することによって時間ディメンションを作成します。](../../analysis-services/multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md)   
 [データ ソースのない時間テーブルを生成することによって、ディメンションを作成します。](../../analysis-services/multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)  
  
  