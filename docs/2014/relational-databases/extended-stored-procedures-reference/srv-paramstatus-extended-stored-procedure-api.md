---
title: srv_paramstatus (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_paramstatus
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 01dc9aa7608cacfabb980803b79a27c9f55f8ce3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195322"
---
# <a name="srvparamstatus-extended-stored-procedure-api"></a>srv_paramstatus (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 特定のリモート ストアド プロシージャ呼び出しのパラメーターの状態を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *n*  
 パラメーターの番号を示します。 最初のパラメーターは 1 です。  
  
## <a name="returns"></a>戻り値  
 このパラメーターの状態フラグを示す `int` 値を返します。 現在、フラグは 1 つだけあります。ビット 0 が 1 に設定されている場合、パラメーターは戻りパラメーターです。 *n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は、-1 を返します。  
  
## <a name="remarks"></a>コメント  
 このルーチンは、リモート ストアド プロシージャ呼び出しのパラメーターに関する状態フラグを返します。  
  
 パラメーターには、リモート ストアド プロシージャを使用してクライアントとアプリケーションとの間で受け渡しされるデータが格納されます。 クライアントは戻りパラメーターとして特定のパラメーターを指定できます。 この戻りパラメーターには、アプリケーションからクライアントに返す値を格納できます。  
  
 現在使用されている唯一の状態フラグは、パラメーターが戻りパラメーターかどうかを示すものです。  
  
 パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。 名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。 エラーが発生しても SRV_RPC ハンドラーは呼び出されますが、パラメーターが存在しないと見なされ、**srv_rpcparams** は 0 を返します。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;](srv-rpcparams-extended-stored-procedure-api.md)  
  
  