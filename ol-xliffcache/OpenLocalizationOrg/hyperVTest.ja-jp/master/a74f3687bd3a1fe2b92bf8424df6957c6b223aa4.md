ms。ContentId: 7dcd6da0-dd72-422d-8752-5eccc8116e02
タイトル: リモートの HYPER-V ホストを管理します。

#Hyper V マネージャーをリモートの HYPER-V ホストを管理します。

HYPER-V マネージャーでは、診断、および、ローカルの HYPER-V ホストとリモート ホストの数が少ないを管理するためのツールを提供します。
この記事では、サポートされているすべての構成で HYPER-V Manager を使用する HYPER-V ホストに接続するための構成手順を説明します。

HYPER-V Manager での HYPER-V ホストに接続するには、ことを確認してください **HYPER-V Manager** 左側のペインで選択し、[ **... のサーバーへの接続** 右側のペインにします。

![](media/HyperVManager-ConnectToHost.png)

##HYPER-V マネージャーでサポートされている HYPER-V ホストの組み合わせ

Windows の 10 の HYPER-V マネージャーでは管理を行うことができます。
* Windows 10
* Windows 8.1 と Windows Server 2012 R2 HYPER-V ホスト
* Windows 8 および Windows 2012 HYPER-V ホスト

Windows 8.1 と Windows Server 2012 R2 で Hyper-v マネージャーでは管理を行うことができます。
* Windows 8.1 と Windows Server 2012 R2 HYPER-V ホスト
* Windows 8 および Windows 2012 HYPER-V ホスト

> **注:** ホストのすべてのバージョンのすべての HYPER-V マネージャーの機能が動作します。

##ローカル ホストを管理します。

HYPER-V ホストとして、HYPER-V マネージャーには、localhost を追加するには、選択 **ローカル コンピューター** で、 **コンピューターの選択** ] ダイアログ ボックス。

![](media/HyperVManager-ConnectToLocalHost.png)

接続を確立することはできません。 場合
*  HYPER-V サーバーの役割が有効になっていることを確認します。
    参照してください、 [の互換性をチェックするためのチュートリアル セクション](../quick_start/walkthrough_compatibility.md)です。
*  自分のユーザー アカウントが、HYPER-V の管理者グループの一部であることを確認します。


##ドメイン内の HYPER-V ホストを管理します。

HYPER-V マネージャーをリモートの HYPER-V ホストを追加するには、次のように選択します。 **別のコンピューター** で、 **コンピューターの選択** ] ダイアログ ボックスと、テキスト フィールドに、リモート ホストのホスト名、NetBIOS、または FQDN を入力します。

![](media/HyperVManager-ConnectToRemoteHost.png)

Windows 10 では、リモート接続の種類の有効な組み合わせが大幅に拡張されています。
これで、リモートの Windows 10 またはホスト名または IP アドレスのいずれかを使用して、後のホストに接続できます。
HYPER-V マネージャーでは、代替の資格情報もできるようになりました。



リモートの HYPER-V ホストを管理するためには両方のコンピューターでリモート管理を有効にする必要があります。

これを行うことができます `システムのプロパティには、リモート管理設定が]-> [` 、管理者として、次の PowerShell コマンドを実行しています。



``` PowerShell
winrm quickconfig
```

現在のユーザー アカウントには、リモート ホスト上の HYPER-V 管理者アカウントが一致すると、クリックしてください **[ok]** に接続します。



これは、Windows 8 または Windows 8.1 での HYPER-V Manager でのリモートのホストを管理するサポートされている唯一の方法です。


###別のユーザーとして、リモート ホストへの接続します。

Windows 10 では、リモート ホストの場合、適切なユーザー アカウントで実行されていない場合は、代替の資格情報を持つ別のユーザーとして接続できます。

をリモートの HYPER-V ホストの資格情報を指定する次のように選択します。 **別のユーザーとして接続します。 * * で、* * コンピューターの選択** ] ダイアログ ボックス、[選択 **ユーザーの設定]**です。

![](media/HyperVManager-ConnectToRemoteHostAltCreds.png)

> 注: これは非常に簡単にユーザーを設定して、ユーザーが指定されていないと、[ok] をクリックすることを忘れないでです。
> 接続に失敗した場合は、実際には、ユーザーが設定でしたを確認します。

###IP アドレスを使用して、リモート ホストへの接続します。

IP アドレスではなくホスト名を使用して接続を簡単に場合があります。
Windows の 10 の使用と、そのためにします。

IP アドレスを使用して接続するに IP アドレスを入力、 **別のコンピューター** テキスト フィールドです。


##ドメインの外部 (またはドメインがありません) は、HYPER-V ホストを管理します。

ローカルの HYPER-V ホスト:
1.  Enable-PSRemoting
    Netowork がパブリックに設定に戻ります。
    実行
    セット NetConnectionProfile-名前の"name"- NetworkCategory プライベート
2. Set-item WSMan:\localhost\Client\TrustedHosts * の強制
3. Enable-wsmancredssp-ロール クライアント - DelegateComputer *

ワークグループの場合のみ。
1. (実行する必要があります)。コンピューター Policy\Administrative システム \ Delegation\Allow を委任する新しい資格情報の → が有効に設定し、WSMAN の追加/*] です。
    コンピューターの一覧は、チェック ボックス forConcatenate OS の既定値と上記の入力
    
2. コンピューター Policy\Administrative システム \ Delegation\Allow 委任することで新しい資格情報 NTLM のみのサーバー認証 → が有効に設定し、WSMAN を追加/* コンピューターの一覧は、チェック ボックスをオンと上記の入力の連結の OS の既定値について
3. コンピューター Policy\Administrative 用テンプレート \windows コンポーネント \windows Remote Management (WinRM) \WinRM Client\Allow CredSSP 認証 → の設定を有効になっています。

リモートの HYPER-V ホスト:
1. :)、ファイアウォールを無効になっています
2. Enable-PSRemoting
3. Set-item WSMan:\localhost\Client\TrustedHosts * の強制
    これを使用してデモ専用の命令です。
    置き換える * 1 台のコンピューターでファイアウォールを無効にして、credssp と winRM を使用できるようにすること






