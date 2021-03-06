---
title: ドライバーのアーキテクチャの概要 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], architecture
- FoxPro ODBC driver [ODBC], architecture
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fdb1789c6640c072ec013c341bd4889b28bb469
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771870"
---
# <a name="driver-architecture-overview"></a>ドライバーのアーキテクチャの概要
Microsoft Visual FoxPro ODBC ドライバーは、32 ビット ドライバーを開き、Microsoft Visual FoxPro データベースまたは開く Database Connectivity (ODBC) インターフェイスを使用して FoxPro テーブルをクエリすることができます。 FoxPro を次の種類のアプリケーションを使用してデータにアクセスできます。  
  
-   Microsoft のクエリを使用して、ODBC との通信に、Microsoft Excel や Microsoft Word などの Microsoft Office アプリケーション。  
  
-   Microsoft Visual C または ODBC SDK API を使用して C# で記述されたアプリケーション。  
  
-   Microsoft Visual Basic または Microsoft Visual Basic for Applications で記述されたアプリケーション。  
  
 各ケースでは、情報の要求は、ODBC API を使用します。 ODBC ドライバー マネージャーを開き、FoxPro テーブルおよびデータベースからデータを取得する Visual FoxPro ODBC ドライバーで動作します。  
  
 アーキテクチャは、次の図で表されます。  
  
 ![ODBC ドライバーのアーキテクチャ](../../odbc/microsoft/media/vfparch.gif "vfparch")  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Visual FoxPro 用語集](../../odbc/microsoft/visual-foxpro-terminology.md)  
  
-   [インストールして、Visual FoxPro ODBC ドライバーの構成](../../odbc/microsoft/installing-and-configuring.md)  
  
-   [Visual FoxPro ODBC ドライバーの使用](../../odbc/microsoft/using-the-visual-foxpro-odbc-driver.md)
