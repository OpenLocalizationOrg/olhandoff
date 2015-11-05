MS. ContentId: 347fa279-d588-4094-90ec-8c2fc241f5b6
título: Administrar contenedores de Windows Server con Docker

#Inicio rápido: Los contenedores de Windows Server y Docker

Este artículo le guiará a través de los fundamentos de la administración de windows Server contenedores con Docker.
Elementos que cubre incluirá crear contenedores de Windows Server y el contenedor de imágenes de Windows Server, quitar los contenedores de Windows Server y las imágenes de contenedor y finalmente implementar una aplicación en un contenedor de Windows Server.
Las lecciones aprendidas en este tutorial deben habilitar para comenzar a explorar la implementación y administración de Windows Server contenedores mediante Docker.

¿Tiene preguntas?
Pídale que en el <g id="23b19220-0c01-479e-998c-5789423e719dCapsExtId1" ctype="x-linkText">foro Windows contenedores</g><g id="23b19220-0c01-479e-998c-5789423e719dCapsExtId2" ctype="x-title"></g>.

> <g id="0c9999f2-3cee-4a59-9d05-acd7d4f7b90d" ctype="x-strong">Nota:</g> contenedores de Windows creados con PowerShell actualmente no puede administrar con versa Docker y visa.
> Para crear contenedores con PowerShell, vea  <g id="da07fa58-f714-4e18-971b-d411a9d120b0CapsExtId1" ctype="x-linkText">Inicio rápido: contenedores de Windows Server y PowerShell</g><g id="da07fa58-f714-4e18-971b-d411a9d120b0CapsExtId2" ctype="x-title"></g>.
> <g id="a6e8132e-f614-41d9-8a6a-b31eb75c3a85" ctype="x-html"></g><g id="41b929b2-63f9-4dca-b0b7-1ef8c34bb8f7" ctype="x-html"></g> Si desea saber más, <g id="f1bd0aa9-6b4b-49f9-ab0f-a19646244776CapsExtId1" ctype="x-linkText">Lea las preguntas más frecuentes</g><g id="f1bd0aa9-6b4b-49f9-ab0f-a19646244776CapsExtId2" ctype="x-title"></g>.

##Requisitos previos

Para completar este tutorial los siguientes elementos deben ser en su lugar.

- Windows Server 2016 TP3 o posterior está configurado con la función de contenedor de Windows Server.
   Si ha completado a la Guía de instalación, se trata la máquina virtual que creó en Azure o Hyper-V.
- Este sistema debe estar conectado a una red y tener acceso a internet.

Si necesita configurar la característica de contenedor, consulte las guías siguientes: <g id="1ef6940a-72ed-4128-96d4-47ed33caf631CapsExtId1" ctype="x-linkText">contenedor configuración en Azure</g><g id="1ef6940a-72ed-4128-96d4-47ed33caf631CapsExtId2" ctype="x-title"></g> o <g id="7e79278d-4df4-428c-94c6-a67020a06ecfCapsExtId1" ctype="x-linkText">contenedor de instalación de Hyper-V</g><g id="7e79278d-4df4-428c-94c6-a67020a06ecfCapsExtId2" ctype="x-title"></g>.

##Administración de contenedor básico con Docker

Este primer ejemplo le guiará a través de los aspectos básicos de la creación y eliminación de contenedores de Windows Server y Windows Server contenedor imágenes con Docker.

Para comenzar el recorrido a través, registro en el contenedor Host de Windows Server System, verá un símbolo del sistema de Windows.

<g id="aa23853d-98d3-49e9-877c-5d34045ecc52" ctype="x-linkText"></g>

Inicie una sesión de PowerShell escribiendo <g id="5c60d873-2dbb-4936-9961-5d8b2b44cf8a" ctype="x-code">powershell</g>.
Sabrá que se encuentra en una sesión de PowerShell cuando cambia el símbolo del sistema de <g id="e6d372b8-36c2-424f-b7c1-255f61f10fbb" ctype="x-code">C:\directory ></g> a <g id="6504bacd-d0b5-43d4-9dda-cb4e988cdd85" ctype="x-code">C:\directory PS ></g>.
```
C:\> powershell
Windows PowerShell
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\>
```
> Este inicio rápido se centrará en comandos Docker, sin embargo, algunos pasos como administrar las reglas de firewall y copiar los archivos que se va a ejecutar con comandos de PowerShell.
> Funciona a través de este tutorial en una sesión de PowerShell.

