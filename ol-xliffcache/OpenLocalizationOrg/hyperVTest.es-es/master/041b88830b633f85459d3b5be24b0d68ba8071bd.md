MS. ContentId: C49DA0E6-2E12-4D51-803A-31B1B5A8F85C
título: referencia de PowerShell


#PowerShell para contenedores

##Instalar ContainerOSImage

<g id="f241a34c-759f-4b22-b055-81824456dc07" ctype="x-strong">NOMBRE</g>      
Instalar ContainerOSImage

<g id="a1dcb69c-8423-4960-858e-c4882a8b0120" ctype="x-strong">SINOPSIS</g>  
El formato WIM determinado se instala como una imagen de sistema operativo del contenedor para su uso con Windows Server o contenedores de Hyper-V.


<g id="87460353-fd97-413a-b17d-000781b72d3d" ctype="x-strong">SINTAXIS</g>
``` PowerShell  
Install-ContainerOSImage [-WimPath] <String> [-Force] [< CommonParameters >]
```

<g id="e5149772-c4c0-4247-9a3f-6cb734b1364b" ctype="x-strong">DESCRIPCIÓN</g>  
Instala una imagen base desde un archivo WIM en el almacén de imágenes central compartida para la característica de contenedores de Hyper-V y Windows Server.

<g id="53f8bc65-4737-4b95-b8a2-7e75219bedd4" ctype="x-strong">PARÁMETROS</g>
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

<g id="c2b4d092-e836-43c6-8e99-8e0e64e1139d" ctype="x-strong">ENTRADAS</g>      
Ninguno

<g id="9f7e7244-479c-41ed-b455-23b64f25918b" ctype="x-strong">SALIDAS</g>  
Ninguno

<g id="2d5d4407-3bde-43e7-b968-a2c16ee780fc" ctype="x-strong">ALIAS</g>  
Ninguno

-------------------------- EXAMPLE 1 --------------------------

``` PowerShell
PS C:\>Install-ContainerOSImage c:\baseimage.wim
```

##ContainerOSImage desinstalar

<g id="cea03ce2-9f23-4dc8-845b-a0aa8c02daed" ctype="x-strong">NOMBRE</g>  
ContainerOSImage desinstalar

<g id="e61a4206-00e7-42a5-835f-e0223f366607" ctype="x-strong">SINOPSIS</g>  
Quita una imagen de sistema operativo instalado previamente contenedor

<g id="8cc1ef42-0256-48ce-a6a3-5366278c6469" ctype="x-strong">SINTAXIS</g>
```PowerShell
Uninstall-ContainerOSImage [-ImageName] <string> [-Force]  [< CommonParameters >]

Uninstall-ContainerOSImage [-ContainerImage] <Object> [-Force]  [< CommonParameters >]
```

<g id="16b9a973-4e17-493f-9298-8655cfae2704" ctype="x-strong">PARÁMETROS</g>
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

<g id="3965a9b2-1120-440f-a66c-870098d8b5a9" ctype="x-strong">ENTRADAS</g>  
Ninguno


<g id="71e50ef3-160e-490b-b4f8-18b9ecc78305" ctype="x-strong">SALIDAS</g>  
System.Object

<g id="dcbb74e2-a882-49bd-aafd-aeebf154e7e1" ctype="x-strong">ALIAS</g>  
Ninguno

##ContainerNetworkAdapter agregar

<g id="b35f154f-703a-4ffd-a401-4cf2d809099a" ctype="x-strong">NOMBRE</g>  
ContainerNetworkAdapter agregar

<g id="b571f105-4613-4ac5-9f0b-c1f6cb9f6b58" ctype="x-strong">SINOPSIS</g>  
Agregar un nuevo adaptador de red a un contenedor existente

