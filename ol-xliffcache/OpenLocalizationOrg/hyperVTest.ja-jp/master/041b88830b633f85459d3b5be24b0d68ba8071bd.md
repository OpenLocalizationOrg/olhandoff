ms.ContentId: C49DA0E6-2E12-4D51-803A-31B1B5A8F85C
タイトル: PowerShell リファレンス


#コンテナー用 PowerShell

##インストール ContainerOSImage

**名**    
インストール ContainerOSImage

**概要**
Windows Server または HYPER-V のコンテナーで使用するためのコンテナーの OS イメージとして指定した wim ファイルをインストールします。


**構文**


``` PowerShell  
Install-ContainerOSImage [-WimPath] <String> [-Force] [< CommonParameters >]
```

**説明**
Windows Server と HYPER-V のコンテナーの機能のサーバーの全体の共有のイメージ ストアに、WIM ファイルからの基本イメージをインストールします。

**パラメータ**
``` PowerShell
    -WimPath <String>
        A path to the WIM file that will be installed.

        Required?                    true
        Position?                    1
        Default value
        Accept pipeline input?       false
        Accept wildcard characters?  false

    -Force [<SwitchParameter>]

        Required?                    false
        Position?                    named
        Default value                False
        Accept pipeline input?       false
        Accept wildcard characters?  false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**    
None

**出力**
None

**別名**
None

-------------------------- 例 1 --------------------------

``` PowerShell
PS C:\>Install-ContainerOSImage c:\baseimage.wim
```

##アンインストール ContainerOSImage

**名**
アンインストール ContainerOSImage

**概要**
以前にインストールされたコンテナーの OS イメージを削除します。

**構文**
 

```PowerShell
Uninstall-ContainerOSImage [-ImageName] <string> [-Force]  [< CommonParameters >]

Uninstall-ContainerOSImage [-ContainerImage] <Object> [-Force]  [< CommonParameters >]
```

**パラメータ**


``` PowerShell
    -ContainerImage <Object>

        Required?                    true
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           ByContainerImage
        Aliases                      None
        Dynamic?                     false

    -Force

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -ImageName <string>

        Required?                    true
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           ByName
        Aliases                      None
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
None


**出力**
System.Object

**別名**
None

##追加 ContainerNetworkAdapter

**名**
追加 ContainerNetworkAdapter

**概要**
新しいネットワーク アダプタを既存のコンテナーに追加します。

**構文**

``` PowerShell  
Add-ContainerNetworkAdapter [-ContainerName] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-SwitchName <string>] [-Name <string>] [-DynamicMacAddress] [-StaticMacAddress
    <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Add-ContainerNetworkAdapter [-Container] <Container[]> [-SwitchName <string>] [-Name <string>]
    [-DynamicMacAddress] [-StaticMacAddress <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Container <Container[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -ContainerName <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -DynamicMacAddress

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -StaticMacAddress <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -SwitchName <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```


**入力**
System.String\[\]
Microsoft.Containers.PowerShell.Objects.Container\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


**別名**
None

##接続 ContainerNetworkAdapter

**名**
接続 ContainerNetworkAdapter

**概要**
コンテナーのネットワーク アダプターを仮想スイッチに接続します。

**構文**


