---
title: '[サブスクリプション] ページ (レポート マネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: cf3a6bd0-e0b2-4875-a532-63ef34cfa860
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 8ae3948d019467590b885c706e6b2c8d1c186da2
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031543"
---
# <a name="subscriptions-page-report-manager"></a>[サブスクリプション] ページ (レポート マネージャー)
  [サブスクリプション] ページは、現在のレポートまたは共有データ ソースのサブスクリプションをすべて表示するために使用します。 [すべてのサブスクリプションを管理] での指定により十分な権限を持っている場合、すべてのユーザーのサブスクリプションを表示できます。 それ以外の場合、このページには自分のサブスクリプションのみが表示されます。  
  
> [!NOTE]  
>  その他のページにもサブスクリプション情報は含まれています。 詳細については、次を参照してください[個人用サブスクリプション ページ&#40;レポート マネージャー&#41; ](../../2014/reporting-services/my-subscriptions-page-report-manager.md) 1 か所ですべてのサブスクリプションにアクセスする、または[新しいサブスクリプションまたはサブスクリプションの編集 ページ&#40;レポート マネージャー&#41; 。](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md)サブスクリプションを作成または編集します。  
  
 一部のオプションは、既存のサブスクリプションを操作しているときにのみ表示されます。 サブスクリプションが定義されていない場合に、レポートからこのページを表示すると、 **[新しいサブスクリプション]** および **[新しいデータ ドリブン サブスクリプション]** 以外のオプションはこのページに表示されません。  
  
 新しいサブスクリプションを作成するには、保存されている資格情報がレポートのデータ ソースで使用されていることを確認する必要があります。 資格情報を保存するには [データ ソース] プロパティ ページを使用します。 詳細については、次を参照してください。[データ ソース プロパティ ページ&#40;レポート マネージャー&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md)します。  
  
> [!NOTE]  
>  この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。 エディションでサポートされている機能の一覧については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を参照してください[機能は、SQL Server 2014 の各エディションでサポートされている](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)します。  
  
## <a name="navigation"></a>ナビゲーション  
 ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。  
  
### <a name="to-open-the-subscriptions-page-for-report"></a>レポートの [サブスクリプション] ページを開くには  
  
1.  レポート マネージャーを開き、サブスクリプションを表示または構成するレポートを探します。  
  
2.  レポートの上にマウス ポインターを移動し、下矢印をクリックします。  
  
3.  ドロップダウン メニューの **[管理]** をクリックします。 この操作により、レポートの [全般] プロパティ ページが開きます。  
  
4.  **[サブスクリプション]** タブをクリックします。  
  
## <a name="options"></a>および  
 **削除**  
 サブスクリプションを削除する場合にクリックします。 削除する各サブスクリプションの隣のチェック ボックスをオンにしてから、サブスクリプションを削除することができます。  
  
 **新しいサブスクリプション**  
 現在のレポートの新しいサブスクリプションを作成する場合にクリックします。 保存されている資格情報がレポートで使用される場合または資格情報が使用されない場合に、このボタンは有効になります。 共有データ ソースの [サブスクリプション] ページを開いた場合、このボタンは無効になります。  
  
 **新しいデータ ドリブン サブスクリプション**  
 情報を含むデータ ストアに対するコマンドやクエリから、サブスクライバーの一覧と配信オプションを生成する場合にクリックします。 保存されている資格情報がレポートで使用される場合または資格情報が使用されない場合に、このボタンは有効になります。 共有データ ソースの [サブスクリプション] ページを開いた場合、このボタンは無効になります。  
  
 **[編集]**  
 説明を表示または編集する場合にクリックします。  
  
 **レポート**  
 共有データ ソースからこのページを開くと、この列でサブスクリプションが定義されているレポートが識別されます。 **[フォルダー]** 列ではレポートの場所が識別されます。  
  
 **[説明]**  
 サブスクリプションの説明が表示されます。  
  
 **トリガー**  
 サブスクリプションが実行される条件を表します。 **TimedSubscription** トリガーは、サブスクリプションを実行する日時を定義したスケジュールに基づいています。 **SnapshotUpdated** トリガーは、レポート スナップショットの更新に基づいています。  
  
 **[所有者]**  
 サブスクリプションを作成したユーザーの名前が表示されます。  
  
 **[最終実行]**  
 サブスクリプションを処理した最終日時が表示されます。  
  
 **ステータス**  
 サブスクリプションの状態が表示されます。 通常、状態値は "新規" またはサブスクリプションが最後に実行された日時のいずれかとなります。  
  
 "無効なデータ" の状態値は、既に無効となった暗号化された値 (つまり、レポートの実行に使用される保存された資格情報) へのポインターがサブスクリプションに含まれている場合に発生します。 データの暗号化および暗号化の解除に使用される対称キーがレポート サーバー上で再作成されると、既存の暗号化された値は使用できなくなります。  
  
 サブスクリプションが非アクティブ化されている場合、そのサブスクリプションは処理できません。 サブスクリプションを更新し、操作可能な状態にするには、サブスクリプションを開いてから保存します。  
  
## <a name="see-also"></a>参照  
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [作成、変更、および標準のサブスクリプションを削除&#40;Reporting Services のネイティブ モード&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)   
 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)   
 [レポート マネージャー F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