<g id="ad6bd7be-9c9a-4490-a64a-313714883279" ctype="x-strong">SINTAXIS</g>
``` PowerShell  
Add-ContainerNetworkAdapter [-ContainerName] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-SwitchName <string>] [-Name <string>] [-DynamicMacAddress] [-StaticMacAddress
    <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Add-ContainerNetworkAdapter [-Container] <Container[]> [-SwitchName <string>] [-Name <string>]
    [-DynamicMacAddress] [-StaticMacAddress <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="333d5cf3-7b75-413a-b42a-0ed1ac859ead" ctype="x-strong">PARÁMETROS</g>
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


<g id="8422dee9-a4a2-4e43-adcb-80aeaaf8d719" ctype="x-strong">ENTRADAS</g>  
System.String\[\]  
Microsoft.Containers.PowerShell.Objects.Container\[\]


<g id="16e5b859-89e9-44eb-975f-0e854a0dd5e9" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


<g id="e2338200-3099-4986-9c7b-f3bf9eb9eb58" ctype="x-strong">ALIAS</g>  
Ninguno

##ContainerNetworkAdapter conectar

<g id="c44cde6a-c259-4b7c-9cee-c2034f6516eb" ctype="x-strong">NOMBRE</g>  
ContainerNetworkAdapter conectar

<g id="8c17d363-38b1-4cac-9ed5-8850590d9b45" ctype="x-strong">SINOPSIS</g>  
Conectar un adaptador de red del contenedor a un conmutador virtual

<g id="f9cfb51b-e513-4a07-9af9-c367ceebe340" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Connect-ContainerNetworkAdapter [-ContainerName] <string[]> [[-Name] <string[]>] [-SwitchName] <string>
    [-Passthru] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>] [-WhatIf]
    [-Confirm]  [<CommonParameters>]

    Connect-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter[]> [-SwitchName] <string> [-Passthru]
    [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="65a9b711-a5cb-4811-bc36-de0c7548317b" ctype="x-strong">PARÁMETROS</g>
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

<g id="fb812d38-e141-4bc7-9a49-5f8c0eced49b" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter\[\]


<g id="b03d168e-eed0-4e70-bf9b-22414a84133e" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


<g id="1dc9e667-72b4-4397-bdf1-681617ea303c" ctype="x-strong">ALIAS</g>  
Ninguno

##ContainerNetworkAdapter desconectar

<g id="69d174a2-770f-48f7-bc56-086707d06d59" ctype="x-strong">NOMBRE</g>  
ContainerNetworkAdapter desconectar

<g id="22cdfd23-cf23-48d3-8174-2d81a41b3dbe" ctype="x-strong">SINOPSIS</g>  
Desconectar un adaptador de red del contenedor de un conmutador virtual

<g id="5d74376d-8889-411c-b755-6cc340bf7027" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Disconnect-ContainerNetworkAdapter [-ContainerName] <string[]> [[-Name] <string[]>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Disconnect-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter[]> [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

<g id="8d79b543-c707-4250-b1e0-4a441f9e52fa" ctype="x-strong">PARÁMETROS</g>
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

<g id="da7db587-5f9e-4564-a07f-b94b1b0224ba" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter\[\]


<g id="6baece9e-8b09-4122-bfde-d387ffc83c89" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


<g id="c647f5ec-4c78-4e44-9b8a-4bd56e2e8794" ctype="x-strong">ALIAS</g>  
Ninguno

##ContainerImage de exportación

<g id="944d0257-0ced-4958-8c33-d841dedac291" ctype="x-strong">NOMBRE</g>  
ContainerImage de exportación

<g id="fbf29044-327a-40ff-8271-fa2185324c22" ctype="x-strong">SINOPSIS</g>  
Copiar la imagen de contenedor fuera del almacén local

<g id="c3adbb66-0d2a-4397-8b2b-52904218140f" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Export-ContainerImage [[-Name] <string>] [-Path] <string> [[-Version] <version>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]

    Export-ContainerImage [-Image] <ContainerImage[]> [-Path] <string> [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

<g id="334d79e3-77ae-4894-9d35-e34d7a99373e" ctype="x-strong">PARÁMETROS</g>
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

<g id="beebb658-3dbf-465f-a037-70ed1523b8be" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage\[\]


<g id="d2bcb4d4-187a-4e10-8bb2-8eb2e855154c" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage


<g id="30b8bc6d-6c26-4606-ada2-3ca568c6dcf1" ctype="x-strong">ALIAS</g>  
Ninguno

##Get-Container

<g id="85e2cf20-d1d9-43c7-bfae-213b1f474b65" ctype="x-strong">NOMBRE</g>  
Get-Container

<g id="341eb18a-fe7c-4530-860b-90ccc49acb42" ctype="x-strong">SINOPSIS</g>  
Enumerar los contenedores del sistema actual

<g id="d3262734-366a-4ed9-8cab-2e89b0f969d8" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Get-Container [[-Name] <string[]>] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>]  [<CommonParameters>]

    Get-Container [[-Id] <guid>] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>]  [<CommonParameters>]
```

<g id="11e1d7bb-04cc-4b61-819f-48fe7eed86b3" ctype="x-strong">PARÁMETROS</g>
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