``` PowerShell
    Connect-ContainerNetworkAdapter [-ContainerName] <string[]> [[-Name] <string[]>] [-SwitchName] <string>
    [-Passthru] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>] [-WhatIf]
    [-Confirm]  [<CommonParameters>]

    Connect-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter[]> [-SwitchName] <string> [-Passthru]
    [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name_SwitchName
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name_SwitchName
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -ContainerName <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Name_SwitchName
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name_SwitchName
        Aliases                      None
        Dynamic?                     false

    -Name <string[]>

        Required?                    false
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           Name_SwitchName
        Aliases                      None
        Dynamic?                     false

    -NetworkAdapter <ContainerNetworkAdapter[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Object_SwitchName
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -SwitchName <string>

        Required?                    true
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           Object_SwitchName, Name_SwitchName
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


**別名**
None

##切断 ContainerNetworkAdapter

**名**
切断 ContainerNetworkAdapter

**概要**
コンテナーのネットワーク アダプターを仮想スイッチから切断します。

**構文**


``` PowerShell
    Disconnect-ContainerNetworkAdapter [-ContainerName] <string[]> [[-Name] <string[]>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Disconnect-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter[]> [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -ContainerName <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Name <string[]>

        Required?                    false
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -NetworkAdapter <ContainerNetworkAdapter[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           ResourceObject
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


**別名**
None

##エクスポート ContainerImage

**名**
エクスポート ContainerImage

**概要**
ローカル ストアからコンテナーのイメージをコピーします。

**構文**


``` PowerShell
    Export-ContainerImage [[-Name] <string>] [-Path] <string> [[-Version] <version>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]

    Export-ContainerImage [-Image] <ContainerImage[]> [-Path] <string> [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

**パラメータ**
``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Image <ContainerImage[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Image Object
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Path <string>

        Required?                    true
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Publisher <string>

        Required?                    false
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Version <version>

        Required?                    false
        Position?                    2
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.ContainerImage\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerImage


**別名**
None

##Get コンテナー

**名**
Get コンテナー

**概要**
現在のシステムでのコンテナーを列挙します。

**構文**


``` PowerShell
    Get-Container [[-Name] <string[]>] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>]  [<CommonParameters>]

    Get-Container [[-Id] <guid>] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Id, Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Id, Name
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name, Id
        Aliases                      None
        Dynamic?                     false

    -Id <guid>

        Required?                    false
        Position?                    0
        Accept pipeline input?       true (ByValue, ByPropertyName)
        Parameter set name           Id
        Aliases                      None
        Dynamic?                     false

    -Name <string[]>

        Required?                    false
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
System.String\[\]
System.Guid


**出力**
Microsoft.Containers.PowerShell.Objects.Container


**別名**
None

##Get ContainerHost

**名**
Get ContainerHost

**概要**
コンテナーのホストのホスト オブジェクトを取得します。

**構文**


``` PowerShell
    Get-ContainerHost [[-ComputerName] <string[]>] [[-Credential] <pscredential[]>]  [<CommonParameters>]

    Get-ContainerHost [-CimSession] <CimSession[]>  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByPropertyName)
        Parameter set name           CimSession
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           ComputerName
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    1
        Accept pipeline input?       true (ByValue)
        Parameter set name           ComputerName
        Aliases                      None
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Management.Infrastructure.CimSession\[\]
System.String\[\]
System.Management.Automation.PSCredential\


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerHost


**別名**
None

##Get ContainerImage

**名**
Get ContainerImage

**概要**
コンテナーのホストでコンテナーのイメージの表示

**構文**


``` PowerShell
Get-ContainerImage [[-Name] <string>] [[-Publisher] <string>] [[-Version] <version>] [-ChildOf <ContainerImage>]
[-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -ChildOf <ContainerImage>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Publisher <string>

        Required?                    false
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Version <version>

        Required?                    false
        Position?                    2
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
None


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerImage


**別名**
None

##Get ContainerNetworkAdapter

**名**
Get ContainerNetworkAdapter

**概要**
コンテナーに関連付けられているネットワーク アダプターを一覧表示

**構文**


``` PowerShell
    Get-ContainerNetworkAdapter [-ContainerName] <string[]> [[-Name] <string>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>]  [<CommonParameters>]

    Get-ContainerNetworkAdapter [-Container] <Container[]> [[-Name] <string>]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Container <Container[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -ContainerName <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.Container\[\]
System.String\[\]




**出力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter




**別名**
None



##インポート ContainerImage

**名**
インポート ContainerImage

**概要**
別のコンピューターからエクスポートされたコンテナーのイメージをインポートします。

**構文**


``` PowerShell
    Import-ContainerImage [-Path] <string> [-AsJob] [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Path <string>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
System.String


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerImage


**別名**
None

##移動 ContainerImageRepository

**名**
移動 ContainerImageRepository

**概要**
コンテナーのイメージを格納する場所を変更します。
ローカル ディスク上の場所にある必要があります。
イメージが、システムに存在しない場合のみ変更されたことができます。

**構文**


``` PowerShell
    Move-ContainerImageRepository [-Path] <string> [-AsJob] [-Passthru] [-CimSession <CimSession[]>] [-ComputerName
    <string[]>] [-Credential <pscredential[]>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Path <string>

        Required?                    true
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
None


**出力**
Microsoft.HyperV.PowerShell.VMHost


**別名**
None

##新しいコンテナー

**名**
新しいコンテナー

**概要**
新しいコンテナーを作成します。

**構文**


``` PowerShell
    New-Container [[-Name] <string>] -ContainerImageName <string> [-ContainerImagePublisher <string>]
    [-ContainerImageVersion <version>] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-MemoryStartupBytes <long>] [-SwitchName <string>] [-Path <string>] [-AsJob] [-WhatIf]
    [-Confirm]  [<CommonParameters>]

    New-Container [[-Name] <string>] -ContainerImage <ContainerImage> [-MemoryStartupBytes <long>] [-SwitchName
    <string>] [-Path <string>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Image Identifiers
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Image Identifiers
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -ContainerImage <ContainerImage>

        Required?                    true
        Position?                    Named
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Image Object
        Aliases                      None
        Dynamic?                     false

    -ContainerImageName <string>

        Required?                    true
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Image Identifiers
        Aliases                      None
        Dynamic?                     false

    -ContainerImagePublisher <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Image Identifiers
        Aliases                      None
        Dynamic?                     false

    -ContainerImageVersion <version>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Image Identifiers
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Image Identifiers
        Aliases                      None
        Dynamic?                     false

    -MemoryStartupBytes <long>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Container Image Identifiers, Container Image Object
        Aliases                      None
        Dynamic?                     false

    -Path <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -SwitchName <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.ContainerImage


**出力**
Microsoft.Containers.PowerShell.Objects.Container


**別名**
None

##ContainerImage で新しい

**名**
ContainerImage で新しい

**概要**
既存のコンテナーからの新しいイメージをコンテナーの作成します。

**構文**


``` PowerShell
    New-ContainerImage [-ContainerName] <string> [-Name] <string> [-Publisher] <string> [-Version] <version>
    [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>] [-WhatIf] [-Confirm]
    [<CommonParameters>]

    New-ContainerImage [-Container] <Container> [-Name] <string> [-Publisher] <string> [-Version] <version> [-WhatIf]
    [-Confirm]  [<CommonParameters>]

    New-ContainerImage [-ContainerId] <guid> [-Name] <string> [-Publisher] <string> [-Version] <version> [-CimSession
    <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Id, Container Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name, Container Id
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Container <Container>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -ContainerId <guid>

        Required?                    true
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Container Id
        Aliases                      None
        Dynamic?                     false

    -ContainerName <string>

        Required?                    true
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name, Container Id
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    true
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Publisher <string>

        Required?                    true
        Position?                    2
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Version <version>

        Required?                    true
        Position?                    3
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.Container


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerImage


**別名**
None

##コンテナーの削除

**名**
コンテナーの削除

**概要**
システムから、既存のコンテナーを削除します。

**構文**


``` PowerShell
    Remove-Container [-Name] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-Force] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Remove-Container [-Container] <Container[]> [-Force] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Container <Container[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Force

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Name <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
System.String\[\]
Microsoft.Containers.PowerShell.Objects.Container\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.Container


**別名**
None

##削除 ContainerImage

**名**
削除 ContainerImage

**概要**
コンテナーのホストからコンテナーのイメージを削除します。

**構文**


``` PowerShell
    Remove-ContainerImage [[-Name] <string>] [[-Publisher] <string>] [[-Version] <version>] [-CimSession
    <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>] [-Force] [-WhatIf] [-Confirm]
    [<CommonParameters>]

    Remove-ContainerImage [-Image] <ContainerImage> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Force

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -Image <ContainerImage>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Image Object
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Publisher <string>

        Required?                    false
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Version <version>

        Required?                    false
        Position?                    2
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.ContainerImage


**出力**
System.Object

**別名**
None

##削除 ContainerNetworkAdapter

**名**
削除 ContainerNetworkAdapter

**概要**
ネットワーク アダプタをコンテナーから削除します。

**構文**


``` PowerShell
    Remove-ContainerNetworkAdapter [-ContainerName] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-Name <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Remove-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter[]> [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]

    Remove-ContainerNetworkAdapter [-Container] <Container[]> [-Name <string>] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Container <Container[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -ContainerName <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name, Container Object
        Aliases                      None
        Dynamic?                     false

    -NetworkAdapter <ContainerNetworkAdapter[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           ResourceObject
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter\[\]
System.String\[\]
Microsoft.Containers.PowerShell.Objects.Container\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


**別名**
None

##セット ContainerNetworkAdapter

**名**
セット ContainerNetworkAdapter

**概要**
コンテナー内のネットワーク アダプターで MAC アドレスを設定します。

**構文**


``` PowerShell
    Set-ContainerNetworkAdapter [-ContainerName] <string> [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-Name <string>] [-DynamicMacAddress] [-StaticMacAddress <string>] [-Passthru]
    [-WhatIf] [-Confirm]  [<CommonParameters>]

    Set-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter> [-DynamicMacAddress] [-StaticMacAddress
    <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Set-ContainerNetworkAdapter [-Container] <Container> [-Name <string>] [-DynamicMacAddress] [-StaticMacAddress
    <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Container <Container>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -ContainerName <string>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Name
        Aliases                      None
        Dynamic?                     false

    -DynamicMacAddress

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           ResourceObject, Container Object, Container Name
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Container Object, Container Name
        Aliases                      None
        Dynamic?                     false

    -NetworkAdapter <ContainerNetworkAdapter>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           ResourceObject
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -StaticMacAddress <string>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           ResourceObject, Container Object, Container Name
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
System.String
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter
Microsoft.Containers.PowerShell.Objects.Container


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


**別名**
None

##複数コンテナーに開始

**名**
複数コンテナーに開始

**概要**
コンテナーを開始します。

**構文**


``` PowerShell
    Start-Container [-Name] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Start-Container [-Container] <Container[]> [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Container <Container[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Name <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.Container\[\]
System.String\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.Container


**別名**
None

##停止コンテナー

**名**
停止コンテナー

**概要**
コンテナーを停止します。

**構文**


``` PowerShell
    Stop-Container [-Name] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-TurnOff] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Stop-Container [-Container] <Container[]> [-TurnOff] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Container <Container[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Object
        Aliases                      None
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Name <string[]>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Passthru

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -TurnOff

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.Container\[\]
System.String\[\]


**出力**
Microsoft.Containers.PowerShell.Objects.Container


**別名**
None

##テスト ContainerImage

**名**
テスト ContainerImage

**概要**
コンテナーのホスト システムにコンテナーのイメージを検証します。

**構文**


``` PowerShell
    Test-ContainerImage [[-Name] <string>] [[-Publisher] <string>] [[-Version] <version>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Test-ContainerImage [-Image] <ContainerImage> [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

**パラメータ**


``` PowerShell
    -AsJob

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      None
        Dynamic?                     false

    -CimSession <CimSession[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -ComputerName <string[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Confirm

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      cf
        Dynamic?                     false

    -Credential <pscredential[]>

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Image <ContainerImage>

        Required?                    true
        Position?                    0
        Accept pipeline input?       true (ByValue)
        Parameter set name           Container Image Object
        Aliases                      None
        Dynamic?                     false

    -Name <string>

        Required?                    false
        Position?                    0
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Publisher <string>

        Required?                    false
        Position?                    1
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -Version <version>

        Required?                    false
        Position?                    2
        Accept pipeline input?       false
        Parameter set name           Name
        Aliases                      None
        Dynamic?                     false

    -WhatIf

        Required?                    false
        Position?                    Named
        Accept pipeline input?       false
        Parameter set name           (All)
        Aliases                      wi
        Dynamic?                     false

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).
```

**入力**
Microsoft.Containers.PowerShell.Objects.ContainerImage


**出力**
Microsoft.Containers.PowerShell.Objects.ContainerImageReport


**別名**
None



