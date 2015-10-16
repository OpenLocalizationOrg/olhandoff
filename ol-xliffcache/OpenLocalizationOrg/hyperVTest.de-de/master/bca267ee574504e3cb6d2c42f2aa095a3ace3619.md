MS. ContentId: 71a03c62-50fd-48dc-9296-4d285027a96a
Titel: Setup Windows-Container auf einem lokalen virtuellen Computer

#Vorbereiten der Technologievorschau der Windows Server für Windows Server-Container

Zum Erstellen und Verwalten von Windows Server-Container, muss die Technologievorschau der Windows Server 2016 Umgebung vorbereitet werden.
Dieses Handbuch führt durch die Konfiguration von Windows Server-Container auf einem virtuellen Hyper-V-Computer.

> Handbücher mit anderen ersten Schritten:
* Führen Sie im Windows Server-Container [Azure](./azure_setup.md).
* Führen Sie im Windows Server-Container [einer vorhandenen virtuellen Maschine](./inplace_setup.md).
* Einrichten von Windows Server-Container [auf einer physischen Windows Server Core-Installation](./inplace_setup.md).
    
    **Bitte lesen Sie vor dem Installieren der CONTAINER BETRIEBSSYSTEMABBILD:**  dem Lizenzvertrag von Microsoft Windows Server-Vorabversion der Software ("Lizenzbedingungen") für die Verwendung des Microsoft Windows-Container-Betriebssystemabbild Zusatzes ("zusätzliche Software) anwenden.
    Durch Herunterladen und verwenden die Zusatzsoftware, stimmen Sie dem Lizenzvertrag und können Sie nicht verwenden, wenn Sie dem Lizenzvertrag nicht akzeptiert haben.
    Windows Server-Vorabversion der Software und die Zusatzsoftware werden von der Microsoft Corporation lizenziert.
    


    * System unter Windows 10 / Windows Server Technical Preview 2 oder höher.
    * Hyper-V-Rolle aktiviert ([finden Sie unter Hinweise](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install#UsingPowerShell)).
    * 20GB freier Speicherplatz für Container Host Image, Base Betriebssystemabbild und Setup-Skripts.
    * Administratorberechtigungen auf dem Hyper-V-Host.

> Windows Server-Container erfordern keine Hyper-V, aber der Einfachheit halber dieses Handbuch setzt voraus, dass eine Hyper-V-Umgebung verwendet wird, um den Container für Windows Server-Host ausgeführt werden.

##Einen neuen Container-Host auf einen neuen virtuellen Computer einrichten

Windows Server-Container bestehen aus mehreren Komponenten, z. B. die Windows Server-Container-Host und die Basis-Betriebssystemabbild Container.
Wir haben ein Skript zusammengestellt, die herunterladen und konfigurieren diese Elemente für Sie.
Führen Sie diese Schritte, um einen neuen Hyper-V virtuelle Computer bereitstellen und Konfigurieren dieses System als Windows Server-Host-Container.

Starten einer PowerShell-Sitzungs als Administrator an.
Dies kann durch Rechtsklick auf das Symbol "PowerShell" und Auswählen von "Ausführen als Administrator" oder durch Ausführen des folgenden Befehls aus einer PowerShell-Sitzung erfolgen.

``` powershell
start-process powershell -Verb runAs
```

Verwenden Sie den folgenden Befehl, um das Skript herunterzuladen.
Das Skript kann auch manuell heruntergeladen werden von diesem Speicherort - [-Konfigurationsskript](http://aka.ms/newcontainerhost).

``` PowerShell
wget -uri https://aka.ms/newcontainerhost -OutFile New-ContainerHost.ps1
```

Führen Sie den folgenden Befehl zum Erstellen und konfigurieren Sie die Container, in dem `< Containerhost >` werden der Name des virtuellen Computers und `< Kennwort >` wird das Kennwort des Administratorkontos zugewiesen werden.

``` powershell
.\New-ContainerHost.ps1 –VmName <containerhost> -Password <password>
```

Zu Beginn des Skripts werden Sie aufgefordert, die gelesen und stimme Ihnen Lizenzierung.

```
Before installing and using the Windows Server Technical Preview 3 with Containers virtual machine you must:
    1. Review the license terms by navigating to this link: http://aka.ms/WindowsServerTP3ContainerVHDEula
    2. Print and retain a copy of the license terms for your records.
By downloading and using the Windows Server Technical Preview 3 with Containers virtual machine you agree to such
license terms. Please confirm you have accepted and agree to the license terms.
[N] No  [Y] Yes  [?] Help (default is "N"): Y
```

Das Skript beginnt dann herunterladen und konfigurieren die Komponenten der Windows Server-Container.
Dieser Vorgang kann einige Zeit aufgrund der großen Download dauern.
Wenn Sie fertig ist, wird der virtuelle Computer konfiguriert und für Sie erstellen und Verwalten von Windows Server-Container und Windows Server-Container-Images mit PowerShell und Docker.



Sie erhalten die folgende Meldung während des Bereitstellungsprozesses für Fenster Servercontainer Host.

```
This VM is not connected to the network. To connect it, run the following:
Get-VM | Get-VMNetworkAdapter | Connect-VMNetworkAdapter -Switchname <switchname>
```
Wenn Sie dies tun, überprüfen Sie die Eigenschaften des virtuellen Computers, und verbinden Sie den virtuellen Computer mit einem virtuellen Switch. Sie können auch den folgenden PowerShell-Befehl ausführen, in denen `< Switchname >` ist der Name des virtuellen Hyper-V-Switches, die Sie mit dem virtuellen Computer eine Verbindung herstellen möchten.

``` powershell 
Get-VM | Get-VMNetworkAdapter | Connect-VMNetworkAdapter -Switchname <switchname>
```

Wenn das Skript abgeschlossen ist, starten Sie den virtuellen Computer.
Der virtuelle Computer mit Windows Server 2016 Core konfiguriert ist und sieht wie folgt aus.

<center>![](./media/containerhost2.png)</center><br />

Schließlich melden Sie sich mit das Kennwort angegeben werden, bei der Konfiguration des virtuellen Computers, und stellen Sie sicher, dass die virtuelle Maschine über eine gültige IP-Adresse verfügt.
Mit diesen Elementen abgeschlossen sollte Ihr System für die Windows Server-Container bereit.


##Video zur exemplarischen Vorgehensweise

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Configure-Windows-Server-Containers-on-a-Local-System/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##Nächste Schritte – starten Sie mithilfe von Containern

Jetzt, eine Windows Server-2016 durch Ausführen der Funktion Servercontainer Windows System zur Arbeit mit Windows Server-Containern und Windows Server-Container Bilder die folgenden Handbücher zu wechseln.


[Schnellstart: Windows Server-Container und Docker](./manage_docker.md)


[Schnellstart: Windows Server-Container und PowerShell](./manage_powershell.md)


-------------------


[Zurück zur Startseite von Container](../containers_welcome.md)  
[Bekannte Probleme bei der aktuellen Version](../about/work_in_progress.md)




