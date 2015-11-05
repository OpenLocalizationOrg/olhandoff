MS. ContentId: d0a07897-5fd2-41a5-856d-dc8b499c6783
título: Administrar contenedores de servidor de Windows con PowerShell

#Inicio rápido: Contenedores de Windows Server y PowerShell

Este artículo le guiará a través de los fundamentos de administración de Windows Server contenedores con PowerShell.
Elementos que cubre incluirá crear contenedores de Windows Server y el contenedor de imágenes de Windows Server, quitar los contenedores de Windows Server y las imágenes de contenedor y finalmente implementar una aplicación en un contenedor de Windows Server.
Las lecciones aprendidas en este tutorial deben habilitar para comenzar a explorar la implementación y administración de Windows Server contenedores mediante PowerShell.

¿Tiene preguntas?
Pídale que en el <g id="0b8e5b55-7c84-4cc6-b206-88c666816b49CapsExtId1" ctype="x-linkText">foro Windows contenedores</g><g id="0b8e5b55-7c84-4cc6-b206-88c666816b49CapsExtId2" ctype="x-title"></g>.

> <g id="c2a31f13-96ba-4ec9-879e-96988f62e1c4" ctype="x-strong">Nota:</g> Windows Server contenedores creados con PowerShell actualmente no puede administrar con versa Docker y visa.
> Para crear contenedores con Docker en su lugar, vea <g id="b6283a9d-4377-4fb5-85a5-69cae9522953CapsExtId1" ctype="x-linkText">Inicio rápido: contenedores de Windows Server y Docker</g><g id="b6283a9d-4377-4fb5-85a5-69cae9522953CapsExtId2" ctype="x-title"></g>.
> <g id="4c5ab674-7be9-43b7-8ef6-cafe069dbda5" ctype="x-html"></g><g id="3ff71654-35f2-4757-8bd8-edb669b07227" ctype="x-html"></g> Si desea saber más, <g id="16b6d7a0-e45f-4958-8b86-549312a5437aCapsExtId1" ctype="x-linkText">Lea las preguntas más frecuentes</g><g id="16b6d7a0-e45f-4958-8b86-549312a5437aCapsExtId2" ctype="x-title"></g>.

##Requisitos previos

Para completar este tutorial los siguientes elementos deben ser en su lugar.

- Windows Server 2016 TP3 o posterior configurada con la característica de contenedores de Windows Server.
   Si ha completado a la Guía de instalación, se trata la máquina virtual que creó en Azure o Hyper-V.
- Este sistema debe estar conectado a una red y tener acceso a internet.

Si necesita configurar la característica de contenedor, consulte las guías siguientes: <g id="57aaf394-cbc3-456b-b50d-618f806815b6CapsExtId1" ctype="x-linkText">contenedor configuración en Azure</g><g id="57aaf394-cbc3-456b-b50d-618f806815b6CapsExtId2" ctype="x-title"></g> o <g id="632a2412-5164-4857-8682-132bf0ec157aCapsExtId1" ctype="x-linkText">contenedor de instalación de Hyper-V</g><g id="632a2412-5164-4857-8682-132bf0ec157aCapsExtId2" ctype="x-title"></g>.

##Administración de contenedor básico con PowerShell

Este primer ejemplo le guiará a través de los aspectos básicos de la creación y eliminación de contenedores de Windows Server y Windows Server contenedor imágenes con PowerShell.

Para comenzar el recorrido a través, registro en el contenedor Host de Windows Server System, verá un símbolo del sistema de Windows.

<g id="99aa5c88-ed5d-4b4d-a47a-8f17c5d450ac" ctype="x-linkText"></g>

Inicie una sesión de PowerShell escribiendo <g id="79fa383b-6c69-4688-b617-a2d9508f73de" ctype="x-code">powershell</g>.
Sabrá que se encuentra en una sesión de PowerShell cuando cambia el símbolo del sistema de <g id="6c3f1f37-329a-4348-a4e1-3f2b644704c9" ctype="x-code">C:\directory ></g> a <g id="43480075-ac9c-46d8-876a-1855cdf525bb" ctype="x-code">C:\directory PS ></g>.

