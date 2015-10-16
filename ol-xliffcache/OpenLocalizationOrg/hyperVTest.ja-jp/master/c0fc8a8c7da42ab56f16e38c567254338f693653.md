ms。ContentId: 347fa279-d588-4094-90ec-8c2fc241f5b6
タイトル: Docker と Windows Server のコンテナーの管理

#クイック スタート: Windows Server のコンテナーおよび Docker

この記事は windows Docker を使用してコンテナーをサーバーの管理の基礎について説明します。
Windows Server のコンテナーとサーバーのコンテナーの Windows イメージを作成する、Windows Server のコンテナーおよびコンテナーのイメージの削除、および最後に、アプリケーションを Windows Server のコンテナーに展開する対象となるアイテムが含まれます。
このチュートリアルで得られた教訓では、Docker を使用して、Windows のサーバー コンテナの展開と管理の調査を開始するを有効にする必要があります。

ご質問があるでしょうか。
依頼、 [Windows コンテナー フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers)です。

> **注:** PowerShell で作成された Windows コンテナーいない現在使用して管理できる Docker および visa 逆の場合。
> PowerShell では、コンテナーを作成するを参照してください。  [クイック スタート: Windows Server のコンテナーおよび PowerShell](./manage_powershell.md)です。
> <br /><br /> 詳細を知りたい場合 [faq](../about/faq.md#WhydoIhavetopickbetweenDockerandPowerShellforWindowsServerContainermanagement)です。

##前提条件

このチュートリアルを完了するのには、次の項目を適所に配置する必要があります。

- Windows Server 2016 TP3 か、後で、Windows Server のコンテナーの機能を構成します。
    セットアップ ガイドを完了したら、これが Azure または HYPER-V で作成された VM です。
- このシステムは、ネットワークに接続されていると、インターネットにアクセスすることである必要があります。

コンテナーの機能を構成する必要がある場合は、次のガイドを参照してください: [Azure でのコンテナー セットアップ](./azure_setup.md) または [HYPER-V でのコンテナーのセットアップ](./container_setup.md)です。


##Docker で基本的なコンテナーの管理

この最初の例は、作成および Windows Server のコンテナーと Docker での Windows サーバー コンテナーのイメージを削除するための基本事項について説明します。

Windows Server のコンテナーのホスト システムにログを通じてウォークを開始するには、Windows のコマンド プロンプトが表示されます。

![](media/cmd.png)

」と入力して、PowerShell セッションを開始 `powershell`です。
プロンプトを変更するときに、PowerShell セッションであることがわかります `C:\directory >` に `PS C:\directory >`です。
```
C:\> powershell
Windows PowerShell
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\>
```
> このクイック スタートは、PowerShell コマンドを使用してファイアウォール ルールを管理して、ファイルのコピーなどのいくつかの手順を実行します。 ただし、Docker コマンドに注目が。
> PowerShell セッションからには、このチュートリアルを使用します。

次に、システムでは、有効な IP アドレスを使用して、持っていることを確認 `ipconfig` し、後で使用するのには、このアドレスを書き留めます。
```
ipconfig

Ethernet adapter Ethernet 3:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb::e
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb:a8c1:a3e:96b7:ffcb
   Link-local IPv6 Address . . . . . : fe80::a8c1:a3e:96b7:ffcb%5
   IPv4 Address. . . . . . . . . . . : 192.168.1.25
```

使用せずに Azure の仮想マシンから作業しているかどうかは `ipconfig` を Azure の仮想マシンのパブリック IP アドレスを取得する必要があります。

![](media/newazure9.png)

###手順 1 - 新しいコンテナーを作成します。

Docker と Windows Server のコンテナーを作成する前に、名前または exsisitng サーバー コンテナーの Windows イメージの ID が必要です。

使用して、コンテナーのホストに読み込まれたすべてイメージを表示する、 `docker イメージ` コマンド。

``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
windowsservercore   latest              9eca9231f4d4        30 hours ago        9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        30 hours ago        9.613 GB
```

使用して、 `実行 docker` に新しい Windows Server のコンテナーを作成します。
以下に示すように、このコマンドは Docker デーモンは、イメージ 'windowsservercore' から ' dockerdemo' という名前の新しいコンテナーを作成し、対話型を開くように指示されます (-こと) により、コンテナーのセッション (cmd) のコンソールです。

``` PowerShell
docker run -it --name dockerdemo windowsservercore cmd
```
コマンドの完了時に、処理するコンソール セッションで、コンテナーにします。

コンテナーでの作業は、仮想または物理コンピューターにインストールされているウィンドウの操作とほぼ同じです。
などのコマンドを実行することができます `ipconfig` コンテナー内の IP アドレスを返す `mkdir` 、新しいディレクトリを作成または `powershell` PowerShell セッションを開始します。
ファイルまたはフォルダーの作成などのコンテナーを変更してください。
たとえば、次のコマンドでは、コンテナーに関するネットワーク構成データを格納するファイルが作成されます。

``` PowerShell
ipconfig > c:\ipconfig.txt
```

コマンドを正常に完了したことを確認するファイルの内容を読み取ることができます。
テキスト ファイルに含まれている IP アドレスが、コンテナーのと一致することに注意してください。

``` PowerShell
type c:\ipconfig.txt

Ethernet adapter vEthernet (Virtual Switch-94a3e12ad262b3059e08edc4d48fca3c8390e38c3b219023d4a0a4951883e658-0):

   Connection-specific DNS Suffix  . : 
   Link-local IPv6 Address . . . . . : fe80::cc1f:742:4126:9530%18
   IPv4 Address. . . . . . . . . . . : 172.16.0.2
   Subnet Mask . . . . . . . . . . . : 255.240.0.0
   Default Gateway . . . . . . . . . : 172.16.0.1
```

コンテナーを変更すると、これでは、バックアップを作成するコンテナーのホストのコンソール セッションに配置するコンソール セッションを停止するのには、次を実行します。

``` PowerShell
exit
```

最後に、コンテナーのコンテナーの一覧を表示するホストを使用して、 `docker ps – a` コマンド。
コンテナーが 'dockerdemo' という名前の出力からの通知が作成されました。

``` PowerShell
docker ps -a

CONTAINER ID        IMAGE               COMMAND        CREATED             STATUS                     PORTS     NAMES
4f496dbb8048        windowsservercore   "cmd"          2 minutes ago       Exited (0) 2 minutes ago             dockerdemo
```

###手順 2 - 新しいコンテナーのイメージを作成します。

このコンテナーから、イメージを行うようになりましたことができます。
このイメージは、コンテナーのスナップショットのように動作し、再展開できます何度もします。

次のコマンド実行の新しいイメージを作成します。
このコマンドは、'newcontainerimage'、'deckerdemo' コンテナーに加えられたすべての変更に含まれるという名前の新しいイメージを作成するには、Docker エンジンに指示します。

``` PowerShell
docker commit dockerdemo newcontainerimage
```

を、ホスト上のすべてのイメージを表示する次のように実行します。 `docker イメージ`です。
'Newcontainerimage' という名前の新しいイメージが作成されたことに注意してください。

``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
newcontainerimage   latest              4f8ebcf0a334        2 minutes ago       9.613 GB
windowsservercore   latest              9eca9231f4d4        30 hours ago        9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        30 hours ago        9.613 GB
```

###ステップ 3 - イメージから新しいコンテナーを作成します。

コンテナーのカスタム イメージがある場合は、これでは、'newcontainerimage' から '新しい' がコンテナーをという名前の新しいコンテナーを展開し、コンテナーに、対話型シェル セッションを開きます。

``` PowerShell
docker run –it --name newcontainer newcontainerimage cmd
```

この新しいコンテナーの c:\ ドライブを見てし、ipconfig.txt ファイルが存在することを確認します。

![](media/docker3.png)

コンテナーのホスト コンソール セッションに戻るには、新しく作成されたコンテナーを終了します。

``` PowerShell
exit
```

ここでは、変更されたコンテナーから取得したイメージのすべての変更が含まれる説明しました。
次の例では、単純なファイルの変更でしたが、web サーバーなどのコンテナー内にソフトウェアをインストールした場合は、同じ適用されます。
これらのメソッドを使用して、カスタム イメージを作成できますが、アプリケーションの準備完了のコンテナーを展開します。

###手順 4.-コンテナーを削除して、イメージ

不要になった後に、コンテナーを削除するを使用するために必要な `docker rm` コマンド。
次のコマンドでは、コンテナー名 '新しいコンテナー' が削除されます。

``` PowerShell
docker rm newcontainer
```
不要になったときに、コンテナーのイメージを削除するを使用するために必要な `docker rmi` コマンド。
既存のコンテナーによって参照されている場合は、イメージを削除することはできません。

次のコマンドでは、'newcontainerimage' という名前のコンテナーのイメージを削除します。
``` PowerShell
docker rmi newcontainerimage

Untagged: newcontainerimage:latest
Deleted: 4f8ebcf0a334601e75070a92294d993b0f182abb6f4c88740c75b05093e6acff
```

##コンテナー内の Web サーバーをホストします。

次の例では、Windows Server のコンテナーのより実用的な使用例を示します。
この演習では含まれている手順で Windows Server のコンテナー内でホストされる web アプリケーションを展開するために使用できる web サーバー コンテナーのイメージを作成する手順を説明します。

###ステップ 1 - Web サーバーのソフトウェアのダウンロード

Web コンテナーのイメージを作成する前に、サーバー ソフトウェアは、ダウンロードして、コンテナーのホストで事前設定する必要があります。
私たちに使用する、nginx この例については、Windows ソフトウェア。
**注** この手順で、インターネットに接続するコンテナーのホストを要求することです。
この手順を生成した場合、接続、または名前の解決エラーは、コンテナーのホストのネットワーク構成を確認します。

この例で使用されるディレクトリ構造を作成するコンテナーのホスト上には、次のコマンドを実行します。

``` PowerShell
mkdir c:\build\nginx\source
```

'C:\nginx-1.9.3.zip' nginx のソフトウェアをダウンロードするコンテナーのホスト上には、このコマンドを実行します。

``` PowerShell
wget -uri 'http://nginx.org/download/nginx-1.9.3.zip' -OutFile "c:\nginx-1.9.3.zip"
```

最後に、次のコマンドでは、'C:\build\nginx\source' nginx ソフトウェアが抽出されます。


``` PowerShell
Expand-Archive -Path C:\nginx-1.9.3.zip -DestinationPath C:\build\nginx\source -Force
```

###手順 2 - Web サーバーのイメージを作成します。

前の例では、手動で作成、更新し、コンテナーのイメージをキャプチャします。
この例では、Dockerfile を使用して、コンテナーのイメージを作成するための自動方法を示します。
Dockerfiles では、Docker エンジンを使用して作成および変更のコンテナーであり、する指示を含むし、コンテナーをコンテナーのイメージにコミットします。
Dockerfiles の詳細については、次を参照してください。 [Dockerfile 参照](https://docs.docker.com/reference/builder/)です。

次のコマンドを使用すると、空の dockerfile を作成できます。

``` PowerShell
new-item -Type File c:\build\nginx\dockerfile
```
メモ帳で、dockerfile を開きます。

```
notepad.exe c:\build\nginx\dockerfile
```

コピーし、次のテキストをメモ帳を閉じる、ファイルの保存、メモ帳に貼り付けます。

``` PowerShell
FROM windowsservercore
LABEL Description="nginx For Windows" Vendor="nginx" Version="1.9.3"
ADD source /nginx
```

この時点で、dockerfile は 'c:\build\nginx' および 'c:\build\nginx\source' に抽出 nginx ソフトウェアになります。
Dockerfile の指示に基づく web サーバー コンテナーのイメージを作成する準備が整いました。
これを行うには、コンテナーのホスト上、次のコマンドを実行します。

``` PowerShell
docker build -t nginx_windows C:\build\nginx
```
このコマンドが、docker のエンジンにある dockerfile を使用するように指示 `C:\build\nginx` 'nginx_windows' という名前のイメージを作成します。

出力は、次のようになります。

![](media/docker1.png)

完了したらを見て、イメージを使用して、ホスト上、 `docker イメージ` コマンド。
'Nginx_windows' という名前の新しいイメージを表示する必要があります。
``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE

nginx_windows       latest              d792268338d0        5 seconds ago       9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        35 hours ago        9.613 GB
windowsservercore   latest              9eca9231f4d4        35 hours ago        9.613 GB
```

###ステップ 3: コンテナー アプリケーションのネットワークを構成します。

コンテナー内の web サイトをホストするため、いくつかのネットワーク関連にする必要性を構成しています。
最初のファイアウォール ルールでは、web サイトにアクセスを許可するコンテナーのホストで作成する必要があります。
この例ではアクセスするサイト ポート 80 を使用します。
このファイアウォール規則を作成するのには、次のスクリプトを実行します。
このスクリプトは、VM にコピーすることができます。


``` powershell
if (!(Get-NetFirewallRule | where {$_.Name -eq "TCP80"})) {
    New-NetFirewallRule -Name "TCP80" -DisplayName "HTTP on TCP/80" -Protocol tcp -LocalPort 80 -Action Allow -Enabled True
}
```

次に Azure から作業しているし、仮想マシンのエンドポイントにまだ作成していない場合には、ここで作成する必要があります。
Azure VM のエンドポイントの詳細については、この記事を参照してください。 [Azure VM のエンドポイントのセットアップ](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-set-up-endpoints/)です。

###手順 4 - Web サーバーの準備完了のコンテナーを展開します。

'Nginx_windows' に基づく Windows Server のコンテナーを展開するのには、コンテナーは、次のコマンドを実行します。
'Nginxcontainer' という名前の新しいコンテナーを作成、コンテナーでコンソール セッションを開始します。
このコマンドの – p 80:80 部分では、コンテナーのポート 80 へのホスト上のポート 80 の間のポート マッピングを作成します。


``` powershell
docker run -it --name nginxcontainer -p 80:80 nginx_windows cmd
```
コンテナーの内部正常に機能して、nginx web サーバーを開始し、web コンテンツのステージングします。
Nginx web サーバーを起動するには、nginx のインストール ディレクトリに変更します。

``` powershell
cd c:\nginx\nginx-1.9.3
```

Nginx の web サーバーを起動します。
``` powershell
start nginx
```
###ステップ 5: コンテナーのホストされる web サイトにアクセス

により作成された、web サーバー コンテナーでは、これで、コンテナーでホストされるアプリケーションは、チェック アウトすることができます。
これを行うには、別のコンピューターでのブラウザーを開きを入力 `http://containerhost-ipaddress`です。
ここではするが、コンテナーのホストとコンテナー自体の IP アドレスを参照することに注意してください。
作業している場合は、Azure の仮想マシンからこのなります、パブリック IP アドレスまたはクラウド サービスの名前。


すべて正しく構成されている場合は、nginx の開始ページが表示されます。

![](media/nginx.png)

この時点では、自由に、web サイトを更新します。
独自のサンプルの web サイトにコピーまたはに nginx の開始ページを"Hello World"web ページに置き換えて、コンテナー内の次のコマンドを実行します。

```powershell
powershell wget -uri 'https://raw.githubusercontent.com/Microsoft/Virtualization-Documentation/master/doc-site/virtualization/windowscontainers/quick_start/SampleFiles/index.html' -OutFile "C:\nginx\nginx-1.9.3\html\index.html"
```

Web サイトが更新された後の移動に `http://containerhost-ipaddress`です。

![](media/hello.png)

> **注:** Docker デーモンの設定 (がリッスンするポートを変更するか、コンテナーにリモート接続するなど) を変更するし、コンテナーにファイル"C:\ProgramData\docker\runDockerDaemon.cmd"を編集する必要がありますし、PowerShell を使用したサービスを再起動する必要が、次のようを使用して `サービスを再開 docker`です。

##ビデオ チュートリアル

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Deploying-and-Managing-Windows-Server-Containers-with-Docker/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

##次の手順

コンテナーを設定し、ツールの概要がある場合は、これでは、コンテナー化、独自のアプリの構築を参照してください。

ただし、これは、 **プレビュー** バグがあるし、多数の進行中の作業があります。
[このページ](../about/work_in_progress.md) 、既知の問題の多くが含まれています。

いくつかの既知の Docker コマンドことに注意 [が機能しない](../about/work_in_progress.md#DockermanagementDockercommandsthatdontworkwithWindowsServerContainers) といくつかのみ [部分的に作業](../about/work_in_progress.md#DockermanagementDockercommandsthatpartiallyworkwithWindowsServerContainers)

また監視、 [フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers) 非常に密接にします。

上に作成済みのサンプルも [GitHub](https://github.com/Microsoft/Virtualization-Documentation/tree/master/windows-server-container-samples)です。

-----------------------------------

[コンテナーのホームに戻る](../containers_welcome.md) 
[現在のリリースに関する既知の問題](../about/work_in_progress.md)



