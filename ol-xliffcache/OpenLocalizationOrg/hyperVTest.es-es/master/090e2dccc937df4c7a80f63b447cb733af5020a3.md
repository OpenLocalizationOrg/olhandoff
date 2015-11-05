MS. ContentId: 5bbac9eb-c31e-40db-97b1-f33ea59ac3a3
título: trabajo en curso

#Trabajo en curso

Si no ve su problema abordan o tiene alguna pregunta, publíquelas en el [foro](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

-----------------------


##Funcionalidad general

###Contenedor de imagen de Windows debe coincidir exactamente con el host de contenedor

Un contenedor de Windows Server requiere una imagen de sistema operativo que coincide con el host de contenedor en sentido para generar y nivel de revisión.
Una falta de coincidencia le llevará al comportamiento de inestabilidad y o impredecible para el contenedor o el host.

Si instala las actualizaciones en el sistema operativo que se necesitará actualizar el contenedor base del host de contenedor de Windows actualiza la imagen del sistema operativo para que la coincidencia.


**Solución alternativa:**   
Descargue e instale una imagen base de contenedor que coinciden con el nivel de versión y revisión de SO del host del contenedor.


###Comandos esporádicamente producirá un error, vuelva a intentarlo

En nuestras pruebas, en ocasiones comandos deben ejecutarse varias veces.
El mismo principio se aplica a otras acciones.
Por ejemplo, si crea un nuevo archivo y no aparece, intente tocar el archivo.

Si tiene que hacerlo, háganoslo saber a través de [los foros](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

** Solución alternativa: **  
Crear secuencias de comandos que intentan comandos varias veces.
Si se produce un error en un comando, vuelva a intentarlo.

###Todos los que no sea C: / unidades se asignan automáticamente a nuevos contenedores

Todos los que no sea C: / las unidades disponibles para el host de contenedor se asignan automáticamente a los nuevos contenedores de servidor de Windows está ejecutando.

En este momento no hay ninguna manera selectivamente asignar carpetas en un contenedor, como un trabajo provisional en torno a unidades de disco se asignan automáticamente.

** Solución alternativa: **  
Estamos trabajando en él.
En el futuro hay carpeta compartirán.


###Contenedores de Windows Server se están iniciando muy lentamente

Si el contenedor está tardando más de 30 segundos en iniciarse, que esté realizando muchas exploraciones de virus duplicados.

Muchas soluciones antimalware, como Windows Defender, quizás innecesariamente digitalización de imágenes de con de contenedor de archivos incluidos todos los archivos y los archivos binarios del sistema operativo en la imagen de sistema operativo del contenedor.
Esto se produce cuando existe, se crea un nuevo contenedor y desde la perspectiva del anti-malware todos los "archivos del contenedor" son similares a los archivos nuevos que no se ha analizado anteriormente.
Así que cuando intentan leer estos archivos procesos dentro del contenedor de los componentes de antimalware analizar primero antes de permitir el acceso a los archivos.
En realidad estos archivos ya se analizan cuando se importó o extraída al servidor de la imagen del contenedor.
En el futuro nueva infraestructura de vistas previas será en su lugar tal que soluciones antimalware, incluido Windows Defender, pueden conocer estas situaciones y pueden actuar en consecuencia para evitar múltiples recorridos.

--------------------------


##Funciones de red

###Número de compartimentos de red por contenedor

En esta versión se admite un compartimiento de red por contenedor.
Esto significa que si tiene un contenedor con varios adaptadores de red, no tiene acceso el mismo puerto de red en cada adaptador (por ejemplo, 192.168.0.1:80 y 192.168.0.2:80 que pertenecen al mismo contenedor).

** Solución alternativa: **  
Si varios extremos necesitan estar expuesto por un contenedor, utilice la asignación de puertos NAT.

###Contenedores de Windows no obtienen direcciones IP

Si se conecta a los contenedores de windows server con los modificadores de la máquina virtual de DHCP es posible que el host de contenedor recibir un wwhile IP que los contenedores no.

Los contenedores de obtienen un 169.254.***. *** Dirección IP de APIPA.

**Solución alternativa:**
Se trata de un efecto secundario de uso compartido del kernel.
Todos los contenedores efectivamente tienen la misma dirección mac.

Habilitar la suplantación en el host de contenedor de direcciones MAC.

Esto puede lograrse mediante PowerShell
```
Get-VMNetworkAdapter -VMName "[YourVMNameHere]"  | Set-VMNetworkAdapter -MacAddressSpoofing On
```

###Crear recursos compartidos de archivos no funciona en un contenedor

Actualmente no es posible crear un recurso compartido de archivos dentro de un contenedor.
Si ejecuta `net share` verá un error similar al siguiente:

```
The Server service is not started.

Is it OK to start it? (Y/N) [Y]: y
The Server service is starting.
The Server service could not be started.

A service specific error occurred: 2182.

More help is available by typing NET HELPMSG 3547.
```

** Solución alternativa: **
Si desea copiar archivos en un contenedor puede utilizar la otra manera de ida y vuelta ejecutando `net use` dentro del contenedor.
Por ejemplo:
```
net use S: \\your\sources\here /User:shareuser [yourpassword]
```

--------------------------


##Compatibilidad de aplicaciones

Hay por lo que mnay preguntas sobre qué aplicaciones funcionarán y no funcionan en Windows Server contenedores, hemos decidido dividir la información de compatibilidad de aplicaciones en [su propio artículo](../reference/app_compat.md).

Algunos de los problemas más comunes se encuentran aquí también.

###WinRM no se inicia en un contenedor de Windows Server

WinRM se inicia, produce un error y se detiene de nuevo.
No se registran errores en el registro de eventos.

**Solución alternativa:**
Utilizar WMI, [RDP](#RemoteDesktopAccessOfContainers), o el valor de Enter-PSSession - ContainerID

###No se puede instalar ASP.NET 4.5 o 3.5 de ASP.NET con IIS en un contenedor mediante DISM

Instalar IIS ASPNET45 en un contenedor no funciona dentro de un contenedor de Windows Server.
Palos de progreso de instalación alrededor 95,5%.

``` PowerShell
Enable-WindowsOptionalFeature -Online -FeatureName IIS-ASPNET45
```

Se produce un error porque ASP.NET 4.5 no se ejecuta en un contenedor.

**Solución alternativa:**  
En su lugar, instale el rol de servidor Web para utilizar IIS.
¿Funciona ASP 5.0.

``` PowerShell
Enable-WindowsOptionalFeature -Online -FeatureName Web-Server
```

Consulte la [artículo de compatibilidad de aplicaciones](../reference/app_compat.md) para obtener más información acerca de qué aplicaciones pueden ser containerized.

--------------------------



##Administración de docker

###Clientes de docker no seguras de forma predeterminada

En esta versión preliminar, comunicación docker es pública si sabe dónde buscar.

###Comandos de docker que no funcionan con Windows Server contenedores

Comandos conocidos un error:

| **Comando docker**| **Donde se ejecuta**| **Error**| **Notas**|
|:-----|:-----|:-----|:-----|
| **confirmación de docker**| imagen| Docker deja de ejecutarse el contenedor y no se muestra el mensaje de error correcto| Confirmar un funciona contenedor detenida.Para ejecutar contenedores: estamos trabajando en él :)|
| **diferencias de docker**| demonio| Error: El graphdriver de windows no admite Changes()| |
| **kill docker**| contenedor| Error: Señal no es válido: Error de eliminación: no se pudo eliminar contenedores:]| |
| **carga docker**| imagen| Devuelve un error silenciosamente| Ningún error, pero la imagen no está cargando cualquiera|
| **pausa docker**| contenedor| Error: No se puede pausar el contenedor de Windows.Puede no ser compatible| |
| **puerto docker**| contenedor| | No obtener aparece ningún puerto incluso somos capaces de RDP.
| **extracción de docker**| demonio| Error: El sistema no encuentra la ruta de acceso de archivo.Nos contenedor no se puede ejecutar con esta imagen.| Obtener se agrega la imagen no se puede utilizar.Estamos trabajando en él :)|
| **reinicio de docker**| contenedor| Error: El cierre del sistema está en curso.| |
| **reanude docker**| contenedor| | No se puede probar porque pausa no funciona aún.|
Si todo lo que no se encuentra en esta lista se produce un error o si falla un comando diferente de lo esperado, háganoslo saber a través de [los foros](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).



