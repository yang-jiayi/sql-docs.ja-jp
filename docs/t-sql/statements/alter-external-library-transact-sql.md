---
title: ALTER EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cc590bb618f9a95a0fbe7b0a9c173a64698cdf1e
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017968"
---
# <a name="alter-external-library-transact-sql"></a>ALTER EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

既存の外部パッケージ ライブラリのコンテンツを変更します。

> [!NOTE]
> SQL Server 2017 では、R 言語と Windows プラットフォームがサポートされています。 Windows プラットフォームの R、Python、Java は SQL Server 2019 CTP 2.3 でサポートされています。 Linux は今後のリリースでサポートされる予定です。

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax-for-sql-server-2019"></a>SQL Server 2019 の構文

```text
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = <language> )
[ ; ]

<file_spec> ::=
{
    (CONTENT = { <client_library_specifier> | <library_bits> | NONE}
    [, PLATFORM = WINDOWS )
}

<client_library_specifier> :: =
{
      '[\\computer_name\]share_name\[path\]manifest_file_name'
    | '[local_path\]manifest_file_name'
    | '<relative_path_in_external_data_source>'
}

<library_bits> :: =
{ 
      varbinary_literal 
    | varbinary_expression 
}

<language> :: = 
{
      'R'
    | 'Python'
    | 'Java'
}
```
::: moniker-end
::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
## <a name="syntax-for-sql-server-2017"></a>SQL Server 2017 の構文

```text
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = 'R' )
[ ; ]

<file_spec> ::=
{
    (CONTENT = { <client_library_specifier> | <library_bits> | NONE}
    [, PLATFORM = WINDOWS )
}

<client_library_specifier> :: =
{
      '[\\computer_name\]share_name\[path\]manifest_file_name'
    | '[local_path\]manifest_file_name'
    | '<relative_path_in_external_data_source>'
}

<library_bits> :: =
{ 
      varbinary_literal 
    | varbinary_expression 
}
```
::: moniker-end

### <a name="arguments"></a>引数

**library_name**

既存のパッケージ ライブラリの名前を指定します。 ライブラリは、ユーザーに範囲指定されます。 ライブラリ名は、特定のユーザーまたは所有者のコンテキスト内で一意と見なされる必要があります。

ライブラリ名を任意に割り当てることはできません。 つまり、呼び出し元のランタイムがパッケージの読み込み時に想定している名前を使用する必要があります。

**owner_name**

外部ライブラリを所有しているユーザーまたはロールの名前を指定します。

**file_spec**

特定のプラットフォーム用のパッケージのコンテンツを指定します。 プラットフォームごとに 1 つのファイル成果物のみがサポートされます。

ファイルは、ローカル パスまたはネットワーク パスの形式で指定することができます。 データ ソース オプションが指定されている場合、ファイル名は `EXTERNAL DATA SOURCE` で参照されているコンテナーに対する相対パスにすることができます。

必要に応じて、ファイルの OS プラットフォームを指定できます。 特定の言語またはランタイムの OS プラットフォームごとに 1 つのファイル成果物またはコンテンツのみが許可されます。

**library_bits**

アセンブリと同様に、パッケージのコンテンツを 16 進数のリテラルとして指定します。 

このオプションは、ライブラリを変更するのにアクセス許可はあるが、サーバー上のファイルへのアクセスが制限されていて、サーバーがアクセスできるパスにコンテンツを保存できない場合に役に立ちます。

代わりに、パッケージのコンテンツを変数としてバイナリ形式で渡すことができます。

**PLATFORM = WINDOWS**

ライブラリのコンテンツのプラットフォームを指定します。 この値は、さまざまなプラットフォームを追加する既存のライブラリを変更する場合に必要です。 サポートされているプラットフォームは Windows のみです。

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
**language**

パッケージの言語を指定します。 値には **R**、**Python**、**Java** があります。
::: moniker-end

## <a name="remarks"></a>Remarks

R 言語の場合、Windows の .ZIP 拡張子を使用して、ZIP アーカイブ ファイルの形式でパッケージを準備する必要があります。 現時点では、Windows プラットフォームのみがサポートされています。  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
Python 言語の場合、.whl または .zip ファイルのパッケージは zip アーカイブ ファイルの形式で準備する必要があります。 パッケージが既に .zip ファイルになっている場合、新しい .zip ファイルに含める必要があります。 現在のところ、.whl または .zip ファイルとしてパッケージを直接アップロードすることはできません。
::: moniker-end

`ALTER EXTERNAL LIBRARY` ステートメントは、ライブラリ ビットのデータベースへのアップロードのみを行います。 ユーザーがライブラリを呼び出す [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) でコードを実行すると、変更したライブラリがインストールされます。

## <a name="permissions"></a>アクセス許可

既定では、**dbo** ユーザーまたはロール **db_owner** のすべてのメンバーが、ALTER EXTERNAL LIBRARY を実行する権限を持っています。 さらに、外部ライブラリを作成したユーザーも、その外部ライブラリを変更できます。

## <a name="examples"></a>使用例

次の例では、`customPackage` と呼ばれる外部ライブラリを変更します。

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. ファイルを使用してライブラリのコンテンツを置き換える

次の例では、更新されたビットを含む ZIP 形式のファイルを使用して、`customPackage` と呼ばれる外部ライブラリを変更します。

```sql
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```

更新されたライブラリをインストールするには、ストアド プロシージャ `sp_execute_external_script` を実行します。

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'library(customPackage)'
;
```

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
SQL Server 2019 の Python 言語の場合、`'R'` を `'Python'` に替えてもこの例は機能します。
::: moniker-end
### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>B. バイト ストリームを使用して既存のライブラリを変更する

次の例では、新しいビットを 16 進数リテラルとして渡すことで、ライブラリを変更します。

```SQL
ALTER EXTERNAL LIBRARY customLibrary 
SET (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
SQL Server 2019 の Python 言語の場合、`'R'` を `'Python'` に替えてもこの例は機能します。
::: moniker-end

> [!NOTE]
> このコード サンプルは構文のみを示しています。`CONTENT =` のバイナリ値は読みやすさのため切り捨てられており、作業ライブラリを作成しません。 バイナリ変数の実際の内容はこれよりも長くなります。

## <a name="see-also"></a>参照

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md) 
