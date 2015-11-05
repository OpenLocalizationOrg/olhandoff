MS. ContentId: 44b138bb-962f-4474-a0c4-284646a872e2
título: el programa de instalación de contenedores de Windows en su lugar

#Preparar una máquina física o una máquina virtual existente para contenedores de Windows Server

Con el fin de crear y administrar contenedores de Windows Server, se debe preparar el entorno de la vista previa técnica de Windows Server 2016.
Esta guía le orientará durante la configuración de Windows Server contenedores de reconstrucción completa o en una máquina virtual existente que ejecuta Windows Server 2016 Technical Preview.

> Otras guías de introducción:
* Ejecutar Windows Server contenedores en [Azure](./azure_setup.md).
* Ejecutar Windows Server contenedores en [una nueva máquina virtual de Hyper-V](./container_setup.md).
   
   **Leer antes de instalar el contenedor de imagen del sistema operativo:**  los términos de licencia del software de versión preliminar de Microsoft Windows Server ("términos de licencia") que se aplican al uso del complemento de la imagen del sistema operativo Microsoft Windows contenedor (el "software complementario).
   Al descargar y usar el software complementario, acepta los términos de licencia y no puede utilizar si no ha aceptado los términos de licencia.
   El software de versión preliminar de Windows Server y el software complementario cuentan con licencia de Microsoft Corporation.

**Requisitos del sistema (o VM):**
* Sistema que se ejecuta Windows Server Technical Preview 3 Server Core.
* 10GB de almacenamiento disponible para las secuencias de comandos de instalación y la imagen del sistema operativo Base.
* Permisos de administrador en el equipo o máquina virtual.

##Configuración de un host de máquina Virtual o una reconstrucción completa existente de contenedores

Contenedores de Windows Server requieren la imagen de Base del sistema operativo de contenedor.
Hemos reunido un script que se descargarán e instalarán esto por usted.
Siga estos pasos para configurar el sistema como un Host de contenedor de Windows Server.

Inicie una sesión de PowerShell como administrador.
Esto puede hacerse ejecutando el comando siguiente desde la línea de comandos.

``` powershell
powershell.exe
```

Asegúrese de que el título de las ventanas es "Windows PowerShell del administrador:".
Si no dice administrador, ejecute este comando para ejecutar con privilegios de administrador:

``` powershell
start-process powershell -Verb runas
```

Utilice el comando siguiente para descargar el script de configuración.
También se puede descargar manualmente la secuencia de comandos desde esta ubicación - [secuencia de comandos de configuración](http://aka.ms/setupcontainers).

``` PowerShell
wget -uri https://aka.ms/setupcontainers -OutFile C:\ContainerSetup.ps1
```

Una vez finalizada la descarga, ejecute el script.
``` PowerShell
C:\ContainerSetup.ps1
```

La secuencia de comandos comenzará a descargar y configurar los componentes del contenedor de Windows Server.
Este proceso puede tardar bastante tiempo debido a la descarga de gran tamaño.
Puede reiniciar el equipo durante el proceso.
Cuando termina el equipo se configurará y está listo para crear y administrar contenedores de Windows Server y Windows Server contenedor imágenes con PowerShell y Docker.

Con estos elementos completados del sistema debería estar listo para contenedores de Windows Server.


##Pasos siguientes: comenzar a usar contenedores

Ahora que está ejecutando Windows Server contenedores, saltar a las guías siguientes para empezar a trabajar con imágenes de contenedores de Windows Server y Windows Server contenedor.

[Inicio rápido: Los contenedores de Windows Server y Docker](./manage_docker.md)

[Inicio rápido: Contenedores de Windows Server y PowerShell](./manage_powershell.md)

-------------------


[Volver a la página principal de contenedor](../containers_welcome.md)  
[Problemas conocidos de la versión actual](../about/work_in_progress.md)



