MS. ContentId: e586a11a-870f-403b-8af8-4c2931589d26
Titel: Verwalten von Windows mit PowerShell Direct


#Verwalten von Windows mit PowerShell Direct

PowerShell Direct können Sie um eine Windows 10 oder Technical Preview für Windows Server-virtuellen Computer von einem Windows 10 oder Windows Server Technische Vorschau Hyper-V-Host Remote zu verwalten.
PowerShell Direct ermöglicht die Verwaltung von PowerShell innerhalb einer Virtual machine unabhängig von der Konfiguration des Netzwerks oder remote-Management-Einstellungen auf dem Hyper-V-Host oder des virtuellen Computers.
Dies erleichtert es Hyper-V-Administratoren zur Automatisierung und Verwaltung virtueller Computer und Konfiguration Skript.

Es gibt zwei Verfahren zum Ausführen von PowerShell direkt:


* Erstellen und Beenden einer PowerShell Direct-Sitzungs mit PSSession-cmdlets
* Ausführen von Skripts oder Befehls mit dem Invoke-Command-cmdlet

Wenn Sie ältere virtuelle Computer verwalten, verwenden Sie die Verbindung mit virtuellen Computern (VMConnect) oder [Konfigurieren eines virtuellen Netzwerks für den virtuellen Computer](http://technet.microsoft.com/library/cc816585.aspx).


##Erstellen und Beenden einer PowerShell Direct-Sitzungs mit PSSession-cmdlets

1. Öffnen Sie Windows PowerShell als Administrator, auf dem Hyper-V-Host.
    
3. Führen Sie einen der folgenden Befehle, um eine Sitzung mit dem Namen des virtuellen Computers oder GUID zu erstellen:
    

``` PowerShell
Enter-PSSession -VMName <VMName>
Enter-PSSession -VMGUID <VMGUID>
```

4. Führen Sie beliebige Befehle werden müssen.
    Diese Befehle führen Sie auf dem virtuellen Computer, dem Sie der Sitzung erstellt.
5. Wenn Sie fertig sind, führen Sie den folgenden Befehl aus, um die Sitzung zu schließen:
    

``` PowerShell
Exit-PSSession 
```

> Hinweis: Wenn Sie die Sitzung sind wird nicht herstellen, stellen Sie sicher, dass Sie Anmeldeinformationen für den virtuellen Computer, die Sie eine zur – nicht dem Hyper-V-Host Verbindung verwenden.

Weitere Informationen zu diesen Cmdlets finden Sie unter [Enter-PSSession](http://technet.microsoft.com/library/hh849707.aspx) und [Exit-PSSession](http://technet.microsoft.com/library/hh849743.aspx).


##Ausführen von Skripts oder Befehls mit dem Cmdlet "Invoke-Command"

Sie können die [Invoke-Command](http://technet.microsoft.com/library/hh849719.aspx) Cmdlet, um einen vordefinierten Satz von Befehlen auf dem virtuellen Computer ausführen.
Hier ist ein Beispiel für die Verwendung des Invoke-Command-Cmdlets, in dem PSTest ist der Name des virtuellen Computers und das Skript ausführen (foo.ps1) befindet sich im Skriptordner auf dem Laufwerk C: / Laufwerk:

 ``` PowerShell
 Invoke-Command -VMName PSTest -FilePath C:\script\foo.ps1 
 ```

Führen Sie einen einzelnen Befehl mit der **- Skriptblock** Parameter:

 ``` PowerShell
 Invoke-Command -VMName PSTest -ScriptBlock { cmdlet } 
 ```

##Was ist erforderlich, um PowerShell direkt zu verwenden?

Zum Erstellen einer PowerShell-Direct-Sitzung auf einem virtuellen Computer
* Die virtuelle Maschine muss lokal auf dem Host ausgeführt werden und gestartet.
    
* Sie müssen in dem Hostcomputer als Hyper-V-Administrator angemeldet sein.
* Sie müssen gültige Anmeldeinformationen für die virtuelle Maschine angeben.
* Das Hostbetriebssystem muss Windows 10, Technical Preview für Windows Server oder einer höheren Version ausgeführt werden.
    

* Der virtuelle Computer muss Windows 10, Technical Preview für Windows Server oder einer höheren Version ausgeführt werden.
    


Sie können die [Get-VM](http://technet.microsoft.com/library/hh848479.aspx) Cmdlet überprüfen, ob die verwendeten Anmeldeinformationen der Hyper-V-Administratorrolle verfügen und die VMs werden lokal auf dem Host ausgeführt und gestartet.

##Was können Sie mit PowerShell Direct?

Finden Sie unter [PowerShell Direct Ausschnitte](../develop/powershell_snippets.md) für zahlreiche Beispiele zum Verwenden von PowerShell direkt in Ihrer Umgebung als auch als Tipps und tricks zu zum Schreiben von Hyper-V-Skripts mit PowerShell.