```
C:\> powershell
Windows PowerShell
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\>
```

Utilice <g id="81ca8654-7a3a-4e43-9f8e-8e9b7bb8b1d6" ctype="x-code">Get-Command</g> para ver los comandos disponibles en el módulo de contenedores

```
PS C:\> Get-Command -Module containers

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Install-ContainerOSImage                           1.0.0.0    Containers
Function        Uninstall-ContainerOSImage                         1.0.0.0    Containers
Cmdlet          Add-ContainerNetworkAdapter                        1.0.0.0    Containers
Cmdlet          Connect-ContainerNetworkAdapter                    1.0.0.0    Containers
Cmdlet          Disconnect-ContainerNetworkAdapter                 1.0.0.0    Containers
Cmdlet          Export-ContainerImage                              1.0.0.0    Containers
Cmdlet          Get-Container                                      1.0.0.0    Containers
Cmdlet          Get-ContainerHost                                  1.0.0.0    Containers
Cmdlet          Get-ContainerImage                                 1.0.0.0    Containers
Cmdlet          Get-ContainerNetworkAdapter                        1.0.0.0    Containers
Cmdlet          Import-ContainerImage                              1.0.0.0    Containers
Cmdlet          Move-ContainerImageRepository                      1.0.0.0    Containers
Cmdlet          New-Container                                      1.0.0.0    Containers
Cmdlet          New-ContainerImage                                 1.0.0.0    Containers
Cmdlet          Remove-Container                                   1.0.0.0    Containers
Cmdlet          Remove-ContainerImage                              1.0.0.0    Containers
Cmdlet          Remove-ContainerNetworkAdapter                     1.0.0.0    Containers
Cmdlet          Set-ContainerNetworkAdapter                        1.0.0.0    Containers
Cmdlet          Start-Container                                    1.0.0.0    Containers
Cmdlet          Stop-Container                                     1.0.0.0    Containers
Cmdlet          Test-ContainerImage                                1.0.0.0    Containers
```


A continuación, asegúrese de que el sistema tiene una dirección IP válida utilizando <g id="ebb047b6-92ba-46a8-a063-82288b2fd5ad" ctype="x-code">ipconfig</g> y tome nota de esta dirección para su uso posterior.

```
ipconfig

Ethernet adapter Ethernet 3:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb::e
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb:a8c1:a3e:96b7:ffcb
   Link-local IPv6 Address . . . . . : fe80::a8c1:a3e:96b7:ffcb%5
   IPv4 Address. . . . . . . . . . . : 192.168.1.25
```

Si está trabajando desde una máquina virtual de Azure en lugar de utilizar <g id="66eede50-4b5c-4877-a06b-040e4f66ab54" ctype="x-code">ipconfig</g> debe obtener la dirección IP pública de la máquina Virtual de Azure.

<g id="d15ef803-5799-4fed-879f-b702d2e068c5" ctype="x-linkText"></g>

###Paso 1: crear un contenedor nuevo

Antes de crear un contenedor de Windows Server necesitará el nombre de una imagen de contenedor y el nombre de un conmutador virtual que se asociará al nuevo contenedor.

Utilice la <g id="1c3f5a12-83af-4add-b09d-52f8c4837c28" ctype="x-code">ContainerImage Get</g> comando para devolver una lista de imágenes de contenedor se carga en el host.
Tome nota del nombre de imagen que va a utilizar para crear el contenedor.
``` PowerShell
Get-ContainerImage

Name              Publisher    Version      IsOSImage
----              ---------    -------      ---------
WindowsServerCore CN=Microsoft 10.0.10514.0 True
```

Utilice la <g id="73e7f2f4-da63-4b31-b4d9-c412b1b02c69" ctype="x-code">Get-VMSwitch</g> comando para devolver una lista de modificadores de comandos disponibles en el host.
Tome nota del nombre del conmutador que se usará con el contenedor.

