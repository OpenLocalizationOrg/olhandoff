MS. ContentId: 5bbac9eb-c31e-40db-97b1-f33ea59ac3a3
Titel: In Bearbeitung

#In Bearbeitung

Wenn Sie keine finden Sie Ihr Problem hier behandelt oder Fragen haben, stellen Sie sie auf die [Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

-----------------------


##Allgemeine Funktionen

###Windows-Container-Abbild muss genau mit dem Container Host übereinstimmen.

Ein Windows Server-Container erfordert ein Betriebssystemabbild, die den Host Container in Bezug zum Erstellen und Patchen Ebene entspricht.
Ein Konflikt führen zu Systeminstabilität und oder unvorhersehbaren Verhalten für den Container bzw. den Host.

Wenn Sie Updates für die Windows-Container Hostbetriebssystem installieren, die können, Sie den Container Basis aktualisieren müssen, aktualisiert Betriebssystemabbild auf dem entsprechenden.


**Zu umgehen:**   
Herunterladen und Installieren eines Container-Basisabbilds Abgleich der Betriebssystemebene und Patchebene des Container-Hosts.


###Sporadisch Befehle fehlschlagen – versuchen Sie es erneut

Bei unseren Tests Befehle gelegentlich mehrere Male ausgeführt werden müssen.
Das gleiche Prinzip gilt für andere Aktionen.
Wenn Sie eine neue Datei erstellen nicht angezeigt wird, führen Sie z. B. berührt die Datei.



Wenn Sie dies durchführen müssen, lassen Sie uns wissen über [in den Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

** Zu umgehen: **  
Erstellen Sie Skripts so, dass diese Befehle mehrere Male versuchen.
Wenn ein Befehl fehlschlägt, versuchen Sie es erneut.



###Alle nicht-C: / Laufwerke automatisch in den neuen Container zugeordnet sind

Alle nicht-C: / Laufwerke zur Verfügung, mit dem Host Container automatisch in neue ausgeführten Windows Server-Container zugeordnet.

Zu diesem Zeitpunkt besteht keine Möglichkeit, selektiv Ordner in einem Container zugeordnet, wie eine vorläufige Umgehung Laufwerke werden automatisch zugeordnet.

** Zu umgehen: **  
Wir arbeiten auf.
Die zukünftige dort werden Ordner frei.


###Windows Server-Container werden nur sehr langsam gestartet.

Wenn Ihr Container zu mehr als 30 Sekunden dauert, möglicherweise viele doppelte Virenscans ausführen werden.

Viele Anti-Malware-Lösungen, wie z. B. Windows Defender, vielleicht Dateien mit-in Container Bilder, einschließlich aller OS-Binärdateien und Dateien im Container Betriebssystemabbild unnötigerweise scannen.
Dieser Fehler tritt bei jedem ein neuer Container erstellt wird und hinsichtlich der Anti-Malware Aussehen aller Dateien"des Containers" neue Dateien, die zuvor noch nicht gescannt.
Also wenn Prozesse innerhalb des Containers versuchen, diese Dateien lesen Scannen Antimalware-Komponenten zuerst diese vor dem Zugriff auf die Dateien.
In Wirklichkeit wurden diese Dateien bereits gescannt, wenn das Container-Bild importiert oder an den Server abgerufen wurde.
In Zukunft wird neue Vorschau-Infrastruktur vorhanden sein, dass Antimalware-Lösungen, einschließlich Windows Defender, werden diese Situationen kennen und entsprechend vorgehen können, um mehrere Scans zu vermeiden.


--------------------------


##Netzwerk

###Anzahl der Netzwerk-Depots pro container

In dieser Version wird ein Netzwerk Depot pro Container unterstützt.
Dies bedeutet, dass wenn Sie einen Container mit mehreren Netzwerkadaptern verfügen, den gleichen Netzwerkport für die einzelnen Adapter zugreifen kann (z. B. 192.168.0.1:80 und 192.168.0.2:80, die auf den gleichen Container gehört).

** Zu umgehen: **  
Wenn mehrere Endpunkte von einem Container verfügbar gemacht werden müssen, verwenden Sie die NAT-Port-Zuordnung.

###Windows-Container werden IP-Adressen nicht abrufen.

Wenn Sie auf die Windows Server-Container mit DHCP-VM-Switches herstellen ist es für den Container-Host eine IP-Wwhile empfangen, die Container nicht, möglich.

Der Container eine 169.254. abgerufen werden.***. *** APIPA IP-Adresse.

**Zu umgehen:**
Dies ist ein Nebeneffekt den Kernel freigeben.
Alle Container haben affectively dieselbe Mac-Adresse.

Aktivieren Sie auf dem Host Container spoofing von MAC-Adresse.

Dies kann erreicht werden mithilfe von PowerShell
```
Get-VMNetworkAdapter -VMName "[YourVMNameHere]"  | Set-VMNetworkAdapter -MacAddressSpoofing On
```

###Erstellen von Dateifreigaben funktioniert nicht in einem Container

Derzeit ist es nicht möglich, eine Dateifreigabe in einem Container zu erstellen.
Wenn das Ausführen `net Share` erhalten Sie eine Fehlermeldung wie folgt:

```
The Server service is not started.

Is it OK to start it? (Y/N) [Y]: y
The Server service is starting.
The Server service could not be started.

A service specific error occurred: 2182.

More help is available by typing NET HELPMSG 3547.
```

** Zu umgehen: **
Sie ggf. zum Kopieren von Dateien in einen Container können umgekehrt round durch Ausführen von `net Use` innerhalb des Containers.
Beispiel:

```
net use S: \\your\sources\here /User:shareuser [yourpassword]
```

--------------------------


##Anwendungskompatibilität

Sind daher Mnay Fragen dazu, welche Anwendung arbeiten und funktionieren nicht in Windows Server-Container, wir entschieden, Informationen zur Kompatibilität der Anwendung unterbrechen [einen eigenen Artikel](../reference/app_compat.md).

Einige der häufigsten Probleme befinden sich hier ebenfalls.

###WinRM wird nicht in einem Windows Server-Container gestartet.

WinRM gestartet wird, löst einen Fehler aus und wieder beendet.
Fehler werden im Ereignisprotokoll nicht protokolliert.

**Zu umgehen:**
Verwenden von WMI, [RDP](#RemoteDesktopAccessOfContainers), oder geben Sie-PSSession - des-Elements

###ASP.NET 4.5 oder ASP.NET 3.5 können nicht mit IIS in einem Container mit DISM installiert werden

Installieren von IIS-ASPNET45 in einem Container funktioniert nicht in einem Windows Server-Container.
Die Installation Fortschritt Sticks rund 95.5 %.

``` PowerShell
Enable-WindowsOptionalFeature -Online -FeatureName IIS-ASPNET45
```

Dies schlägt fehl, da ASP.NET 4.5 nicht in einem Container ausgeführt wird.

**Zu umgehen:**  
Installieren Sie stattdessen die Webserverrolle, um IIS zu verwenden.
ASP 5.0 funktioniert.


``` PowerShell
Enable-WindowsOptionalFeature -Online -FeatureName Web-Server
```

Finden Sie die [Anwendungskompatibilität Artikel](../reference/app_compat.md) Weitere Informationen, welche Programme in Containern werden können.

--------------------------



##Docker-Verwaltung

###Docker-Clients, die nicht standardmäßig gesichert

In dieser Vorabversion ist Docker Kommunikation öffentlich, wenn Sie wissen, wo Sie suchen.

###Docker-Befehle, die nicht mit Windows Server-Containern funktionieren

Befehle, die bekanntermaßen fehl:

| **Docker-Befehl**| **Bei dem es ausgeführt wird.**| **Fehler**| **Hinweise**|
|:-----|:-----|:-----|:-----|
| **Docker Festschreiben**| image| Docker beendet, Container und nicht korrekte Fehlermeldung angezeigt| Ausführen eines Commits für eine beendete Container funktioniert.Für die Ausführung von Containern: Wir arbeiten daran, es :)|
| **Docker diff**| Daemon| Fehler: Die Windows-Graphdriver Changes() nicht unterstützt| |
| **Kill docker**| Container| Fehler: Ungültiger Signal: KILL-Fehler: Fehler beim Beenden von Containern:]| |
| **Docker laden**| image| Im Hintergrund fehlschlägt| Kein Fehler, aber das Abbild nicht entweder geladen.|
| **Docker anhalten**| Container| Fehler: Windows-Container kann nicht angehalten werden.Möglicherweise wird nicht unterstützt| |
| **Docker-port**| Container| | Kein Port lautet erste auch wir können RDP.
| **Docker Abruf**| Daemon| Fehler: Den Pfad nicht System gefunden werden.Wir führen kann-Container, die mit diesem Abbild.| Bild hinzugefügt wird nicht verwendet werden.Wir arbeiten jedoch daran :)|
| **Docker neu starten**| Container| Fehler: Das Herunterfahren des Systems wird ausgeführt.| |
| **Docker angehaltenen Status aufzuheben**| Container| | Nicht testen, da anhalten noch funktioniert.|
Wenn alle Elemente, die nicht in diese fehlschlägt (oder ein Befehl anders als erwartet fehlschlägt), teilen Sie uns Ihre Liste wissen über [in den Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).



