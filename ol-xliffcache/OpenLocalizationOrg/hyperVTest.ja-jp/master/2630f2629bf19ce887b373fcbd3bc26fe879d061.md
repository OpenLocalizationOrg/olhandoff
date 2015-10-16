ms。ContentId: e586a11a-870f-403b-8af8-4c2931589d26
タイトル: Windows PowerShell のダイレクトとの管理


#Windows PowerShell のダイレクトとの管理します。

PowerShell のダイレクトを使用すると、Windows 10 または Windows Server テクニカル プレビュー HYPER-V ホストから 10 の Windows または Windows Server に関するテクニカル プレビューの仮想マシンをリモートで管理します。
PowerShell のダイレクトでは、ネットワークの構成またはいずれかの HYPER-V ホスト上のリモート管理の設定に関係なく、virtual machine または仮想マシン内の PowerShell の管理ができます。
これにより、HYPER-V の管理者を自動化し、仮想マシン管理と構成スクリプトを作成しやすくなります。

直接の PowerShell を実行する 2 つの方法はあります。


* 作成し、PSSession コマンドレットを使用して、直接の PowerShell セッションを終了します。
* Invoke-command コマンドレットにスクリプトまたはコマンドを実行します。

古い仮想マシンを管理している場合は、仮想マシン接続 (VMConnect) を使用してまたは [、仮想マシン用の仮想ネットワークを構成する](http://technet.microsoft.com/library/cc816585.aspx)です。


##作成し、PSSession コマンドレットを使用して、直接の PowerShell セッションを終了します。

1. HYPER-V ホストでは、Windows PowerShell を管理者として開きます。
    
3. バーチャル マシンの名前または GUID を使用してセッションを作成するには、次のコマンドのいずれかを実行します。
    

``` PowerShell
Enter-PSSession -VMName <VMName>
Enter-PSSession -VMGUID <VMGUID>
```

4. 必要がある任意のコマンドを実行します。
    これらのコマンドは、使用してセッションを作成した仮想マシンで実行します。
5. 次のように完了したら、セッションを終了するには、次のコマンドを実行します。
    

``` PowerShell
Exit-PSSession 
```

> 注: セッションの場合はありません接続であることを確認 - HYPER-V ホストではなくに接続する仮想マシンの資格情報を使用しています。

これらのコマンドレットの詳細については、次を参照してください。 [Enter-pssession](http://technet.microsoft.com/library/hh849707.aspx) と [終了 PSSession](http://technet.microsoft.com/library/hh849743.aspx)です。


##Invoke-command コマンドレットにスクリプトまたはコマンドを実行します。

使用することができます、 [Invoke-command](http://technet.microsoft.com/library/hh849719.aspx) 、仮想マシンで事前に決められた一連のコマンドを実行するコマンドレットです。
Invoke-command コマンドレットを使用する方法の例を次に示します PSTest が仮想マシンの名前であり、(foo.ps1) を実行するスクリプトが、スクリプトのフォルダー、c:/ドライブします。

 ``` PowerShell
 Invoke-Command -VMName PSTest -FilePath C:\script\foo.ps1 
 ```

1 つのコマンドを実行するには、使用、 **- ScriptBlock** パラメーター。

 ``` PowerShell
 Invoke-Command -VMName PSTest -ScriptBlock { cmdlet } 
 ```

##PowerShell を使用して何が必要なでしょうか。

バーチャル マシンの場合は、直接の PowerShell セッションを作成するには
* 仮想マシンでは、ホスト上でローカルに実行する必要があり、起動します。
    
* HYPER-V の管理者として、ホスト コンピューターには、ログインする必要があります。
* 仮想マシンの有効なユーザーの資格情報を指定する必要があります。
* ホストのオペレーティング システムには、10 の Windows、Windows サーバーに関するテクニカル プレビュー、または以降のバージョンを実行する必要があります。
    

* 仮想マシンには、10 の Windows、Windows サーバーに関するテクニカル プレビュー、または以降のバージョンを実行する必要があります。
    


使用することができます、 [Get VM](http://technet.microsoft.com/library/hh848479.aspx) コマンドレットを使用している資格情報に、HYPER-V の管理者ロールがあることを確認し、Vm がホストにローカルで実行しているし、起動を確認するためです。

##PowerShell のダイレクトでは、何をことができますか。

参照してください [PowerShell ダイレクト スニペット](../develop/powershell_snippets.md) も環境で PowerShell ダイレクトを使用する方法の例についてはさまざまなとしてに関するヒントし、テクニック PowerShell を使用した HYPER-V のスクリプトを記述します。






