---
title: メンバーまたはコレクションを再アクティブ化する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], reactivating
- consolidated members [Master Data Services], reactivating
- reactivating members [Master Data Services]
- members [Master Data Services], reactivating
- reactivating collections [Master Data Services]
- leaf members [Master Data Services], reactivating
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 85653036f4e5348e7bb9d53959b0d6957564f18a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52783054"
---
# <a name="reactivate-a-member-or-collection-master-data-services"></a>メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、次のいずれかの状態にあったメンバーを再アクティブ化できます。  
  
-   ステージング処理によって非アクティブにされた。  
  
-   MDS [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]で削除された。  
  
-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションで削除された。  
  
 メンバーを再アクティブ化すると、階層およびコレクションのメンバーの属性とメンバーシップが復元されます。  
  
 また、コレクションを再アクティブ化することもできます。 その場合、コレクションの属性と、コレクションに属するメンバーが復元されます。  
  
 メンバーまたはコレクションを再アクティブ化すると、以前のトランザクションがすべて復元されます。  
  
## <a name="prerequisites"></a>Prerequisites  
 この手順を実行するには  
  
-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]の **[バージョン管理]** 機能領域に対する権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「 [管理者 (マスター データ サービス)](../master-data-services/administrators-master-data-services.md)にアクセスすることなくグループに対してユーザーの追加または削除を行うことができます。  
  
### <a name="to-reactivate-a-member-or-collection"></a>メンバーまたはコレクションを再アクティブ化するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、 **[バージョン管理]** をクリックします。  
  
2.  メニュー バーの **[トランザクション]** をクリックします。  
  
3.  **[トランザクション]** ページで、 **[モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[バージョン]** ボックスの一覧からバージョンを選択します。  
  
5.  **[トランザクション]** ペインで、再アクティブ化するメンバーまたはコレクションの行をクリックします。 この行の **[以前の値]** 列に **[アクティブ]** 、 **[新しい値]** 列に **[非アクティブ]** と表示されます。  
  
6.  **[トランザクションの破棄]** をクリックします。  
  
7.  確認のダイアログ ボックスで **[OK]** をクリックします。 **[新しい値]** 列に **[アクティブ]** と表示され、新しいトランザクションが追加されます。  
  
## <a name="see-also"></a>参照  
 [メンバーまたはコレクションを削除する (マスター データ サービス)](../master-data-services/delete-a-member-or-collection-master-data-services.md)   
 [メンバー (マスター データ サービス)](../master-data-services/members-master-data-services.md)   
 [コレクション (マスター データ サービス)](../master-data-services/collections-master-data-services.md)  
  
  