###Docker-Befehle, die teilweise mit Windows Server-Container

Befehle mit teilweise Funktionalität:

| **Docker-Befehl**| **Wird auf wird ausgeführt...**| **Parameter**| **Hinweise**|
|:-----|:-----|:-----|:-----|
| **Docker anhängen**| Container| --kein Stdin = False| Der Befehl nicht beenden, wenn STRG-P-Q STRG gedrückt wird|
| | | --Sig-Proxy = True| Works|
| **Docker erstellen**| Bilder| -f,--Datei| Fehler: Konnte nicht vorbereitet Kontext: konnte nicht abgerufen Synlinks|
| | | --Force-Rm = False| Works|
| | | --kein Cache = False| Works|
| | | -Q,--Quiet = False| |
| | | --Rm = True| Works|
| | | -t,--Tag = ""| Works|
| **Docker Anmeldung**| Daemon| -e, -p, -u| sporratic-Verhalten|
| **Docker push**| Daemon| | Erste gelegentliche Fehler "Repository ist nicht vorhanden".|
| **Docker rm**| Container| -f| Fehler: Das Herunterfahren des Systems wird ausgeführt.|
Wenn alle Elemente, die nicht in dieser Liste schlägt fehl, wenn ein Befehl anders als erwartet ausfällt, oder finden Sie dieses Verhalten umgehen möchten, lassen Sie uns wissen über [in den Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).


