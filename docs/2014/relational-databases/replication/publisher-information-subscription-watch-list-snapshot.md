---
title: パブリッシャー情報、[サブスクリプション ウォッチ リスト] (スナップショット パブリケーション、SQL Server 2005 以降) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publisherinfo.subscriptionssummary.snapshot.f1
ms.assetid: 2ebeee62-7f54-4c77-9d37-15708bc5cc23
caps.latest.revision: 31
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2587fd42df38098f1fa68ed477d3c47c065229bb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37307432"
---
# <a name="publisher-information-subscription-watch-list-snapshot-publication-sql-server-2005-and-later"></a>パブリッシャー情報、[サブスクリプション ウォッチ リスト] (スナップショット パブリケーション、SQL Server 2005 以降)
  **以降を実行しているディストリビューターでは、** [サブスクリプション ウォッチ リスト] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] タブを使用できます。このタブは、選択されているパブリッシャーで使用できるすべてのパブリケーションのサブスクリプションについて情報を表示するために用意されています。 サブスクリプションの一覧にフィルターをかけて、エラー、警告、および動作に問題があるサブスクリプションを確認できます。 このタブは、パブリッシャーにおけるすべてのレプリケーション動作を管理者が一元的に監視できる場所です。レプリケーション モニターは、選択されているレプリケーションの種類と **[表示]** ボックスで選択されたオプションに基づいて、注意が必要なすべてのサブスクリプションを表示します。 このタブに表示されるアイテムは現在の状態およびパフォーマンスに基づいているので、現時点での **[表示]** ボックスのオプションに一致する場合にのみ、このページにサブスクリプションが表示されます。  
  
## <a name="options"></a>および  
 サブスクリプションに関する詳細情報やタスクを調べるには、そのサブスクリプションの行を右クリックし、ショートカット メニューのオプションをクリックします。 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。  
  
-   **[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。  
  
-   **[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。  
  
-   **[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 **[スナップショット サブスクリプションの表示]**  
 選択したパブリッシャーに対して表示するサブスクリプションの種類 (トランザクション、スナップショット、またはマージ) を選択します。  
  
 **[表示]**  
 サブスクリプション状態を選択すると、選択した種類の状態のサブスクリプションが表示されます。 たとえば、エラーを含むサブスクリプションのみを表示するように設定できます。  
  
 **ステータス**  
 各サブスクリプションの状態です。スナップショット エージェントまたはディストリビューション エージェントの状態 (より高い優先度の状態が表示されます) によって決定されます。  
  
 既定では、サブスクリプション情報を表示するグリッドは **[状態]** 列の順序で並べられています。 表示される状態の値と、その値の並べ替え順 (たとえば、エラーは常にグリッドの上部に表示されます) を次に示します。  
  
-   [エラー]  
  
-   まもなく期限切れ/期限切れ  
  
-   [初期化されていないサブスクリプション]  
  
-   [失敗したコマンドの再試行]  
  
-   [同期中]  
  
-   [同期されていません]  
  
 特定のサブスクリプションが複数の状態である場合に表示される値も、並べ替え順によって決まります。 たとえば、サブスクリプションにエラーがあり、まもなく期限切れになる場合、 **[状態]** 列には **[エラー]** と表示されます。  
  
 状態値 **[まもなく期限切れ/期限切れ]** および **[初期化されていないサブスクリプション]** は警告です。 警告が表示される場合、 **[状態]** 列にはエージェントが実行中かどうかも表示されます。 たとえば、 **[実行中]、[まもなく期限切れ/期限切れ]** という形式で状態が表示されます。  
  
 状態値 **[まもなく期限切れ/期限切れ]** は、しきい値が設定されている場合のみ表示されます。 しきい値の設定方法の詳細については、「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。  
  
 **サブスクリプション**  
 各サブスクリプションの名前です。 *SubscriberName: SubscriptionDatabaseName*という形式になります。  
  
 **パブリケーション**  
 サブスクリプションと同期するパブリケーションの名前です。 *PublicationDatabaseName: PublicationName*という形式になります。  
  
 **[最後の同期]**  
 ディストリビューション エージェントが最後に実行された時刻です。 同期が進行中の場合は、 **[実行中]** と表示されます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](monitor/start-the-replication-monitor.md)   
 [パブリッシャーの情報を表示し、タスクを実行する &#40;レプリケーション モニター&#41;](monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [レプリケーションの監視](monitoring-replication.md)  
  
  