###Comandos de docker que funcionan parcialmente con contenedores de Windows Server

Comandos con funcionalidad parcial:

| **Comando docker**| **Se ejecuta en...**| **Parámetro**| **Notas**|
|:-----|:-----|:-----|:-----|
| **adjuntar docker**| contenedor| --no stdin = false| El comando no cierre cuando se presiona Ctrl-P y CTRL-Q|
| | | --sig proxy = true| Works|
| **compilación docker**| imágenes| -f,--archivo| Error: No se puede preparar el contexto: no se puede obtener synlinks|
| | | --force-rm = false| Works|
| | | --sin caché = false| Works|
| | | -q,--quiet = false| |
| | | --rm = true| Works|
| | | -t,--etiqueta = ""| Works|
| **inicio de sesión docker**| demonio| -p, -u -e,| comportamiento de sporratic|
| **inserción de docker**| demonio| | Obtener ocasional errores "no salir del repositorio".|
| **rm docker**| contenedor| -f| Error: El cierre del sistema está en curso.|
Si todo lo que no se encuentra en esta lista se produce un error, si falla un comando diferente de la esperada, o si encuentra una solución alternativa, háganoslo saber a través de [los foros](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).


###Pegar los comandos de la sesión interactiva de Docker está limitada a 50 caracteres

