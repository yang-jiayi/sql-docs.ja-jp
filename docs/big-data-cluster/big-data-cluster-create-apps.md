---
title: Mssqlctl を使用してアプリケーションをデプロイします。
titleSuffix: SQL Server 2019 big data clusters
description: SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリケーションとしては、Python または R スクリプトを展開します。
author: TheBharath
ms.author: bharaths
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 8d784b82c56ca99027491bf257c90dddf4eb9b6b
ms.sourcegitcommit: c0b3b3d969af668d19b1bba04fa0c153cc8970fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57756637"
---
# <a name="how-to-deploy-an-app-on-sql-server-2019-big-data-cluster-preview"></a>SQL Server 2019 ビッグ データ クラスター (プレビュー) でアプリをデプロイする方法

この記事では、デプロイし、SQL Server 2019 ビッグ データ クラスター (プレビュー) 内でアプリケーションとして R と Python スクリプトを管理する方法について説明します。

## <a name="whats-new-and-improved"></a>新機能と強化

- クラスターとアプリを管理する 1 つのコマンド ライン ユーティリティです。
- Spec ファイルで詳細に制御を提供しながら、アプリのデプロイを簡略化します。
- ホストの追加のアプリケーションの種類の SSIS と MLeap (CTP 2.3) の新機能をサポートします。
- [VS Code 拡張機能](app-deployment-extension.md)アプリケーションの展開を管理するには

アプリケーションが展開されを使用して管理`mssqlctl`コマンド ライン ユーティリティです。 この記事では、コマンドラインからのアプリをデプロイする方法の例を示します。 使用する方法についてをこの Visual Studio Code で参照してください。 [VS Code 拡張機能](app-deployment-extension.md)します。

次の種類のアプリがサポートされています。
- R と Python のアプリ (関数、モデル、およびアプリ)
- MLeap サービスを提供します。
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>前提条件

- [SQL Server 2019 ビッグ データ クラスター](deployment-guidance.md)
- [mssqlctl コマンド ライン ユーティリティ](deploy-install-mssqlctl.md)

## <a name="capabilities"></a>Capabilities

SQL Server 2019 (プレビュー) CTP 2.3 作成、削除、説明、初期化では、一覧を実行し、アプリケーションを更新します。 次の表は、アプリケーションの展開コマンドで使用できる**mssqlctl**します。

|コマンド |説明 |
|:---|:---|
|`mssqlctl login` | SQL Server のビッグ データ クラスターにログインします。 |
|`mssqlctl app create` | アプリケーションを作成します。 |
|`mssqlctl app delete` | アプリケーションを削除します。 |
|`mssqlctl app describe` | アプリケーションをについて説明します。 |
|`mssqlctl app init` | Kickstart の新しいアプリケーションのスケルトンです。 |
|`mssqlctl app list` | アプリケーションの一覧を表示します。 |
|`mssqlctl app run` | アプリケーションを実行します。 |
|`mssqlctl app update`| アプリケーションを更新します。 |

ヘルプを表示できる、`--help`次の例のようにパラメーター。

```bash
mssqlctl app create --help
```

次に、これらのコマンドについて詳しく説明します。

## <a name="log-in"></a>ログイン

展開するアプリケーションとやり取りする前に、最初にログイン、SQL Server を使用したクラスターのビッグ データ、`mssqlctl login`コマンド。 外部 IP アドレスを指定、`endpoint-service-proxy`サービス (例: `https://ip-address:30777`) およびユーザー名とクラスターへのパスワード。

```bash
mssqlctl login -e https://<ip-address-of-endpoint-service-proxy>:30777 -u <user-name> -p <password>
```

## <a name="aks"></a>AKS

AKS を使用している場合は、IP アドレスを取得するには、次のコマンドを実行する必要があります、 `endpoint-service-proxy` bash または cmd ウィンドウでこのコマンドを実行してサービス。


```bash
kubectl get svc endpoint-service-proxy -n <name of your cluster>
```

## <a name="kubeadm-or-minikube"></a>Kubeadm または Minikube

クラスターにログインする IP アドレスを取得する Kubeadm または次のコマンドを実行して Minikube を使用する場合

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>アプリを作成します。

使用するアプリケーションを作成する`mssqlctl`で、`app create`コマンド。 これらのファイルからアプリを作成しているコンピューターでローカルに存在します。

ビッグ データ クラスターで新しいアプリを作成するのにには、次の構文を使用します。

