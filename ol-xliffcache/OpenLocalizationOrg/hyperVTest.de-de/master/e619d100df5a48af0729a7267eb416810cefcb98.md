MS. ContentId: 6C7EB25D-66FB-4B6F-AB4A-79D6BB424637
Titel: Stellen Sie einen neue Management-Dienst

#Stellen Sie einen neue Management-Dienst

In diesem Dokument werden die VM-Dienste, die auf Hyper-V-Sockets und die ersten Schritte mit ihnen aufbaut.

##Was ist eine VM-Dienst?

Hinzufügen von diesem Satz für HO Kont Testverfahren.
VM-Dienste sind Dienste, die die Hyper-V-Hosts und virtuellen Maschinen auf dem Host ausgeführte umfassen.

Hyper-V jetzt (Windows 10 und Server 2016 +) bietet eine Verbindung von außerhalb des Netzwerks der Aufteilung der Host/virtual Machine-Grenze Beibehaltung Grundvoraussetzungen Hyper-V, um Mandanten/Hoster Isolation-Steuerelement erstellen kann und diagnosable.

Hyper-V bietet weiterhin einen Basissatz von in-Box-Dienste (Integrationsservices) für die Grundlagen (z. B. Synchronisierung) und häufige Anfragen, die wir erhalten, aber jetzt kann jeder schreiben und Bereitstellen einen VM-Dienst, wenn erforderlich.

PowerShell Direct ist ein integriertes Beispiel einer VM-Dienst.

##Was ist ein Socket Hyper-V?

Hyper-V-Sockets sind wie TCP-Sockets mit keine Abhängigkeit vom Netzwerk.
Verwenden von Hyper-V-Sockets, Dienste können unabhängig von den Netzwerkstapel ausgeführt und alle Datenfluss bleibt im Arbeitsspeicher des Hosts.

##Systemanforderungen

**Unterstützte Host-BS**
*   Windows-10
*   Windows Server-Technical Preview 3
*   Zukünftige Versionen (Server 2016 +)

**Unterstützte Gastbetriebssysteme**
*   Windows-10
*   Windows Server-Technical Preview 3
*   Zukünftige Versionen (Server 2016 +)
*   Linux

##Stärken und Schwächen

Kernel-Modus oder im Benutzermodus  
Nur-Datenstrom    
Kein Block Arbeitsspeicher also nicht optimal für Backup-video



##Erste Schritte

Dieses Handbuch wird davon ausgegangen, dass Sie mit der Socket in C/C++-Programmierung vertraut sind.

###Schritt 1: Registrieren Sie den Dienst auf dem Hyper-V-host

Um einen benutzerdefinierten Dienst integriert mit Hyper-V verwenden, muss der neue Dienst mit dem Hyper-V-Host-Registrierung registriert werden.

Durch die Registrierung des Diensts in der Registrierung erhalten Sie folgende Aktionen ausführen:
*  WMI-Verwaltung für aktivieren, deaktivieren und die verfügbaren Dienste auflisten
*  Klicken Sie auf die Liste der Dienste, die direkt mit virtuellen Computern kommunizieren.

** Registrierungsspeicherort und Informationen **



``` 
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\VirtualDevices\6C09BB55-D683-4DA0-8931-C9BF705F6480\GuestCommunicationServices\
```
In diesem Registrierungsspeicherort sehen Sie mehrere GUIDS.
Unsere integrierte Dienste sind.

Die Informationen in der Registrierung nach Dienst:
* `Dienst-GUID`
     

    * `ElementName (REG_SZ)` – Dies ist der Dienst-Anzeigename

Um einen eigenen Dienst zu registrieren, erstellen Sie einen neuen Registrierungsschlüssel, die über eine eigene GUID und den Anzeigenamen.

Der Registrierungseintrag sieht folgendermaßen aus:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\GuestCommunicationServices\
    999E53D4-3D5C-4C3E-8779-BED06EC056E1\
        ElementName REG_SZ  VM Session Service
    YourGUID\
        ElementName REG_SZ  Your Service Friendly Name
```

> ** Tipp: **  zum Generieren einer GUID in PowerShell, und kopieren Sie ihn in die Zwischenablage, ausführen:
> 

``` PowerShell
[System.Guid]::NewGuid().ToString() | clip.exe
```



###Schritt 2: Erstellen eines einfachen hostseitige-Diensts

###Schritt 3: Erstellen eines einfachen Gastseite Diensts

##Weitere Informationen zu AF_HYPERV

Da Hyper-V-Sockets nicht Netzwerkstapel, TCP/IP, DNS, abhängen benötigt usw. der Socket-Endpunkt eine IP-Adressen, nicht Hostname, Format, die nach wie vor die Verbindung beschreibt.
Anstelle einer IP-Adresse oder ein Hostname abhängen auf zwei GUIDS stark AF_HYPERV Endpunkte:


* VM-ID – ist dies die eindeutige ID, die pro virtueller Maschine zugewiesen.
    Eine VM-ID kann mit dem folgenden PowerShell-Ausschnitt gefunden werden.
```PowerShell
(Get-VM -Name vmname).Id
```
* Dienst-ID-GUID, die unter dem der Dienst in der Hyper-V-Host-Registrierung registriert ist.
    Finden Sie unter [Registrieren eines neuen Dienstes](#GettingStarted).

Für Verbindungen mit einem Dienst auf dem Host an den Dienst auf einem virtuellen Computer:  
VMID und die Dienst-ID
Für Verbindungen mit einem Dienst auf einem virtuellen Computer mit dem Dienst auf dem Host:  
0 (null) GUID und die Dienst-ID

##Unterstützte Socket-Befehle

Socket()
BIND()
Verbinden)
Send()
Listen()
Accept()







