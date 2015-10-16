ms。ContentId: 71a03c62-50fd-48dc-9296-4d285027a96a
タイトル: ローカル VM で Windows コンテナーのセットアップ

#Windows Server のコンテナーのための Windows サーバーに関するテクニカル プレビューの準備

作成して、Windows Server のコンテナーの管理をするためには、Windows Server 2016 に関するテクニカル プレビュー環境を準備する必要があります。
このガイドは、HYPER-V 仮想マシンで Windows Server のコンテナーの構成方法を説明します。

> その他のファースト ステップ ガイド。
* Windows Server のコンテナーの実行 [Azure](./azure_setup.md)です。
* Windows Server のコンテナーの実行 [既存のバーチャル マシン](./inplace_setup.md)です。
* Windows Server のコンテナーをセットアップ [物理的な Windows Server Core インストールで](./inplace_setup.md)です。
    
    **してください。 読み取り前にインストールする、コンテナー OS イメージ:**  、Microsoft Windows Server のプレリリース版ソフトウェア (以下、"ライセンス条項") のライセンス条項は、Microsoft Windows のコンテナーの OS イメージは、(以下「補足的なソフトウェア) 本追加ソフトウェアの使用に適用します。
    をダウンロードして、追加のソフトウェアを使用して、ライセンス条項に同意して、ライセンス条項に同意していない場合に使用できません。
    Microsoft Corporation によっては、Windows Server のプレリリース版のソフトウェアと追加のソフトウェアの両方がライセンス供与します。
    


    * Windows の 10 を実行しているシステムと Windows Server 技術のプレビュー 2 またはそれ以降。
    * HYPER-V ロールが有効になっている ([手順を参照してください。](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install#UsingPowerShell))。
    * コンテナーのホスト イメージ、OS ベース イメージおよびセットアップ スクリプトの使用可能記憶域を 20 GB です。
    * HYPER-V ホスト上の管理者のアクセス許可。

> Windows Server のコンテナーでは、このガイドわかりやすくには、Windows Server のコンテナーのホストを実行する HYPER-V 環境が使用されていると仮定していますが、HYPER-V は必要ありません。

##新しいバーチャル マシン上の新しいコンテナー ホストのセットアップ

Windows Server のコンテナーは、Windows Server のコンテナーのホスト OS ベース イメージのコンテナーなどのいくつかのコンポーネントで構成されます。
まとめたものをダウンロードおよびをこれらの項目を構成するスクリプトです。
新しい HYPER-V バーチャル マシンを展開し、Windows Server のコンテナーのホストとしてこのシステムを構成するには、この手順に従います。

管理者として PowerShell セッションを開始します。
これは、PowerShell アイコンを右クリックして [管理者として実行] を選択すると、または任意の PowerShell セッションから、次のコマンドを実行して行うことができます。

``` powershell
start-process powershell -Verb runAs
```

構成スクリプトをダウンロードするのにには、次のコマンドを使用します。
スクリプトも手動でダウンロードできます - この場所から [構成スクリプト](http://aka.ms/newcontainerhost)です。

``` PowerShell
wget -uri https://aka.ms/newcontainerhost -OutFile New-ContainerHost.ps1
```

作成し、コンテナーのホストを構成するには、次のコマンドを実行する場所 `< containerhost >` は仮想マシンの名前になりますと `< パスワード >` 管理者アカウントに割り当てられているパスワードになります。

``` powershell
.\New-ContainerHost.ps1 –VmName <containerhost> -Password <password>
```

スクリプトの開始時に読み取りおよびライセンスの条項に同意になります。

```
Before installing and using the Windows Server Technical Preview 3 with Containers virtual machine you must:
    1. Review the license terms by navigating to this link: http://aka.ms/WindowsServerTP3ContainerVHDEula
    2. Print and retain a copy of the license terms for your records.
By downloading and using the Windows Server Technical Preview 3 with Containers virtual machine you agree to such
license terms. Please confirm you have accepted and agree to the license terms.
[N] No  [Y] Yes  [?] Help (default is "N"): Y
```

ダウンロードして、Windows Server のコンテナーのコンポーネントを構成するスクリプトが再開されます。
このプロセスでは、大きなファイルをダウンロードするためには、かなり時間がかかります。
仮想マシンを構成が完了すると、Windows Server のコンテナーおよび PowerShell と Docker の両方の Windows Server コンテナーのイメージ作成および管理の準備ができています。



ウィンドウのサーバーのコンテナーのホストの展開プロセス中には、次のメッセージがあります。

```
This VM is not connected to the network. To connect it, run the following:
Get-VM | Get-VMNetworkAdapter | Connect-VMNetworkAdapter -Switchname <switchname>
```
場合は、仮想マシンのプロパティを確認し、仮想マシンを仮想スイッチに接続します。また、次の PowerShell コマンドを実行することもできます。 ここで `< switchname >` 仮想マシンに接続するには、Hyper-v 仮想スイッチの名前を指定します。

``` powershell 
Get-VM | Get-VMNetworkAdapter | Connect-VMNetworkAdapter -Switchname <switchname>
```

構成スクリプトの実行が完了すると、仮想マシンを起動します。
VM では、Windows Server 2016 core が構成されは、次のようになります。

<center>![](./media/containerhost2.png)</center><br />

最後に、構成プロセス中に指定したパスワードを使用して仮想マシンにログインし、バーチャル マシンが有効な IP アドレスを持つかどうかを確認します。
完了した次の項目を含む、システムは、Windows Server のコンテナーの準備ができてする必要があります。


##ビデオ チュートリアル

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Configure-Windows-Server-Containers-on-a-Local-System/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##次の手順 - は、コンテナーの使用を開始します。

Windows Server のコンテナーの機能を実行しているシステムがイメージを Windows のサーバーのコンテナーおよび Windows Server のコンテナーを作業を開始する、次のガイドにジャンプ、Windows Server 2016 をしたとします。


[クイック スタート: Windows Server のコンテナーおよび Docker](./manage_docker.md)


[クイック スタート: Windows Server のコンテナーと PowerShell](./manage_powershell.md)


-------------------


[コンテナーのホームに戻る](../containers_welcome.md)
[現在のリリースに関する既知の問題](../about/work_in_progress.md)




