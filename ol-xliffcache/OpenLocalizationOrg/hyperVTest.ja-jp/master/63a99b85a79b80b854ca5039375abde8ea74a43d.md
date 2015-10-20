ms。ContentId: 1ab7bfe1-da35-4ff1-916f-936fedf536a0
タイトル: Azure で Windows コンテナーのセットアップ

#テストPreparing Microsoft Azure for Windows Server Containersテスト終わり

テストThis is a test edit!!!テスト終わり
作成と Azure での Windows Server のコンテナーを管理する前に、Windows Server のコンテナーの機能が、あらかじめ設定されている Windows Server 2016 に関するテクニカル プレビュー イメージを展開する必要があります。
このガイドでは、このプロセスを説明します。

> その他のファースト ステップ ガイド。
* テストRun Windows Server Containers in [a new Hyper-V virtual machine](./container_setup.md).テスト終わり
* テストRun Windows Server Containers in [an existing virtual machine](./inplace_setup.md)テスト終わり
* テストSetup Windows Server Containers [on a physical Windows Server Core installation](./inplace_setup.md)テスト終わり

##Azure ポータルの使用を開始します。

テストIf you have an Azure account, skip straight to [Create a Container Host VM](#CreateacontainerhostVM).テスト終わり

1. テストGo to [azure.com](https://azure.com) and follow the steps for an [Azure Free Trial](https://azure.microsoft.com/en-us/pricing/free-trial/).テスト終わり
2. Microsoft アカウントでサインインします。
3. テストWhen your account is ready to go, sign into the [Azure Management Portal](https://portal.azure.com).テスト終わり

##コンテナーのホスト仮想マシンを作成します。

テストClick on the following link to start the VM creation process – [New Windows Server Container Host in Azure](https://portal.azure.com/#gallery/Microsoft.WindowsServer2016TechnicalPreviewwithContainers).テスト終わり


Azure のギャラリーのイメージを検索することもできます。

テストClick on the `create` button.テスト終わり

テスト![](./media/newazure1.png)テスト終わり

により、仮想マシンの名前は、ユーザー名とパスワードを選択します。

テスト![](media/newazure2.png)テスト終わり

オプションの構成の選択 > エンドポイント > 以下に示すように、プライベートおよびパブリック ポートは 80 の HTTP エンドポイントを入力します。
ときに完了した] をクリックには、2 回が [ok] です。

テスト![](./media/newazure3.png)テスト終わり

テストSelect the `create` button to start the Virtual Machine deployment process.テスト終わり

テスト![](media/newazure2.png)テスト終わり

VM の展開が完了すると、Windows Server のコンテナーのホストで RDP セッションを開始する [接続] ボタンを選択します。

テスト![](media/newazure6.png)テスト終わり

ユーザー名と、VM の作成ウィザードの中に指定されたパスワードを使用して VM にログインします。
Windows のコマンド プロンプトで、そのでする検索は 1 回ログに記録します。

テスト![](media/newazure7.png)テスト終わり


##ビデオ チュートリアル

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Configure-Windows-Server-Containers-in-Microsoft-Azure/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##次の手順 - は、コンテナーの使用を開始します。

Windows Server のコンテナーの機能を実行しているシステムがイメージを Windows のサーバーのコンテナーおよび Windows Server のコンテナーを作業を開始する、次のガイドにジャンプ、Windows Server 2016 をしたとします。


テスト[Quick Start: Windows Server Containers and Docker](./manage_docker.md)  
[Quick Start: Windows Server Containers and PowerShell](./manage_powershell.md)テスト終わり


-------------------

テスト
[Back to Container Home](../containers_welcome.md)  
[Known Issues for Current Release](../about/work_in_progress.md)テスト終わり