```bash
mssqlctl app create -n <app_name> -v <version_number> --spec <directory containing spec file>
```

次のコマンドは、このコマンドの例を示しています。

これはという名前のファイルがあることを前提としています`spec.yaml`内、`addpy`フォルダー。
`addpy`フォルダーが含まれています、`add.py`と`spec.yaml`、`spec.yaml`のファイルの仕様、`add.py`アプリ。


`add.py` 次の python アプリを作成します。

```py
#add.py
def add(x,y):
        result = x+y
        return result
result=add(x,y)
```

次のスクリプトは、サンプルの内容の`spec.yaml`:

```yaml
#spec.yaml
name: add-app #name of your python script
version: v1  #version of the app
runtime: Python #the language this app uses (R or Python)
src: ./add.py #full path to the location of the app
entrypoint: add #the function that will be called upon execution
replicas: 1  #number of replicas needed
poolsize: 1  #the pool size that you need your app to scale
inputs:  #input parameters that the app expects and the type
  x: int
  y: int
output: #output parameter the app expects and the type
  result: int
```

これには、ディレクトリ内の 2 つのファイルに、上記のコード行をコピー`addpy`として`add.py`と`spec.yaml`し、次のコマンドを実行します。

```bash
mssqlctl app create --spec ./addpy
```

一覧のコマンドを使用して、アプリをデプロイするかどうかを確認できます。

```bash
mssqlctl app list
```

デプロイが完了していない場合は表示、`state`表示`WaitingforCreate`として次の例。

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

デプロイが成功した後が表示されます、`state`変更`Ready`状態。

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>アプリを登録します。

正常に作成されたすべてのアプリの一覧を表示することができます、`app list`コマンド。

次のコマンドでは、ビッグ データ クラスター内のすべての利用可能なアプリケーションが表示されます。

```bash
mssqlctl app list
```

名前とバージョンを指定する場合は、その特定のアプリとその状態 (作成または準備完了) を示します。

```bash
mssqlctl app list --name <app_name> --version <app_version>
```

次の例では、このコマンドを示しています。

```bash
mssqlctl app list --name add-app --version v1
```

次の例のような出力が表示されます。

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>アプリを実行します。

アプリがある場合、`Ready`状態を指定された入力パラメーターで実行して使用することができます。 アプリを実行するのにには、次の構文を使用します。

```bash
mssqlctl app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

次のコマンドの例では、run コマンドを示しています。

```bash
mssqlctl app run --name add-app --version v1 --inputs x=1,y=2
```

実行が成功した場合、アプリの作成時に指定すると、出力が表示されます。 以下に例を示します。

```json
{
  "changedFiles": [],
  "consoleOutput": "",
  "errorMessage": "",
  "outputFiles": {},
  "outputParameters": {
    "result": 3
  },
  "success": true
}
```

## <a name="create-an-app-skeleton"></a>アプリのスケルトンを作成します。

Init コマンドでは、アプリを展開するために必要な関連する成果物とスキャフォールディングを提供します。 次の例では、次のコマンドを実行してこれを行うこんにちはを作成します。

```bash
mssqlctl app init --name hello --version v1 --template python
```

これにより、こんにちはという名前のフォルダーが作成されます。  できます`cd`ディレクトリに表示され、フォルダーに生成されたファイルを調べる。 spec.yaml では、名前、バージョン、およびソース コードなど、アプリを定義します。 名前、バージョン、入力と出力を変更する仕様を編集できます。

フォルダーに表示される init コマンドからの出力サンプルを次に示します

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>アプリをについて説明します。

Describe コマンドは、クラスター内の終点を含むアプリに関する詳細情報を提供します。 これは通常使用して、アプリの開発者 swagger クライアントを使用して、rest ベースの方法で、アプリと対話する web サービスを使用してアプリをビルドします。

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30777/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30777/api/app/add-app/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

## <a name="delete-an-app"></a>アプリを削除します。

ビッグ データ クラスターからアプリを削除するには、次の構文を使用します。

```bash
mssqlctl app delete --name add-app --version v1
```

## <a name="next-steps"></a>次のステップ

その他のサンプルを確認することもできます。[アプリの展開サンプル](https://aka.ms/sql-app-deploy)します。

ビッグ データの SQL Server クラスターの詳細については、次を参照してください。 [SQL Server 2019 ビッグ データ クラスターには何ですか?](big-data-cluster-overview.md)します。
