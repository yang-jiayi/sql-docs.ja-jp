---
title: '[サブスクリプションの検証オプション] (トランザクション サブスクリプション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 10d1920a4205bb1ec258c0b81303b2b61a50cb1f
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54123632"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>[サブスクリプションの検証オプション]\(トランザクション サブスクリプション)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **[サブスクリプションの検証オプション]** ダイアログ ボックスを使用すると、検証に行数のみを使用するか、行数とバイナリ チェックサムを使用するかを指定できます。  
  
## <a name="options"></a>オプション  
 **[サブスクライバーとパブリッシャーでレプリケートされたデータの行数が同じであることを確認します。]**  
 実行する行数の検証の種類を選択します。 Oracle パブリケーションの場合、使用できるオプションは **[テーブルに直接クエリすることにより、実際の行数を計算する]** のみとなります。  
  
 **[行データを比較するためにチェックサムを比較する (この処理には時間がかかります)]**  
 パブリッシャーとサブスクライバーの行数に加え、バイナリ チェックサム アルゴリズムを使用して、すべてのデータのチェックサムが計算されます。 行数の検証で失敗となった場合、チェックサムは実行されません。  
  
 **[検証完了後にディストリビューション エージェントを停止する]**  
 既定では、ディストリビューション エージェントは継続的に実行されます。 検証の実行後にエージェントを停止するには、このオプションを選択します。 これにより、サブスクライバーへのデータのレプリケートを継続する前に、検証が成功したかどうかをチェックできます。  
  
## <a name="see-also"></a>参照  
 [サブスクライバーでのデータの検証](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
