MS. ContentId: 7dcd6da0-dd72-422d-8752-5eccc8116e02
título: administración de hosts de Hyper-V remotos

#Administrar los Hosts de Hyper-V remotos con el Administrador de Hyper-V

Administrador de Hyper-V proporciona herramientas para diagnosticar y administrar el host de Hyper-V local y un pequeño número de hosts remotos.
En este artículo se documenta los pasos de configuración para conectarse a los hosts de Hyper-V mediante el Administrador de Hyper-V en todas las configuraciones compatibles.

Para conectarse a un host de Hyper-V en el Administrador de Hyper-V, asegúrese de que <g id="cc977c94-2674-4707-88d1-9f0c435b88a7" ctype="x-strong">Administrador de Hyper-V</g> está seleccionado en el panel izquierdo y, a continuación, seleccione <g id="9a7f017b-0fd9-43ee-9442-746c9882ead1" ctype="x-strong">conectar al servidor...</g> en el panel derecho.

<g id="71bbae65-a430-4443-ad68-905060965490" ctype="x-linkText"></g>

##Combinaciones admitidas del host de Hyper-V con el Administrador de Hyper-V

Administrador de Hyper-V en Windows 10 le permite administrar:
* 10 de Windows
* Hosts de Windows 8.1 y Windows Server 2012 R2 Hyper-V
* Hosts de Windows 8 y Windows 2012 Hyper-V

Administrador de Hyper-V en Windows 8.1 y Windows Server 2012 R2 le permite administrar:
* Hosts de Windows 8.1 y Windows Server 2012 R2 Hyper-V
* Hosts de Windows 8 y Windows 2012 Hyper-V

> <g id="a1304d07-46f5-4160-9d0c-cd630529767c" ctype="x-strong">Nota:</g> no toda la funcionalidad de administrador de Hyper-V funciona para todas las versiones de host.

##Administrar localhost

Para agregar localhost a Administrador de Hyper-V como un host de Hyper-V, seleccione <g id="b92681db-267d-4e52-ba64-1e1ae900396b" ctype="x-strong">equipo Local</g> en el <g id="7d20b0e5-4999-4f80-ab20-d7a0db4eb995" ctype="x-strong">Seleccionar equipo</g> cuadro de diálogo.

<g id="c9f8d732-f013-4cbc-88ff-ed8e7aa0fe57" ctype="x-linkText"></g>

Si no se puede establecer una conexión:
*  Asegúrese de que el rol de servidor Hyper-V está habilitado.
   Consulte la <g id="676abc89-5337-4a5b-97ef-53196c532eebCapsExtId1" ctype="x-linkText">para comprobar la compatibilidad de la sección del tutorial</g><g id="676abc89-5337-4a5b-97ef-53196c532eebCapsExtId2" ctype="x-title"></g>.
*  Confirme que su cuenta de usuario forma parte del grupo de administradores de Hyper-V.


##Administrar un host de Hyper-V en el dominio

Para agregar un host de Hyper-V remoto al administrador de Hyper-V, seleccione <g id="2e030d78-c1ae-439c-be02-056999ed7b37" ctype="x-strong">otro equipo</g> en el <g id="9b4996fa-eabd-4ea4-89b6-a8ee4af85be7" ctype="x-strong">Seleccionar equipo</g> cuadro de diálogo y escriba el nombre de host, NetBIOS o FQDN del host remoto en el campo de texto.

<g id="3e27e7fd-7951-4e94-829e-cdbf2cdea8a8" ctype="x-linkText"></g>

Windows 10 había ampliado enormemente las posibles combinaciones de tipos de conexiones remotas.
Ahora puede conectarse a una remota de Windows de 10 o posterior host utilizando el nombre de host o la dirección IP.
Administrador de Hyper-V ahora admite también credenciales alternativas.

Para administrar los hosts de Hyper-V remotos, administración remota debe habilitarse en ambos equipos.

Puede hacerlo a través de <g id="f6de2212-019d-4338-b73d-b23348e6b81a" ctype="x-code">las propiedades del sistema -> configuración de administración remota</g> o ejecutando el siguiente comando de PowerShell como administrador:

``` PowerShell
winrm quickconfig
```

Si su cuenta de usuario actual coincide con una cuenta de administrador de Hyper-V en el host remoto, siga adelante y presione <g id="ce38afbf-eb71-4a89-bbdf-d0ff6df78d6c" ctype="x-strong">Aceptar</g> a conectar.

Esta es la única manera admitida para administrar un host remoto en el Administrador de Hyper-V en Windows 8 o Windows 8.1.


###Conectar con el host remoto como un usuario diferente

En el 10 de Windows, si no se ejecuta con la cuenta de usuario correctos para el host remoto, puede conectarse como otro usuario con credenciales alternativas.

Para especificar las credenciales para el host de Hyper-V remoto, seleccione <g id="d42091ec-d02e-4f6f-a7c4-054ed4633ead" ctype="x-strong">conectarse como otro usuario: ** en el ** Seleccionar equipo</g> cuadro de diálogo, a continuación, seleccione <g id="88065c2c-13f5-43a9-a4ac-b5e1ab0a7842" ctype="x-strong">Establecer usuario</g>.

<g id="ea2672dd-fada-4833-a7ab-c8819e10d2f6" ctype="x-linkText"></g>

> Nota: Es muy fácil olvidarse de establecer el usuario y haga clic en Aceptar con el usuario no especificado.
> Si se produce un error en la conexión, asegúrese de que realmente ha definido el usuario.

###Conectar con el host remoto mediante la dirección IP

A veces es más fácil conectarse utilizando el nombre de dirección en lugar de host IP.
10 de Windows le permite a su hacer eso.

Para conectarse mediante la dirección IP, escriba la dirección IP en el <g id="5ede8d91-fc19-4aea-87b7-334f175ce953" ctype="x-strong">otro equipo</g> campo de texto.


##Administrar un host de Hyper-V fuera de su dominio (o sin dominio)

Host de Hyper-V local:
1.  Enable-PSRemoting
De vuelta a la red pública.
   Se ejecutó
Set-NetConnectionProfile-NetworkCategory - privado de nombre "nombre"
2. Elemento de conjunto WSMan:\localhost\Client\TrustedHosts *-Force
3. Enable-WSManCredSSP-cliente rol - DelegateComputer *

Grupo de trabajo sólo:
1. (es necesario) Equipo local\Plantillas Templates\System\Credentials Delegation\Allow delegación de credenciales nuevas → habilitado y agregue WSMAN / *].
   En la lista de equipos, compruebe los valores predeterminados del cuadro forConcatenate SO con la entrada anterior
   
2. Equipo local\Plantillas Templates\System\Credentials Delegation\Allow delegación de credenciales nuevas con autenticación sólo NTLM de servidor → habilitado y agregue WSMAN / * a la lista de equipos, active la casilla para los valores predeterminados de SO concatenar con la entrada anterior
3. Equipo local\Plantillas administrativas\Componentes Windows\Windows Remote Management (WinRM) \WinRM Client\Allow CredSSP autenticación → establecido en habilitado

Host de Hyper-V remoto:
1. Deshabilita el firewall :)
2. Enable-PSRemoting
3. Elemento de conjunto WSMan:\localhost\Client\TrustedHosts *-Force
Eso es las instrucciones de demostración sólo que he usado.
   Reemplazar * y desactivar firewall de un único equipo y dejar que credssp y winRM a través de






