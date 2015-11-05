MS. ContentId: e586a11a-870f-403b-8af8-4c2931589d26
título: administración de Windows con PowerShell Direct

#Administrar Windows con PowerShell Direct

Puede usar PowerShell directa para administrar de forma remota un 10 de Windows o la máquina virtual de vista previa técnica de Windows Server desde un host 10 de Windows o Windows Server Technical Preview Hyper-V.
PowerShell directa permite la administración de PowerShell dentro de un virtual machine independientemente de la configuración de red o la configuración de administración remota en el host de Hyper-V o la máquina virtual.
Esto facilita a los administradores de Hyper-V automatizar y secuencia de comandos de configuración y administración de máquinas virtuales.

Hay dos maneras de ejecutar PowerShell directa:
* Crear y salir de una sesión de PowerShell directa mediante cmdlets de PSSession
* Ejecutar secuencia de comandos o un comando con el cmdlet Invoke-Command

Si está administrando más antiguos de las máquinas virtuales, use conexión a máquina Virtual (VMConnect) o <g id="76c6a425-b9c5-42e9-ab30-9e25f30a853cCapsExtId1" ctype="x-linkText">Configurar una red virtual para la máquina virtual</g><g id="76c6a425-b9c5-42e9-ab30-9e25f30a853cCapsExtId2" ctype="x-title"></g>.

##Crear y salir de una sesión de PowerShell directa mediante cmdlets de PSSession

1. En el host de Hyper-V, abra Windows PowerShell como administrador.
   
3. Ejecute uno de los siguientes comandos para crear una sesión mediante el nombre de la máquina virtual o GUID:
``` PowerShell
Enter-PSSession -VMName <VMName>
Enter-PSSession -VMGUID <VMGUID>
```

4. Ejecute los comandos que necesita.
   Estos comandos se ejecutan en la máquina virtual que creó la sesión con.
5. Cuando haya terminado, ejecute el siguiente comando para cerrar la sesión:
``` PowerShell
Exit-PSSession 
```

> Nota: Si le sesión no conectarse, asegúrese de que está utilizando las credenciales de la máquina virtual que se conecta, no el host de Hyper-V.

Para obtener más información acerca de estos cmdlets, consulte <g id="baa69d3d-ad91-480e-bdc4-62bb88df849fCapsExtId1" ctype="x-linkText">Enter-PSSession</g><g id="baa69d3d-ad91-480e-bdc4-62bb88df849fCapsExtId2" ctype="x-title"></g> y <g id="38e0d289-6063-44a4-b243-c8af6fa6d99dCapsExtId1" ctype="x-linkText">Exit-PSSession</g><g id="38e0d289-6063-44a4-b243-c8af6fa6d99dCapsExtId2" ctype="x-title"></g>.

##Ejecutar secuencia de comandos o un comando con el cmdlet Invoke-Command

Puede utilizar el <g id="4cc06c47-a1d3-42da-9b7c-87ba1d867535CapsExtId1" ctype="x-linkText">Invoke-Command</g><g id="4cc06c47-a1d3-42da-9b7c-87ba1d867535CapsExtId2" ctype="x-title"></g> cmdlet para ejecutar un conjunto predeterminado de comandos en la máquina virtual.
Este es un ejemplo de cómo puede usar el cmdlet Invoke-Command donde PSTest es el nombre de la máquina virtual y el script se ejecute (foo.ps1) está en la carpeta de secuencia de comandos en la unidad C: / unidad:

 ``` PowerShell
 Invoke-Command -VMName PSTest -FilePath C:\script\foo.ps1 
 ```

Para ejecutar un único comando, use la <g id="1fd0a62a-5111-4fa7-8801-ceec74347b94" ctype="x-strong">- ScriptBlock</g> parámetro:

 ``` PowerShell
 Invoke-Command -VMName PSTest -ScriptBlock { cmdlet } 
 ```

##¿Los requisitos para utilizar PowerShell Direct?

Para crear una sesión de PowerShell directamente en una máquina virtual,
* La máquina virtual debe ejecutarse localmente en el host y arranque.
* Debe iniciar sesión en el equipo host como un administrador de Hyper-V.
* Debe proporcionar credenciales de usuario válidas para la máquina virtual.
* 10 de Windows, vista previa técnica de Windows Server o una versión posterior, debe ejecutar el sistema operativo host.
* La máquina virtual debe ejecutar Windows 10, vista previa técnica de Windows Server o una versión posterior.

Puede utilizar el <g id="c89668e6-3b23-4d86-a62e-f405914903dfCapsExtId1" ctype="x-linkText">Get-VM</g><g id="c89668e6-3b23-4d86-a62e-f405914903dfCapsExtId2" ctype="x-title"></g> cmdlet para comprobar que las credenciales que utiliza tienen la función de administrador de Hyper-V y ver qué máquinas virtuales se ejecutan localmente en el host y arranque.

##¿Qué puede hacer con PowerShell Direct?

Vea <g id="3fa7eefd-7155-4d13-a4f2-b5008f4a1f8eCapsExtId1" ctype="x-linkText">fragmentos de código de PowerShell Direct</g><g id="3fa7eefd-7155-4d13-a4f2-b5008f4a1f8eCapsExtId2" ctype="x-title"></g> para numerosos ejemplos de cómo usar PowerShell directamente en su entorno, así como sugerencias y trucos para escribir secuencias de comandos de Hyper-V con PowerShell.