``` PowerShell
Get-VMSwitch

Name           SwitchType NetAdapterInterfaceDescription
----           ---------- ------------------------------
Virtual Switch NAT
```

Ejecute el siguiente comando para crear un contenedor.
Cuando se ejecuta <g id="d4b9463c-5bf4-40a0-acf5-bfa087cec0e9" ctype="x-code">nuevo contenedor</g> se asignar nombre al contenedor, especifique la imagen de contenedor y seleccione el conmutador de red para usar con el contenedor.
Observe que en este ejemplo que la salida se coloca en una variable $container.
Esto será útil más adelante en este ejercicio.

``` PowerShell
$container = New-Container -Name "MyContainer" -ContainerImageName WindowsServerCore -SwitchName "Virtual Switch"
```

Para ver una lista de contenedores en el host y compruebe que se creó el contenedor, utilice la <g id="25867921-14c8-49f6-a1dd-c18f48765e5c" ctype="x-code">Get Container</g> comando.
Observe que se ha creado un contenedor con el nombre de MyContainer, sin embargo, no se ha iniciado.

``` PowerShell
Get-Container

Name        State Uptime   ParentImageName
----        ----- ------   ---------------
MyContainer Off   00:00:00 WindowsServerCore
```

Para iniciar el contenedor, utilice <g id="5a7a5c5a-d18a-4837-87ac-6185392bc5ce" ctype="x-code">Inicio contenedor</g> proivding el nombre del contenedor.

``` PowerShell
Start-Container -Name "MyContainer"
```

Puede interactuar con los contenedores mediante comandos de comunicación remota de PowerShell como <g id="f3a10238-9e21-46fa-bebe-b056de315b6f" ctype="x-code">Invoke-Command</g>, o <g id="1b6aa0f0-d2b0-4ef7-8a68-1ccdb5a80954" ctype="x-code">Enter-PSSession</g>.
El ejemplo siguiente crea una sesión remota de PowerShell en el contenedor mediante el <g id="7d72bfae-0b85-4886-91c1-d28c57672feb" ctype="x-code">Enter-PSSession</g> comando.
Este comando necesita el identificador del contenedor para crear la sesión remota.
El identificador del contenedor se almacenó en la <g id="a4b644e9-b61f-4cc7-af76-73b0d64214e0" ctype="x-code">$container</g> variable cuando se creó el contenedor.

Tenga en cuenta que una vez creada la sesión remota el símbolo cambiará para incluir los primero 11 caracteres del Id. de contenedor <g id="5e05b2a2-8557-4a10-b805-9c5fa7a7dbb2" ctype="x-code">[2446380e-629]</g>.

``` PowerShell
Enter-PSSession -ContainerId $container.ContainerId -RunAsAdministrator

[2446380e-629]: PS C:\Windows\system32>
```

Un contenedor se puede administrar mucho como una máquina física o virtual.
Comando como <g id="01071d63-da03-4666-8ab7-34e334c1dd1f" ctype="x-code">ipconfig</g> para devolver la dirección IP del contenedor, <g id="ef801698-8209-409c-bcb4-b18bda18f668" ctype="x-code">mkdir</g> para crear un directorio en el contenedor y los comandos de PowerShell como <g id="18e8114e-a82b-4570-a594-2eeacf4792f9" ctype="x-code">Get-ChildItem</g> todo el trabajo.
Siga adelante y realizar un cambio en el contenedor, como la creación de un archivo o carpeta.
Por ejemplo, el comando siguiente crea un archivo que contiene datos de configuración de red sobre el contenedor.

``` PowerShell
ipconfig > c:\ipconfig.txt
```

Puede leer el contenido del archivo para asegurarse el comando se completó correctamente.
Observe que la dirección IP incluida en el archivo de texto coincide con el contenedor.

