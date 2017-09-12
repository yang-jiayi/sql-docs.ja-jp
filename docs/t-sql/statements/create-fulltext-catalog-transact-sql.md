---
title: "CREATE FULLTEXT CATALOG (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CATALOG_TSQL
- CREATE_FULLTEXT_TSQL
- FULLTEXT_TSQL
- FULLTEXT CATALOG
- CREATE FULLTEXT CATALOG
- CREATE_FULLTEXT_CATALOG_TSQL
- CATALOG
- FULLTEXT_CATALOG_TSQL
- CREATE FULLTEXT
- FULLTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- CREATE FULLTEXT CATALOG statement
ms.assetid: d7a8bd93-e2d7-4a40-82ef-39069e65523b
caps.latest.revision: 60
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 303908a306661c764b9cd258147fcc911d2d3983
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-fulltext-catalog-transact-sql"></a>CREATE FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベースのフルテキスト カタログを作成します。 1 つのフルテキスト カタログには複数のフルテキスト インデックスを格納できますが、1 つのフルテキスト インデックスは 1 つのフルテキスト カタログにしか格納できません。 各データベースには、任意の数のフルテキスト カタログを格納できます。  
  
 フルテキスト カタログを作成することはできません、**マスター**、**モデル**、または**tempdb**データベース。  
  
> [!IMPORTANT]  
>  以降で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、フルテキスト カタログは、仮想オブジェクトで、任意のファイル グループに属していません。 フルテキスト カタログは、フルテキスト インデックスのグループを指す論理的概念です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE FULLTEXT CATALOG catalog_name  
     [ON FILEGROUP filegroup ]  
     [IN PATH 'rootpath']  
     [WITH <catalog_option>]  
     [AS DEFAULT]  
     [AUTHORIZATION owner_name ]  
  
<catalog_option>::=  
     ACCENT_SENSITIVITY = {ON|OFF}  
  
```  
  
## <a name="arguments"></a>引数  
 *catalog_name*  
 新しいカタログの名前を指定します。 このカタログ名は、現在のデータベース内にあるすべてのカタログ名の中で一意であることが必要です。 また、フルテキスト カタログに対応するファイルの名前 (ON FILEGROUP を参照) は、データベース内にある全ファイルの中で一意であることが必要です。 カタログの名前が別のカタログ、データベースで既に使用されている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。  
  
 カタログ名は半角 120 文字以内で指定してください。  
  
 ON FILEGROUP *filegroup*  
 以降で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、この句が影響を与えません。  
  
 パスに**'***rootpath***'**  
 > [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 以降で[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、この句が影響を与えません。  
  
 ACCENT_SENSITIVITY = {ON|OFF}   
 カタログのフルテキスト インデックス作成でアクセントを区別するかどうかを指定します。 このプロパティを変更すると、インデックスの再構築が必要になります。 既定では、データベースの照合順序の指定に従って、アクセントの区別が決定されます。 表示するにはデータベースの照合順序を使用して、 **sys.databases**カタログ ビューです。  
  
 フルテキスト カタログの現在のアクセントの区別に関するプロパティの設定を確認するのに、FULLTEXTCATALOGPROPERTY 関数を使用して、 **accentsensitivity**プロパティの値に対して*catalog_name*です。 値 '1' が返された場合、フルテキスト カタログではアクセントが区別され、値 '0' が返された場合、アクセントは区別されません。  
  
 AS DEFAULT   
 カタログが既定のカタログであることを指定します。 フルテキスト カタログを明示的に指定せずにフルテキスト インデックスを作成するときには、既定のカタログが使用されます。 既存のフルテキスト カタログが既に AS DEFAULT となっている場合、この新しいカタログを AS DEFAULT として設定すると、新しいカタログが既定のフルテキスト カタログになります。  
  
 承認*owner_name*  
 フルテキスト カタログの所有者として、データベース ユーザーまたはロールの名前を設定します。 場合*owner_name*ロール、ロールがメンバーである現在のユーザー、ロールの名前にする必要がありますまたはステートメントを実行しているユーザーが、データベース所有者またはシステム管理者にする必要があります。  
  
 場合*owner_name*は、ユーザー名、ユーザー名は、次のいずれかにする必要があります。  
  
-   ステートメントを実行するユーザーの名前。  
  
-   コマンドを実行するユーザーが持つ借用権限に対応するユーザーの名前。  
  
-   コマンドを実行するユーザーがデータベース所有者またはシステム管理者であること。  
  
 *owner_name*指定されたフルテキスト カタログに対する TAKE OWNERSHIP 権限を与える必要もあります。  
  
## <a name="remarks"></a>解説  
 フルテキスト カタログ Id は、00005 から開始され、新しいカタログが作成されるごとに 1 つがインクリメントされます。  
  
## <a name="permissions"></a>Permissions  
 ユーザーが、データベースに対する CREATE FULLTEXT CATALOG 権限を持っているかのメンバーである必要があります、 **db_owner**、または**db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、フルテキスト カタログとフルテキスト インデックスを作成します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE FULLTEXT CATALOG ftCatalog AS DEFAULT;  
GO  
CREATE FULLTEXT INDEX ON HumanResources.JobCandidate(Resume) KEY INDEX PK_JobCandidate_JobCandidateID;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fulltext_catalogs & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)   
 [新しいフルテキスト カタログ & #40 です。[全般] ページ &#41;](http://msdn.microsoft.com/library/5ed6f7cd-d9af-4439-9f33-fc935b883d91)  
  
  