MS. ContentId: 52DAFFBE-40F5-46D2-96F3-FB8659581594 
título: Novedades de Hyper-V para Windows 10

#Novedades de Hyper-V en Windows 10

En este tema se explica la funcionalidad nueva y modificada en Hyper-V en 10 de Windows ®.

##Windows PowerShell directa

Hay ahora una manera fácil y confiable para ejecutar comandos de Windows PowerShell en una máquina virtual desde el sistema operativo host.
No existen requisitos de red o firewall ni una configuración especial.
Funciona independientemente de la configuración de administración remota.
Para usarlo, debe ejecutar Windows 10 o versión preliminar técnica de Windows Server en el host y el sistema operativo de invitado de máquina virtual.

Para crear una sesión de PowerShell directamente, utilice uno de los siguientes comandos:

``` PowerShell
Enter-PSSession -VMName VMName
Invoke-Command -VMName VMName -ScriptBlock { commands }
```

En la actualidad, los administradores de Hyper-V se basan en dos categorías de herramientas para conectarse a una máquina virtual en su host de Hyper-V:
- Herramientas de administración remota como PowerShell o escritorio remoto
- Conexión a máquina Virtual de Hyper-V (conexión de máquina virtual)

Ambas tecnologías funcionan bien, pero cada uno tiene ventajas e inconvenientes a medida que crece la implementación de Hyper-V.
VMConnect es confiable, pero puede ser difícil de automatizar.
PowerShell remoto es eficaz, pero puede ser difícil de instalación y mantener.

Windows PowerShell directo proporciona que un scripting y automatización eficaz experimentan con la simplicidad de VMConnect.
Dado que Windows PowerShell directa se ejecuta entre el host y máquina virtual, no es necesario para una conexión de red o para habilitar la administración remota.
Necesita credenciales de invitado para iniciar sesión en la máquina virtual.

####Requisitos

- Debe estar conectado a un host de vista previa técnica de Windows Server con máquinas virtuales que ejecutan Windows 10 o versión preliminar técnica de Windows Server como invitados o el 10 de Windows.
- Debe iniciar la sesión con credenciales de administrador de Hyper-V en el host.
- Debe tener credenciales de usuario para la máquina virtual.
- La máquina virtual que desea conectarse debe estar en ejecución y arrancado.


##Sin interrupción, agregar y quitar para adaptadores de red y memoria

Ahora puede agregar o quitar un adaptador de red mientras se ejecuta la máquina virtual, sin tiempo de inactividad.
Esto funciona para las máquinas virtuales de generación 2 con sistemas operativos Windows y Linux.

También puede ajustar la cantidad de memoria asignada a una máquina virtual mientras se está ejecutando, incluso si no ha habilitado la memoria dinámica.
Esto funciona en las generaciones 1 y máquinas virtuales de generación 2.

##Puntos de control de producción

Los puntos de control de producción permiten crear fácilmente imágenes "punto en vez" de una máquina virtual, que se pueden restaurar más adelante de forma que se admite completamente para todas las cargas de trabajo de producción.
Esto se logra mediante la tecnología de copia de seguridad dentro del invitado para crear el punto de control, en lugar de utilizar tecnología de estado guardado.
Para los puntos de control de producción, se utiliza el servicio de instantáneas de volumen (VSS) dentro de máquinas virtuales de Windows.
Las máquinas virtuales Linux vaciar sus búferes de sistema de archivos para crear un punto de comprobación coherente sistema de archivos.
Si desea crear puntos de comprobación mediante la tecnología de estado guardado, todavía puede usar puntos de control estándar para la máquina virtual.


> **Importante:** será el valor predeterminado de nuevas máquinas virtuales crear puntos de comprobación de producción con una reserva de puntos de control estándar.


##Mejoras del Administrador de Hyper-V