``` PowerShell
type c:\ipconfig.txt

Ethernet adapter vEthernet (Virtual Switch-E0D87408-325B-4818-ADB2-2EC7A2005739-0):

   Connection-specific DNS Suffix  . : corp.microsoft.com
   Link-local IPv6 Address . . . . . : fe80::400e:1e0e:591c:beef%18
   IPv4 Address. . . . . . . . . . . : 172.16.0.2
   Subnet Mask . . . . . . . . . . . : 255.240.0.0
   Default Gateway . . . . . . . . . : 172.16.0.1
```

Ahora que se ha modificado el contenedor, salga de la sesión remota de PowerShell.

``` PowerShell
exit
```

Detener el contenedor proporcionando el nombre del contenedor para el <g id="af899963-e9f7-4c23-bf5a-9dd471b258ba" ctype="x-code">Stop contenedor</g> comando.
Este comando se ha completado, estará en el control del contenedor host.

``` PowerShell
Stop-Container -Name "MyContainer"
```

###Paso 2: crear una nueva imagen de contenedor

Una imagen ahora se pueden realizar desde este contenedor.
Esta imagen se comportará como una instantánea del contenedor y se puede volver a implementarse varias veces.

Para crear una imagen nueva denominada 'newimage' Utilice el <g id="6dc4eae0-2d48-4f6d-b98f-44af9d938eb1" ctype="x-code">nueva ContainerImage</g> comando.
Cuando se usa este comando especificará el contenedor para capturar un nombre para la nueva imagen y metadatos adicionales como se ve a continuación.

``` PowerShell
$newimage = New-ContainerImage -ContainerName MyContainer -Publisher Demo -Name newimage -Version 1.0
```

Utilice <g id="b025f3b6-1b66-4487-befc-baf7228670fa" ctype="x-code">Get ContainerImage</g> para devolver una lista de imágenes del contenedor.
Observe que se ha creado una imagen nueva con el nombre 'newimage'.

``` PowerShell
Get-ContainerImage

Name              Publisher    Version      IsOSImage
----              ---------    -------      ---------
newimage          CN=Demo      1.0.0.0      False
WindowsServerCore CN=Microsoft 10.0.10254.0 True
```

###Paso 3: crear el contenedor de imagen

Ahora que ha creado una imagen personalizada del contenedor, siga adelante e implementar un nuevo contenedor de esta imagen.

Crear un contenedor denominado 'newcontainer' de la imagen de contenedor denominada 'newimage', el resultado a una variable denominada '$newcontainer'.

``` PowerShell
$newcontainer = New-Container -Name "newcontainer" -ContainerImageName newimage -SwitchName "Virtual Switch"
```

Inicie el nuevo contenedor.
``` PowerShell
Start-Container $newcontainer
```

Crear una sesión remota de PowerShell con el contenedor.
``` PowerShell
Enter-PSSession -ContainerId $newcontainer.ContainerId -RunAsAdministrator
```

Por último, tenga en cuenta que este nuevo contenedor contiene el archivo ipconfig.txt que creó anteriormente en este ejercicio.

``` PowerShell
type c:\ipconfig.txt

Ethernet adapter vEthernet (Virtual Switch-E0D87408-325B-4818-ADB2-2EC7A2005739-0):

   Connection-specific DNS Suffix  . : corp.microsoft.com
   Link-local IPv6 Address . . . . . : fe80::400e:1e0e:591c:beef%18
   IPv4 Address. . . . . . . . . . . : 172.16.0.2
   Subnet Mask . . . . . . . . . . . : 255.240.0.0
   Default Gateway . . . . . . . . . : 172.16.0.1
```

Una vez que haya terminado de trabajar con este contenedor, salga de la sesión remota de PowerShell.

``` PowerShell
exit
```

Este ejercicio ha demostrado que una imagen procedente de un contenedor modificado incluirá todas las modificaciones.
Aunque este ejemplo era una modificación simple de archivos, el mismo aplicaría si fuera a instalar software en el contenedor, como un servidor web.
Con estos métodos, imágenes personalizadas pueden crearse que implementará listo contenedores de aplicación.

