MS. ContentId: 71a03c62-50fd-48dc-9296-4d285027a96a
título: contenedores de Windows del programa de instalación en una máquina virtual local

#Preparando la vista previa técnica de Windows Server para contenedores de Windows Server

Con el fin de crear y administrar contenedores de Windows Server, se debe preparar el entorno de la vista previa técnica de Windows Server 2016.
Esta guía le guiará a través de la configuración de contenedores de Windows Server en una máquina Virtual de Hyper-V.

> Otras guías de introducción:
* Ejecutar Windows Server contenedores en [Azure](./azure_setup.md).
* Ejecutar Windows Server contenedores en [una máquina virtual existente](./inplace_setup.md).
* La instalación de Windows Server contenedores [en una instalación Server Core de Windows física](./inplace_setup.md).
   
   **Leer antes de instalar el contenedor de imagen del sistema operativo:**  los términos de licencia del software de versión preliminar de Microsoft Windows Server ("términos de licencia") que se aplican al uso del complemento de la imagen del sistema operativo Microsoft Windows contenedor (el "software complementario).
   Al descargar y usar el software complementario, acepta los términos de licencia y no puede utilizar si no ha aceptado los términos de licencia.
   El software de versión preliminar de Windows Server y el software complementario cuentan con licencia de Microsoft Corporation.
   
   * Sistema que ejecuta Windows 10 / Windows Server Technical Preview 2 o posterior.
   * Rol de Hyper-V habilitado ([Consulte instrucciones](https://msdn.microsoft.com/virtualization/hyperv_on_windows/quick_start/walkthrough_install#UsingPowerShell)).
   * 20GB de almacenamiento disponibles para los scripts de imagen, la imagen del sistema operativo Base y la configuración de host de contenedor.
   * Permisos de administrador en el host de Hyper-V.

> Contenedores de Windows Server no requieren Hyper-V, sin embargo, para mantener la simplicidad, esta guía asume que se está utilizando un entorno de Hyper-V para ejecutar el host del contenedor de Windows Server.

##Programa de instalación de un nuevo Host de contenedor en una nueva máquina Virtual

Contenedores de Windows Server constan de varios componentes, como la imagen de Base de SO de contenedor y el contenedor Host de Windows Server.
Hemos reunido una secuencia de comandos que van a descargar y configurar estos elementos para usted.
Siga estos pasos para implementar una nueva máquina Virtual de Hyper-V y configurar el sistema como un Host de contenedor de Windows Server.

Inicie una sesión de PowerShell como administrador.
Esto puede hacerse, haga clic en el icono de PowerShell y seleccione 'Ejecutar como administrador', o bien ejecutando el siguiente comando de cualquier sesión de PowerShell.

``` powershell
start-process powershell -Verb runAs
```

Utilice el comando siguiente para descargar el script de configuración.
También se puede descargar manualmente la secuencia de comandos desde esta ubicación - [secuencia de comandos de configuración](http://aka.ms/newcontainerhost).

``` PowerShell
wget -uri https://aka.ms/newcontainerhost -OutFile New-ContainerHost.ps1
```

Ejecute el comando siguiente para crear y configurar el contenedor del host donde `< containerhost >` será el nombre de la máquina virtual y `< contraseña >` será la contraseña asignada a la cuenta de administrador.

``` powershell
.\New-ContainerHost.ps1 –VmName <containerhost> -Password <password>
```

Cuando se inicia la secuencia de comandos se les pedirá que lea y acepte los términos de licencia.

```
Before installing and using the Windows Server Technical Preview 3 with Containers virtual machine you must:
    1. Review the license terms by navigating to this link: http://aka.ms/WindowsServerTP3ContainerVHDEula
    2. Print and retain a copy of the license terms for your records.
By downloading and using the Windows Server Technical Preview 3 with Containers virtual machine you agree to such
license terms. Please confirm you have accepted and agree to the license terms.
[N] No  [Y] Yes  [?] Help (default is "N"): Y
```

La secuencia de comandos comenzará a descargar y configurar los componentes del contenedor de Windows Server.
Este proceso puede tardar bastante tiempo debido a la descarga de gran tamaño.
Cuando termine la máquina Virtual se configurarán y está listo para crear y administrar contenedores de Windows Server y Windows Server contenedor imágenes con PowerShell y Docker.

Puede recibir el siguiente mensaje durante el proceso de implementación de contenedor de servidor de la ventana host.
```
This VM is not connected to the network. To connect it, run the following:
Get-VM | Get-VMNetworkAdapter | Connect-VMNetworkAdapter -Switchname <switchname>
```
Si lo hace, compruebe las propiedades de la máquina virtual y conecte la máquina virtual a un conmutador virtual. También puede ejecutar el siguiente comando PowerShell donde `< switchname >` es el nombre del conmutador virtual Hyper-V que desea conectar a la máquina virtual.

``` powershell 
Get-VM | Get-VMNetworkAdapter | Connect-VMNetworkAdapter -Switchname <switchname>
```

Cuando haya finalizado la secuencia de comandos de configuración, iniciar la máquina virtual.
La máquina virtual se configura con Windows Server Core de 2016 y tendrá una apariencia similar al siguiente.

<center>![](./media/containerhost2.png)</center><br />

Finalmente, inicie sesión en la máquina virtual con la contraseña especificada durante el proceso de configuración y asegúrese de que la máquina Virtual tiene una dirección IP válida.
Con estos elementos completados del sistema debería estar listo para contenedores de Windows Server.

##Tutorial en vídeo

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Configure-Windows-Server-Containers-on-a-Local-System/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##Pasos siguientes: comenzar a usar contenedores

Ahora que dispone de un sistema Windows Server 2016 ejecutando el contenedor del servidor Windows característica saltar a las guías siguientes para empezar a trabajar con imágenes de contenedores de Windows Server y Windows Server contenedor.

[Inicio rápido: Los contenedores de Windows Server y Docker](./manage_docker.md)

[Inicio rápido: Contenedores de Windows Server y PowerShell](./manage_powershell.md)

-------------------


[Volver a la página principal de contenedor](../containers_welcome.md)  
[Problemas conocidos de la versión actual](../about/work_in_progress.md)




