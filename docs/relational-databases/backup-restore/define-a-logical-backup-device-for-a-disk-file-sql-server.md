---
title: ディスク ファイルの論理バックアップ デバイスの定義 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4766fc9d680bc90a6017424162aa72a50b516c43
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797420"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a>ディスク ファイルの論理バックアップ デバイスの定義 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でディスク ファイルの論理バックアップ デバイスを定義する方法について説明します。 論理バックアップ デバイスとは、特定の物理バックアップ デバイス (ディスク ファイルまたはテープ ドライブ) を示すユーザー定義名です。  物理デバイスは、後で、つまりバックアップがバックアップ デバイスに書き込まれたときに初期化されます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
     [Security](#Security)  
  
-   **ディスク ファイルの論理バックアップ デバイスを定義する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   論理デバイス名は、サーバー インスタンス上のすべての論理バックアップ デバイスで一意になる必要があります。 既存の論理デバイス名を表示するには、 [sys.backup_devices](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md) カタログ ビューに対してクエリを実行します。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   バックアップ ディスクには、データベースのデータ ディスクやログ ディスクとは別のディスクを使用することをお勧めします。 これは、データ ディスクやログ ディスクで障害が発生した場合に確実にバックアップにアクセスできるようにするために必要です。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 **diskadmin** 固定サーバー ロールのメンバーシップが必要です。  
  
 ディスクに対する書き込み権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a>ディスク ファイルの論理バックアップ デバイスを定義するには  
  
1.  オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[サーバー オブジェクト]** を展開し、 **[バックアップ デバイス]** を右クリックします。  
  
3.  **[新しいバックアップ デバイス]** をクリックします。 **[バックアップ デバイス]** ダイアログ ボックスが開きます。  
  
4.  デバイス名を入力します。  
  
5.  バックアップ先として、 **[ファイル]** をクリックし、ファイルの完全なパスを指定します。  
  
6.  新しいデバイスを定義するには、 **[OK]** をクリックします。  
  
 この新しいデバイスをバックアップするには、このデバイスを **[データベースのバックアップ]** ダイアログ ボックス (**[全般]** ページ) の **[バックアップ先]** フィールドに追加します。 詳細については、データベースの完全バックアップの作成 [データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)を使用してデータベースの差分バックアップを作成します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a>ディスク ファイルの論理バックアップを定義するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。 この例では、 [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md) を使用して、ディスク ファイルの論理バックアップ デバイスを定義します。 この例では、 `mydiskdump`という物理名を持つ、 `c:\dump\dump1.bak`というディスク バックアップ デバイスを追加します。  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [sys.backup_devices &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-backup-devices-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_dropdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdevice-transact-sql.md)   
 [テープ ドライブの論理バックアップ デバイスの定義 &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [論理バックアップ デバイスのプロパティと内容の表示 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
