---
title: "DECRYPTBYPASSPHRASE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DECRYPTBYPASSPHRASE
- DECRYPTBYPASSPHRASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- decryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], DECRYPTBYPASSPHRASE function
- DECRYPTBYPASSPHRASE function
ms.assetid: ca34b5cd-07b3-4dca-b66a-ed8c6a826c95
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0af2f19acced57d722427c8f341db62dbdb34198
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="decryptbypassphrase-transact-sql"></a>DECRYPTBYPASSPHRASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  パスフレーズを使用して暗号化されたデータの暗号化を解除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DecryptByPassPhrase ( { 'passphrase' | @passphrase }   
    , { 'ciphertext' | @ciphertext }  
  [ , { add_authenticator | @add_authenticator }  
    , { authenticator | @authenticator } ] )  
```  
  
## <a name="arguments"></a>引数  
 *パスフレーズ*  
 暗号化解除キーを作成するために使用されるパスフレーズを指定します。  
  
 @passphrase  
 型の変数は、 **nvarchar**、 **char**、 **varchar**、または**nchar**キーの生成に使用されるパスフレーズを含む復号化します。  
  
 '*暗号化テキスト*'  
 暗号化を解除する暗号文です。  
  
 @ciphertext  
 型の変数は、 **varbinary**暗号文を格納しています。 最大サイズは 8,000 バイトです。  
  
 *add_authenticator*  
 認証子がプレーン テキストと共に暗号化されているかどうかを示します。 認証子が使用されている場合は 1 です。 **int**です。  
  
 @add_authenticator  
 認証子がプレーン テキストと共に暗号化されているかどうかを示します。 認証子が使用されている場合は 1 です。 **int**です。  
  
 *認証子*  
 認証子のデータを指定します。 **sysname**です。  
  
 @authenticator  
 認証子の派生元のデータを含む変数を指定します。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary** 8,000 バイトの最大サイズ。  
  
## <a name="remarks"></a>解説  
 この関数を実行するには、権限は必要ありません。  
  
 間違ったパスフレーズまたは認証子の情報が使用された場合、NULL が返されます。  
  
 パスフレーズは暗号化解除キーの生成に使用され、保存されません。  
  
 暗号文が暗号化されたときに認証子が含まれていた場合、暗号化を解除するときにその認証子を提供する必要があります。 暗号化を解除するときに提供された認証子の値が、そのデータで暗号化された認証子の値と一致しない場合、暗号化解除は失敗します。  
  
## <a name="examples"></a>使用例  
 次の例で更新されたレコードを復号化[EncryptByPassPhrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md)です。  
  
```  
USE AdventureWorks2012;  
-- Get the pass phrase from the user.  
DECLARE @PassphraseEnteredByUser nvarchar(128);  
SET @PassphraseEnteredByUser   
= 'A little learning is a dangerous thing!';  
  
-- Decrypt the encrypted record.  
SELECT CardNumber, CardNumber_EncryptedbyPassphrase   
    AS 'Encrypted card number', CONVERT(nvarchar,  
    DecryptByPassphrase(@PassphraseEnteredByUser, CardNumber_EncryptedbyPassphrase, 1   
    , CONVERT(varbinary, CreditCardID)))  
    AS 'Decrypted card number' FROM Sales.CreditCard   
    WHERE CreditCardID = '3681';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [暗号化アルゴリズムの選択](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](../../t-sql/functions/encryptbypassphrase-transact-sql.md)  
  
  