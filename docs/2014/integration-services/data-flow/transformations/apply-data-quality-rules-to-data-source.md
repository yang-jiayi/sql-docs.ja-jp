---
title: データ ソースにデータ品質ルールを適用する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a965e8f2-004d-4ccc-8523-a185b35b26e2
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 232ea4b3c3d8c54d0d4fa3938ccab5cb91664b03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160853"
---
# <a name="apply-data-quality-rules-to-data-source"></a>データ ソースにデータ品質ルールを適用する
  Data Quality Services (DQS) を使用して、DQS クレンジング変換をデータ ソースに接続することで、パッケージ データ フロー内のデータを修正できます。 DQS の詳細については、「 [Data Quality Services の概念](../../../data-quality-services/data-quality-services-concepts.md)」を参照してください。 変換の詳細については、「[DQS クレンジング変換](dqs-cleansing-transformation.md)」を参照してください。  
  
 DQS クレンジング変換によってデータを処理すると、データ品質プロジェクトが Data Quality Server に作成されます。 データ品質クライアントを使用してプロジェクトを管理します。 詳細については、「[データ品質プロジェクトの管理 &#40;開く、ロック解除、名前の変更、および削除&#41;](../../../data-quality-services/manage-open-unlock-rename-and-delete-a-data-quality-project.md)」を参照してください。  
  
### <a name="to-correct-data-in-the-data-flow"></a>データ フロー内のデータを修正するには  
  
1.  パッケージを作成します。  
  
2.  DQS クレンジング変換を追加し、構成します。 詳細については、「[[DQS クレンジング変換エディター] ダイアログ ボックス](../../dqs-cleansing-transformation-editor-dialog-box.md)」を参照してください。  
  
3.  データ ソースに DQS クレンジング変換を接続します。  
  
  