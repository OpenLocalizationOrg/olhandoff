MS. ContentId: D1D4969F-52FD-43A2-982B-B531B0343D2B 
título: solución de problemas

#Solución de problemas de Hyper-V en Windows 10

##Actualiza a Windows 10 y ahora no puedo conectarme a mi host de nivel inferior (Windows 8.1 o Server 2012 R2)

En el 10 de Windows, Administrador de Hyper-V se mueve a WinRM para la administración remota.
Lo que significa es ahora la administración remota debe estar habilitada en el host remoto para poder utilizar Administrador de Hyper-V para administrarlo.

Para obtener más información, vea <g id="73b79073-a899-4b6b-8ab8-009c40182c3bCapsExtId1" ctype="x-linkText">administración de Hosts de Hyper-V remoto</g><g id="73b79073-a899-4b6b-8ab8-009c40182c3bCapsExtId2" ctype="x-title"></g>

##Se ha cambiado el tipo de punto de comprobación, pero todavía tiene un tipo de punto de comprobación incorrecto

Si va a llevar el punto de control de VMConnect y cambia el tipo de punto de comprobación en el Administrador de Hyper-V realizada el punto de comprobación ser cualquier tipo de punto de comprobación se especificó cuando se abrió VMConnect.

VMConnect de cierre y vuelva a abrirlo para que tenga el tipo de punto de comprobación correcto.

##Cuando se intenta crear un disco duro virtual en una unidad flash, se muestra un mensaje de error

Hyper-V no admite unidades de disco con formato FAT o FAT32, ya que estos sistemas de archivos no proporcionan listas de control de acceso (ACL) y no admiten archivos mayores de 4GB.
ExFAT discos formateados solo proporcionan una funcionalidad limitada ACL y, por tanto, tampoco se admiten por razones de seguridad.
El mensaje de error mostrado en PowerShell es "no se pudo crear el sistema ' \[path a VHD\]': no se pudo completar la operación solicitada debido a una limitación del sistema de archivos (0x80070299)."

Utilice NTFS unidad con formato en su lugar.

##Al intentar instalar aparece este mensaje: "no se puede instalar Hyper-V: el procesador no es compatible con traducción de direcciones de nivel de segundo (SLAT)."

Hyper-V requiere LISTÓN para ejecutar máquinas virtuales.
Si el equipo no admite SLAT, no puede ser un host de virtual mahchines.

Si sólo está intentando instalar las herramientas de administración, anule la selección de <g id="cc15402d-66f3-4c56-ac9a-ee5bdb0c5bbc" ctype="x-strong">plataforma Hyper-V</g> en <g id="26a6a0af-1d25-406f-a428-16b93e00d520" ctype="x-strong">programas y características</g> > <g id="c9f3dd81-c35e-48a9-be2e-e238b8523391" ctype="x-strong">o desactivar las características de Windows Active</g>.




