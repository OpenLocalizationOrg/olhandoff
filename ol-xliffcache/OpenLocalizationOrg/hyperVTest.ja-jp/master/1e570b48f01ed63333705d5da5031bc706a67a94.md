ms.ContentId: 8DE9250B-556B-47BC-AD9A-8992B3D3D0F9
タイトル: PowerShell スニペット

#PowerShell のスニペット

ホー HB プロセスをテストするためには、この文を追加します。
PowerShell は、素晴らしいスクリプティング、オートメーション、および管理ツール HYPER-V 用です。ここでは、いくつかのすばらしいものを実行できる検証用のツールボックスです。

すべての HYPER-V 管理では、すべてのスクリプトと管理者とスニペットは、HYPER-V の管理者アカウントから管理者として実行する必要があります、実行が必要です。

適切なアクセス許可があるかどうか不明でない場合は、入力 `Get VM` 移動する準備ができたら、エラーなしで実行している場合があるとします。


##PowerShell の直接のツール

すべてのスクリプトとスニペットでは、このセクションでは、次の基本原則に依頼します。

**要件** :


*  PowerShell のダイレクトします。
    Windows の 10 のゲストとホスト OS です。

**共通変数** :
`$VMName` -VMName での文字列です。
使用可能な Vm の一覧を参照してください `Get VM`。
`$cred` -ゲスト OS の資格情報。
使用して設定できます `$cred = Get-credential`



###ゲストが起動されているかどうかの確認します。

HYPER-V マネージャーでは、多くの場合、ゲスト OS が起動されているかどうかがわかりにくく、ゲスト オペレーティング システムに可視性を提供します。

ゲストが起動されているかどうかを確認するのにには、このコマンドを使用します。

``` PowerShell
if((Invoke-Command -VMName $VMName -Credential $cred {"Test"}) -ne "Test"){Write-Host "Not Booted"} else {Write-Host "Booted"}
```

**結果**
ゲスト OS の状態を宣言するわかりやすいメッセージを出力します。


###スクリプトが、ゲストの起動時までロック

次の関数では、PowerShell まで待機する同じ原則が (つまり、OS が起動して、ほとんどのサービスを実行している)、ゲストで使用可能な使用を待機しを返します。

``` PowerShell
function waitForPSDirect([string]$VMName, $cred){
   Write-Output "[$($VMName)]:: Waiting for PowerShell Direct (using $($cred.username))"
   while ((Invoke-Command -VMName $VMName -Credential $cred {"Test"} -ea SilentlyContinue) -ne "Test") {Sleep -Seconds 1}}
```

**結果**
VM への接続が成功するまでは、わかりやすいメッセージとロックを出力します。
サイレント モードでは成功します。

###スクリプトは、ゲストには、ネットワーク時までロック

PowerShell の直接仮想マシンを前に仮想マシン内の PowerShell セッションに接続することは、IP アドレスを受け取りました。

``` PowerShell
# Wait for DHCP
while ((Get-NetIPAddress | ? AddressFamily -eq IPv4 | ? IPAddress -ne 127.0.0.1).SuffixOrigin -ne "Dhcp") {sleep -Milliseconds 10}
```

** 結果の **
DHCP リースを受信するまでロックされます。
このスクリプトはしない検索、特定のサブネットまたは IP アドレスの場合は、どのようなネットワークの構成に関係なく、機能しています。
サイレント モードでは成功します。

##PowerShell を使用した資格情報の管理

HYPER-V のスクリプトでは、1 つまたは複数の仮想マシン、HYPER-V ホスト、またはその両方の資格情報の処理を頻繁に必要です。

これを実現する PowerShell の直接接続または標準の PowerShell リモート処理を使用するときに複数の方法はあります。

1. 最初の (そして最も単純な) 方法は、ホストとゲスト、またはローカルおよびリモート ホストで有効であるのと同じユーザー資格情報です。
    これはやドメイン環境である場合は、Microsoft アカウントでログインしている場合に非常に簡単です。
    このシナリオでのみ実行できます `Invoke-command VMName の"test"{get プロセス}`です。
    
2. 資格情報を要求する PowerShell を使用します。
    資格情報が一致しない場合は、資格情報プロンプトが、仮想マシンの適切な資格情報を提供することができますを自動的に表示されます。
    
3. 再利用するための変数には、資格情報を格納します。
    次のような単純なコマンドを実行しています。
    

  ``` PowerShell
  $localCred = Get-Credential
   ```
  And then running something like this:
  ``` PowerShell
  Invoke-Command -VMName "test" -Credential $localCred  {get-process} 
  ```
  ことのみが表示されたら、資格情報のスクリプトと PowerShell セッションを意味します。

4. スクリプトに、資格情報をコードです。
    **これを行わないため、実際のワークロードやシステム**
    > 警告: (_d) これを行わない実稼働システムでします。
    > これを実際のパスワードを持つ _。
    
    渡すことができますをいくつかのコードを次のような PSCredential オブジェクトを作成します。
    

  ``` PowerShell
  $localCred = New-Object -typename System.Management.Automation.PSCredential -argumentlist "Administrator", (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) 
  ```
大きな安全でないがテストに役立ちます。
ようになりましたが表示ないこのセッションですべての画面の指示します。






