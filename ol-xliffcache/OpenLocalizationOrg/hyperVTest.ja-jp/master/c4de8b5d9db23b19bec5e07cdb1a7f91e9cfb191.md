ms.ContentId: B9414110-BEFD-423F-9AD8-AFD5EE612CDA
タイトル: 手順 8: Windows PowerShell でのテスト

#手順 8: は、Windows PowerShell を使用したテストします。

これで、HYPER-V を展開し、バーチャル マシンの作成および、これらの仮想マシンを管理するための基本事項を確認、PowerShell でこれらのアクティビティの多くを自動化する方法について説明します。

###HYPER-V のコマンドの一覧を返します

1.  Windows の [スタート] ボタンの種類をクリックして **PowerShell**です。
2.  PowerShell コマンドと、HYPER-V の PowerShell モジュールで利用可能な検索可能な一覧を表示するには、次のコマンドを実行します。

 ```powershell
get-command –module hyper-v | out-gridview
```
  You get something like this:

  ![](media\command_grid.png)

3. To learn more about a particular PowerShell command use `get-help`. For instance running the following command will return information about the `get-vm` Hyper-V command.

  ```powershell
get-help get-vm
```
 The output shows you how to structure the command, what the required and optional parameters are, and the aliases that you can use.

 ![](media\get_help.png)


### Return a list of virtual machines

Use the `get-vm` command to return a list of virtual machines.

1. In PowerShell, run the following command:

 ```powershell
get-vm
```
 This displays something like this:

 ![](media\get_vm.png)

2. To return a list of only powered on virtual machines add a filter to the `get-vm` command. A filter can be added by using the where-object command. For more information on filtering see the [Using the Where-Object](https://technet.microsoft.com/en-us/library/ee177028.aspx) documentation.   

 ```powershell
 get-vm | where {$_.State –eq ‘Running’}
 ```
3.  電源のすべての仮想マシンの一覧を表示する、状態を無効には、次のコマンドを実行します。
    このコマンドは、'Running' から 'Off' に変更、フィルターを使用して、手順 2. のコマンドのコピーです。

 ```powershell
 get-vm | where {$_.State –eq ‘Off’}
 ```

###起動し、仮想マシンをシャット ダウン

1. 特定のバーチャル マシンを開始するには、仮想マシンの名前で、次のコマンドを実行します。

 ```powershell
 Start-vm –Name <virtual machine name>
 ```

2. 中のすべての電源を切り、仮想マシンを開始するには、これらのマシンの一覧を取得し、' start vm' コマンドのリストをパイプします。

  ```powershell
 get-vm | where {$_.State –eq ‘Off’} | start-vm
 ```
3. To shut down all running virtual machines, run this:

  ```powershell
 get-vm | where {$_.State –eq ‘Running’} | stop-vm
 ```

### Create a VM checkpoint

To create a checkpoint using PowerShell, select the virtual machine using the `get-vm` command and pipe this to the `checkpoint-vm` command. Finally give the checkpoint a name using `-snapshotname`. The complete command will look like the following:

 ```powershell
 get-vm -Name <VM Name> | checkpoint-vm -snapshotname <name for snapshot>
 ```
For example, here is a checkpoint with the name DEMOCP:

 ![](media\POSH_CP2.png)

### Create a new virtual machine

The following example shows how to create a new virtual machine in the PowerShell Integrated Scripting Environment (ISE). This is a simple example and could be expanded on to include additional PowerShell features and more advanced VM deployments.

1. To open the PowerShell ISE click on start, type **PowerShell ISE**.
2. Run the following code to create a virtual machine. See the [New-VM](https://technet.microsoft.com/en-us/library/hh848537.aspx) documentation for detailed information on the New-VM command.

  ```powershell
 $VMName = "VMNAME"

 $VM = @{
     Name = $VMName 
     MemoryStartupBytes = 2147483648
     Generation = 2
     NewVHDPath = "C:\Virtual Machines\$VMName\$VMName.vhdx"
     NewVHDSizeBytes = 53687091200
     BootDevice = "VHD"
     Path = "C:\Virtual Machines\$VMName "
     SwitchName = (get-vmswitch).Name[0]
 }

 New-VM @VM
  ```

##ラップし、参照

このドキュメントはいくつかのサンプル シナリオと同様に、HYPER-V の PowerShell モジュールに、エクスプ ローラーにいくつかの簡単な手順を説明しました。
PowerShell HYPER-V モジュールの詳細については、次を参照してください。、 [の参照を Windows PowerShell での Hyper-v コマンドレット](https://technet.microsoft.com/%5Clibrary/Hh848559.aspx)です。






