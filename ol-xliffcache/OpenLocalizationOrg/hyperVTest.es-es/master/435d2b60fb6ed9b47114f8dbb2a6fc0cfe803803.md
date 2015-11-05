MS. ContentId: 6C7EB25D-66FB-4B6F-AB4A-79D6BB424637
título: hacer que un nuevo servicio de administración

#Hacer que un nuevo servicio de administración

Se trata de una prueba.
Este documento presenta los servicios de máquinas virtuales basadas en sockets de Hyper-V y cómo comenzar a utilizarlas.

##¿Qué es un servicio de VM?

Agregar esta frase para probar el proceso de HO HB.Agregar esta frase para probar el proceso de HO HB.
Servicios de máquina virtual son servicios que abarcan el host de Hyper-V y máquinas virtuales que se ejecutan en el host.

Hyper-V ahora (10 de Windows y servidor 2016 +) proporciona una conexión de red no lo que permite crear servicios que abarcan el límite de la máquina virtual host conservando los requisitos fundamentales de Hyper-V alrededor de aislamiento de inquilinos/anfitrión, control, y disturbio.

Hyper-V seguirá proporcionando un conjunto básico de servicios de la Bandeja de entrada (integration services) para aspectos básicos (como la sincronización de tiempo) y comunes solicitudes que recibamos, pero ahora cualquiera puede escribir y distribuir un servicio máquinas virtuales según sea necesario.

PowerShell directa es un ejemplo de bandeja de entrada de un servicio de máquina virtual.

##¿Qué es un socket de Hyper-V?

Los sockets de Hyper-V son sockets TCP como sin ninguna dependencia en las redes.
Usar sockets de Hyper-V, los servicios pueden ejecutarse independientemente de la pila de red y todo el flujo de datos permanece en memoria del host.

##Requisitos del sistema

<g id="75ba42d6-5961-481d-a85d-d4f32d3dcb30" ctype="x-strong">Sistema operativo del Host admitido</g>
*   10 de Windows
*   Windows Server Technical Preview 3
*   Las versiones futuras (servidor 2016 +)

<g id="79e8c13c-31b6-4eee-bbb5-a2ff50e0c489" ctype="x-strong">SO invitado admitido</g>
*   10 de Windows
*   Windows Server Technical Preview 3
*   Las versiones futuras (servidor 2016 +)
*   Linux

##Capacidades y limitaciones

Modo de usuario o modo núcleo  
Sólo el flujo de datos    
No hay memoria de bloque no lo mejor para copia de seguridad y vídeo

##Introducción

Esta guía se asume que está familiarizado con el socket de programación de C o C++.

###Paso 1: registrar el servicio en el host de Hyper-V

Para poder utilizar un servicio personalizado que se integra con Hyper-V, el nuevo servicio debe estar registrado en registro del Host de Hyper-V.

Al registrar el servicio en el registro, obtendrá:
*  Administración de WMI para habilitar, deshabilitar y enumerar servicios disponibles
*  En la lista de servicios puede comunicarse directamente con las máquinas virtuales.

<g id="d414dc86-9587-4742-8de3-b162cc6d2cfe" ctype="x-em">* Información y ubicación del registro *</g>

``` 
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\VirtualDevices\6C09BB55-D683-4DA0-8931-C9BF705F6480\GuestCommunicationServices\
```
En esta ubicación del registro, verá varios GUID.
Éstos son nuestros servicios en el equipo.

Información del registro por cada servicio:
* <g id="298de918-5cb0-49fb-b5f8-958c5c6fdf08" ctype="x-code">GUID de servicio</g>
   * <g id="4ddeb0a9-8c13-4185-90d8-252b9d5cb88d" ctype="x-code">ElementName (REG_SZ)</g> --esto es el nombre del servicio descriptivo

Para registrar su propio servicio, cree una nueva clave del registro con su propio GUID y el nombre descriptivo.

La entrada del registro tendrá este aspecto:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\GuestCommunicationServices\
    999E53D4-3D5C-4C3E-8779-BED06EC056E1\
        ElementName REG_SZ  VM Session Service
    YourGUID\
        ElementName REG_SZ  Your Service Friendly Name
```

> <g id="20c664a6-040d-4d7c-8358-ba53140114c1" ctype="x-em">* Sugerencia: *</g>  para generar un GUID en PowerShell y cópielo en el Portapapeles, ejecute:
``` PowerShell
[System.Guid]::NewGuid().ToString() | clip.exe
```



###Paso 2: crear un servicio del host simple

###Paso 3: crear un simple servicio de invitado

##Para obtener más información acerca de AF_HYPERV

Puesto que los sockets de Hyper-V no dependen de una pila de red TCP/IP, DNS, etc. el punto final de socket necesita un no IP, no hostname, formato que sigue describe la conexión.
En lugar de un IP o nombre de host, los extremos AF_HYPERV dependen en gran medida dos GUID:
* Id. de VM: este es el identificador único asignado por máquina virtual.
   Identificador de la máquina virtual se encuentra utilizando el siguiente fragmento de PowerShell.
```PowerShell
(Get-VM -Name vmname).Id
```
* Id. de servicio: GUID en la que el servicio está registrado en el registro de host de Hyper-V.
   Vea <g id="d7ad437b-7aba-4e21-b6ab-b5929b8ee143CapsExtId1" ctype="x-linkText">registrar un nuevo servicio</g><g id="d7ad437b-7aba-4e21-b6ab-b5929b8ee143CapsExtId2" ctype="x-title"></g>.

Para las conexiones de un servicio en el host para el servicio en una máquina virtual:  
Id. de VMID y servicio
Para las conexiones de un servicio en una máquina virtual para el servicio en el host:  
Cero ID GUID y el servicio.

##Comandos de socket admitidos

Socket()
Bind()
Conectar)
Send()
Listen()
Accept()