- **Alternar la compatibilidad con las credenciales** : ahora puede utilizar un conjunto diferente de credenciales de administrador de Hyper-V cuando se conecte a otro host remoto de Windows Vista previa técnica de 10.
   También puede guardar estas credenciales por lo que es más fácil de iniciar sesión posteriormente.
   
- **Administración de nivel inferior** -ahora puede usar el Administrador de Hyper-V para administrar más versiones de Hyper-V.
   Con el Administrador de Hyper-V en Windows Vista previa técnica de 10, puede administrar equipos que ejecutan Hyper-V en Windows Server 2012, Windows 8, Windows Server 2012 R2 y Windows 8.1.
   
- **Actualiza el protocolo de administración de** -Administrador de Hyper-V se ha actualizado para comunicarse con los hosts de Hyper-V remotos utilizando el protocolo WS-MAN, que permite la autenticación CredSSP, Kerberos o NTLM.
   Cuando usa CredSSP para conectarse a un host de Hyper-V remoto, permite realizar una migración en vivo sin primera habilitar la delegación restringida en Active Directory.
   Infraestructura basada en WS-MAN también simplifica la configuración necesaria para habilitar un host para la administración remota.
   WS-MAN se conecta en el puerto 80, que es abre de forma predeterminada.


##Conectado funciona del modo de espera

Cuando se habilita Hyper-V en un equipo que utiliza el modelo de alimentación conectado siempre de On/Always (AOAC), el estado de energía del modo de espera conectado ahora está disponible.