###Paso 4: quitar contenedores e imágenes de contenedor

Para detener todos los contenedores de ejecución, ejecute el siguiente comando.
Si los contenedores están en un estado de detención cuando ejecuta este comando, recibirá una advertencia, que es correcta.

``` PowerShell
Get-Container | Stop-Container
```
Ejecute el siguiente procedimiento para quitar todos los contenedores.

``` PowerShell
Get-Container | Remove-Container -Force
```
Para quitar la imagen de contenedor con nombre 'newimage', ejecute lo siguiente.

``` PowerShell
Get-ContainerImage -Name newimage | Remove-ContainerImage -Force
```

##Hospedar un servidor Web en un contenedor

En el ejemplo siguiente se demuestra un caso de uso más práctico para los contenedores de Windows Server.
Los pasos incluidos en este ejercicio le guiará por la creación de una imagen de contenedor de servidor web que se puede utilizar para implementar las aplicaciones web hospedadas dentro de un contenedor de Windows Server.

###Paso 1: crear el contenedor de la imagen del sistema operativo Windows Server Core

Para crear una imagen de contenedor del servidor web, primero debe implementar e iniciar un contenedor de la imagen de sistema operativo de Windows Server Core.
``` PowerShell
$container = New-Container -Name webbase -ContainerImageName WindowsServerCore -SwitchName "Virtual Switch"
```

Inicie el contenedor.
``` PowerShell
Start-Container $container
```

Cuando el contenedor esté operativo, cree una sesión remota de PowerShell con el contenedor.
``` PowerShell
Enter-PSSession -ContainerId $container.ContainerId -RunAsAdministrator
```

###Paso 2: instalar el Software de servidor de Web

El siguiente paso es instalar el software de servidor web.
En este ejemplo se utilizará nginx para Windows.
Utilice los siguientes comandos para descargar y extraer el software nginx c:\nginx-1.9.3 automáticamente.
<g id="bd672555-718a-48b5-b6b8-1fbec8dd2cc1" ctype="x-strong">Nota</g> que este paso será necesario estar conectado a internet en el host del contenedor.
Si este paso produce un error de resolución de conectividad o nombre Compruebe la configuración de red del host del contenedor.

Descargue el software de nginx.
``` PowerShell
wget -uri 'http://nginx.org/download/nginx-1.9.3.zip' -OutFile "c:\nginx-1.9.3.zip"
```

Extraiga el software de nginx.
``` PowerShell
Expand-Archive -Path C:\nginx-1.9.3.zip -DestinationPath c:\ -Force
```
Esto es todo lo que necesita para completar la instalación del software de nginx.

Salga de la sesión remota de PowerShell.
``` PowerShell
exit
```

Detener el contenedor mediante el siguiente comando.
``` PowerShell
Stop-Container $container
```
###Paso 3: crear la imagen desde el contenedor del servidor Web

Con el contenedor modificado para incluir el software de servidor web nginx, ahora puede crear una imagen de este contenedor.
Para ello, ejecute el siguiente comando:
``` PowerShell
$webserverimage = New-ContainerImage -Container $container -Publisher Demo -Name nginxwindows -Version 1.0
```
Cuando haya completado, use la <g id="8586d945-8467-485d-ad64-27d9ef6a6320" ctype="x-code">ContainerImage Get</g> comando para validar que se ha creado la imagen.

``` PowerShell
Get-ContainerImage

Name              Publisher    Version      IsOSImage
----              ---------    -------      ---------
nginxwindows      CN=Demo      1.0.0.0      False
WindowsServerCore CN=Microsoft 10.0.10254.0 True
```

###Paso 4: implementación de contenedor lista de servidor Web

Para implementar un contenedor de servidores de Windows basado en la imagen 'nginxwindows', use la <g id="fb2f6730-478a-41f4-a9ea-b34b24c3251d" ctype="x-code">nuevo contenedor</g> comando de PowerShell.

