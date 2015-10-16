MS. ContentId: 3fdd690d-4259-4066-8781-360bb0554512
Titel: ausgeführten Apps in Windows-Containern

#Anwendung der Anwendungskompatibilität in Windows Server-Containern

Hinzufügen von diesem Satz für HO Kont Testverfahren.
Ist etwas nicht in dieser Liste?
Lassen Sie uns wissen, was ein Fehler auftritt und erfolgreich in Ihrer Umgebung über [in den Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

##Führen Sie die Anwendung in einem Windows Server-Container

Wir haben versucht, auf die folgenden Programme in einem Windows Server-Container ausgeführt werden.
Diese Ergebnisse garantieren nicht, dass die Anwendung ausgeführt wird.
Der einzige Zweck besteht unsere Erfahrung freigeben.

| **Name**| **Version**| **Funktioniert das?**| **Anmerkungen**|
|:-----|:-----|:-----|:-----|
| .NET| 3.5| Nein| Nicht ordnungsgemäß installiert.|
| .NET| 4.6| Ja| Im Basisabbild enthalten|
| .NET CLR| 5 Beta 6| Ja| X 64- und X 86|
| Aktive Python| 3.4.1| Ja| |
| Apache CouchDB| 1.6.1| Nein| |
| Apache HTTPD| 2.4| Ja| |
| Apache Tomcat| 8.0.24 X 64| Ja| |
| ASP.NET| 3.5| Nein| |
| ASP.NET| 4.5| Nein| |
| ASP.NET| 5 Beta 6| Ja| X 64- und X 86|
| Erlang/OTP| 18.0| Nein| |
| FileZilla FTP-Server| 0.9| Ja| In den Container über eine RDP-Sitzung installiert werden muss|
| Gehen Sie Progamming Sprache| 1.4.2| Ja| |
| Internet-Informationsdienste| 10.0| Ja| |
| Java| 1.8.0_51| Ja| Verwenden Sie die Serverversion.Die Clientversion ist nicht ordnungsgemäß installiert.|
| Jetty| 9.3| Teilweise| Ausführen von Demo-Basis ein Fehler auftritt.|
| MineCraft-Server| 1.8.5| Ja| |
| MongoDB| 3.0.4| Ja| |
| MySQL| 5.6.26| Ja| |
| NGinx| 1.9.3| Ja| |
| Node.js| 0.12.6| Teilweise| Ausführen von Knoten mit Js-Dateien funktioniert.NPM kann keine Pakete herunterzuladen.Interaktives Ausführen von Knoten funktioniert nicht ordnungsgemäß.|
| PHP| 5.6.11| Teilweise| Mit Apache wird IIS mit FastCGI derzeit nicht ausgeführt.|
| PostgreSQL| 9.4.4| Ja| |
| Python| 3.4.3| Ja| |
| R| 3.2.1| Nein| |
| RabbitMQ| 3.5.x| Ja| In den Container über eine RDP-Sitzung installiert werden muss|
| Redis| 2.8.2101| Ja| |
| Ruby| 2.2.2| Ja| X 64- und X 86|
| Ruby on Rails| 4.2.3| Ja| |
| SQLite| 3.8.11.1| Ja| |
| SQL Server Express| 2014 LocalDB| Nein| |
| Sysinternals-Tools| *| Ja| Versucht, nur diejenigen, die eine GUI nicht.PsExec kann nicht vom aktuellen Entwurf verwendet werden.|
##Welche optionale Windows-Features können werden installiert?

Die folgenden optionalen Windows-Funktionen haben bestätigt wurde, als zu installieren.
Viele funktionieren nicht, wenn sie zu diesem Zeitpunkt installiert sind.

* AD-Zertifikat
* ADCS Zertifizierungsstelle
* Dateidienste
    * EA-Dateiserver
    * EA-VSS-Agent
* DirectAccess-VPN
* Routing
* Remote Desktop Services
* VolumeActivation
* Web-Server
* Web-WebServer
* Web-Common-Http
* Web-Default-Doc
* Web-Dir-Browsing
* Web-Http-Fehler
* Statische Webinhalte
* Web-Http-Umleitung
* DAV-Webpublishing
* Web-Integrität
* Web-Http-Protokollierung
* Web-Custom-Protokollierung
* Web-Log-Libraries
* Web-ODBC-Protokollierung
* Web-Request-Monitor
* Leistung des Webservers
* Web-Stat-Compression
* Web-Dyn-Komprimierung
* Web-Sicherheit
* Web-Filterung
* Web-Basic-Auth
* Web-CertProvider
* Web-Client-Authentifizierung
* Web-Digest-Authentifizierung
* Web-Cert-Auth
* Web-IP-Sicherheit
* Web-Url-Auth
* Web-Windows-Authentifizierung
* Web-App-Entwickler
* Web-AppInit
* Web-CGI
* Web-ISAPI-Erweiterung
* Web-ISAPI-Filter
* Web enthält
* Web-WebSockets
* Web-Mgmt-Anwendungskompatibilität
* Web-Metabasis
* BitLocker
* EnhancedStorage
* GPMC
* Isolierte UserMode
* Server-Media-Foundation
* MSMQ-DCOM
* MultiPoint-Connector-Funktion
* qWave
* RDC
* RSAT-Feature-Tools-BitLocker
* RSAT-Clustering-PowerShell
* RSAT-Clustering-automationserver umgewandelt
* RSAT-Clustering-CmdInterface
* RSAT-abgeschirmt-VM-Tools
* RSAT-AD-Tools
* RSAT-AD-PowerShell
* REMOTESERVER-VERWALTUNGSTOOLS WIRD HINZUGEFÜGT
* RSAT-AD-AdminCenter
* RSAT-fügt-Tools
* RSAT-ADLDS
* Hyper-V-PowerShell
* UpdateServices-API
* Remoteserver-Verwaltungstools NetworkController
* Windows-Fabric-Tools
* Remoteserver-Verwaltungstools HostGuardianService
* EA-SMBBW
* Speicher-Replikat
* Telnet-Client
* WURDE
    * WAR-Prozessmodell
    * WAR-Config-APIs
* Windows Server-Sicherung
* Migration

Ist etwas nicht in dieser Liste?
Lassen Sie uns wissen, was ein Fehler auftritt und erfolgreich in Ihrer Umgebung über [in den Foren](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).




