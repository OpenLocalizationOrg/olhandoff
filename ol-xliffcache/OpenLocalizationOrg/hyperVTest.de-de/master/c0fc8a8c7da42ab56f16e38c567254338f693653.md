MS. ContentId: 347fa279-d588-4094-90ec-8c2fc241f5b6
Titel: Verwalten von Windows Server-Container mit Docker

#Schnellstart: Windows Server-Container und Docker

In diesem Artikel werden die Grundlagen der Verwaltung von Windows Server-Container mit Docker durchlaufen.
Container für Windows Server und Windows Server-Container-Images erstellen, entfernen Windows Server-Container und Container Bilder und Bereitstellen einer Anwendung in einem Windows Server-Container, werden die behandelten Elemente umfassen.
Die gewonnenen Erkenntnisse in dieser exemplarischen Vorgehensweise sollten Sie zu untersuchen, Bereitstellung und Verwaltung von Windows Server-Container mit Docker aktivieren.

Haben Sie Fragen?
Bitten Sie sie auf die [Windows-Containern Forum](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

> **Hinweis:** mit PowerShell erstellten Windows-Container kann zurzeit nicht mit Docker und Visa umgekehrt verwaltet werden.
> Container mit PowerShell erstellen, finden Sie unter  [Schnellstart: Windows Server-Container und PowerShell](./manage_powershell.md).
> <br /><br /> Wenn Sie mehr wissen möchten, [häufig gestellte Fragen](../about/faq.md#WhydoIhavetopickbetweenDockerandPowerShellforWindowsServerContainermanagement).

##Voraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise müssen die folgenden Elemente vorhanden sein.

- Windows Server 2016 TP3 oder später mit dem Container-Feature von Windows Server konfiguriert.
    Wenn Sie das Handbuch abgeschlossen haben, ist dies die VM, die in Azure oder Hyper-V erstellt wurde.
- Dieses System muss mit einem Netzwerk verbunden und auf das Internet zugreifen kann.

Wenn Sie die Container-Funktion konfigurieren müssen, finden Sie unter den folgenden Handbüchern: [Container Einrichtung in Azure](./azure_setup.md) oder [Container Setup in Hyper-V-](./container_setup.md).


##Grundlegender Container-Verwaltung mit Docker

In diesem ersten Beispiel werden die Grundlagen zum Erstellen und Entfernen von Containern für Windows Server und Windows Server-Container-Images mit Docker geführt.

Die erörtert, Protokoll in Windows Server-Container Hostsystems zunächst sehen Sie eine Windows-Befehlszeile.

![](media/cmd.png)

PowerShell-Sitzung starten, indem Sie eingeben `Powershell`.
Sehen Sie, dass Sie in einem PowerShell-Sitzung bei die Aufforderung ändert sich werden von `C:\Directory >` auf `PS C:\Directory >`.
```
C:\> powershell
Windows PowerShell
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\>
```
> Dieser Schnellstart konzentriert werden, jedoch einige Schritte ausführen, wie z. B. Verwalten von Firewallregeln und Kopieren von Dateien mit PowerShell-Befehlen ausgeführt werden, auf Docker-Befehle.
> Durcharbeiten dieser exemplarischen Vorgehensweise aus einer PowerShell-Sitzung.

Im nächsten Schritt stellen Sie sicher, dass das System hat eine gültige IP-Adresse mit `Ipconfig` und notieren Sie diese Adresse für die spätere Verwendung.
```
ipconfig

Ethernet adapter Ethernet 3:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb::e
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb:a8c1:a3e:96b7:ffcb
   Link-local IPv6 Address . . . . . : fe80::a8c1:a3e:96b7:ffcb%5
   IPv4 Address. . . . . . . . . . . : 192.168.1.25
```

Wenn Sie statt einer Azure-VM arbeiten `Ipconfig` müssen Sie die öffentliche IP-Adresse der Azure-Computer zu erhalten.

![](media/newazure9.png)

###Schritt 1: Erstellen eines neuen Containers

Vor dem Erstellen einer Windows Server-Container mit Docker benötigen Sie den Namen oder die ID eines Exsisitng Container für Windows Server-Abbilds.

Um alle Bilder geladen werden, auf dem Host Container verwenden, finden Sie unter der `Docker Bilder` Befehl.

``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
windowsservercore   latest              9eca9231f4d4        30 hours ago        9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        30 hours ago        9.613 GB
```

Verwenden Sie nun `Docker ausführen` um einen neuen Windows Server-Container zu erstellen.
Mit diesem Befehl wie folgt wird den Daemon Docker erstellen einen neuen Container mit dem Namen "Dockerdemo" aus dem Abbild 'Windowsservercore', und öffnen Sie eine interaktive angewiesen (-es)-Konsole Sitzung (Cmd) mit dem Container.

``` PowerShell
docker run -it --name dockerdemo windowsservercore cmd
```
Nach Abschluss des Befehls werden Sie in einer Konsolen-Sitzung für den Container arbeiten.

Arbeiten in einem Container ist fast identisch mit der Arbeit mit Windows auf einem virtuellen oder physischen Computer installiert.
Sie können z. B. Befehle ausführen `Ipconfig` zum Zurückgeben der IP-Adresse des Containers, `Mkdir` ein neues Verzeichnis erstellen oder `Powershell` zum Starten einer PowerShell-Sitzung.
Fahren Sie fort, und nehmen Sie eine Änderung an dem Container, z. B. das Erstellen einer Datei oder eines Ordners.
Der folgende Befehl wird beispielsweise eine Datei erstellt die Netzwerkkonfigurationsdaten über den Container enthält.

``` PowerShell
ipconfig > c:\ipconfig.txt
```

Lesen Sie den Inhalt der Datei, um sicherzustellen, dass den Befehl erfolgreich ausgeführt.
Beachten Sie, dass die IP-Adresse, die in der Textdatei enthaltenen des Containers entspricht.

``` PowerShell
type c:\ipconfig.txt

Ethernet adapter vEthernet (Virtual Switch-94a3e12ad262b3059e08edc4d48fca3c8390e38c3b219023d4a0a4951883e658-0):

   Connection-specific DNS Suffix  . : 
   Link-local IPv6 Address . . . . . : fe80::cc1f:742:4126:9530%18
   IPv4 Address. . . . . . . . . . . : 172.16.0.2
   Subnet Mask . . . . . . . . . . . : 255.240.0.0
   Default Gateway . . . . . . . . . : 172.16.0.1
```

Jetzt, dass der Container geändert wurde, führen Sie Folgendes ein, um das Beenden der Konsole Sitzung platzieren Sie in der Konsole-Sitzung des Hosts Container zurück.

``` PowerShell
exit
```

Schließlich zu einer Liste von Containern für den Container finden Sie unter Host verwenden, der `Docker Ps – eine` Befehl.
Beachten Sie, dass in der Ausgabe ein Container mit der Bezeichnung "Dockerdemo" wurde erstellt.

``` PowerShell
docker ps -a

CONTAINER ID        IMAGE               COMMAND        CREATED             STATUS                     PORTS     NAMES
4f496dbb8048        windowsservercore   "cmd"          2 minutes ago       Exited (0) 2 minutes ago             dockerdemo
```

###Schritt 2: Erstellen Sie ein neues Container-Bild

Ein Bild kann nun von diesem Container vorgenommen werden.
Dieses Bild kann verhält sich wie eine Momentaufnahme des Containers und erneut bereitgestellt, oft.

Erstellen Sie ein neues Abbild führen Sie die folgenden.
Dieser Befehl weist das Modul Docker, erstellen Sie ein neues Bild mit dem Namen "Newcontainerimage", die alle Änderungen an den Container "Deckerdemo" enthalten sein sollen.

``` PowerShell
docker commit dockerdemo newcontainerimage
```

Um alle Bilder auf dem Host anzuzeigen, führen `Docker Bilder`.
Beachten Sie, dass ein neues Bild mit dem Namen "Newcontainerimage" erstellt wurde.

``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
newcontainerimage   latest              4f8ebcf0a334        2 minutes ago       9.613 GB
windowsservercore   latest              9eca9231f4d4        30 hours ago        9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        30 hours ago        9.613 GB
```

###Schritt 3: Erstellen von neuen Container aus Bild

Nun, da Sie ein benutzerdefinierter Container Bild haben, Bereitstellen Sie einen neuen Container mit dem Namen 'Newcontainer' von 'Newcontainerimage', und öffnen Sie eine interaktive Shell-Sitzung mit dem Container.

``` PowerShell
docker run –it --name newcontainer newcontainerimage cmd
```

Betrachten Sie das Laufwerk c:\ für diesen Container, und beachten Sie, dass die ipconfig.txt-Datei vorhanden ist.

![](media/docker3.png)

Beenden Sie den neu erstellten Container mit der Container Hosts Konsole zurückgegeben.

``` PowerShell
exit
```

In dieser Übung ergab, dass ein Abbild stammt aus einer geänderten Container alle Änderungen enthalten sein sollen.
Im Beispiel wird eine einfache Änderung war, zwar gilt die gleiche würden Sie Software in den Container, z. B. einen Webserver zu installieren.
Mithilfe dieser Methoden können benutzerdefinierte Abbilder erstellen, die Anwendung bereit Containern bereitgestellt werden soll.

###Schritt 4: Entfernen von Containern und Bilder

Um einen Container zu entfernen, wenn es nicht mehr benötigt verwenden die `Docker Rm` Befehl.
Der folgende Befehl entfernt den Container "Newcontainer".

``` PowerShell
docker rm newcontainer
```
Container-Abbilder zu entfernen, wenn sie nicht mehr sind nötig verwenden die `Docker Rmi` Befehl.
Ein Bild kann nicht entfernt werden, wenn es mit einem vorhandenen Container verwiesen wird.

Der folgende Befehl entfernt das Container-Abbild mit dem Namen "Newcontainerimage".
``` PowerShell
docker rmi newcontainerimage

Untagged: newcontainerimage:latest
Deleted: 4f8ebcf0a334601e75070a92294d993b0f182abb6f4c88740c75b05093e6acff
```

##Hosten von einem Webserver in einem Container

Im folgenden Beispiel wird einen praktikabler Anwendungsfall für Windows Server-Container gezeigt.
In dieser Übung enthaltenen Schritte führt Sie durch die Erstellung einer Web-Container Serverabbild, das zum Bereitstellen von Web-Applikationen in einem Windows Server-Container verwendet werden kann.

###Schritt 1 - Webserver-Software herunterladen

Server-Software müssen vor dem Erstellen eines Abbilds Container im Web heruntergeladen und auf dem Host Container bereitgestellt werden.
Wir werden die Nginx für Windows-Software in diesem Beispiel verwenden.
**Hinweis** dass dieser Schritt bei den Container-Host mit dem Internet verbunden sein.
Wenn dieser Schritt führt ein Auflösung Fehler Konnektivität oder den Namen die Netzwerkkonfiguration des Hosts Container überprüfen.

Führen Sie den folgenden Befehl auf dem Host Container zum Erstellen der Verzeichnisstruktur, die für dieses Beispiel verwendet werden.

``` PowerShell
mkdir c:\build\nginx\source
```

Führen Sie diesen Befehl auf dem Host Container zum Herunterladen der Software Nginx auf 'c:\nginx-1.9.3.zip'.

``` PowerShell
wget -uri 'http://nginx.org/download/nginx-1.9.3.zip' -OutFile "c:\nginx-1.9.3.zip"
```

Schließlich wird der folgende Befehl die Nginx-Software für die 'C:\build\nginx\source' extrahiert.


``` PowerShell
Expand-Archive -Path C:\nginx-1.9.3.zip -DestinationPath C:\build\nginx\source -Force
```

###Schritt 2: Erstellen von Web-Server-Image

Im vorherigen Beispiel, indem Sie manuell erstellt, aktualisiert und ein Container-Abbild erfasst.
In diesem Beispiel wird gezeigt, dass eine automatisierte Methode zum Erstellen von Container-Bildern, die mit einem Dockerfile.
Dockerfiles Anweisungen enthalten, die das Docker-Modul verwendet wird, einen Container zu erstellen, und übernehmen Sie den Container zu einem Container-Abbild.
Weitere Informationen über Dockerfiles, finden Sie unter [Dockerfile Verweis](https://docs.docker.com/reference/builder/).

Verwenden Sie den folgenden Befehl aus, um eine leere Dockerfile zu erstellen.

``` PowerShell
new-item -Type File c:\build\nginx\dockerfile
```
Öffnen Sie die Dockerfile mit Notepad.

```
notepad.exe c:\build\nginx\dockerfile
```

Kopieren Sie den folgenden Text in Editor, speichern Sie die Datei, und schließen Sie Editor.

``` PowerShell
FROM windowsservercore
LABEL Description="nginx For Windows" Vendor="nginx" Version="1.9.3"
ADD source /nginx
```

An diesem Punkt werden die Dockerfile in 'c:\build\nginx' und 'c:\build\nginx\source' extrahiert Nginx-Software.
Sie können nun das Web Container Serverabbild basierend auf den Anweisungen in der Dockerfile zu erstellen.
Führen Sie dazu den folgenden Befehl auf dem Host des Containers.

``` PowerShell
docker build -t nginx_windows C:\build\nginx
```
Dieser Befehl weist das Docker-Modul verwenden, die am Dockerfile `C:\build\nginx` ein Abbild mit dem Namen "Nginx_windows" erstellen.

Die Ausgabe sieht etwa wie folgt:

![](media/docker1.png)

Wenn abgeschlossen ist, sehen Sie sich die Bilder auf dem Host mit der `Docker Bilder` Befehl.
Ein neues Bild mit dem Namen "Nginx_windows" sollte angezeigt werden.
``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE

nginx_windows       latest              d792268338d0        5 seconds ago       9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        35 hours ago        9.613 GB
windowsservercore   latest              9eca9231f4d4        35 hours ago        9.613 GB
```

###Schritt 3 – Konfigurieren Sie Netzwerke für Container-Anwendung

Da Sie eine Website in einem Container gehostet werden im Zusammenhang mit einigen Netzwerken Konfigurationen vorgenommen werden müssen.
Zuerst muss eine Firewallregel auf dem Host Container erstellt werden, die Zugriff auf die Website ermöglichen.
In diesem Beispiel werden wir die Website über Port 80 zugreifen.
Führen Sie das folgende Skript aus, um diese Firewallregel zu erstellen.
Dieses Skript kann auf dem virtuellen Computer kopiert werden.


``` powershell
if (!(Get-NetFirewallRule | where {$_.Name -eq "TCP80"})) {
    New-NetFirewallRule -Name "TCP80" -DisplayName "HTTP on TCP/80" -Protocol tcp -LocalPort 80 -Action Allow -Enabled True
}
```

Wenn Sie von Azure arbeiten und nicht bereits einen Endpunkt des virtuellen Computers erstellt haben müssen Sie als Nächstes jetzt eine erstellen.
Weitere Informationen zum Azure-VM-Endpunkten finden Sie in diesem Artikel: [Azure VM-Endpunkte eingerichtet](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-set-up-endpoints/).

###Schritt 4: Bereitstellen der Container der Web-Server bereit

Führen den folgenden Befehl, um einen Windows Server-Container basiert, von der 'Nginx_windows' bereitstellen Container.
Erstellt einen neuen Container mit dem Namen 'Nginxcontainer' und starten eine konsolensitzung für die für den Container.
Der – p 80:80 Teil dieser Befehl erstellt eine Port-Zuordnung zwischen Port 80 auf dem Host auf Port 80 für den Container.


``` powershell
docker run -it --name nginxcontainer -p 80:80 nginx_windows cmd
```
Sobald innerhalb des Containers zu arbeiten, kann der Webserver Nginx gestartet werden und Web-Inhalte bereitgestellt werden.
Um den Nginx-Webserver zu starten, legen Sie zum Installationsverzeichnis von Nginx.

``` powershell
cd c:\nginx\nginx-1.9.3
```

Starten Sie den Nginx-Webserver.
``` powershell
start nginx
```
###Schritt 5: Zugriff auf die Container-gehosteten Website

Mit dem Webcontainer erstellt haben können Sie jetzt zur Kasse gehen die in den Container gehostete Anwendung.
Hierzu öffnen Sie einen Browser auf anderen Computer aus, und geben Sie `http://containerhost-ipaddress`.
Beachten Sie, dass Sie die IP-Adresse von Host-Container und der Container selbst nicht durchsuchen.
Bei Verwendung von virtuellen Azure-Computer werden die öffentlichen IP-Adresse oder Cloud-Dienst.


Wenn alles richtig konfiguriert wurde, sehen Sie die Nginx-Willkommensseite.

![](media/nginx.png)

An diesem Punkt können Sie die Website zu aktualisieren.
In Ihrer eigenen Beispielwebsite kopieren Sie, oder führen Sie den folgenden Befehl im Container Nginx-Willkommensseite durch eine Webseite "Hello World" zu ersetzen.

```powershell
powershell wget -uri 'https://raw.githubusercontent.com/Microsoft/Virtualization-Documentation/master/doc-site/virtualization/windowscontainers/quick_start/SampleFiles/index.html' -OutFile "C:\nginx\nginx-1.9.3\html\index.html"
```

Nachdem die Website aktualisiert wurde, navigieren Sie zurück zu `http://containerhost-ipaddress`.

![](media/hello.png)

> **Hinweis:** verwenden, wenn die Docker-Daemon-Einstellungen (z. B. den Port zu ändern, es überwacht, Remoteverbindung zu einem Container) ändern möchten, Sie zum Bearbeiten der Datei "C:\ProgramData\docker\runDockerDaemon.cmd" im Container müssen und Sie den Dienst mit PowerShell neu starten müssen, `Restart-Service-Docker`.

##Video zur exemplarischen Vorgehensweise

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Deploying-and-Managing-Windows-Server-Containers-with-Docker/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

##Nächste Schritte

Nun die Container einrichten sowie eine Einführung in die Tools, fahren Sie Ihren eigenen Sammelartikeleinheit apps zu erstellen.

Beachten Sie, dass dies ist ein **Vorschau** Fehler vorhanden sind, und wir haben viel Arbeit.
[Auf dieser Seite](../about/work_in_progress.md) enthält viele unserer bekannter Probleme.

Beachten Sie, dass es gibt einige bekannte Docker Befehle, die [funktionieren nicht](../about/work_in_progress.md#DockermanagementDockercommandsthatdontworkwithWindowsServerContainers) und einige, die nur [teilweise arbeiten](../about/work_in_progress.md#DockermanagementDockercommandsthatpartiallyworkwithWindowsServerContainers)

Wir sind auch Überwachung der [Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers) sehr genau.

Dazu gehören auch vorgefertigte Beispiele auf [GitHub](https://github.com/Microsoft/Virtualization-Documentation/tree/master/windows-server-container-samples).

-----------------------------------

[Zurück zur Startseite von Container](../containers_welcome.md)   
[Bekannte Probleme bei der aktuellen Version](../about/work_in_progress.md)