###Einfügen von Befehlen zum interaktiven Docker-Sitzung ist auf 50 Zeichen begrenzt.

Wenn Sie über die Befehlszeile in einer interaktiven Docker Sitzung kopieren, ist es derzeit auf 50 Zeichen begrenzt.
Die eingefügte Zeichenfolge wird einfach abgeschnitten.

Dies ist nicht beabsichtigt, wir arbeiten daran, für die Aufhebung der Einschränkung.

###Net Use zurück Systemfehler 1223 Benutzernamens oder Kennworts auffordern, sondern

Lösung: Geben Sie an, den Benutzernamen und das Kennwort, wenn net Use ausgeführt.
Beispiel:
```
net use S: \\your\sources\here /User:shareuser [yourpassword]
```

###HCS-Shim-Fehler beim Erstellen der neuen Container-images

Wenn Sie Fehlermeldungen wie folgt auftreten:
```
hcsshim::ExportLayer - Win32 API call returned error r1=2147942523 err=The filename, directory name, or volume label syntax is incorrect. layerId=606a2c430fccd1091b9ad2f930bae009956856cf4e6c66062b188aac48aa2e34 flavour=1 folder=C:\ProgramData\docker\windowsfilter\606a2c430fccd1091b9ad2f930bae009956856cf4e6c66062b188aac48aa2e34-1868857733
```

Sie haben ein Problem durch die 0 Tage Patch für Windows Server 2016 TP3 drücken.
Dieser Fehler kann auch auftreten, wenn die Python-3.4.3.msi Installer oder Knoten v0.12.7.msi in einem Container ausgeführt wird.

Wenn Sie andere Hcsshim Fehler erreicht haben, teilen Sie uns über [in den Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).


##Beim Zugriff auf den Windows Server-Container mit Remotedesktop

Windows Server-Container kann verwaltet/Interaktion über eine RDP-Sitzung.

Die folgenden Schritte sind erforderlich, Remoteverbindung mit einem Windows Server-Container mit RDP.
Es wird vorausgesetzt, dass der Container mit dem Netzwerk über einen NAT-Switch verbunden ist.
Dies ist die Standardeinstellung, bei der Einrichtung eines Container-Hosts über das Installationsskript oder erstellen einen neuen virtuellen Computer in Azure.

** Im Container herstellen sollen **

Die folgenden Schritte erfordern, Verwalten von den Container mithilfe von Docker oder bei der Verwendung von PowerShell angeben der `- RunAsAdministrator` beim Verbinden mit dem Container zu wechseln.
Bitte nehmen Sie die folgenden Schritte aus, in dem Container, um eine Verbindung herstellen möchten.