<g id="fb50febb-678c-48d4-9ddb-129bee4b70c3" ctype="x-strong">ENTRADAS</g>  
System.String\[\]  
System.Guid


<g id="2a5c6102-b8b0-4233-9d69-df1c277bb955" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.Container


<g id="6201aabc-3320-4013-a620-d6101e073454" ctype="x-strong">ALIAS</g>  
Ninguno

##Get-ContainerHost

<g id="1004f6f1-7b59-44ff-b562-80857a5a7769" ctype="x-strong">NOMBRE</g>  
Get-ContainerHost

<g id="3b7841dc-72a8-4955-961f-ce3dba3ca554" ctype="x-strong">SINOPSIS</g>  
Obtenga el objeto host para el host de contenedor

<g id="3fc15208-745c-4e7d-b4ac-8c464773ee07" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Get-ContainerHost [[-ComputerName] <string[]>] [[-Credential] <pscredential[]>]  [<CommonParameters>]

    Get-ContainerHost [-CimSession] <CimSession[]>  [<CommonParameters>]
```

<g id="5bac118f-3957-46fa-8d3b-5aca417957a1" ctype="x-strong">PARÁMETROS</g>
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

<g id="2abe75a5-77cb-4cec-bc1b-a5bc3d672d01" ctype="x-strong">ENTRADAS</g>  
Microsoft.Management.Infrastructure.CimSession\[\]  
System.String\[\]  
[] System.Management.Automation.PSCredential\


<g id="04aa4eff-b3d8-497c-adc7-2a88d27cfbae" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerHost


<g id="bdfd0d14-67a0-44c4-bad2-5701cf948780" ctype="x-strong">ALIAS</g>  
Ninguno

##Get-ContainerImage

<g id="fd5bcc42-bdea-4cc2-bb64-c9f699f50865" ctype="x-strong">NOMBRE</g>  
Get-ContainerImage

<g id="fa2045d5-3531-4a34-a04a-a9b1a05d503c" ctype="x-strong">SINOPSIS</g>  
Lista de imágenes de contenedor en el host de contenedor

<g id="aded4661-f359-4d74-bd49-712e8ae4a46f" ctype="x-strong">SINTAXIS</g>
``` PowerShell
Get-ContainerImage [[-Name] <string>] [[-Publisher] <string>] [[-Version] <version>] [-ChildOf <ContainerImage>]
[-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>]  [<CommonParameters>]
```

<g id="eadd0dc7-3a56-4424-aeb7-dcf0d6617a86" ctype="x-strong">PARÁMETROS</g>
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

<g id="cd30a60d-20f5-44d4-a614-0053fe93ff37" ctype="x-strong">ENTRADAS</g>  
Ninguno


<g id="9edde9ae-a607-460d-a28a-ce05a30cdcb0" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage


<g id="ca829d5b-9570-4e8f-b9c7-df0ab33649ff" ctype="x-strong">ALIAS</g>  
Ninguno

##Get-ContainerNetworkAdapter

<g id="c54bad94-f06b-499f-8220-bfd1a17be526" ctype="x-strong">NOMBRE</g>  
Get-ContainerNetworkAdapter

<g id="cb80ef35-21dd-4d52-8d64-5c2f17e6be21" ctype="x-strong">SINOPSIS</g>  
Adaptadores de red de lista asociados a un contenedor

<g id="ffd81aff-33eb-480b-9b8f-cf1e3b543b59" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Get-ContainerNetworkAdapter [-ContainerName] <string[]> [[-Name] <string>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>]  [<CommonParameters>]

    Get-ContainerNetworkAdapter [-Container] <Container[]> [[-Name] <string>]  [<CommonParameters>]
```

<g id="4f2961cf-61ae-47cb-aa07-5b193fef2261" ctype="x-strong">PARÁMETROS</g>
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

<g id="32317855-4663-4431-b125-0e73347d08bb" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.Container\[\]  
System.String\[\]


<g id="66383e68-9ebd-4f73-a473-420edb39ba99" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


<g id="ea9464dc-5b9f-4cf2-8f72-104ff73c4923" ctype="x-strong">ALIAS</g>  
Ninguno

##ContainerImage de importación

<g id="796ad40d-445a-4b7e-a08e-1ae966d450fd" ctype="x-strong">NOMBRE</g>  
ContainerImage de importación

<g id="b2cc6313-8ff0-4b3e-a095-00d1d790c8f7" ctype="x-strong">SINOPSIS</g>  
Importar una imagen de contenedor que se ha exportado desde otro equipo