``` PowerShell
$webservercontainer = New-Container -Name webserver1 -ContainerImageName nginxwindows -SwitchName "Virtual Switch"
```

Inicie el contenedor.
``` PowerShell
Start-Container $webservercontainer
```

Crear una sesión remota de PowerShell con el nuevo contenedor.
``` PowerShell
Enter-PSSession -ContainerId $webservercontainer.ContainerId -RunAsAdministrator
```

Una vez que trabaja dentro del contenedor, se puede iniciar el servidor web de nginx y ensayo de contenido web.
Para iniciar el servidor web de nginx, cambie el directorio de instalación de nginx.
``` PowerShell
cd c:\nginx-1.9.3\
```

Inicie el servidor web de nginx.
``` PowerShell
start nginx
```

Y salir de esta sesión de PS.
Se seguirán ejecutando el servidor web.
``` PowerShell
exit
```

###Paso 5: configurar la red de contenedor

Según la configuración del contenedor host y red, un contenedor o recibirá una dirección IP desde un servidor DHCP o el host del contenedor mediante la traducción de direcciones de red (NAT).
Este recorrido guiado por está configurado para usar NAT.
En esta configuración se asigna un puerto desde el contenedor a un puerto en el host del contenedor.
A continuación, se tiene acceso a la aplicación hospedada en el contenedor a través de la dirección IP o nombre del host del contenedor.
Por ejemplo si el puerto 80 del contenedor se asignó al puerto 55534 en el host de contenedor, una solicitud de http típica para la aplicación tendría el aspecto este http://contianerhost:55534.
Esto permite a un host de contenedor ejecutar muchos contenedores y permitir que las aplicaciones en estos contenedores responder a las solicitudes que usan el mismo puerto.

Para este laboratorio, necesitamos crear esta asignación de puerto.
Para ello, necesitamos saber la dirección IP del contenedor y la interna (aplicación) y puertos externos (host de contenedor) que se van a configurar.
En este ejemplo vamos simpleza y asignar el puerto 80 del contenedor al puerto 80 del host.
Mediante la <g id="792bb17d-d40d-494a-b0e4-e7116245e7ce" ctype="x-code">NetNatStaticMapping agregar</g> comando, el <g id="20441edd-c312-48b2-814f-3c8346f91bcc" ctype="x-code">: InternalIPAddress</g> será la dirección IP del contenedor que, para este tutorial, debe ser '172.16.0.2'.

``` PowerShell
Add-NetNatStaticMapping -NatName "ContainerNat" -Protocol TCP -ExternalIPAddress 0.0.0.0 -InternalIPAddress 172.16.0.2 -InternalPort 80 -ExternalPort 80
```
Cuando se ha creado la asignación de puertos también necesitará configurar una regla de firewall de entrada para el puerto configurado.
Para ello, para el puerto 80 ejecute el siguiente comando.
Esta secuencia de comandos se pueden copiar en la máquina virtual.

``` PowerShell
if (!(Get-NetFirewallRule | where {$_.Name -eq "TCP80"})) {
    New-NetFirewallRule -Name "TCP80" -DisplayName "HTTP on TCP/80" -Protocol tcp -LocalPort 80 -Action Allow -Enabled True
}
```

A continuación si trabaja en Azure y todavía no ha creado un extremo de la máquina Virtual debe crear uno ahora.
Para obtener más información sobre los extremos de la máquina virtual de Azure, consulte este artículo: <g id="a6608384-aafb-4a4b-b4cc-bcb4d2363837CapsExtId1" ctype="x-linkText">configurar los extremos de la máquina virtual de Azure</g><g id="a6608384-aafb-4a4b-b4cc-bcb4d2363837CapsExtId2" ctype="x-title"></g>.

###Paso 6: acceder al sitio Web hospedado de contenedor