A continuación, asegúrese de que el sistema tiene una dirección IP válida utilizando <g id="b3d5003f-4edb-412e-8cdd-a01eaea70ba5" ctype="x-code">ipconfig</g> y tome nota de esta dirección para su uso posterior.
```
ipconfig

Ethernet adapter Ethernet 3:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb::e
   IPv6 Address. . . . . . . . . . . : 2601:600:8f01:84eb:a8c1:a3e:96b7:ffcb
   Link-local IPv6 Address . . . . . : fe80::a8c1:a3e:96b7:ffcb%5
   IPv4 Address. . . . . . . . . . . : 192.168.1.25
```

Si está trabajando desde una máquina virtual de Azure en lugar de utilizar <g id="8d0b5780-0486-4508-af71-5ff69cb13cfe" ctype="x-code">ipconfig</g> debe obtener la dirección IP pública de la máquina Virtual de Azure.

<g id="7b144c11-9c01-41fb-a61d-e9c940625c59" ctype="x-linkText"></g>

###Paso 1: crear un contenedor nuevo

Antes de crear un contenedor de Windows Server con Docker debe el nombre o identificador de una imagen de Windows Server contenedor exsisitng.

Para ver todas las imágenes cargadas en el host de contenedor usan el <g id="806b632d-031a-4694-9932-cbd45a2cf9f9" ctype="x-code">imágenes docker</g> comando.

``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
windowsservercore   latest              9eca9231f4d4        30 hours ago        9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        30 hours ago        9.613 GB
```

Ahora, utilice <g id="610361ad-5b4f-47fb-9c85-ac606e76c120" ctype="x-code">docker ejecutar</g> para crear un nuevo contenedor de Windows Server.
Este comando tal como se muestra a continuación indicará el daemon Docker para crear un nuevo contenedor denominado 'dockerdemo' de la imagen 'windowsservercore' y abrir interactivo (-se) sesión (cmd) con el contenedor de la consola.

``` PowerShell
docker run -it --name dockerdemo windowsservercore cmd
```
Cuando se completa el comando trabajará en una sesión de consola en el contenedor.

Trabajar en un contenedor es casi idéntico al trabajar con Windows instaladas en una máquina virtual o física.
Puede ejecutar comandos como <g id="53e6fbbc-4529-453d-93e5-dc57a0fc8bec" ctype="x-code">ipconfig</g> para devolver la dirección IP del contenedor, <g id="63f188ba-1f25-4104-9cc7-99796de18bcc" ctype="x-code">mkdir</g> para crear un nuevo directorio, o <g id="18794193-a2b5-4762-8edb-8a6e3735b77b" ctype="x-code">powershell</g> para iniciar una sesión de PowerShell.
Siga adelante y realizar un cambio en el contenedor, como la creación de un archivo o carpeta.
Por ejemplo, el comando siguiente crea un archivo que contiene datos de configuración de red sobre el contenedor.

``` PowerShell
ipconfig > c:\ipconfig.txt
```

Puede leer el contenido del archivo para asegurarse el comando se completó correctamente.
Observe que la dirección IP incluida en el archivo de texto coincide con el contenedor.

``` PowerShell
type c:\ipconfig.txt

Ethernet adapter vEthernet (Virtual Switch-94a3e12ad262b3059e08edc4d48fca3c8390e38c3b219023d4a0a4951883e658-0):

   Connection-specific DNS Suffix  . : 
   Link-local IPv6 Address . . . . . : fe80::cc1f:742:4126:9530%18
   IPv4 Address. . . . . . . . . . . : 172.16.0.2
   Subnet Mask . . . . . . . . . . . : 255.240.0.0
   Default Gateway . . . . . . . . . : 172.16.0.1
```

Ahora que se ha modificado el contenedor, ejecute el siguiente procedimiento para detener la sesión de consola puesta que hacer en la sesión de consola del host del contenedor.

``` PowerShell
exit
```

Por último para ver una lista de contenedores en el contenedor host use la <g id="a7ed39dc-25a6-4f92-a3f1-3e9550de8bb9" ctype="x-code">docker ps: una</g> comando.
Observe en el resultado que un contenedor denominado 'dockerdemo' se ha creado.

``` PowerShell
docker ps -a

