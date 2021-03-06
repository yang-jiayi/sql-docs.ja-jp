---
title: レポート履歴へのスナップショットの追加 (レポート マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report history [Reporting Services], adding snapshots
- historical data [Reporting Services]
- snapshots [Reporting Services], adding report snapshots
- adding snapshots to report history
- report snapshots [Reporting Services], adding
ms.assetid: 3aafb183-789e-46ac-966c-881dc549b31d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 859d4ae6557300582b866d6dcd6d0cd3ed124d2e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014983"
---
# <a name="add-a-snapshot-to-report-history-report-manager"></a>レポート履歴へのスナップショットの追加 (レポート マネージャー)
  レポート履歴とは、時間の経過と共に作成されるレポート スナップショットの集まりです。 レポート スナップショットは、特定の時点で取得されたレイアウト情報およびクエリ結果を含むレポートです。 レポートを選択したときに最新のクエリ結果を取得する要求時レポートとは異なり、レポート スナップショットはスケジュールに従って処理され、その後、レポート サーバーに保存されます。 表示するレポート スナップショットを選択すると、レポート サーバーによってレポート サーバー データベースに格納されたレポートが取得され、スナップショット作成時点のレポートで最新だったデータとレイアウトを表示します。  
  
 レポート スナップショットは、特定の表示形式では保存されません。 その代わりに、レポート スナップショットは、ユーザーまたはアプリケーションが要求したときのみ、最終的な表示形式 (HTML など) で表示されます。 遅延表示により、スナップショットの移植性が実現します。 レポートは、要求元のデバイスまたは Web ブラウザーの適切な形式で表示できます。  
  
### <a name="to-manually-add-snapshots-to-report-history"></a>レポート履歴にスナップショットを手動で追加するには  
  
1.  レポート マネージャーで、 **[コンテンツ]** ページに移動し、履歴を表示するアイテムの上にマウス ポインターを移動して、下矢印をクリックします。  
  
2.  ドロップダウン メニューの **[レポート履歴の表示]** をクリックします。  
  
3.  **[新しいスナップショット]** をクリックします。 **[実行時]** 列に新しいスナップショットが作成されます。  
  
    > [!NOTE]  
    >  レポート履歴にスナップショットを追加するには、管理者がレポート履歴の構成で **[履歴の手動作成を許可する]** に設定しておく必要があります。 詳細については、 [レポート履歴を制限する (レポート マネージャー)](../reports/limit-report-history-report-manager.md)をクリックします。  
  
4.  **[適用]** をクリックします。  
  
### <a name="to-automatically-add-all-snapshots-to-report-history"></a>レポート履歴にすべてのスナップショットを自動で追加するには  
  
1.  既にレポート実行スナップショットとして実行するように構成されたレポートでは、追加のプロパティを設定することで、スナップショットが更新されるたびにスナップショットのコピーをレポート履歴に保存できます。  
  
2.  レポート マネージャーで、 **[コンテンツ]** ページに移動し、履歴を表示するアイテムの上にマウス ポインターを移動して、下矢印をクリックします。  
  
3.  ドロップダウン メニューの **[管理]** をクリックします。  
  
4.  **[スナップショット オプション]** をクリックします。  
  
5.  **[すべてのレポート実行スナップショットを履歴に格納する]** チェック ボックスをオンにします。  
  
6.  **[適用]** をクリックします。  
  
### <a name="to-automatically-add-snapshots-to-report-history-based-on-a-schedule"></a>スケジュールを基にスナップショットを自動でレポート履歴に追加するには  
  
1.  レポート マネージャーで、 **[コンテンツ]** ページに移動し、履歴を表示するアイテムの上にマウス ポインターを移動して、下矢印をクリックします。  
  
2.  ドロップダウン メニューの **[管理]** をクリックします。  
  
3.  **[スナップショット オプション]** をクリックします。  
  
4.  **[次のスケジュールを使用して、スナップショットをレポート履歴に追加する]** チェック ボックスをオンにします。 次のいずれかを実行します。  
  
    -   **[レポート固有のスケジュール]** をクリックします。 スケジュールの詳細を入力し、スケジュールの開始日と終了日を選択して、 **[OK]** をクリックします。  
  
    -   **[共有スケジュール]** を選択します。 一覧から適切なスケジュールを選択します。  
  
5.  **[適用]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポートの実行プロパティを構成する (レポート マネージャー)](../reports/configure-execution-properties-for-a-report-report-manager.md)   
 [レポートを開閉する (レポート マネージャー)](../reports/open-and-close-a-report-report-manager.md)   
 [レポート履歴を制限する (レポート マネージャー)](../reports/limit-report-history-report-manager.md)   
 [[スケジュール]](../subscriptions/schedules.md)   
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)  
  
  