1. Die IP-Adresse des Containers abrufen

  ```
  ipconfig
  ```

  Gibt die etwa wie folgt

  ```
  Windows IP Configuration

  Ethernet adapter vEthernet (Virtual Switch-f758a5a9519e1956cc3bef06eb03e5728d3fb61cf6d310246185587be490210a-0):

  Connection-specific DNS Suffix  . :
  Link-local IPv6 Address . . . . . : fe80::91cd:fb4c:4ea5:51df%17
  IPv4 Address. . . . . . . . . . . : 172.16.0.2
  Subnet Mask . . . . . . . . . . . : 255.240.0.0
  Default Gateway . . . . . . . . . : 172.16.0.1
  ```

  Bitte beachten Sie die IPv4-Adresse in der Regel in das Format 172.16.x.x

2. Legen Sie das Kennwort für den Container für den integrierten Administrator-Benutzer

  ```
  net user administrator [yourpassword]
  ```

3. Aktivieren Sie den integrierten Administrator-Benutzer für den Container

  ```
  net user administrator /active:yes
  ```

** Auf dem Host Container **

Seit Windows Server die Windows-Firewall mit erweiterter Sicherheit standardmäßig aktiviert ist, müssen wir einige Ports für die Kommunikation damit RDP zu öffnen.
Darüber hinaus wird eine Port-Zuordnung erstellt, sodass der Container über einen Port auf dem Container Host erreichbar ist.

Die folgenden Schritte erfordern eine PowerShell als Administrator auf dem Host Container gestartet.

1. Standard-RDP-Port, über die Windows-Firewall erweiterte zulassen

  ```
  New-NetFirewallRule -Name "RDP" -DisplayName "Remote Desktop Protocol" -Protocol TCP -LocalPort @(3389) -Action Allow
  ```

2. Ermöglichen Sie einen zusätzlichen Port für RDP-Verbindung mit dem Container

  ```
  New-NetFirewallRule -Name "ContainerRDP" -DisplayName "RDP Port for connecting to Container" -Protocol TCP -LocalPort @(3390) -Action Allow
  ```

Dieser Schritt öffnet Port 3390 auf dem Host des Containers.
Es wird zum Öffnen einer RDP-Sitzung auf den Container verwendet werden.
Wenn Sie mehrere Container herstellen möchten, können Sie diesen Schritt wiederholen, und gleichzeitig zusätzliche Portnummern.


3. Fügen Sie eine Port-Zuordnung für den vorhandenen NAT
    
    In diesem Schritt benötigen Sie die IP-Adresse aus Schritt 1 innerhalb des Containers

  ```
  Add-NetNatStaticMapping -NatName ContainerNAT -Protocol TCP -ExternalPort 3390 -ExternalIPAddress 0.0.0.0 -InternalPort 3389 -InternalIPAddress [your container IP]
  ```

  Hier stellen Sie sicher, dass Kommunikation mit dem Container-Host der Port 3390 stammt umgeleitet wird, um Port 3389 für den Container mit der IP-Adresse, die Sie angeben.

** Herstellen einer Verbindung mit dem Container über RDP **

Schließlich können Sie auf den Container über RDP verbinden.
Ausführen, führen Sie den folgenden Befehl auf einem System mit Remote Desktop-Client installiert (z. B. Ihr System mit der Container-Host-VM):


```
mstsc /v:[ContainerHostIP]:3390 /prompt
```

Geben Sie `Administrator` wie den Benutzernamen und das Kennwort, das Sie als Kennwort gewählt haben.

Der Remotedesktop-Verbindung werden Sie gefragt, ob das System trotz der Zertifikatfehler herstellen soll.
Wenn Sie "Ja" auswählen, wird die RDP-Verbindung geöffnet.



**Hinweis:** die Container RDP-Sitzung beenden, ohne Abmeldung Container verhindern möglicherweise heruntergefahren.
Stellen Sie sicher, dass die RDP-Sitzung beenden durch Eingabe von "Abmelden" (anstelle von "exit" oder einfach das RDP-Fenster geschlossen) vor dem Herunterfahren des Containers.

--------------------------


##PowerShell-Verwaltung

###Geben Sie PSSession hat Argument des Elements, New-PSSession nicht.

Dies ist korrekt.
Wir planen zur vollständigen Cimsession-Unterstützung in der Zukunft.


Gerne Voice-Feature-Anfragen im [die Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).


--------------------------

[Zurück zur Startseite von Container](../containers_welcome.md)



