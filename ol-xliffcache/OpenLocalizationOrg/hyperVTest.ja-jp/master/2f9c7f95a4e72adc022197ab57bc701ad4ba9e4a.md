ms.ContentId: d0a07897-5fd2-41a5-856d-dc8b499c6783
タイトル: PowerShell を使用した Windows Server のコンテナーの管理

#クイック スタート: Windows Server のコンテナーと PowerShell

この記事は、PowerShell を使用した Windows Server のコンテナーの管理の基礎について説明します。
Windows Server のコンテナーとサーバーのコンテナーの Windows イメージを作成する、Windows Server のコンテナーおよびコンテナーのイメージの削除、および最後に、アプリケーションを Windows Server のコンテナーに展開する対象となるアイテムが含まれます。
このチュートリアルで得られた教訓では、PowerShell を使用して Windows Server のコンテナーの展開と管理の調査を開始するを有効にする必要があります。

ご質問があるでしょうか。
依頼、 [Windows コンテナー フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers)です。

> **注:** PowerShell で作成された Windows Server のコンテナーいない現在使用して管理できる Docker および visa 逆の場合。
> 代わりに、Docker とコンテナーを作成するを参照してください。 [クイック スタート: Windows Server のコンテナーと Docker](./manage_docker.md)です。
> <br /><br /> 詳細を知りたい場合 [faq](../about/faq.md#WhydoIhavetopickbetweenDockerandPowerShellforWindowsServerContainermanagement)です。

##前提条件

このチュートリアルを完了するのには、次の項目を適所に配置する必要があります。

- Windows Server 2016 TP3 か、後で、Windows Server のコンテナーの機能を構成します。
    セットアップ ガイドを完了したら、これが Azure または HYPER-V で作成された VM です。
- このシステムは、ネットワークに接続されていると、インターネットにアクセスすることである必要があります。

コンテナーの機能を構成する必要がある場合は、次のガイドを参照してください: [Azure でのコンテナー セットアップ](./azure_setup.md) または [HYPER-V でのコンテナーのセットアップ](./container_setup.md)です。


##PowerShell を使用した基本的なコンテナーの管理

この最初の例は、作成および Windows Server のコンテナーと PowerShell での Windows サーバー コンテナーのイメージを削除するための基本事項について説明します。

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

使用して `Get-command` コンテナー モジュールで利用可能なコマンドを表示するには

```
PS C:\> Get-Command -Module containers

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Install-ContainerOSImage                           1.0.0.0    Containers
Function        Uninstall-ContainerOSImage                         1.0.0.0    Containers
Cmdlet          Add-ContainerNetworkAdapter                        1.0.0.0    Containers
Cmdlet          Connect-ContainerNetworkAdapter                    1.0.0.0    Containers
Cmdlet          Disconnect-ContainerNetworkAdapter                 1.0.0.0    Containers
Cmdlet          Export-ContainerImage                              1.0.0.0    Containers
Cmdlet          Get-Container                                      1.0.0.0    Containers
Cmdlet          Get-ContainerHost                                  1.0.0.0    Containers
Cmdlet          Get-ContainerImage                                 1.0.0.0    Containers
Cmdlet          Get-ContainerNetworkAdapter                        1.0.0.0    Containers
Cmdlet          Import-ContainerImage                              1.0.0.0    Containers
Cmdlet          Move-ContainerImageRepository                      1.0.0.0    Containers
Cmdlet          New-Container                                      1.0.0.0    Containers
Cmdlet          New-ContainerImage                                 1.0.0.0    Containers
Cmdlet          Remove-Container                                   1.0.0.0    Containers
Cmdlet          Remove-ContainerImage                              1.0.0.0    Containers
Cmdlet          Remove-ContainerNetworkAdapter                     1.0.0.0    Containers
Cmdlet          Set-ContainerNetworkAdapter                        1.0.0.0    Containers
Cmdlet          Start-Container                                    1.0.0.0    Containers
Cmdlet          Stop-Container                                     1.0.0.0    Containers
Cmdlet          Test-ContainerImage                                1.0.0.0    Containers
```


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

Windows Server のコンテナーを作成する前に、コンテナーのイメージの名前と、新しいコンテナーに追加される仮想スイッチの名前を必要があります。

使用して、 `Get ContainerImage` 、ホスト上にコンテナーのイメージの一覧を返すコマンドが読み込まれます。
コンテナーの作成に使用するイメージの名前を書き留めます。
``` PowerShell
Get-ContainerImage

Name              Publisher    Version      IsOSImage
----              ---------    -------      ---------
WindowsServerCore CN=Microsoft 10.0.10514.0 True
```

使用して、 `Get-vmswitch` コマンドをホスト上の使用可能なスイッチの一覧を返します。
コンテナーで使用されるスイッチの名前を書き留めます。

``` PowerShell
Get-VMSwitch

Name           SwitchType NetAdapterInterfaceDescription
----           ---------- ------------------------------
Virtual Switch NAT
```

コンテナーを作成するには、次のコマンドを実行します。
実行しているときに `新規コンテナー` をコンテナーの名前、コンテナーのイメージを指定して、コンテナーで使用するネットワーク スイッチを選択します。
$Container の変数に出力を配置するこの例に注意してください。
この演習の後半に便利になります。


``` PowerShell
$container = New-Container -Name "MyContainer" -ContainerImageName WindowsServerCore -SwitchName "Virtual Switch"
```

ホスト上のコンテナーの一覧を参照してください。 または、コンテナーが作成されたことを確認を使用、 `Get コンテナー` コマンド。
ただし、開始されていない、MyContainer の名前を持つコンテナーが作成されたことに注意してください。

``` PowerShell
Get-Container

Name        State Uptime   ParentImageName
----        ----- ------   ---------------
MyContainer Off   00:00:00 WindowsServerCore
```

コンテナーを開始するには、次のように使用します。 `開始コンテナー` proivding コンテナーの名前。

``` PowerShell
Start-Container -Name "MyContainer"
```

PowerShell リモート処理コマンドを使用するコンテナーと対話できます `Invoke-command`, 、または `Enter-pssession`です。
次の例では、リモート PowerShell セッションを作成、コンテナーを使用して、 `Enter-pssession` コマンド。
このコマンドでは、リモート セッションを作成するのには、コンテナーの id が必要があります。
コンテナー id が格納されていた、 `$container` 変数は、コンテナーの作成時にします。


リモート セッションを作成した後は、コマンド プロンプトはコンテナー id の最初の 11 文字が含まれる変更に注意してください。 `[2446380e 629]`です。

``` PowerShell
Enter-PSSession -ContainerId $container.ContainerId -RunAsAdministrator

[2446380e-629]: PS C:\Windows\system32>
```

コンテナーは、物理マシンまたはバーチャル マシンのように非常によく管理できます。
などのコマンド `ipconfig` コンテナー内の IP アドレスを返す `mkdir` コンテナーとのように、PowerShell コマンドでディレクトリを作成する `Get-childitem` すべての作業です。
ファイルまたはフォルダーの作成などのコンテナーを変更してください。
たとえば、次のコマンドでは、コンテナーに関するネットワーク構成データを格納するファイルが作成されます。

``` PowerShell
ipconfig > c:\ipconfig.txt
```

コマンドを正常に完了したことを確認するファイルの内容を読み取ることができます。
テキスト ファイルに含まれている IP アドレスが、コンテナーのと一致することに注意してください。

``` PowerShell
type c:\ipconfig.txt

Ethernet adapter vEthernet (Virtual Switch-E0D87408-325B-4818-ADB2-2EC7A2005739-0):

   Connection-specific DNS Suffix  . : corp.microsoft.com
   Link-local IPv6 Address . . . . . : fe80::400e:1e0e:591c:beef%18
   IPv4 Address. . . . . . . . . . . : 172.16.0.2
   Subnet Mask . . . . . . . . . . . : 255.240.0.0
   Default Gateway . . . . . . . . . : 172.16.0.1
```

これで、コンテナーが変更されている、リモートの PowerShell セッションを終了します。

``` PowerShell
exit
```

コンテナー名を提供することで、コンテナーを停止、 `停止コンテナー` コマンド。
このコマンドが完了したら、コンテナーのホストの管理にチェックインされます。

``` PowerShell
Stop-Container -Name "MyContainer"
```

###手順 2 - 新しいコンテナーのイメージを作成します。

このコンテナーから、イメージを行うようになりましたことができます。
このイメージは、コンテナーのスナップショットのように動作し、再展開できます何度もします。

名前付き 'newimage' を使用する新しいイメージを作成する、 `新規 ContainerImage` コマンド。
このコマンドを使用する場合は、新しいイメージは、次に見られるよう追加メタデータの名前をキャプチャするコンテナーを指定します。

``` PowerShell
$newimage = New-ContainerImage -ContainerName MyContainer -Publisher Demo -Name newimage -Version 1.0
```

使用して `Get ContainerImage` コンテナーのイメージの一覧を返します。
'Newimage' という名前の新しいイメージが作成されたことに注意してください。

``` PowerShell
Get-ContainerImage

Name              Publisher    Version      IsOSImage
----              ---------    -------      ---------
newimage          CN=Demo      1.0.0.0      False
WindowsServerCore CN=Microsoft 10.0.10254.0 True
```

###ステップ 3 - イメージから新しいコンテナーを作成します。

コンテナーのカスタマイズされたイメージを作成したら、これでは、このイメージから新しいコンテナーを展開してください。

'新しいコンテナー' 'newimage' という名前のコンテナーのイメージからをという名前のコンテナーを作成、'$newcontainer' という名前の変数に結果を出力します。

``` PowerShell
$newcontainer = New-Container -Name "newcontainer" -ContainerImageName newimage -SwitchName "Virtual Switch"
```

新しいコンテナーを開始します。
``` PowerShell
Start-Container $newcontainer
```

により、コンテナーには、PowerShell のリモート セッションを作成します。
``` PowerShell
Enter-PSSession -ContainerId $newcontainer.ContainerId -RunAsAdministrator
```

最後にこの新しいコンテナーに、この演習で前に作成 ipconfig.txt ファイルが含まれていることを確認します。

``` PowerShell
type c:\ipconfig.txt

Ethernet adapter vEthernet (Virtual Switch-E0D87408-325B-4818-ADB2-2EC7A2005739-0):

   Connection-specific DNS Suffix  . : corp.microsoft.com
   Link-local IPv6 Address . . . . . : fe80::400e:1e0e:591c:beef%18
   IPv4 Address. . . . . . . . . . . : 172.16.0.2
   Subnet Mask . . . . . . . . . . . : 255.240.0.0
   Default Gateway . . . . . . . . . : 172.16.0.1
```

 完了した時点リモート PowerShell セッションを終了するは、このコンテナーを使用します。

``` PowerShell
exit
```

ここでは、変更されたコンテナーから取得したイメージのすべての変更が含まれる説明しました。
次の例では、単純なファイルの変更でしたが、web サーバーなどのコンテナー内にソフトウェアをインストールした場合は、同じ適用されます。
これらのメソッドを使用して、カスタム イメージを作成できますが、アプリケーションの準備完了のコンテナーを展開します。

###手順 4.-削除のコンテナーおよびコンテナーのイメージ

停止するには、実行中のすべてのコンテナーは、次のコマンドを実行します。
任意のコンテナーは、このコマンドを実行すると、停止状態には、これは、[ok] と、警告が表示されます。

``` PowerShell
Get-Container | Stop-Container
```
すべてのコンテナーを削除するのには、次を実行します。

``` PowerShell
Get-Container | Remove-Container -Force
```
'Newimage' という名前のコンテナーのイメージを削除するには次の手順を実行します。

``` PowerShell
Get-ContainerImage -Name newimage | Remove-ContainerImage -Force
```

##コンテナー内の Web サーバーをホストします。

次の例では、Windows Server のコンテナーのより実用的な使用例を示します。
この演習では含まれている手順で Windows Server のコンテナー内でホストされる web アプリケーションを展開するために使用できる web サーバー コンテナーのイメージを作成する手順を説明します。

###手順 1 – Windows Server コア OS イメージからコンテナーの作成

Web サーバーのコンテナーのイメージを作成するには、まず、展開および Windows Server のコア OS イメージからコンテナーを開始する必要があります。
``` PowerShell
$container = New-Container -Name webbase -ContainerImageName WindowsServerCore -SwitchName "Virtual Switch"
 ```

Start the container.
``` PowerShell
Start-Container $container
```

コンテナーがある場合は、コンテナーとリモート PowerShell セッションを作成します。
``` PowerShell
Enter-PSSession -ContainerId $container.ContainerId -RunAsAdministrator
```

###手順 2 - Web サーバーのソフトウェアのインストール

次の手順では、web サーバーのソフトウェアをインストールします。
この例では、Windows の nginx が使用されます。
自動的にダウンロードして、c:\nginx-1.9.3 nginx ソフトウェアを展開するには、次のコマンドを使用します。
**注** この手順で、インターネットに接続するコンテナーのホストを要求することです。
この手順を生成した場合、接続、または名前の解決エラーは、コンテナーのホストのネットワーク構成を確認します。

Nginx のソフトウェアをダウンロードします。
``` PowerShell
wget -uri 'http://nginx.org/download/nginx-1.9.3.zip' -OutFile "c:\nginx-1.9.3.zip"
```

Nginx のソフトウェアを展開します。
``` PowerShell
Expand-Archive -Path C:\nginx-1.9.3.zip -DestinationPath c:\ -Force
```
これは、nginx ソフトウェアのインストールを完了する必要があることだけです。

リモートの PowerShell セッションを終了します。
``` PowerShell
exit
```

次のコマンドを使用して、コンテナーを停止します。

``` PowerShell
Stop-Container $container
```
###ステップ 3 - Web サーバーのコンテナーからイメージを作成

により、コンテナーを nginx web サーバーのソフトウェアが含まれるように変更すると、このコンテナーからイメージを作成できます。
これを行うには、次のコマンドを実行します。
``` PowerShell
$webserverimage = New-ContainerImage -Container $container -Publisher Demo -Name nginxwindows -Version 1.0
```
完了したら、使用、 `Get ContainerImage` 、イメージが作成されたことを検証するコマンド。

``` PowerShell
Get-ContainerImage

Name              Publisher    Version      IsOSImage
----              ---------    -------      ---------
nginxwindows      CN=Demo      1.0.0.0      False
WindowsServerCore CN=Microsoft 10.0.10254.0 True
```

###手順 4 - Web サーバーの準備完了のコンテナーを展開します。

'Nginxwindows' イメージに基づく Windows Server のコンテナーを展開するには、使用、 `新規コンテナー` PowerShell コマンド。

``` PowerShell
$webservercontainer = New-Container -Name webserver1 -ContainerImageName nginxwindows -SwitchName "Virtual Switch"
```

コンテナーを開始します。
``` PowerShell
Start-Container $webservercontainer
```

新しいコンテナーとリモート PowerShell セッションを作成します。
``` PowerShell
Enter-PSSession -ContainerId $webservercontainer.ContainerId -RunAsAdministrator
```

コンテナーの内部正常に機能して、nginx web サーバーを開始し、web コンテンツのステージングします。
Nginx web サーバーを起動するには、nginx のインストール ディレクトリに変更します。
``` PowerShell
cd c:\nginx-1.9.3\
```

Nginx の web サーバーを起動します。
``` PowerShell
start nginx
```

この PS セッションを終了します。
Web サーバーは引き続き実行されます。
``` PowerShell
exit
```

###ステップ 5 - ネットワークのコンテナーを構成します。

構成によっては、コンテナーのホストとネットワークのコンテナーはか、IP アドレスを受け取る、DHCP サーバーまたはコンテナーのホストからネットワーク アドレス変換 (NAT) を使用してそれ自体です。
このガイド付きひととおりが NAT を使用するように構成
この構成では、コンテナーからのポートは、コンテナーのホスト上のポートにマップされます。
コンテナーでホストされているアプリケーションは、IP アドレスを使用してアクセス/コンテナーのホストの名前。
たとえば、アプリケーションに一般的な http 要求をこの http://contianerhost:55534 のようになりますポート 80、コンテナーからが、コンテナーのホスト上のポート 55534 にマップされていた場合。
これにより、多くのコンテナーを実行し、同じポートを使用して要求に応答するは、これらのコンテナー内のアプリケーションでは、コンテナーのホストできます。


この実習では、このポートのマッピングを作成する必要があります。
実行するのには、コンテナーと内部の (アプリケーション)、および構成される外部 (コンテナーのホスト) ポートの IP アドレスを知っておく必要があります。
この例については、単純さの維持し、ポート、ホストのポート 80 に、コンテナーから 80 をマップしてみましょうします。
使用して、 `追加 NetNatStaticMapping` のコマンドを `– InternalIPAddress` は、このチュートリアルでは '172.16.0.2' にする必要がありますコンテナーの IP アドレスを指定します。

``` PowerShell
Add-NetNatStaticMapping -NatName "ContainerNat" -Protocol TCP -ExternalIPAddress 0.0.0.0 -InternalIPAddress 172.16.0.2 -InternalPort 80 -ExternalPort 80
```
ポートのマッピングが作成されたときに、構成されたポートの受信のファイアウォール規則を構成する必要があります。
そのためにはポート 80 が次のコマンドを実行します。
このスクリプトは、VM にコピーすることができます。


``` PowerShell
if (!(Get-NetFirewallRule | where {$_.Name -eq "TCP80"})) {
    New-NetFirewallRule -Name "TCP80" -DisplayName "HTTP on TCP/80" -Protocol tcp -LocalPort 80 -Action Allow -Enabled True
}
```

次に Azure から作業しているし、仮想マシンのエンドポイントにまだ作成していない場合には、ここで作成する必要があります。
Azure VM のエンドポイントの詳細については、この記事を参照してください。 [Azure VM のエンドポイントのセットアップ](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-set-up-endpoints/)です。

###ステップ 6: コンテナーのホストされる web サイトにアクセス

により作成された、web サーバー コンテナーでは、これで、コンテナーでホストされるアプリケーションは、チェック アウトすることができます。
これを行うには、別のコンピューターでのブラウザーを開きを入力 `http://containerhost-ipaddress`です。
ここではするが、コンテナーのホストとコンテナー自体の IP アドレスを参照することに注意してください。
作業している場合は、Azure の仮想マシンからこのなります、パブリック IP アドレスまたはクラウド サービスの名前。


すべて正しく構成されている場合は、nginx の開始ページが表示されます。

![](media/nginx.png)

この時点では、自由に、web サイトを更新します。
独自のサンプルの web サイトにコピーするか、このデモをまだ作成して単純な"Hello World"サンプル サイトを使用します。
サンプルを使用するには、は、まず、コンテナーと PS のリモート セッションを再確立する必要があります。

まず、コンテナーとは、リモートの PS セッションを再作成する必要があります。
``` PowerShell
Enter-PSSession -ContainerId $webservercontainer.ContainerId -RunAsAdministrator
```
ダウンロードして、index.html ファイルを置換するには、次のコマンドを実行します。

``` powershell
wget -uri 'https://raw.githubusercontent.com/Microsoft/Virtualization-Documentation/master/doc-site/virtualization/windowscontainers/quick_start/SampleFiles/index.html' -OutFile "C:\nginx-1.9.3\html\index.html"
```

Web サイトが更新された後の移動に `http://containerhost-ipaddress`です。

![](media/hello.png)

##ビデオ チュートリアル

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Deploying-and-Managing-Windows-Server-Containers-with-PowerShell/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##次の手順

コンテナーを設定し、ツールの概要がある場合は、これでは、コンテナー化、独自のアプリの構築を参照してください。

ここより詳細な [PowerShell リファレンス](../reference/powershell_overview.md)です。

ただし、これは、 **プレビュー** バグがあるし、多数の進行中の作業があります。
[このページ](../about/work_in_progress.md) 、既知の問題の多くが含まれています。

また監視、 [フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers) 非常に密接にします。

上に作成済みのサンプルも [GitHub](https://github.com/Microsoft/Virtualization-Documentation/tree/master/windows-server-container-samples)です。

-----------------------------------

[コンテナーのホームに戻る](../containers_welcome.md) 
[現在のリリースに関する既知の問題](../about/work_in_progress.md)




