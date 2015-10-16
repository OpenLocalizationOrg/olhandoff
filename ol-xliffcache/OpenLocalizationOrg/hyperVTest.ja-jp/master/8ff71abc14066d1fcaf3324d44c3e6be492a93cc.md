ms。ContentId: 44b138bb-962f-4474-a0c4-284646a872e2
タイトル: の場所で Windows コンテナーのセットアップ

#Windows Server のコンテナーの物理マシンまたは既存のバーチャル マシンを準備します。

作成して、Windows Server のコンテナーの管理をするためには、Windows Server 2016 に関するテクニカル プレビュー環境を準備する必要があります。
このガイドは、ベア メタルまたは Windows Server 2016 に関するテクニカル プレビューを実行している既存のバーチャル マシンで Windows Server のコンテナーの構成方法を説明します。


> その他のファースト ステップ ガイド。
* Windows Server のコンテナーの実行 [Azure](./azure_setup.md)です。
* Windows Server のコンテナーの実行 [新しい HYPER-V VM](./container_setup.md)です。
    
    **してください。 読み取り前にインストールする、コンテナー OS イメージ:**  、Microsoft Windows Server のプレリリース版ソフトウェア (以下、"ライセンス条項") のライセンス条項は、Microsoft Windows のコンテナーの OS イメージは、(以下「補足的なソフトウェア) 本追加ソフトウェアの使用に適用します。
    をダウンロードして、追加のソフトウェアを使用して、ライセンス条項に同意して、ライセンス条項に同意していない場合に使用できません。
    Microsoft Corporation によっては、Windows Server のプレリリース版のソフトウェアと追加のソフトウェアの両方がライセンス供与します。
    


**システム (または VM) の要件:**
* Windows Server テクニカル プレビュー 3 の Server Core を実行しているシステム。
* 10 GB OS ベース イメージおよびセットアップのスクリプトの使用可能なストレージです。
* コンピューターまたは VM で管理者権限です。

##コンテナーの既存のバーチャル マシンまたはベア メタル ホストのセットアップ

Windows Server のコンテナーでは、コンテナーの OS のベース イメージが必要です。
まとめたものをダウンロードして、このクライアントをインストールするのスクリプトです。
Windows Server のコンテナーのホストとして、システムを構成する次の手順に従います。

管理者として PowerShell セッションを開始します。
これは、コマンドラインから次のコマンドを実行して実行できます。

``` powershell
powershell.exe
```

ウィンドウのタイトルが"管理者:: Windows PowerShell"であることを確認してください。
管理者が記載されていないことがある場合は、管理者権限で実行するには、このコマンドを実行します。

``` powershell
start-process powershell -Verb runas
```

セットアップ スクリプトをダウンロードするのにには、次のコマンドを使用します。
スクリプトも手動でダウンロードできます - この場所から [構成スクリプト](http://aka.ms/setupcontainers)です。

``` PowerShell
wget -uri https://aka.ms/setupcontainers -OutFile C:\ContainerSetup.ps1
```

 ダウンロードが完了したら後、は、スクリプトを実行します。
``` PowerShell
C:\ContainerSetup.ps1
```

ダウンロードして、Windows Server のコンテナーのコンポーネントを構成するスクリプトが再開されます。
このプロセスでは、大きなファイルをダウンロードするためには、かなり時間がかかります。
処理中に、コンピューターが再起動可能性があります。
コンピューターを構成が完了すると、Windows Server のコンテナーおよび PowerShell と Docker の両方の Windows Server コンテナーのイメージ作成および管理の準備ができています。


 完了した次の項目を含む、システムは、Windows Server のコンテナーの準備ができてする必要があります。



##次の手順 - は、コンテナーの使用を開始します。

Windows Server のコンテナーを実行していることは、Windows Server のコンテナーおよび Windows Server のコンテナーのイメージでの作業を開始する、次のガイドにジャンプします。


[クイック スタート: Windows Server のコンテナーおよび Docker](./manage_docker.md)


[クイック スタート: Windows Server のコンテナーと PowerShell](./manage_powershell.md)


-------------------


[コンテナーのホームに戻る](../containers_welcome.md)
[現在のリリースに関する既知の問題](../about/work_in_progress.md)