<g id="089736b7-60a0-4e99-80f6-2ad9541b24f8" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Import-ContainerImage [-Path] <string> [-AsJob] [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="47029f9b-2345-42e0-ade3-9a7cae6f50d3" ctype="x-strong">PARÁMETROS</g>
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

<g id="12761985-9e10-4ef6-be0c-f387226db97e" ctype="x-strong">ENTRADAS</g>  
System.String


<g id="6cf4cf52-1738-4bd2-b1aa-50e53ed85810" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage


<g id="6eb3fe87-b2ba-4f03-97fd-4d6e0921307f" ctype="x-strong">ALIAS</g>  
Ninguno

##Mover ContainerImageRepository

<g id="e3e96c62-31a8-4238-be77-ba9f7b29f057" ctype="x-strong">NOMBRE</g>  
Mover ContainerImageRepository

<g id="03d0d7c4-7c61-4f5a-892b-7011e250786c" ctype="x-strong">SINOPSIS</g>  
Cambiar la ubicación donde se almacenan las imágenes de contenedor.
Debe ser una ubicación en un disco local.
Sólo puede cambiarse cuando hay imágenes están presentes en el sistema.

<g id="fa73a816-97f2-4967-9d35-d536f2c3e902" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Move-ContainerImageRepository [-Path] <string> [-AsJob] [-Passthru] [-CimSession <CimSession[]>] [-ComputerName
    <string[]>] [-Credential <pscredential[]>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="e2886ccb-d730-4a1b-9d0f-3a7c35bfb9f4" ctype="x-strong">PARÁMETROS</g>
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

<g id="72882ee6-1124-4e73-ae1b-d193bebfedcb" ctype="x-strong">ENTRADAS</g>  
Ninguno


<g id="e48dbb26-0cdc-4164-8f84-72c9e6150cf9" ctype="x-strong">SALIDAS</g>  
Microsoft.HyperV.PowerShell.VMHost


<g id="4959f892-9841-44a4-aebe-2bf7f7269cd9" ctype="x-strong">ALIAS</g>
Ninguno

##Nuevo contenedor

<g id="6acfde11-9159-4773-b470-0d89792a1dcd" ctype="x-strong">NOMBRE</g>  
Nuevo contenedor

<g id="4dbc6ce0-8806-4237-af79-3e2b99b621b7" ctype="x-strong">SINOPSIS</g>  
Crear un nuevo contenedor

<g id="4924d16e-5b1f-49c3-8db7-be4af48c5029" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    New-Container [[-Name] <string>] -ContainerImageName <string> [-ContainerImagePublisher <string>]
    [-ContainerImageVersion <version>] [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-MemoryStartupBytes <long>] [-SwitchName <string>] [-Path <string>] [-AsJob] [-WhatIf]
    [-Confirm]  [<CommonParameters>]

    New-Container [[-Name] <string>] -ContainerImage <ContainerImage> [-MemoryStartupBytes <long>] [-SwitchName
    <string>] [-Path <string>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="ebbb52b0-b8e4-4913-9985-e66fda475e78" ctype="x-strong">PARÁMETROS</g>
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

<g id="03d14dd6-df1e-4fd2-b70e-fd80259ad319" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage


<g id="c547225a-b7e6-463d-8ab1-c0153e99605e" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.Container


<g id="95b0e861-9cae-48ed-a722-b72a8776d43b" ctype="x-strong">ALIAS</g>  
Ninguno

##Nueva ContainerImage

<g id="58bb6af8-2872-4072-856d-8314c4ce6b3f" ctype="x-strong">NOMBRE</g>  
Nueva ContainerImage

<g id="ccd2200c-f135-4bbf-aabb-1361939565dd" ctype="x-strong">SINOPSIS</g>  
Crear una nueva imagen de contenedor de un contenedor existente

<g id="d27f0f5a-d998-4a61-a776-09b1bc89e809" ctype="x-strong">SINTAXIS</g>
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

<g id="18e2f14b-daae-44a8-8275-d45959f34b53" ctype="x-strong">PARÁMETROS</g>
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

<g id="edb3ee18-b25c-4bc0-bcf3-262533b8ca42" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.Container


<g id="c8436316-3981-402e-8b6e-c0f427278f4d" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage


<g id="08e83b92-ea85-4e4a-9c72-2be722ab5bd5" ctype="x-strong">ALIAS</g>  
Ninguno

##Quitar contenedores

<g id="13efa64f-0ee3-4fb7-9e16-c34a13756e7b" ctype="x-strong">NOMBRE</g>  
Quitar contenedores

<g id="2857ce1c-adba-4504-acce-393ab33d8dbf" ctype="x-strong">SINOPSIS</g>  
Quitar un contenedor existente del sistema

<g id="fe02f505-238b-4359-8868-9651eed3a1e4" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Remove-Container [-Name] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-Force] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Remove-Container [-Container] <Container[]> [-Force] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

<g id="5fc0e538-78ae-457b-bf5e-c848e944be7e" ctype="x-strong">PARÁMETROS</g>
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

<g id="d6db3b59-4b25-40d0-bcb1-0b0dabd49142" ctype="x-strong">ENTRADAS</g>  
System.String\[\]  
Microsoft.Containers.PowerShell.Objects.Container\[\]


<g id="a27bcb94-956d-463f-9b1a-1aaa33884531" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.Container


<g id="206206bd-5d1b-43b6-9ddd-a548de707e23" ctype="x-strong">ALIAS</g>  
Ninguno

##Quitar ContainerImage

<g id="74b090a4-941d-447c-8b35-eeed54ef245a" ctype="x-strong">NOMBRE</g>  
Quitar ContainerImage

<g id="22cfcc59-5c51-445b-a0bf-c6fa8616ca18" ctype="x-strong">SINOPSIS</g>  
Quitar una imagen de contenedor del host del contenedor

<g id="1d4e3b21-d718-4708-b283-c6066ca8ad2c" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Remove-ContainerImage [[-Name] <string>] [[-Publisher] <string>] [[-Version] <version>] [-CimSession
    <CimSession[]>] [-ComputerName <string[]>] [-Credential <pscredential[]>] [-Force] [-WhatIf] [-Confirm]
    [<CommonParameters>]

    Remove-ContainerImage [-Image] <ContainerImage> [-Force] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="1c30b1a8-991e-4fea-bf3d-b3f788eb685f" ctype="x-strong">PARÁMETROS</g>
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

<g id="cd5941b3-f656-44bf-bf42-0295bb12351c" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage


<g id="c161d3a7-b1cb-4ea5-9920-5dc025775c1d" ctype="x-strong">SALIDAS</g>  
System.Object

<g id="9d2f092b-df7e-4273-8f2f-da31d05dbf05" ctype="x-strong">ALIAS</g>  
Ninguno

##Quitar ContainerNetworkAdapter

<g id="663d8384-ea5d-43ab-84fd-08000e30ec48" ctype="x-strong">NOMBRE</g>  
Quitar ContainerNetworkAdapter

<g id="64b50265-15f0-4470-b14f-28954dd93319" ctype="x-strong">SINOPSIS</g>  
Quitar un adaptador de red de un contenedor

<g id="fe811f42-a5cf-464a-adfe-e14321bce4cb" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Remove-ContainerNetworkAdapter [-ContainerName] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-Name <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Remove-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter[]> [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]

    Remove-ContainerNetworkAdapter [-Container] <Container[]> [-Name <string>] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

<g id="df62ec25-9aff-4542-8f03-5373d2ce4701" ctype="x-strong">PARÁMETROS</g>
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

<g id="a5d57199-cc11-450e-bfed-2a757dde29e7" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter\[\]  
System.String\[\]  
Microsoft.Containers.PowerShell.Objects.Container\[\]


<g id="ece73cd9-1ff3-4384-9d14-5a06829fbf96" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


<g id="d77c7e9f-db3d-47d8-af0b-075572fd57a8" ctype="x-strong">ALIAS</g>  
Ninguno

##Conjunto de ContainerNetworkAdapter

<g id="6d479220-629a-469b-a889-53c36f9f35ad" ctype="x-strong">NOMBRE</g>  
Conjunto de ContainerNetworkAdapter

<g id="f0cbe285-d55b-4fdf-9175-69d87abb1345" ctype="x-strong">SINOPSIS</g>  
Establecer la dirección MAC en un adaptador de red en un contenedor

<g id="c48218ef-37ae-49cf-927c-141e36fe325f" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Set-ContainerNetworkAdapter [-ContainerName] <string> [-CimSession <CimSession[]>] [-ComputerName <string[]>]
    [-Credential <pscredential[]>] [-Name <string>] [-DynamicMacAddress] [-StaticMacAddress <string>] [-Passthru]
    [-WhatIf] [-Confirm]  [<CommonParameters>]

    Set-ContainerNetworkAdapter [-NetworkAdapter] <ContainerNetworkAdapter> [-DynamicMacAddress] [-StaticMacAddress
    <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Set-ContainerNetworkAdapter [-Container] <Container> [-Name <string>] [-DynamicMacAddress] [-StaticMacAddress
    <string>] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="ef474dde-20c7-4ec1-808b-e6a2dbe0dbd7" ctype="x-strong">PARÁMETROS</g>
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

<g id="54099594-c136-46e2-be84-32feebb694be" ctype="x-strong">ENTRADAS</g>  
System.String  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter  
Microsoft.Containers.PowerShell.Objects.Container


<g id="5b346c2e-e71e-43fd-9ed7-235719f52972" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerNetworkAdapter


<g id="ede0edef-a129-42db-b25d-fe9e5e735fc1" ctype="x-strong">ALIAS</g>  
Ninguno

##Contenedor de inicio

<g id="d6bf012d-9fe0-4a6e-b76c-c392dba014d3" ctype="x-strong">NOMBRE</g>  
Contenedor de inicio

<g id="4a9f495d-0960-40f7-adba-82fa429b4dbd" ctype="x-strong">SINOPSIS</g>  
Iniciar un contenedor

<g id="160b8683-4be2-4561-aec7-3dd52d4206c7" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Start-Container [-Name] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Start-Container [-Container] <Container[]> [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="f75be7c8-204a-40d4-bf30-21d8a2df6852" ctype="x-strong">PARÁMETROS</g>
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

<g id="8d0a96b2-8a4f-4bbe-b99b-56fafe4fadea" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.Container\[\]  
System.String\[\]


<g id="6e80bf82-9d27-41d1-b453-b2b2518a073e" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.Container


<g id="0bbc354a-2e8d-4d97-a506-2b065d86ae0f" ctype="x-strong">ALIAS</g>  
Ninguno

##Contenedor de detención

<g id="333ab4af-a0f5-48b8-98c4-b69e63242bd6" ctype="x-strong">NOMBRE</g>  
Contenedor de detención

<g id="5ddd24b1-18d9-4823-91c9-62d18d6860d6" ctype="x-strong">SINOPSIS</g>  
Detener un contenedor

<g id="9c66d163-ea94-46d3-937a-13a68c270b99" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Stop-Container [-Name] <string[]> [-CimSession <CimSession[]>] [-ComputerName <string[]>] [-Credential
    <pscredential[]>] [-TurnOff] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Stop-Container [-Container] <Container[]> [-TurnOff] [-AsJob] [-Passthru] [-WhatIf] [-Confirm]
    [<CommonParameters>]
```

<g id="9be9709f-f458-4261-8142-5acb54a6e9d7" ctype="x-strong">PARÁMETROS</g>
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

<g id="1255858b-09f4-4eb9-b91d-617be108f469" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.Container\[\]  
System.String\[\]


<g id="ed91426d-f90a-495a-825d-3d47934aae6c" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.Container


<g id="fa2ca570-d32f-42bc-aa4a-4c164e908e93" ctype="x-strong">ALIAS</g>  
Ninguno

##ContainerImage de prueba

<g id="498543bd-d2e5-4c75-a781-bf2a3d831c1e" ctype="x-strong">NOMBRE</g>  
ContainerImage de prueba

<g id="45f9cf72-cd81-4532-b642-47534bc6b969" ctype="x-strong">SINOPSIS</g>  
Validar la imagen de un contenedor en el sistema de host de contenedor

<g id="3c11e625-ed08-4364-ac8d-024ca1769699" ctype="x-strong">SINTAXIS</g>
``` PowerShell
    Test-ContainerImage [[-Name] <string>] [[-Publisher] <string>] [[-Version] <version>] [-CimSession <CimSession[]>]
    [-ComputerName <string[]>] [-Credential <pscredential[]>] [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]

    Test-ContainerImage [-Image] <ContainerImage> [-AsJob] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

<g id="34f834db-761b-4a34-a40d-1c80532d0533" ctype="x-strong">PARÁMETROS</g>
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

<g id="021381d5-74ec-4c64-a16e-51bf486653c4" ctype="x-strong">ENTRADAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImage


<g id="fb4e81e1-c107-45b3-bafc-e98a0aa55bc7" ctype="x-strong">SALIDAS</g>  
Microsoft.Containers.PowerShell.Objects.ContainerImageReport


<g id="37a6e68d-df59-4366-8169-5a7cbae55149" ctype="x-strong">ALIAS</g>  
Ninguno



