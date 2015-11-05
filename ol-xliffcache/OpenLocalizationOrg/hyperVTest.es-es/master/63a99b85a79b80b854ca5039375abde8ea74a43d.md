MS. ContentId: 1ab7bfe1-da35-4ff1-916f-936fedf536a0
título: el programa de instalación Windows contenedores en Azure

#Preparación de Microsoft Azure para contenedores de Windows Server

Se trata de una edición de prueba.
Antes de crear y administrar contenedores de Windows Server en Azure deberá implementar una imagen de vista previa técnica de Windows Server 2016 que se ha configurado previamente con la característica de contenedores de Windows Server.
Esta guía le guiará a través de este proceso.

> Otras guías de introducción:
* Ejecutar Windows Server contenedores en [una nueva máquina virtual de Hyper-V](./container_setup.md).
* Ejecutar Windows Server contenedores en [una máquina virtual existente](./inplace_setup.md)
* La instalación de Windows Server contenedores [en una instalación Server Core de Windows física](./inplace_setup.md)

##Empezar a usar el Portal de Azure

Si tiene una cuenta de Azure, vaya directamente a [crear una máquina virtual Host de contenedor](#CreateacontainerhostVM).

1. Vaya a [azure.com](https://azure.com) y siga los pasos para una [evaluación gratuita de Azure](https://azure.microsoft.com/en-us/pricing/free-trial/).
2. Inicie sesión con su cuenta de Microsoft.
3. Cuando la cuenta esté preparada para comenzar, inicie sesión en el [Portal de administración de Azure](https://portal.azure.com).

##Crear una máquina virtual del Host de contenedor

Haga clic en el vínculo siguiente para iniciar el proceso de creación de VM: [nuevo Windows Server contenedor Host de Azure](https://portal.azure.com/#gallery/Microsoft.WindowsServer2016TechnicalPreviewwithContainers).

También puede buscar la imagen en la Galería de Azure.

Haga clic en el `crear` botón.

![](./media/newazure1.png)

Dé la máquina Virtual de un nombre, seleccione un nombre de usuario y una contraseña.

![](media/newazure2.png)

Seleccione la configuración opcional > extremos > y escriba un extremo HTTP con un puerto privado y público de 80, tal como se muestra a continuación.
Cuando completa haga clic en Aceptar dos veces.

![](./media/newazure3.png)

Seleccione el `crear` botón para iniciar el proceso de implementación de máquina Virtual.

![](media/newazure2.png)

Una vez completada la implementación de máquina virtual, seleccione el botón Conectar para iniciar una sesión de RDP con el Host de contenedor de Windows Server.

![](media/newazure6.png)

Inicie sesión en la máquina virtual con el nombre de usuario y la contraseña especificados durante el Asistente para la creación de máquinas virtuales.
Una vez registrada en se verán en el símbolo del sistema de Windows.

![](media/newazure7.png)

##Tutorial en vídeo

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Configure-Windows-Server-Containers-in-Microsoft-Azure/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##Pasos siguientes: comenzar a usar contenedores

Ahora que dispone de un sistema Windows Server 2016 ejecutando el contenedor del servidor Windows característica saltar a las guías siguientes para empezar a trabajar con imágenes de contenedores de Windows Server y Windows Server contenedor.

[Inicio rápido: Los contenedores de Windows Server y Docker](./manage_docker.md)  
[Inicio rápido: Contenedores de Windows Server y PowerShell](./manage_powershell.md)

-------------------

[Volver a la página principal de contenedor](../containers_welcome.md)  
[Problemas conocidos de la versión actual](../about/work_in_progress.md)