En Windows 8 y 8.1, Hyper-V produce equipos que usan el modelo de alimentación conectado siempre de On/Always (AOAC) (también conocido como InstantON) en modo de suspensión nunca.
Vea este ([artículo de KB]
https://support.Microsoft.com/en-us/KB/2973536) para una descripción completa.


##Arranque seguro de Linux

Ahora puede arrancar más sistemas operativos Linux, se ejecutan en máquinas virtuales de generación 2, con la opción de arranque seguro habilitada.
Ubuntu 14.04 y versiones posterior y SUSE Linux Enterprise Server 12, están habilitadas para el arranque seguro en hosts que ejecutan la versión preliminar técnica.
Antes de iniciar la máquina virtual por primera vez, debe especificar que la máquina virtual debe utilizar la entidad de certificación de Microsoft UEFI.
En un símbolo de Windows Powershell con privilegios elevados, escriba:

    Set-VMFirmware vmname -SecureBootTemplate MicrosoftUEFICertificateAuthority

Para obtener más información acerca de cómo ejecutar máquinas virtuales de Linux en Hyper-V, vea [Linux y FreeBSD máquinas virtuales Hyper-V](http://technet.microsoft.com/library/dn531030.aspx).


##Versión de configuración de máquina virtual

Al mover o importar una máquina virtual a un host que ejecuta Hyper-V en Windows 10 de host que ejecuta Windows 8.1, no se actualiza automáticamente el archivo de configuración de la máquina virtual.
Esto permite que la máquina virtual para moverse a un host que ejecuta Windows 8.1.
No tendrá acceso a las nuevas características de máquina virtual hasta que actualice manualmente la versión de configuración de máquina virtual.

La versión de configuración de máquina virtual representa la versión de Hyper-V configuración de la máquina virtual, el estado guardado y es compatible con los archivos de instantáneas.
Las máquinas virtuales con la versión 5 de configuración son compatibles con Windows 8.1 y puede ejecutarse en Windows 8.1 y 10 de Windows.
Las máquinas virtuales con la versión 6 de configuración son compatibles con 10 de Windows y no se ejecutará en Windows 8.1.

####¿Cómo puedo comprobar la versión de la configuración de las máquinas virtuales que se ejecutan en Hyper-V?

Desde un símbolo del sistema con privilegios elevados, ejecute el siguiente comando:

``` PowerShell
Get-VM * | Format-Table Name, Version
```

####¿Cómo se puede actualizar la versión de configuración de una máquina virtual?

Desde un símbolo de Windows PowerShell con privilegios elevados, ejecute uno de los siguientes comandos:

``` PowerShell
Update-VmConfigurationVersion <vmname>
```

O

``` PowerShell
Update-VmConfigurationVersion <vmobject>
```


** Importante: **
- Después de actualizar la versión de configuración de máquina virtual, no se puede mover la máquina virtual a un host que ejecuta Windows 8.1.
- No puede cambiar la versión de configuración de máquina virtual de la versión 6 a la versión 5.
- Debe desactivar la máquina virtual para actualizar la configuración de máquina virtual.
- Después de la actualización, la máquina virtual usa el nuevo formato de archivo de configuración.
   Para obtener más información, vea el nuevo formato de archivo de configuración de máquina virtual.


##Nuevo formato de archivo de configuración de máquina virtual

Máquinas virtuales tienen ahora un nuevo formato de archivo de configuración que está diseñado para aumentar la eficacia de lectura y escritura de datos de configuración de máquina virtual.
También se ha diseñado para reducir la posibilidad de daños en los datos si se produce un error de almacenamiento.
Uso de archivos de la nueva configuración de la. Extensión VMCX de datos de configuración de máquina virtual y el. Extensión VMRS para datos de estado en tiempo de ejecución.


> **Importante:** el. Archivo VMCX es un formato binario.
> Editar directamente el. VMCX o. Archivo VMRS no se admite.



##Servicios de integración ofrecidos a través de Windows Update

Ahora se distribuyen las actualizaciones de los servicios de integración para invitados de Windows a través de Windows Update.

Componentes de integración (también denominados servicios de integración) son el conjunto de controladores artificiales que permiten una máquina virtual para comunicarse con el sistema operativo host.
Controlan servicios que van desde la sincronización horaria para la copia de archivos de invitado.
Hemos estado hablando a los clientes acerca de la instalación de componentes de integración y actualización durante el año pasado para descubrir que son una gran dificultad durante el proceso de actualización.


Históricamente, todas las nuevas versiones de Hyper-V suministrada con nuevos componentes de integración.
Actualizar el host de Hyper-V, es necesario actualizar los componentes de integración en las máquinas virtuales.
A continuación, los nuevos componentes de integración se incluían en el host de Hyper-V que se instalaron en las máquinas virtuales mediante vmguest.iso.
Este proceso requiere reiniciar la máquina virtual y no se pudo procesar por lotes con otras actualizaciones de Windows.
Puesto que el Administrador de Hyper-V se tenía que ofrecer vmguest.iso y el Administrador de la máquina virtual se tenían que instalarlos, actualización del componente de integración requiere el Administrador de Hyper-V tiene credenciales de administrador en las máquinas virtuales, que no siempre es el caso.
　　


10 de Windows y en el futuro, integración de todos los componentes se entregan a virtual mecanizar mediante Windows Update junto con otras actualizaciones importantes.


Hay actualizaciones disponibles hoy día para máquinas virtuales que ejecutan:
*  Windows Server 2012
*  Windows Server 2008 R2
*  Windows 8
*  Windows 7

La máquina virtual debe estar conectada a Windows Update o un servidor WSUS.
En el futuro, las actualizaciones de componentes de integración tendrá un identificador de categoría para esta versión, se muestran como Knowledge Base.

Para obtener más información acerca de cómo determinamos la aplicabilidad, consulte esto [entrada de blog](http://blogs.technet.com/b/virtualization/archive/2014/11/24/integration-components-how-we-determine-windows-update-applicability.aspx).


Vea [este blog](http://blogs.msdn.com/b/virtual_pc_guy/archive/2014/11/12/updating-integration-components-over-windows-update.aspx) registrar para obtener un tutorial detallado de instalar integration services.


> **Importante:** vmguest.iso de archivo de imagen ISO el ya no es necesario para actualizar los componentes de integración.
> No se incluye con Hyper-V en Windows 10.




##Paso siguiente

[Recorra Hyper-V de Windows 10](..\quick_start\walkthrough.md)