Si copia una línea de comandos en una sesión interactiva de Docker, es actualmente limitada a 50 caracteres.
Simplemente se trunca la cadena de pegado.

Esto no es así por diseño, estamos trabajando en la restricción de elevación.

###NET use devuelve el error del sistema 1223 en lugar de pedir el nombre de usuario o contraseña

Solución alternativa: especificar, el nombre de usuario y la contraseña, al ejecutar net use.
Por ejemplo:
```
net use S: \\your\sources\here /User:shareuser [yourpassword]
```

###Errores de correcciones de compatibilidad de HCS al crear nuevas imágenes de contenedor

Si encuentra mensajes de error similar al siguiente:
```
hcsshim::ExportLayer - Win32 API call returned error r1=2147942523 err=The filename, directory name, or volume label syntax is incorrect. layerId=606a2c430fccd1091b9ad2f930bae009956856cf4e6c66062b188aac48aa2e34 flavour=1 folder=C:\ProgramData\docker\windowsfilter\606a2c430fccd1091b9ad2f930bae009956856cf4e6c66062b188aac48aa2e34-1868857733
```

Se llega a un problema mencionado en la cero días revisión para Windows Server 2016 TP3.
Este error también puede producirse cuando se ejecuta el instalador de Python 3.4.3.msi o v0.12.7.msi del nodo en un contenedor.

Si encuentra otros errores hcsshim, háganoslo saber a través de [los foros](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).


##Al tener acceso al contenedor de servidor de windows con el escritorio remoto

Contenedores de Windows Server puede ser administrada o interactuar a través de una sesión RDP.

Los pasos siguientes son necesarios para conectarse remotamente a un contenedor de servidores de Windows con RDP.
Se supone que el contenedor está conectado a la red a través de un conmutador NAT.
Esto es el valor predeterminado al configurar un host de contenedor a través de la secuencia de comandos de instalación o crear una nueva máquina virtual en Azure.

** En el contenedor que desea conectar a **

Los pasos siguientes requieren administración del contenedor mediante Docker o, cuando se usa PowerShell, especificando la `- RunAsAdministrator` cambiar cuando se conecta al contenedor.
Por favor, siga estos pasos en el contenedor que desea conectar a.

1. Obtener dirección IP del contenedor

  ```
  ipconfig
  ```

