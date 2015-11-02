MS. ContentId: B9414110-BEFD-423F-9AD8-AFD5EE612CDA
Titel: Schritt 8: experimentieren Sie mit Windows PowerShell

#Schritt 8: Experimentieren Sie mit WindowsPowerShell

Nun, da Sie die Grundlagen der Bereitstellung von Hyper-V, virtuelle Computer erstellen und verwalten diese virtuellen Computer durchlaufen haben, betrachten wir wie diesen Aktivitäten mit PowerShell automatisiert werden können.

###Zurückgeben einer Liste von Hyper-V-Befehle

1.  Klicken Sie auf die Windows-Start-Taste, Typ **PowerShell**.
2.  Führen Sie den folgenden Befehl aus, um eine durchsuchbare Liste mit PowerShell-Befehle zur Verfügung, mit dem Hyper-V-PowerShell-Modul anzuzeigen.

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
3.  Listen Sie alle virtuellen Computer in einen funktionsfähigen Status, off, führen Sie den folgenden Befehl.
    Mit diesem Befehl wird eine Kopie des Befehls aus Schritt 2 mit dem Filter aus 'Running' auf 'Off' geändert.

 ```powershell
 get-vm | where {$_.State –eq ‘Off’}
 ```

###Starten und Herunterfahren von virtuellen Maschinen

1. Um einen bestimmten virtuellen Computer zu starten, führen Sie den folgenden Befehl mit dem Namen des virtuellen Computers:

 ```powershell
 Start-vm –Name <virtual machine name>
 ```

2. Um alle momentan ausgeschaltet für virtuelle Computer zu starten, erhalten Sie eine Liste dieser Computer und übergeben Sie die Liste an den Befehl "Start-Vm":

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

##Wrappen und Verweise

Dieses Dokument hat einige einfache Schritte zum Explorer das Hyper-V-PowerShell-Modul sowie einige Beispielszenarios gezeigt.
Weitere Informationen über die Hyper-V-PowerShell-Modul, finden Sie unter der [Hyper-V-Cmdlets in Windows PowerShell-Referenz](https://technet.microsoft.com/%5Clibrary/Hh848559.aspx).






