---
title: "手順 1: レッスン 1 パッケージのコピー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 7f1616c2-2b4e-4010-be50-27d7b897403a
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b3b601049b8904d439136a1fdc9af7cd84a86b5b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-2-1---copying-the-lesson-1-package"></a>レッスン 2-1-レッスン 1 パッケージのコピー
ここでは、レッスン 1 で作成した Lesson 1.dtsx パッケージのコピーを作成します。 レッスン 1 を終了していない場合は、チュートリアルに含まれている、レッスン 1 を完了した状態のパッケージをプロジェクトに追加した後、コピーすることもできます。 レッスン 2 の実習では、このパッケージの新しいコピーを使用します。  
  
### <a name="to-create-the-lesson-2-package"></a>レッスン 2 のパッケージを作成するには  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools がまだ開いていない場合は、 **[スタート]**ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server 2012]**の順にポイントして、 **[SQL Server Data Tools]**をクリックします。  
  
2.  **[ファイル]** メニューの **[開く]**をクリックし、 **[プロジェクト/ソリューション]**をクリックします。次に、 **SSIS Tutorial** フォルダーをクリックして **[開く]**をクリックし、 **SSIS Tutorial.sln**をダブルクリックします。  
  
3.  ソリューション エクスプローラーで、 **Lesson 1.dtsx**を右クリックし、 **[コピー]**をクリックします。  
  
4.  ソリューション エクスプローラーで **[SSIS パッケージ]**を右クリックし、 **[貼り付け]**をクリックします。  
  
    既定では、コピーしたパッケージの名前は Lesson 2.dtsx になります。  
  
5.  ソリューション エクスプローラーで **Lesson 2.dtsx** をダブルクリックし、パッケージを開きます。  
  
6.  **[制御フロー]** デザイン画面の背景上で任意の場所を右クリックし、 **[プロパティ]**をクリックします。  
  
7.  [プロパティ] ウィンドウで、 **[Name]** プロパティを「 **Lesson 2**」に変更します。  
  
8.  **ID** プロパティのボックスをクリックし、ドロップダウン矢印をクリックし、 **<Generate New ID>**をクリックします。  
  
### <a name="to-add-the-completed-lesson-1-package"></a>レッスン 1 を完了した状態のパッケージを追加するには  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools を開き、SSIS Tutorial プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで **[SSIS パッケージ]**を右クリックし、 **[既存のパッケージを追加]**をクリックします。  
  
3.  **[既存のパッケージのコピーを追加]** ダイアログ ボックスの **[パッケージの場所]**で、 **[ファイル システム]**をクリックします。  
  
4.  参照ボタン ( **[...]** ) をクリックし、コンピューター上の **Lesson 1.dtsx** に移動して、 **[開く]**をクリックします。  
  
    このチュートリアルのレッスン パッケージをすべてダウンロードするには、次の手順を実行します。  
  
    1.  「 [Integration Services 製品サンプル](http://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。  
  
    2.  [ **ダウンロード** ] タブをクリックします。  
  
    3.  SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。  
  
5.  前の手順の手順 3 ～ 8 の説明に従って、レッスン 3 のパッケージをコピーして貼り付けます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 2: Foreach ループ コンテナーの追加と構成](../integration-services/lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