CONTAINER ID        IMAGE               COMMAND        CREATED             STATUS                     PORTS     NAMES
4f496dbb8048        windowsservercore   "cmd"          2 minutes ago       Exited (0) 2 minutes ago             dockerdemo
```

###Paso 2: crear una nueva imagen de contenedor

Una imagen ahora se pueden realizar desde este contenedor.
Esta imagen se comportará como una instantánea del contenedor y se puede volver a implementarse varias veces.

Para crear una nueva imagen, ejecute el siguiente.
Este comando indica al motor de Docker para crear una imagen nueva denominada 'newcontainerimage' que incluirá todos los cambios realizados en el contenedor 'deckerdemo'.

``` PowerShell
docker commit dockerdemo newcontainerimage
```

Para ver todas las imágenes en el host, ejecute <g id="ed4abdf1-c060-4c8f-9068-2c37858a31cd" ctype="x-code">imágenes docker</g>.
Observe que se ha creado una imagen nueva con el nombre 'newcontainerimage'.

``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
newcontainerimage   latest              4f8ebcf0a334        2 minutes ago       9.613 GB
windowsservercore   latest              9eca9231f4d4        30 hours ago        9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        30 hours ago        9.613 GB
```

###Paso 3: crear el contenedor de imagen

Ahora que tiene una imagen de un contenedor personalizado, implemente un nuevo contenedor denominado 'newcontainer' de 'newcontainerimage' y abrir una sesión de shell interactivo con el contenedor.

``` PowerShell
docker run –it --name newcontainer newcontainerimage cmd
```

Eche un vistazo en la unidad c:\ de este nuevo contenedor y observe que el archivo ipconfig.txt está presente.

<g id="13245903-0a80-46bd-96f1-9393fb1ef778" ctype="x-linkText"></g>

Salga del contenedor recién creado para volver a la sesión de consola de hosts de contenedor.

``` PowerShell
exit
```

Este ejercicio ha demostrado que una imagen procedente de un contenedor modificado incluirá todas las modificaciones.
Aunque este ejemplo era una modificación simple de archivos, el mismo aplicaría si fuera a instalar software en el contenedor, como un servidor web.
Con estos métodos, imágenes personalizadas pueden crearse que implementará listo contenedores de aplicación.

###Paso 4: quitar contenedores e imágenes

Para quitar un contenedor después de que ya no es necesario usar el <g id="3fd54f5a-78e6-4218-bc6e-67ce5058e7cd" ctype="x-code">docker rm</g> comando.
El comando siguiente quitará el nombre de contenedor 'newcontainer'.

``` PowerShell
docker rm newcontainer
```
Para quitar imágenes de contenedor cuando ya no necesita usar la <g id="31768a05-c325-4363-813a-cc7f1d9bb837" ctype="x-code">docker rmi</g> comando.
No se puede quitar una imagen si se hace referencia a un contenedor existente.

El comando siguiente quita la imagen de contenedor denominada 'newcontainerimage'.
``` PowerShell
docker rmi newcontainerimage

Untagged: newcontainerimage:latest
Deleted: 4f8ebcf0a334601e75070a92294d993b0f182abb6f4c88740c75b05093e6acff
```

##Hospedar un servidor Web en un contenedor

En el ejemplo siguiente se demuestra un caso de uso más práctico para los contenedores de Windows Server.
Los pasos incluidos en este ejercicio le guiará por la creación de una imagen de contenedor de servidor web que se puede utilizar para implementar las aplicaciones web hospedadas dentro de un contenedor de Windows Server.

###Paso 1: descarga Software de servidor Web

Antes de crear una imagen de contenedor web software de servidor necesitará se descargará y se almacenan en el host del contenedor.
Vamos a usar el nginx para software de Windows para este ejemplo.
<g id="8f16478c-7711-4760-87c9-8da7a934803e" ctype="x-strong">Nota</g> que este paso será necesario estar conectado a internet en el host del contenedor.
Si este paso produce un error de resolución de conectividad o nombre Compruebe la configuración de red del host del contenedor.

Ejecute el siguiente comando en el host de contenedor para crear la estructura de directorios que se utilizará para este ejemplo.

``` PowerShell
mkdir c:\build\nginx\source
```

Ejecute este comando en el host de contenedor para descargar el software de nginx para 'c:\nginx-1.9.3.zip'.

``` PowerShell
wget -uri 'http://nginx.org/download/nginx-1.9.3.zip' -OutFile "c:\nginx-1.9.3.zip"
```

Por último, el siguiente comando extraerá el software nginx 'C:\build\nginx\source'.

``` PowerShell
Expand-Archive -Path C:\nginx-1.9.3.zip -DestinationPath C:\build\nginx\source -Force
```

###Paso 2: crear la imagen del servidor Web

