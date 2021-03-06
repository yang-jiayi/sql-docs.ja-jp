---
title: MSSQLSERVER_1222 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7974805b2756ed1b160a254cfda94261a625824c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721890"
---
# <a name="mssqlserver1222"></a>MSSQLSERVER_1222
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1222|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LK_TIMEOUT|  
|メッセージ テキスト|ロック要求がタイムアウトしました。|  
  
## <a name="explanation"></a>説明  
必要なリソースが、このクエリが待機できる時間より長く別のトランザクションによって拘束されています。  
  
## <a name="user-action"></a>ユーザーの操作  
問題を軽減するには、次の操作を行います。  
  
1.  可能であれば、必要なリソースのロックを保持しているトランザクションを探します。 **sys.dm_os_waiting_tasks** および **sys.dm_tran_locks** 動的管理ビューを使用してください。  
  
2.  トランザクションがロックをまだ保持している場合は、必要に応じてこのトランザクションを中止します。  
  
3.  クエリを再実行します。  
  
このエラーが頻繁に発生する場合は、ロック要求のタイムアウト時間を変更するか、原因となっているトランザクションを修正してロックの拘束時間を短くします。  
  