Con el contenedor del servidor web creado, puede desproteger ahora la aplicación hospedada en el contenedor.
Para ello, abra un explorador en un equipo diferente y escriba <g id="79251e34-d46c-4f29-acdd-028363b2c2f9" ctype="x-code">http://containerhost-ipaddress</g>.
Observe que se está buscando en la dirección IP del Host de contenedor y no el propio contenedor.
Si está trabajando desde una máquina Virtual de Azure será la dirección IP pública o nombre del servicio de nube.

Si todo se ha configurado correctamente, verá la página de bienvenida de nginx.

<g id="1e432f82-42cc-487e-b716-91d6d1ff2670" ctype="x-linkText"></g>

En este momento, no dude en actualizar el sitio Web.
Copiar en su propio sitio Web de ejemplo, o utilice un sitio de ejemplo "Hello World" simple que se ha creado para esta demostración.
Para utilizar el ejemplo primero debe volver a establecer una sesión remota de PS con el contenedor.

En primer lugar, necesitará volver a crear la sesión de PS remota con el contenedor.
``` PowerShell
Enter-PSSession -ContainerId $webservercontainer.ContainerId -RunAsAdministrator
```
A continuación, ejecute el comando siguiente para descargar y reemplace el archivo index.html.

``` powershell
wget -uri 'https://raw.githubusercontent.com/Microsoft/Virtualization-Documentation/master/doc-site/virtualization/windowscontainers/quick_start/SampleFiles/index.html' -OutFile "C:\nginx-1.9.3\html\index.html"
```

Después de que se ha actualizado el sitio Web, vaya a <g id="fd7bbdcf-0234-4e8b-a2db-f7e365ad0f27" ctype="x-code">http://containerhost-ipaddress</g>.

<g id="a3dae21d-ee62-4d5a-adf8-4915bbd09f82" ctype="x-linkText"></g>

##Tutorial en vídeo

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Deploying-and-Managing-Windows-Server-Containers-with-PowerShell/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##Pasos siguientes

Ahora que ha configurado los contenedores y una introducción a las herramientas, vaya a crear sus propias aplicaciones de contenido.

Este es un proceso más completo <g id="6c96e594-f027-4118-ac85-3d8f84dc3220CapsExtId1" ctype="x-linkText">referencia de PowerShell</g><g id="6c96e594-f027-4118-ac85-3d8f84dc3220CapsExtId2" ctype="x-title"></g>.

Recuerde que se trata de un <g id="ca47b3a2-8490-46fb-9bf5-72d6ff9ab529" ctype="x-strong">vista previa</g> hay errores y tenemos una gran cantidad de trabajo en curso.
<g id="b9b849dd-f519-48a0-9b00-5084fa1df719CapsExtId1" ctype="x-linkText">Esta página</g><g id="b9b849dd-f519-48a0-9b00-5084fa1df719CapsExtId2" ctype="x-title"></g> contiene muchos de nuestros problemas conocidos.

También supervisemos la <g id="c67c1c82-f6a1-4497-8aeb-de69fb8b4ed0CapsExtId1" ctype="x-linkText">foros</g><g id="c67c1c82-f6a1-4497-8aeb-de69fb8b4ed0CapsExtId2" ctype="x-title"></g> muy de cerca.

También hay ejemplos creados previamente en <g id="4a918f36-4c11-417a-8d90-d56fa862e9a7CapsExtId1" ctype="x-linkText">GitHub</g><g id="4a918f36-4c11-417a-8d90-d56fa862e9a7CapsExtId2" ctype="x-title"></g>.

-----------------------------------

<g id="197f70f0-a1a9-468c-83c0-9f1e7cd1c777CapsExtId1" ctype="x-linkText">Volver a la página principal de contenedor</g><g id="197f70f0-a1a9-468c-83c0-9f1e7cd1c777CapsExtId2" ctype="x-title"></g>   
<g id="f13ad086-b229-4c6d-891b-cf692d0e8d04CapsExtId1" ctype="x-linkText">Problemas conocidos de la versión actual</g><g id="f13ad086-b229-4c6d-891b-cf692d0e8d04CapsExtId2" ctype="x-title"></g>




