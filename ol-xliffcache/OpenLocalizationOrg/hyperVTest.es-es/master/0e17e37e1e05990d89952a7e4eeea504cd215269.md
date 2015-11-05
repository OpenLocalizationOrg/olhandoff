MS. ContentId: A6DD6776-614C-4D28-9B83-CB2EDFD263A3
título: paso 2: instalar Hyper-V en Windows 10

#Paso 2: Instalar Hyper-V en Windows 10

Antes de comenzar con las máquinas virtuales en Windows 10 deberá habilitar el rol de Hyper-V.
Esto puede hacerse mediante la interfaz de usuario gráfica 10 de Windows PowerShell o DISM.
Estos documentos le guiará a través de cada una de ellas.

##Habilitar Hyper-V mediante la GUI.

1. Haga clic con el botón secundario en el botón de Windows y seleccione "Programas y características".
   
2. Seleccione 'Windows activar o desactivar las características'.
   
3. Seleccione "Hyper-V" y haga clic en 'OK'.
   <br />![](media/enable_role_upd.png)
   
4. Una vez finalizada la instalación, se le pedirá que reinicie el equipo.
   <br />![](media/restart_upd.png)

##Habilitar Hyper-V con PowerShell

1. Abra una consola de PowerShell como administrador.
   
2. Escriba el siguiente comando:

`Enable-WindowsOptionalFeature-en línea - NombreCaracterística Microsoft Hyper-V – todos`

Una vez finalizada la instalación debe reiniciar el equipo.

##Habilitar Hyper-V con DISM.

La herramienta de administración y mantenimiento de imágenes de implementación o DISM se utiliza para mantener imágenes de Windows y preparar la instalación de Windows anterior Evironments.
DISM también puede utilizarse para habilitar las características de Windows en instancias del sistema operativo en ejecución.

Para habilitar el rol de Hyper-V mediante DISM:

1. Abra una sesión de PowerShell o CMD como administrador.
   
2. Escriba el siguiente comando:

`DISM /Online/All Enable-Feature /FeatureName:Microsoft-Hyper-V`

Una vez completado, se le pedirá que reinicie.

![](media/dism_upd.png)


##Paso siguiente

[Paso 3: Crear un conmutador virtual](walkthrough_virtual_switch.md)