En el ejemplo anterior, manualmente crean, actualizan y capturar una imagen de contenedor.
En este ejemplo se demostrará un método automatizado para la creación de imágenes del contenedor mediante un Dockerfile.
Dockerfiles contienen instrucciones que utiliza el motor de Docker para crear y modificar un contenedor y, a continuación, confirmar el contenedor en una imagen de contenedor.
Para obtener más información sobre dockerfiles, consulte <g id="fde22811-2b91-4eac-89af-67745e6bd0dbCapsExtId1" ctype="x-linkText">referencia Dockerfile</g><g id="fde22811-2b91-4eac-89af-67745e6bd0dbCapsExtId2" ctype="x-title"></g>.

Utilice el siguiente comando para crear un dockerfile vacía.

``` PowerShell
new-item -Type File c:\build\nginx\dockerfile
```
Abra la dockerfile con el Bloc de notas.

```
notepad.exe c:\build\nginx\dockerfile
```

Copie y pegue el siguiente texto en el Bloc de notas, guarde el archivo y cierre el Bloc de notas.

``` PowerShell
FROM windowsservercore
LABEL Description="nginx For Windows" Vendor="nginx" Version="1.9.3"
ADD source /nginx
```

En este momento el dockerfile estará en software nginx extraído en 'c:\build\nginx\source' y 'c:\build\nginx'.
Ahora está listo para crear la imagen del contenedor de servidor web según las instrucciones de la dockerfile.
Para ello, ejecute el siguiente comando en el host del contenedor.

``` PowerShell
docker build -t nginx_windows C:\build\nginx
```
Este comando indica al motor de docker utilizar el dockerfile ubicado en <g id="76b5eabb-d5f8-4a0d-9db5-ded835ad22bc" ctype="x-code">C:\build\nginx</g> para crear una imagen denominada 'nginx_windows'.

El resultado será similar al siguiente:

<g id="ee0190c7-3821-47fe-91e5-2f29cd6d88b9" ctype="x-linkText"></g>

Cuando haya completado, examine las imágenes en el host utilizando la <g id="01248d7b-dae1-4eb2-b09b-12fb7a61f1b3" ctype="x-code">imágenes docker</g> comando.
Debería ver una nueva imagen denominada 'nginx_windows'.
``` PowerShell
docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE

nginx_windows       latest              d792268338d0        5 seconds ago       9.613 GB
windowsservercore   10.0.10254.0        9eca9231f4d4        35 hours ago        9.613 GB
windowsservercore   latest              9eca9231f4d4        35 hours ago        9.613 GB
```

###Paso 3: configurar la red para la aplicación de contenedor

Dado que va a hospedar un sitio Web dentro de un contenedor algunas redes relacionados con configuraciones necesitan tomar.
En primer lugar una regla de firewall debe crearse en el host de contenedor que permitan el acceso al sitio Web.
En este ejemplo se tendrá acceso a los sitios a través del puerto 80.
Ejecute el script siguiente para crear esta regla de firewall.
Esta secuencia de comandos se pueden copiar en la máquina virtual.

``` powershell
if (!(Get-NetFirewallRule | where {$_.Name -eq "TCP80"})) {
    New-NetFirewallRule -Name "TCP80" -DisplayName "HTTP on TCP/80" -Protocol tcp -LocalPort 80 -Action Allow -Enabled True
}
```

A continuación si trabaja en Azure y todavía no ha creado un extremo de la máquina Virtual debe crear uno ahora.
Para obtener más información sobre los extremos de la máquina virtual de Azure, consulte este artículo: <g id="80b302e7-42d1-43a4-8706-b263a5cf328dCapsExtId1" ctype="x-linkText">configurar los extremos de la máquina virtual de Azure</g><g id="80b302e7-42d1-43a4-8706-b263a5cf328dCapsExtId2" ctype="x-title"></g>.

###Paso 4: implementación de contenedor lista de servidor Web

Para implementar un contenedor de servidores de Windows basado en el contenedor 'nginx_windows', ejecute el siguiente comando.
Esto creará un nuevo contenedor denominado 'nginxcontainer' e iniciar una sesión de consola en el contenedor.
La parte de 80:80 – p de este comando crea una asignación de puerto entre el puerto 80 en el host con el puerto 80 en el contenedor.

``` powershell
docker run -it --name nginxcontainer -p 80:80 nginx_windows cmd
```
Una vez que trabaja dentro del contenedor, se puede iniciar el servidor web de nginx y ensayo de contenido web.
Para iniciar el servidor web de nginx, cambie el directorio de instalación de nginx.

``` powershell
cd c:\nginx\nginx-1.9.3
```

Inicie el servidor web de nginx.
``` powershell
start nginx
```
###Paso 5: acceder al sitio Web hospedado de contenedor

