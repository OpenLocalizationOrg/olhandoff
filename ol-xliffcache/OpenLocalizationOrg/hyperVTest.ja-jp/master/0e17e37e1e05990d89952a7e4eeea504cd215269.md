ms。ContentId: A6DD6776-614C-4D28-9B83-CB2EDFD263A3
タイトル: 手順 2: インストール HYPER-V の Windows 10

#手順 2: 10 の Windows での HYPER-V のインストールします。

Windows 10 での仮想マシンを使用してを開始する前に、HYPER-V の役割を有効にする必要があります。
これを行う Windows 10 グラフィカル ユーザー インターフェイスが表示され、PowerShell または DISM を使用します。
このドキュメントはこれらの方法を説明します。

##GUI で HYPER-V を有効にします。

1. Windows ボタンを右クリックし、[プログラムと機能] を選択します。
    
2. '[Windows の機能を切り替えます' を選択します。
    
3. 'HYPER-V' を選択し、[OK] をクリックします。
    <br />![](media/enable_role_upd.png)
    
4. インストールが完了したときに、コンピューターを再起動するように求められます。
    <br />![](media/restart_upd.png)

##PowerShell を使用した HYPER-V を有効にします。

1. 管理者として PowerShell コンソールを開きます。
    
2. 次のコマンドを入力します。

`Enable-windowsoptionalfeature-オンライン機能名 Microsoft-HYPER-V-すべて`

インストールが完了すると、コンピューターを再起動する必要があります。

##DISM を使用した HYPER-V を有効にします。

Deployment Image Servicing and Management ツールまたは DISM を Windows イメージをサービスし、Windows の以前のインストール環境を準備するために使用するとします。
DISM は、OS のインスタンスを実行している Windows の機能を有効にすることもできます。

DISM を使用して、HYPER-V ロールを有効にします。

1. 管理者として PowerShell または CMD セッションを開きます。
    
2. 次のコマンドを入力します。

`DISM/online を有効にする機能/All/FeatureName:Microsoft-ハイパー-V`

スキャンが完了したらを再起動するように求められます。

![](media/dism_upd.png)


##次の手順

[手順 3: 仮想スイッチを作成します。](walkthrough_virtual_switch.md)




