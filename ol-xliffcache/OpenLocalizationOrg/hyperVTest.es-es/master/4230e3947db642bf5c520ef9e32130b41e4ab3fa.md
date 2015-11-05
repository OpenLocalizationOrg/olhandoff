MS. ContentId: 34D5925A-D724-4552-9403-C2703A973234 
título: migrar y actualizar las máquinas virtuales

#Migración y actualización de máquinas virtuales

Si mueve las máquinas virtuales a su host de Windows 10 que se crearon inicialmente con Hyper-V en Windows 8.1 o versiones anteriores, no podrá usar las nuevas características de máquina virtual hasta que actualice manualmente la versión de configuración de máquina virtual.

Para actualizar la versión de configuración, apague la máquina virtual y, a continuación, seleccione esta opción para actualizar la configuración de máquina Virtual en el Administrador de Hyper-V.
También puede abrir un elevado símbolo del sistema de Windows PowerShell y escriba:

 ```PowerShell
Update-VmVersion <vmname> | <vmobject>
 ```



##¿Cómo puedo comprobar la versión de la configuración de las máquinas virtuales que se ejecutan en Hyper-V?

Para buscar la versión de configuración, abra un símbolo de Windows PowerShell con privilegios elevados y ejecute el siguiente comando:

<g id="8126f92d-f4a0-42bd-988a-48b1c398111b" ctype="x-strong">Get-VM * | Nombre de tabla de formato de versión</g>

El comando de PowerShell genera la siguiente salida de ejemplo:

```
Name        State       CPUUsage(%) MemoryAssigned(M)   Uptime              Status                  Version

Atlantis    Running         0       1024                00:04:20.5910000    Operating normally      5.0

SGC VM      Running         0       538                 00:02:44.8350000    Operating normally      6.2
```


##¿Qué ocurre si no se actualiza la versión de configuración?

Si tiene máquinas virtuales que ha creado con una versión anterior de Hyper-V, algunas características no funcionen con esas máquinas virtuales hasta que actualice la versión de la máquina virtual.

Versión mínima de configuración de máquina virtual para las nuevas características de Hyper-V:

| <g id="6e16b4fa-8435-4339-b8ad-c840200eef63" ctype="x-strong">Nombre de la característica</g>| <g id="a5d0aa8c-0645-4a82-bc4a-3fde85815842" ctype="x-strong">Versión mínima de VM</g>| |
| :------------------------------------- | -----------------: ||
| Memoria de acceso rápido agregar o quitar| 6.0| |
| Acceso rápido agregar o quitar los adaptadores de red| 5.0| |
| Arranque seguro para las máquinas virtuales de Linux| 6.0| |
| Puntos de control de producción| 6.0| |
| PowerShell directa| 6.2| |
| Virtual módulo de plataforma segura (vTPM)| 6.2| |
| Agrupación de máquina virtual| 6.2| |


##Versión de configuración de máquina virtual

Al mover o importar una máquina virtual a un host que ejecuta Hyper-V en Windows 10 de host que ejecuta Windows 8.1, no se actualiza automáticamente el archivo de configuración de la máquina virtual.
Esto permite que la máquina virtual para moverse a un host que ejecuta Windows 8.1.
No tendrá acceso a las nuevas características de máquina virtual hasta que actualice manualmente la versión de configuración de máquina virtual.

La versión de configuración de máquina virtual representa la versión de Hyper-V configuración de la máquina virtual, el estado guardado y es compatible con los archivos de instantáneas.
Las máquinas virtuales con la versión 5 de configuración son compatibles con Windows 8.1 y puede ejecutarse en Windows 8.1 y 10 de Windows.
Las máquinas virtuales con la versión 6 de configuración son compatibles con 10 de Windows y no se ejecutará en Windows 8.1.

No es necesario actualizar todas las máquinas virtuales simultáneamente.
Puede actualizar las máquinas virtuales específicas cuando sea necesario.
Sin embargo, no tendrá acceso a las características de máquina virtual nueva hasta que actualice manualmente la versión de configuración para cada máquina virtual.


----------------

<g id="fbfe95a1-3279-477f-9f03-cff574f5fd94" ctype="x-em">* Importante *</g>

• Después de actualizar la versión de configuración de máquina virtual, no se puede mover la máquina virtual a un host que ejecuta Windows 8.1.

• No se puede degradar la versión de configuración de máquina virtual de la versión 6 a la versión 5.

• Debe desactivar la máquina virtual para actualizar la configuración de máquina virtual.

• Después de la actualización, la máquina virtual usa el nuevo formato de archivo de configuración.
Para obtener más información, vea el nuevo formato de archivo de configuración de máquina virtual.