Devuelve algo similar a éste

  ```
  Windows IP Configuration

  Ethernet adapter vEthernet (Virtual Switch-f758a5a9519e1956cc3bef06eb03e5728d3fb61cf6d310246185587be490210a-0):

  Connection-specific DNS Suffix  . :
  Link-local IPv6 Address . . . . . : fe80::91cd:fb4c:4ea5:51df%17
  IPv4 Address. . . . . . . . . . . : 172.16.0.2
  Subnet Mask . . . . . . . . . . . : 255.240.0.0
  Default Gateway . . . . . . . . . : 172.16.0.1
  ```

Tenga en cuenta la dirección IPv4 que se encuentra normalmente en el 172.16 de formato

2. Establecer la contraseña del usuario del Administrador de cuentas predefinidas para el contenedor

  ```
  net user administrator [yourpassword]
  ```

3. Permitir que el usuario de administrador de cuentas predefinidas para el contenedor

  ```
  net user administrator /active:yes
  ```

** En el host de contenedor **

Puesto que Windows Server tiene el Firewall de Windows con seguridad avanzada habilitada de forma predeterminada es necesario abrir algunos puertos para la comunicación en orden para RDP para que funcione.
Además, se crea una asignación de puerto para que el contenedor está accesible a través de un puerto en el host del contenedor.

Los pasos siguientes requieren un PowerShell lanzado como administrador en el host del contenedor.

1. Permitir que el valor predeterminado puerto RDP a través del Firewall de Windows avanzada

  ```
  New-NetFirewallRule -Name "RDP" -DisplayName "Remote Desktop Protocol" -Protocol TCP -LocalPort @(3389) -Action Allow
  ```

2. Permitir otro puerto para la conexión RDP en el contenedor

  ```
  New-NetFirewallRule -Name "ContainerRDP" -DisplayName "RDP Port for connecting to Container" -Protocol TCP -LocalPort @(3390) -Action Allow
  ```

Este paso abre el puerto 3390 en el host del contenedor.
Se utilizará para abrir una sesión RDP en el contenedor.
Si desea conectarse a varios contenedores, puede repetir este paso proporcionando los números de puerto adicionales.

3. Agregar una asignación de puerto para NAT existente
   
   En este paso se necesita la dirección IP del paso 1 en el contenedor

  ```
  Add-NetNatStaticMapping -NatName ContainerNAT -Protocol TCP -ExternalPort 3390 -ExternalIPAddress 0.0.0.0 -InternalPort 3389 -InternalIPAddress [your container IP]
  ```

Aquí se asegura de que la comunicación con el host de contenedor que se está acercando puerto 3390 se redirige al puerto 3389 en el contenedor con la dirección IP que especifique.

** Conectar al contenedor a través de RDP **

Por último puede conectarse al contenedor mediante RDP.
Para ello, ejecute el siguiente comando en un sistema que tiene el cliente de escritorio remoto instalado (por ejemplo, el sistema ejecuta la máquina virtual del host de contenedor):

```
mstsc /v:[ContainerHostIP]:3390 /prompt
```

Especifique `administrador` como el nombre de usuario y la contraseña que eligió como la contraseña.

Conexión a Escritorio remoto le preguntará si desea conectarse al sistema a pesar de los errores de certificado.
Si selecciona "Sí", se abrirá la conexión RDP.

**Nota:** salir de la sesión RDP contenedor sin cerrar la sesión puede impedir que el contenedor de apagar el equipo.
Asegúrese de salir de la sesión RDP escribiendo "cerrar sesión" (en lugar de "exit" o simplemente cierre la ventana RDP) antes de apagar el contenedor.

--------------------------


##Administración de PowerShell

###Enter-PSSession tiene el argumento de valor de containerid, no de New-PSSession

Esto es correcto.
Estamos planeando cimsession completa compatibilidad en el futuro.


No dude en las solicitudes de la característica de voz en [los foros](https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowscontainers).

--------------------------

[Volver a la página principal de contenedor](../containers_welcome.md)



