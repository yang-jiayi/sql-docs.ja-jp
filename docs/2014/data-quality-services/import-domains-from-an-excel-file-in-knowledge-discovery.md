---
title: ナレッジ検出でドメインを Excel ファイルからインポートする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4d3a3940-6c2a-4dc4-90eb-86f26012c165
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 4f2e680829f51664fc13116953298a281aae7679
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56035393"
---
# <a name="import-domains-from-an-excel-file-in-knowledge-discovery"></a>ナレッジ検出でドメインを Excel ファイルからインポートする
  このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ナレッジ検出アクティビティで Excel ファイルから 1 つまたは複数のドメインをインポートする方法について説明します。 インポート処理は、ナレッジの生成処理を簡略化し、時間と労力を節約します。 インポートにより、Excel ファイルまたはテキスト ファイルでデータを所有しているユーザーは、そのデータを使用してナレッジ ベースを作成できます。 (既存のナレッジ ベースのドメインへの値のインポートについて詳しくは、「[値を Excel ファイルからドメインへインポートする](../../2014/data-quality-services/import-values-from-an-excel-file-into-a-domain.md)」をご覧ください。)Excel ファイルへのエクスポートはサポートされていません。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
 Excel ファイルからドメインをインポートするには、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] がインストールされているコンピューターに Excel がインストールされていること、ドメイン値を含む Excel ファイルが作成されていること (「 [How the import works](#How)」を参照)、およびドメインをインポートするナレッジ ベースが作成されていて開いていることが必要です。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 Excel ファイルからドメインをインポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールを所有している必要があります。  
  
##  <a name="Import"></a> ドメインを Excel ファイルからナレッジ ベースへインポートする  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]「[Data Quality Client アプリケーションの実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)」をご覧ください。  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、次のいずれかの操作を行います。  
  
    -   インポート先の新しいナレッジ ベースを作成します。これを行うには、 **[新しいナレッジ ベース]** をクリックしてナレッジ ベースの名前を入力し、 **[次の場所からナレッジ ベースを作成]** で **[なし]** を選択します。次に、 **[ナレッジ検出]** アクティビティを選択して、 **[作成]** をクリックします。  
  
    -   既存のナレッジ ベースを開きます。これを行うには、 **[ナレッジ ベースを開く]** をクリックしてナレッジ ベースを選択し、 **[ナレッジ検出]** を選択して **[次へ]** をクリックします。  
  
3.  **[マップ]** ページの **[データ ソース]** で **[Excel ファイル]** を選択します。  
  
4.  **[Excel ファイル]** 行の **[参照]** をクリックします。  
  
5.  **[Excel ファイルの選択]** ダイアログ ボックスで、インポート元の Excel ファイルが格納されているフォルダーに移動し、Excel ファイルを選択して **[開く]** をクリックします。  
  
6.  **[ワークシート]** ボックスの一覧で、インポート元の Excel ファイルのワークシートを選択します。  
  
7.  先頭の行をデータ見出しと見なし、先頭の行の値を列名として使用する場合は、 **[先頭の行を見出しとして使用]** をオンにします。 先頭の行をデータ値と見なす場合は、 **[先頭の行を見出しとして使用]** をオフにします。この場合、DQS は Excel の見出し名 (英文字) を列に使用します。  
  
8.  列を選択し、既存のドメインを列にマップするか、新しいドメインを作成して列にマップします。新しいドメインを作成するには、 **[ドメインの作成]** アイコンをクリックし、 **[ドメインの作成]** ダイアログ ボックスでドメインを作成します。 ドメインのデータ型は列のデータ型と一致する必要があります。 スプレッドシートのすべての列について、この手順を繰り返します。  
  
9. **[次へ]** をクリックします。  
  
10. **[検出]** ページで、 **[開始]** をクリックして Excel スプレッドシート内のデータを分析します。  
  
    > [!NOTE]  
    >  データのアップロードが完了する前にページを閉じた場合は、ファイルのアップロード処理が終了します。  
  
11. 分析が正常に完了したことを確認して、 **[次へ]** をクリックします。  
  
12. **[ドメイン値の管理]** ページで、 **[ドメイン]** ボックスの一覧に正しいドメインが表示されていること、およびドメイン テーブルに値が入力されていることを確認します。  
  
13. **[完了]** をクリックします。次に、ナレッジ ベースを発行する場合は **[発行]** をクリックし、発行しない場合は **[いいえ]** をクリックします。  
  
14. ナレッジ ベースが発行されたことを確認し、 **[OK]** をクリックします。  
  
##  <a name="FollowUp"></a>補足情報: Excel ファイルからドメインをインポートした後  
 Excel ファイルからドメインをインポートした後で、ドメインのコンテンツに応じてナレッジをドメインに追加したり、ドメインをクレンジング プロジェクトや照合プロジェクトで使用したりすることができます。 詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、「[複合ドメインの管理](../../2014/data-quality-services/managing-a-composite-domain.md)」、「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」、「[データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」、または「[データ照合](../../2014/data-quality-services/data-matching.md)」をご覧ください。  
  
##  <a name="How"></a> インポートのしくみ  
 インポート操作では、DQS は Excel ファイルを次のように解釈します。  
  
-   列はドメインを表す  
  
-   行はデータ レコードを表す  
  
-   先頭の行は、 **[先頭の行を見出しとして使用]** チェック ボックスの設定に応じて、ドメインを表すか、最初のデータ値またはレコードになる  
  
 インポート操作には、次のルールが適用されます。  
  
-   この操作では、ドメイン値がナレッジ ベースにインポートされます。 ドメイン ルールまたは照合ポリシーはインポートされません。  
  
-   Excel ファイルの拡張子は、.xlsx、.xls、または .csv です。 ドメイン値または完全なドメインをインポートするには、Microsoft Excel が [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] コンピューターにインストールされている必要があります。 Excel Version 2003 以降がサポートされます。 64 ビット バージョンの Excel を使用する場合は、Excel 2003 ファイルのみがサポートされます。Excel 2007 または 2010 ファイルはサポートされません。  
  
-   64 ビットの Excel では、Excel ファイル タイプ .xlsx はサポートされません。 64 ビットの Excel を使用している場合は、スプレッドシート ファイルを .xls ファイルとして保存してください。  
  
-   .xlsx および .xls ファイルでは、列のデータ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。 セルがそのデータ型に従っていない場合、セルの値は null になります。  
  
-   .csv ファイルでは、データ型は最初の 8 行で最も多く使用されているデータ型によって決定されます。  
  
-   ドメイン ルールに従っていない Excel スプレッドシートの値は無効な値としてインポートされます。  
  
-   Excel ファイルの形式が正しくないか、Excel ファイルが破損している場合は、インポート操作でエラーが発生します。  
  
  