--------






##¿Qué ocurre al actualizar la versión de una máquina virtual?

Al actualizar manualmente la versión de configuración de una máquina virtual a la versión 6.x, va a cambiar la estructura de archivos que se usa para almacenar los archivos de punto de comprobación y la configuración de las máquinas virtuales.

Máquinas virtuales actualizadas utilice un nuevo formato de archivo de configuración, que está diseñado para aumentar la eficacia de lectura y escritura de datos de configuración de máquina virtual.
La actualización también reduce la posibilidad de daños en los datos en caso de un error de almacenamiento.

En la siguiente tabla enumera las ubicaciones de archivo binario y la información de la extensión para una máquina virtual actualizada.

| <g id="b7af8787-2f51-42a8-90c5-6045671f39fa" ctype="x-strong">Los archivos de punto de comprobación y la configuración de máquina virtual (versión 6.x)</g>| <g id="4ab27356-2b67-4596-8d2f-ee547b0f12a4" ctype="x-strong">Descripción</g>| |
|:---------------|:----------------||
| <g id="058cb670-62fa-40b9-bd8d-89e8c1e4b24e" ctype="x-strong">Configuración de máquina virtual</g>| Información de configuración se almacena en un formato de archivo binario que utiliza la extensión .vmcx.| |
| <g id="4478005e-b3e0-478f-afc9-7a9573a9f759" ctype="x-strong">Estado de tiempo de ejecución de máquina virtual</g>| Los datos de estado en tiempo de ejecución se almacenan en un formato de archivo binario que utiliza la extensión .vmrs.| |
| <g id="157d63f6-750d-4a90-995e-db82bd0fe896" ctype="x-strong">Disco duro virtual de máquina virtual</g>| Los archivos de disco duro virtual para la máquina virtual.Utilizan las extensiones de archivo .vhd o .vhdx.| |
| <g id="eaedd90f-17ca-4d0a-8879-8a1a323c922a" ctype="x-strong">Archivos de disco duro virtual automático</g>| Archivos de disco de diferenciación utilizados para los puntos de control de la máquina virtual.Utilizan las extensiones de archivo .avhdx.| |
| <g id="3759b115-ea00-4e73-890b-8b4b44a95946" ctype="x-strong">Archivos de punto de comprobación</g>| Los puntos de control se almacenan en varios archivos de punto de comprobación.Cada punto de comprobación crea un archivo de configuración y el archivo de estado en tiempo de ejecución.Los archivos de punto de comprobación utilizan las extensiones de archivo .vmrs y .vmcx.Estos nuevos formatos de archivo también se usan para los puntos de control de producción y los puntos de control estándar.| |
Después de actualizar la configuración de máquina virtual versión 6.x, no es posible cambiar de la versión 6.x a la versión 5.

La máquina virtual debe desactivarse para actualizar la configuración de máquina virtual.

En la siguiente tabla enumera las ubicaciones de archivo predeterminadas para las máquinas virtuales nuevas o actualizadas.

| <g id="230ab3b9-8bcf-4afc-86fb-3f3358338b04" ctype="x-strong">Archivos de máquina virtual (versión 6.x)</g>| <g id="ca1dffe7-d593-40d5-b59a-87b664b7450d" ctype="x-strong">Descripción</g>| |
|:-----|:-----||
| <g id="a027c023-7022-4e4a-832c-17d08f16f37b" ctype="x-strong">Archivo de configuración de máquina virtual</g>| Máquinas de C:\ProgramData\Microsoft\Windows\Hyper-V\Virtual| |
| <g id="651a183a-264c-4651-9faf-c8262f60de11" ctype="x-strong">Archivo de estado en tiempo de ejecución de máquina virtual</g>| Máquinas de C:\ProgramData\Microsoft\Windows\Hyper-V\Virtual| |
| <g id="03a86aaa-acab-49b0-84bc-237e034ad2a1" ctype="x-strong">Archivos de punto de comprobación (.vmrs, .vmcx)</g>| C:\ProgramData\Microsoft\Windows\Snapshots| |
| <g id="54f21315-a184-4074-8dd3-5936e0bd0817" ctype="x-strong">Archivo de disco duro virtual (.vhd/.vhdx)</g>| Discos duros C:\Users\Public\Documents\Hyper-V\Virtual| |
| <g id="3ca3a1b0-e16a-4cef-996b-ba683a457541" ctype="x-strong">Archivos de disco duro virtual automático (.avhdx)</g>| Discos duros C:\Users\Public\Documents\Hyper-V\Virtual| |







