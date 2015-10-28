MS-TEST:::ms.ContentId: 3fdd690d-4259-4066-8781-360bb0554512
title: Running Apps in Windows Containers

#MS-TEST:::Application Compatability in Windows Server Containers

MS-TEST:::Updating contents on 27-Oct for testing.
MS-TEST:::Adding this sentence for testing HO-HB process.
MS-TEST:::Is something not on this list?
MS-TEST:::Let us know what fails and succeeds in your environment via [the forums](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

##MS-TEST:::Which applications run in a Windows Server Container

MS-TEST:::We have tried to running the following applications in a Windows Server Container.
MS-TEST:::These results do not guarantee that the application is working.
MS-TEST:::The sole purpose is to share our experience.

| MS-TEST:::**Name**| MS-TEST:::**Version**| MS-TEST:::**Does it work?**| MS-TEST:::**Comment**|
|:-----|:-----|:-----|:-----|
| MS-TEST:::.NET| MS-TEST:::3.5| MS-TEST:::No| MS-TEST:::Fails to install properly|
| MS-TEST:::.NET| MS-TEST:::4.6| MS-TEST:::Yes| MS-TEST:::Included in base image|
| MS-TEST:::.NET CLR| MS-TEST:::5 beta 6| MS-TEST:::Yes| MS-TEST:::Both, x64 and x86|
| MS-TEST:::Active Python| MS-TEST:::3.4.1| MS-TEST:::Yes| |
| MS-TEST:::Apache CouchDB| MS-TEST:::1.6.1| MS-TEST:::No| |
| MS-TEST:::Apache HTTPD| MS-TEST:::2.4| MS-TEST:::Yes| |
| MS-TEST:::Apache Tomcat| MS-TEST:::8.0.24 x64| MS-TEST:::Yes| |
| MS-TEST:::ASP.NET| MS-TEST:::3.5| MS-TEST:::No| |
| MS-TEST:::ASP.NET| MS-TEST:::4.5| MS-TEST:::No| |
| MS-TEST:::ASP.NET| MS-TEST:::5 beta 6| MS-TEST:::Yes| MS-TEST:::Both, x64 and x86|
| MS-TEST:::Erlang/OTP| MS-TEST:::18.0| MS-TEST:::No| |
| MS-TEST:::FileZilla FTP Server| MS-TEST:::0.9| MS-TEST:::Yes| MS-TEST:::Has to be installed through an RDP session  into the container|
| MS-TEST:::Go Progamming Language| MS-TEST:::1.4.2| MS-TEST:::Yes| |
| MS-TEST:::Internet Information Service| MS-TEST:::10.0| MS-TEST:::Yes| |
| MS-TEST:::Java| MS-TEST:::1.8.0_51| MS-TEST:::Yes| MS-TEST:::Use the server version.MS-TEST:::The client version does not install properly|
| MS-TEST:::Jetty| MS-TEST:::9.3| MS-TEST:::Partially| MS-TEST:::Running demo-base fails|
| MS-TEST:::MineCraft Server| MS-TEST:::1.8.5| MS-TEST:::Yes| |
| MS-TEST:::MongoDB| MS-TEST:::3.0.4| MS-TEST:::Yes| |
| MS-TEST:::MySQL| MS-TEST:::5.6.26| MS-TEST:::Yes| |
| MS-TEST:::NGinx| MS-TEST:::1.9.3| MS-TEST:::Yes| |
| MS-TEST:::Node.js| MS-TEST:::0.12.6| MS-TEST:::Partially| MS-TEST:::Running node with js files works.MS-TEST:::NPM fails to download packages.MS-TEST:::Running node interactively does not work properly.|
| MS-TEST:::PHP| MS-TEST:::5.6.11| MS-TEST:::Partially| MS-TEST:::With Apache, IIS via FastCGI currently does not work.|
| MS-TEST:::PostgreSQL| MS-TEST:::9.4.4| MS-TEST:::Yes| |
| MS-TEST:::Python| MS-TEST:::3.4.3| MS-TEST:::Yes| |
| MS-TEST:::R| MS-TEST:::3.2.1| MS-TEST:::No| |
| MS-TEST:::RabbitMQ| MS-TEST:::3.5.x| MS-TEST:::Yes| MS-TEST:::Has to be installed through an RDP session  into the container|
| MS-TEST:::Redis| MS-TEST:::2.8.2101| MS-TEST:::Yes| |
| MS-TEST:::Ruby| MS-TEST:::2.2.2| MS-TEST:::Yes| MS-TEST:::Both, x64 and x86|
| MS-TEST:::Ruby on Rails| MS-TEST:::4.2.3| MS-TEST:::Yes| |
| MS-TEST:::SQLite| MS-TEST:::3.8.11.1| MS-TEST:::Yes| |
| MS-TEST:::SQL Server Express| MS-TEST:::2014 LocalDB| MS-TEST:::No| |
| MS-TEST:::Sysinternals Tools| MS-TEST:::*| MS-TEST:::Yes| MS-TEST:::Only tried those not requiring a GUI.MS-TEST:::PsExec does not work by current design|
##MS-TEST:::What Optional Windows Features can I install?

MS-TEST:::The following Windows Optional Features have been confirmed as being able to install.
MS-TEST:::Many do not function once they are installed at this point in time.

* MS-TEST:::AD-Certificate
* MS-TEST:::ADCS-Cert-Authority
* MS-TEST:::File-Services
    * MS-TEST:::FS-FileServer
    * MS-TEST:::FS-VSS-Agent
* MS-TEST:::DirectAccess-VPN
* MS-TEST:::Routing
* MS-TEST:::Remote-Desktop-Services
* MS-TEST:::VolumeActivation
* MS-TEST:::Web-Server
* MS-TEST:::Web-WebServer
* MS-TEST:::Web-Common-Http
* MS-TEST:::Web-Default-Doc
* MS-TEST:::Web-Dir-Browsing
* MS-TEST:::Web-Http-Errors
* MS-TEST:::Web-Static-Content
* MS-TEST:::Web-Http-Redirect
* MS-TEST:::Web-DAV-Publishing
* MS-TEST:::Web-Health
* MS-TEST:::Web-Http-Logging
* MS-TEST:::Web-Custom-Logging
* MS-TEST:::Web-Log-Libraries
* MS-TEST:::Web-ODBC-Logging
* MS-TEST:::Web-Request-Monitor
* MS-TEST:::Web-Performance
* MS-TEST:::Web-Stat-Compression
* MS-TEST:::Web-Dyn-Compression
* MS-TEST:::Web-Security
* MS-TEST:::Web-Filtering
* MS-TEST:::Web-Basic-Auth
* MS-TEST:::Web-CertProvider
* MS-TEST:::Web-Client-Auth
* MS-TEST:::Web-Digest-Auth
* MS-TEST:::Web-Cert-Auth
* MS-TEST:::Web-IP-Security
* MS-TEST:::Web-Url-Auth
* MS-TEST:::Web-Windows-Auth
* MS-TEST:::Web-App-Dev
* MS-TEST:::Web-AppInit
* MS-TEST:::Web-CGI
* MS-TEST:::Web-ISAPI-Ext
* MS-TEST:::Web-ISAPI-Filter
* MS-TEST:::Web-Includes
* MS-TEST:::Web-WebSockets
* MS-TEST:::Web-Mgmt-Compat
* MS-TEST:::Web-Metabase
* MS-TEST:::BitLocker
* MS-TEST:::EnhancedStorage
* MS-TEST:::GPMC
* MS-TEST:::Isolated-UserMode
* MS-TEST:::Server-Media-Foundation
* MS-TEST:::MSMQ-DCOM
* MS-TEST:::MultiPoint-Connector-Feature
* MS-TEST:::qWave
* MS-TEST:::RDC
* MS-TEST:::RSAT-Feature-Tools-BitLocker
* MS-TEST:::RSAT-Clustering-PowerShell
* MS-TEST:::RSAT-Clustering-AutomationServer
* MS-TEST:::RSAT-Clustering-CmdInterface
* MS-TEST:::RSAT-Shielded-VM-Tools
* MS-TEST:::RSAT-AD-Tools
* MS-TEST:::RSAT-AD-PowerShell
* MS-TEST:::RSAT-ADDS
* MS-TEST:::RSAT-AD-AdminCenter
* MS-TEST:::RSAT-ADDS-Tools
* MS-TEST:::RSAT-ADLDS
* MS-TEST:::Hyper-V-PowerShell
* MS-TEST:::UpdateServices-API
* MS-TEST:::RSAT-NetworkController
* MS-TEST:::Windows-Fabric-Tools
* MS-TEST:::RSAT-HostGuardianService
* MS-TEST:::FS-SMBBW
* MS-TEST:::Storage-Replica
* MS-TEST:::Telnet-Client
* MS-TEST:::WAS
    * MS-TEST:::WAS-Process-Model
    * MS-TEST:::WAS-Config-APIs
* MS-TEST:::Windows-Server-Backup
* MS-TEST:::Migration

MS-TEST:::Is something not on this list?
MS-TEST:::Let us know what fails and succeeds in your environment via [the forums](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).




