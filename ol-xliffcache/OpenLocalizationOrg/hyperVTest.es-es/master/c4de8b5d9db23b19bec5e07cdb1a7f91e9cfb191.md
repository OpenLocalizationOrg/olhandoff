MS. ContentId: B9414110-BEFD-423F-9AD8-AFD5EE612CDA
título: paso 8: experimentar con Windows PowerShell

#Paso 8: Experimentar con Windows PowerShell

Ahora que ha visto los aspectos básicos de la implementación de Hyper-V, creación de máquinas virtuales y administrar estas máquinas virtuales, exploremos cómo automatizar muchas de estas actividades con PowerShell.

###Devolver una lista de comandos de Hyper-V

1.  Haga clic en el botón de inicio de Windows, tipo **PowerShell**.
2.  Ejecute el siguiente comando para mostrar una lista de comandos de PowerShell disponibles en el módulo de PowerShell de Hyper-V que se pueden buscar.

 ```powershell
get-command –module hyper-v | out-gridview
 ```
Obtener algo parecido a esto:

![](media\command_grid.png)

3. Para obtener más información acerca de un determinado comando de PowerShell, utilice `get-help`.
   Por ejemplo ejecutando el siguiente comando devolverá información sobre la `get-vm` comando Hyper-V.

  ```powershell
get-help get-vm
  ```
La salida muestra cómo estructurar el comando, ¿cuáles son los parámetros obligatorios y opcionales y los alias que puede utilizar.

![](media\get_help.png)


###Devolver una lista de las máquinas virtuales

Utilice la `get-vm` comando para devolver una lista de las máquinas virtuales.

1. En PowerShell, ejecute el siguiente comando:

 ```powershell
get-vm
 ```
Esto mostrará algo como esto:

![](media\get_vm.png)

2. Para devolver una lista de sólo las máquinas virtuales con la tecnología en Agregar un filtro a la `get-vm` comando.
   Puede agregar un filtro mediante el comando where-object.
   Para obtener más información sobre los filtros, vea el [utilizando el objeto Where](https://technet.microsoft.com/en-us/library/ee177028.aspx) documentación.

 ```powershell
 get-vm | where {$_.State –eq ‘Running’}
 ```
3.  Para enumerar todas las máquinas virtuales en una estado apagado, ejecute el siguiente comando.
   Este comando es una copia del comando del paso 2, con el filtro ha cambiado de 'Running' a 'Off'.

 ```powershell
 get-vm | where {$_.State –eq ‘Off’}
 ```

###Iniciar y apagar las máquinas virtuales

1. Para iniciar una máquina virtual determinada, ejecute el siguiente comando con el nombre de la máquina virtual:

 ```powershell
 Start-vm –Name <virtual machine name>
 ```

2. Para iniciar el apagado todas las máquinas virtuales, obtener una lista de esas máquinas y canalice la lista para el comando 'start-vm':

  ```powershell
 get-vm | where {$_.State –eq ‘Off’} | start-vm
  ```
3. Para cerrar todas las máquinas virtuales en ejecución, ejecute esto:

  ```powershell
 get-vm | where {$_.State –eq ‘Running’} | stop-vm
  ```

###Crear un punto de comprobación de máquina virtual

Para crear un punto de comprobación con PowerShell, seleccione la máquina virtual con el `get-vm` comando y de canalización para la `vm de punto de comprobación` comando.
Por último proporcionar el punto de control un nombre mediante `- snapshotname`.
El comando será similar al siguiente:

 ```powershell
 get-vm -Name <VM Name> | checkpoint-vm -snapshotname <name for snapshot>
 ```
Por ejemplo, este es un punto de control con el nombre DEMOCP:

![](media\POSH_CP2.png)

###Crear una nueva máquina virtual

En el ejemplo siguiente se muestra cómo crear una nueva máquina virtual en el entorno de Scripting integrado en PowerShell (ISE).
Esto es un ejemplo sencillo y podría ampliarse en para incluir características adicionales de PowerShell y las implementaciones de VM más avanzadas.

1. Para abrir el clic de PowerShell ISE en Inicio, escriba **PowerShell ISE**.
2. Ejecute el siguiente código para crear una máquina virtual.
   Consulte la [New-VM](https://technet.microsoft.com/en-us/library/hh848537.aspx) documentación para obtener información detallada sobre el comando New-VM.

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

##Resumir y referencias

Este documento ha demostrado unos pasos sencillos al explorador el módulo de PowerShell de Hyper-V, así como algunos escenarios de ejemplo.
Para obtener más información sobre el módulo de PowerShell de Hyper-V, vea el [Cmdlets de Hyper-V en Windows PowerShell referencia](https://technet.microsoft.com/%5Clibrary/Hh848559.aspx).