Con el contenedor del servidor web creado, puede desproteger ahora la aplicación hospedada en el contenedor.
Para ello, abra un explorador en un equipo diferente y escriba <g id="8d961120-b24b-476e-9606-9b32a0d01c2c" ctype="x-code">http://containerhost-ipaddress</g>.
Observe que se está buscando en la dirección IP del Host de contenedor y no el propio contenedor.
Si está trabajando desde una máquina Virtual de Azure será la dirección IP pública o nombre del servicio de nube.

Si todo se ha configurado correctamente, verá la página de bienvenida de nginx.

<g id="b78027ef-101c-414f-b4aa-45ef22080b34" ctype="x-linkText"></g>

En este momento, no dude en actualizar el sitio Web.
Copiar en su propio sitio Web de ejemplo o ejecute el comando siguiente en el contenedor para reemplazar la página de bienvenida de nginx con una página web de "Hello World".

```powershell
powershell wget -uri 'https://raw.githubusercontent.com/Microsoft/Virtualization-Documentation/master/doc-site/virtualization/windowscontainers/quick_start/SampleFiles/index.html' -OutFile "C:\nginx\nginx-1.9.3\html\index.html"
```

Después de que se ha actualizado el sitio Web, vaya a <g id="30d45cfc-bff0-4c77-a339-cfd8eaf88b06" ctype="x-code">http://containerhost-ipaddress</g>.

<g id="0c6077e1-5914-4608-a790-3828dd363c0a" ctype="x-linkText"></g>

> <g id="c03b899b-d2e2-462c-952e-cff9a7558cfb" ctype="x-strong">Nota:</g> si desea cambiar la configuración de Docker Daemon (tal como para cambiar el puerto de escucha que, para conectarse a un contenedor de forma remota), deberá modificar el archivo "C:\ProgramData\docker\runDockerDaemon.cmd" en el contenedor y, a continuación, deberá reiniciar el servicio con PowerShell, utilizando <g id="6cd3f9d9-ed44-4178-b893-bdc23284b28b" ctype="x-code">docker de reinicio de servicio</g>.

##Tutorial en vídeo

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Deploying-and-Managing-Windows-Server-Containers-with-Docker/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>

##Pasos siguientes

Ahora que ha configurado los contenedores y una introducción a las herramientas, vaya a crear sus propias aplicaciones de contenido.

Recuerde que se trata de un <g id="a71da433-4b7f-4fe2-bac4-da20f6ca1ea9" ctype="x-strong">vista previa</g> hay errores y tenemos una gran cantidad de trabajo en curso.
<g id="30090cf8-0055-43d3-b88f-63f21edbf138CapsExtId1" ctype="x-linkText">Esta página</g><g id="30090cf8-0055-43d3-b88f-63f21edbf138CapsExtId2" ctype="x-title"></g> contiene muchos de nuestros problemas conocidos.

Tenga en cuenta que hay algunas Docker conocido comandos que <g id="981e8ac3-b26d-4531-b163-f468bdb3bc63CapsExtId1" ctype="x-linkText">no funcionan</g><g id="981e8ac3-b26d-4531-b163-f468bdb3bc63CapsExtId2" ctype="x-title"></g> y que sólo algunos <g id="81d19598-a0d6-4d36-afdf-de4ad0db7f4fCapsExtId1" ctype="x-linkText">parcialmente trabajo</g><g id="81d19598-a0d6-4d36-afdf-de4ad0db7f4fCapsExtId2" ctype="x-title"></g>

También supervisemos la <g id="0ca605cd-1c23-41fe-8065-e015cbaf1a10CapsExtId1" ctype="x-linkText">foros</g><g id="0ca605cd-1c23-41fe-8065-e015cbaf1a10CapsExtId2" ctype="x-title"></g> muy de cerca.

También hay ejemplos creados previamente en <g id="5d7d6f4d-c018-4dd1-8b89-cf1a4169b9a0CapsExtId1" ctype="x-linkText">GitHub</g><g id="5d7d6f4d-c018-4dd1-8b89-cf1a4169b9a0CapsExtId2" ctype="x-title"></g>.

-----------------------------------

<g id="9adffbbd-fd8e-44ec-857d-580b065aa9c5CapsExtId1" ctype="x-linkText">Volver a la página principal de contenedor</g><g id="9adffbbd-fd8e-44ec-857d-580b065aa9c5CapsExtId2" ctype="x-title"></g>   
<g id="5cc15094-3632-4db9-bc50-8104a2e49514CapsExtId1" ctype="x-linkText">Problemas conocidos de la versión actual</g><g id="5cc15094-3632-4db9-bc50-8104a2e49514CapsExtId2" ctype="x-title"></g>



