---
title: ユーザー アクセス許可とグループ アクセス許可の重複 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 6b337b716905523d78d3e49d60477c7b6f29f72f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52765324"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a>ユーザー権限とグループ権限の重複 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  ユーザーの権限は、次の権限に基づきます。  
  
-   グループのメンバーシップの権限  
  
-   ユーザーに明示的に割り当てられた権限  
  
 ユーザーが複数のグループのメンバーであり、それらのグループが [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]へのアクセス権を持っている場合、次の規則が適用されます。  
  
-   **拒否** が他のどの権限をオーバーライドします。 あるグループでのオブジェクト権限が **拒否** の場合、適用される権限は "拒否" です。  
  
-   アクセス権限は、グループに適用されるすべての権限の組み合わせになります。 あるグループのオブジェクト権限が **作成** であり、別のグループでは **更新** である場合、適用される権限は **作成** および **更新**になります。  
  
 上記のルールは、 **[モデル]** タブと **[階層メンバー]** タブに適用されます。 権限は、各タブで解決された後で組み合わされます。 詳細については、「 [権限の決定方法 (マスター データ サービス)](../master-data-services/how-permissions-are-determined-master-data-services.md)になります。  
  
> [!NOTE]  
>  ユーザー権限とグループ権限の重複がどのように解決されているかは、ユーザー インターフェイスに表示できます。 **[モデル]** タブと **[階層メンバー]** タブにはドロップダウン リストがあり、そこから **[有効]** をクリックして有効な権限を表示できます。  
  
## <a name="example-1"></a>例 1  
 ![mds_conc_user_group_ex_1](../master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 ユーザーがグループ 1 とグループ 2 に属しています。  
  
 ユーザーには、Product エンティティに対する **読み取り** 権限が与えられています。  
  
 グループ 1 には、Product エンティティに対する **更新** 権限が与えられています。  
  
 グループ 2 には、Product エンティティに対する **読み取り** 権限が与えられています。  
  
 結果:ユーザーの有効な権限は、Product エンティティに対する **更新** 権限となります。  
  
## <a name="example-2"></a>例 2  
 ![mds_conc_user_group_ex_2](../master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 ユーザーがグループ 1 とグループ 2 に属しています。  
  
 ユーザーには、Product エンティティに対する **読み取り** 権限が与えられています。  
  
 グループ 1 には、Product エンティティに対する **更新** 権限が与えられています。  
  
 グループ 2 には、Product エンティティに対する **拒否** 権限が与えられています。  
  
 結果:ユーザーの有効な権限は、Product エンティティに対する **拒否** 権限となります。  
  
## <a name="example-3"></a>例 3  
 ![mds_conc_user_group_ex_3](../master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 ユーザーがグループ 1 とグループ 2 に属しています。  
  
 ユーザーには、階層ノードのメンバーのグループに対する **更新** 権限が与えられています。  
  
 グループ 1 には、階層ノードのメンバーのグループに対する **読み取り** 権限が与えられています。  
  
 グループ 2 には、階層ノードのメンバーのグループに対する **読み取り** 権限が与えられています。  
  
 結果:ユーザーの有効な権限は、メンバーに対する **更新** 権限となります。  
  
## <a name="see-also"></a>参照  
 [権限の決定方法 (マスター データ サービス)](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [モデル アクセス許可とメンバー アクセス許可の重複 (マスター データ サービス)](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
