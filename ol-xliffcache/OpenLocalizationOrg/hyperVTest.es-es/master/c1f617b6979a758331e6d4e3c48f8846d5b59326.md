MS. ContentId: 3fdd690d-4259-4066-8781-360bb0554512
título: aplicaciones de ejecución en contenedores de Windows

#Compatibilidad de aplicaciones en Windows Server contenedores

Actualizar contenido en el 27 de octubre para las pruebas.
Agregar esta frase para probar el proceso de HO HB.
¿Algo no está en esta lista?
Háganos saber lo que se produce un error y se ejecuta correctamente en su entorno mediante [los foros](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

##Las aplicaciones que se ejecutan en un contenedor de Windows Server

Hemos intentado ejecutando las siguientes aplicaciones en un contenedor de Windows Server.
Estos resultados no garantizan que la aplicación funciona.
El único propósito es compartir nuestra experiencia.

| **Nombre**| **Versión**| **¿Funciona?**| **Comentario**|
|:-----|:-----|:-----|:-----|
| .NET| 3.5| No| No se puede instalar correctamente|
| .NET| 4.6| Sí| Incluido en la imagen base|
| CLR DE .NET| 5 beta 6| Sí| X 64 y x 86|
| Active Python| 3.4.1| Sí| |
| CouchDB Apache| 1.6.1| No| |
| Apache HTTPD| 2.4| Sí| |
| Apache Tomcat| 8.0.24 x 64| Sí| |
| ASP.NET| 3.5| No| |
| ASP.NET| 4.5| No| |
| ASP.NET| 5 beta 6| Sí| X 64 y x 86|
| Erlang/OTP| 18.0| No| |
| Servidor de FTP de FileZilla| 0.9| Sí| Debe instalarse a través de una sesión de RDP en el contenedor|
| Consulte lenguaje de programación| 1.4.2| Sí| |
| Servicio Internet Information Server| 10.0| Sí| |
| Java| 1.8.0_51| Sí| Utilice la versión del servidor.La versión del cliente no se instala correctamente|
| Jetty| 9.3| Parcialmente| Se produce un error de base de demostración de ejecución|
| Servidor MineCraft| 1.8.5| Sí| |
| MongoDB| 3.0.4| Sí| |
| MySQL| 5.6.26| Sí| |
| NGinx| 1.9.3| Sí| |
| Node.js| 0.12.6| Parcialmente| Ejecución de nodo con js archivos funciona.No se puede descargar paquetes NPM.Ejecuta de forma interactiva el nodo no funciona correctamente.|
| PHP| 5.6.11| Parcialmente| Con Apache, IIS a través de FastCGI actualmente no funciona.|
| PostgreSQL| 9.4.4| Sí| |
| Python| 3.4.3| Sí| |
| R| 3.2.1| No| |
| RabbitMQ| 3.5| Sí| Debe instalarse a través de una sesión de RDP en el contenedor|
| Redis| 2.8.2101| Sí| |
| Ruby| 2.2.2| Sí| X 64 y x 86|
| Ruby on Rails| 4.2.3| Sí| |
| SQLite| 3.8.11.1| Sí| |
| SQL Server Express| LocalDB de 2014| No| |
| Herramientas de Sysinternals| *| Sí| Las que no requieren una GUI intentar solo.Diseño actual no funciona PsExec|
##¿Qué características opcionales de Windows puede instalar?

Las siguientes características opcionales de Windows se han confirmado como para poder instalar.
Muchos no funcionan una vez que están instalados en este momento.

* Certificado de AD
* Autoridad de certificado ADCS
* Servicios de archivo
   * FileServer FS
   * Agente de VSS de FS
* VPN de DirectAccess
* Enrutamiento
* Servicios de escritorio remoto
* VolumeActivation
* Servidor Web
* Web-WebServer
* Web-Common-Http
* Web-Default-Doc
* Exploración Web-Dir
* Errores de Http de Web
* Contenido estático de Web
* Redirección de Http de Web
* Publicación en Web-DAV
* Estado de Web
* Registro de Http de Web
* Registro de Web personalizado
* Bibliotecas de registro de Web
* Registro de ODBC Web
* Monitor de solicitudes Web
* Rendimiento Web
* Web-Stat-Compression
* Compresión de Dyn Web
* Seguridad en la Web
* Filtrado Web
* Web-Basic-Auth
* CertProvider Web
* Autenticación de cliente Web
* Autenticación de texto implícita de Web
* Autenticación de certificado de Web
* Seguridad de IP de Web
* Dirección Url de Web de autenticación
* Autenticación de Windows de Web
* Desarrollo de aplicaciones Web
* Web AppInit
* CGI Web
* Web-ISAPI-Ext
* Filtro de ISAPI de Web
* Incluye Web
* WebSockets Web
* Compatibilidad de administración de Web
* Metabase de Web
* BitLocker
* EnhancedStorage
* GPMC
* Modo de usuario aislada
* Server-Media-Foundation
* DCOM DE MSMQ
* Característica de conector de multiPoint
* qWave
* RDC
* RSAT-Feature-Tools-BitLocker
* PowerShell clústeres RSAT
* Agrupación en clústeres RSAT-AutomationServer
* Agrupación en clústeres RSAT-CmdInterface
* RSAT-estará protegido-VM-Tools
* Herramientas de AD RSAT
* RSAT PowerShell de AD
* AGREGA RSAT
* RSAT-AD-AdminCenter
* Herramientas RSAT agrega
* RSAT-ADLDS
* Hyper-V PowerShell
* UpdateServices de API
* RSAT NetworkController
* Herramientas de Windows Fabric
* RSAT HostGuardianService
* FS-SMBBW
* Réplica de almacenamiento
* Cliente Telnet
* FUE
   * Modelo de proceso se ha
   * API de configuración se ha
* Backup de Windows Server
* Migración

¿Algo no está en esta lista?
Háganos saber lo que se produce un error y se ejecuta correctamente en su entorno mediante [los foros](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).




