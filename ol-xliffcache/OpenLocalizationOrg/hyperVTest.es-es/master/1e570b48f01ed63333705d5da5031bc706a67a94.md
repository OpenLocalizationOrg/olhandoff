MS. ContentId: 8DE9250B-556B-47BC-AD9A-8992B3D3D0F9
título: fragmentos de código de PowerShell

#Fragmentos de código de PowerShell

Agregar esta frase para probar el proceso de HO HB.
PowerShell es una maravilla secuencias de comandos, herramienta de administración y automatización para Hyper-V.  Este es un cuadro de herramientas para explorar algunas de las cosas interesantes que puede hacer!

Toda la administración de Hyper-V debe ejecutarse como administrador por lo que suponga que todos los scripts y fragmentos de código se deben ejecutar como administrador desde una cuenta de administrador de Hyper-V.

Si no sabe si tiene los permisos adecuados, escriba <g id="f5b0b296-9051-45c3-83ac-10350427d4c7" ctype="x-code">Get-VM</g> y si se ejecuta sin errores, estará listo para ir.


##Herramientas de PowerShell directa

Todas las secuencias de comandos y los fragmentos de código en esta sección se basarán en los siguientes procedimientos básicos.

<g id="4a75d559-c0b8-41c8-8a30-31014d5f38c0" ctype="x-strong">Requisitos</g> :
*  PowerShell directa.
   Invitado de Windows 10 y el sistema operativo host.

<g id="56b50335-805a-43f6-be68-940d669535c0" ctype="x-strong">Variables comunes</g> :  
<g id="1a8c65ec-06d1-464d-9c9c-8ef2fb8f8e55" ctype="x-code">$VMName</g> --esto es una cadena con VMName.
Ver una lista de máquinas virtuales disponibles con <g id="d25d5d8f-6858-4290-8bec-1015e0e1892c" ctype="x-code">Get-VM</g>  
<g id="956485a9-c553-4858-b151-4ad2d4ba875a" ctype="x-code">$cred</g> --credencial para el sistema operativo invitado.
Se pueden rellenar utilizando <g id="feea1200-ff48-4c88-9008-d1f95525bb92" ctype="x-code">$cred = Get-Credential</g>

###Compruebe si se ha iniciado el invitado

Administrador de Hyper-V no proporciona visibilidad en el sistema operativo invitado que a menudo resulta difícil saber si se ha iniciado el SO invitado.

Utilice este comando para comprobar si se ha iniciado el invitado.

``` PowerShell
if((Invoke-Command -VMName $VMName -Credential $cred {"Test"}) -ne "Test"){Write-Host "Not Booted"} else {Write-Host "Booted"}
```

<g id="9fbfd4d1-bd25-43f3-9c6e-b727041eb16b" ctype="x-strong">Resultado</g>  
Imprime un mensaje descriptivo declarar el estado del sistema operativo invitado.


###Secuencia de comandos de bloqueo hasta que el invitado se ha iniciado

La siguiente función espera a que usa el mismo principio que esperar hasta que PowerShell está disponible en el invitado (es decir, el sistema operativo se ha iniciado y se ejecuta la mayoría de los servicios), a continuación, se devuelve.

``` PowerShell
function waitForPSDirect([string]$VMName, $cred){
   Write-Output "[$($VMName)]:: Waiting for PowerShell Direct (using $($cred.username))"
   while ((Invoke-Command -VMName $VMName -Credential $cred {"Test"} -ea SilentlyContinue) -ne "Test") {Sleep -Seconds 1}}
```

<g id="566efe5e-5203-4c7a-904c-a145a49799b6" ctype="x-strong">Resultado</g>  
Imprime un mensaje descriptivo y bloqueos hasta que la conexión a la máquina virtual se realiza correctamente.
Se realiza correctamente en modo silencioso.

###Secuencia de comandos de bloqueo hasta que el invitado tiene una red

Con PowerShell Direct es posible conectarse a una sesión de PowerShell en una máquina virtual antes de la máquina virtual ha recibido una dirección IP.

``` PowerShell
# Wait for DHCP
while ((Get-NetIPAddress | ? AddressFamily -eq IPv4 | ? IPAddress -ne 127.0.0.1).SuffixOrigin -ne "Dhcp") {sleep -Milliseconds 10}
```

<g id="4d5af3f6-c741-4be8-8fff-baaf09302e7a" ctype="x-em">* Resultado *</g>
Se bloquea hasta que se recibe una concesión de DHCP.
Puesto que esta secuencia de comandos no está buscando una subred específica o la dirección IP no funciona importar qué configuración de red está usando.
Se realiza correctamente en modo silencioso.

##Administración de credenciales con PowerShell

Scripts de Hyper-V con frecuencia necesitan controlar las credenciales para una o más máquinas virtuales, el host de Hyper-V o ambos.

Hay varias formas de lograr esto al trabajar con PowerShell directa o remota de PowerShell estándar:

1. La forma de primer (y más sencilla) es tener las mismas credenciales de usuario válidas en el host y el invitado o el host local y remota.
   Esto es bastante fácil si se registra con su cuenta de Microsoft - o si se encuentra en un entorno de dominio.
   En este escenario puede ejecutar simplemente <g id="ef2bba48-01d5-480d-9d58-415d277feae0" ctype="x-code">Invoke-Command - VMName "test" {get-process}</g>.
   
2. Permiten PowerShell pedir credenciales  
Si sus credenciales no coinciden, automáticamente obtendrá una petición de credenciales, lo que permite proporcionar las credenciales adecuadas para la máquina virtual.
   
3. Almacenar las credenciales en una variable para su reutilización.
   Ejecutar un comando simple similar al siguiente:
  ``` PowerShell
  $localCred = Get-Credential
  ```
Y, a continuación, ejecutar algo parecido a esto:
  ``` PowerShell
  Invoke-Command -VMName "test" -Credential $localCred  {get-process} 
  ```
Significa que se sólo le pida una vez por sesión de secuencia de comandos/PowerShell sus credenciales.

4. Codificar sus credenciales en las secuencias de comandos.
   <g id="c1da8dd7-a749-4881-b32c-00218008d4ea" ctype="x-strong">No hacer esto para cualquier carga de trabajo real o el sistema</g>
   > Advertencia: _No no hacer esto en un sistema de producción.
   > De no hacerlo con contraseñas reales. _
   
   Puede pasar elaborar un objeto PSCredential con algún código similar al siguiente:
  ``` PowerShell
  $localCred = New-Object -typename System.Management.Automation.PSCredential -argumentlist "Administrator", (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) 
  ```
Terriblemente insegura - pero útil para realizar pruebas.
Ahora no obtendrá ningún mensaje en esta sesión.





