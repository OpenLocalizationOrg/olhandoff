MS. ContentId: 178899C9-8EA6-4D82-A0B0-8BE4DDD78DAE
título: paso 5: conectarse a la máquina virtual y finalizar la instalación

#Paso 5: Conectarse a la máquina virtual y finalizar la instalación

Para finalizar la creación de la máquina virtual, debe iniciar la máquina virtual y durante la instalación del sistema operativo.

##Conéctese a la máquina virtual

1. En **Administrador de Hyper-V**, haga doble clic en la máquina virtual.
   Se iniciará la herramienta VMConnect.
2. En VMConnect, haga clic en el color verde **iniciar** botón ![](media/start.png).
   Esto equivale a presionar el botón de encendido en un equipo físico.
3. La máquina virtual se iniciará en el programa de instalación y puede recorrer la instalación como lo haría en un equipo físico.

> **Nota:** a menos que se está ejecutando una versión de licencia por volumen de Windows 10, necesita una licencia independiente para Windows que se ejecuta en una máquina virtual.
> Sistema operativo de la máquina virtual es completamente independiente del sistema operativo host.


##Otras cosas que puede hacer en VMConnect

Aquí están todos los botones y las teclas de método abreviado asignadas a lo que hacen.

| **Para hacer esto...**| Haga clic aquí...| **O bien, hacer esto...**| |
| ----- | ----- | ----- | ----- |
| Iniciar la máquina virtual| ![](media/start.png)| CTRL + S| |
| Desactivar la máquina virtual| ![](media/turnoff.png)| | |
| Apagar una máquina virtual| ![](media/shutdown.png)| | |
| Guardar| ![](media/save.png)| | |
| Pausa| ![](media/pause.png)| | |
| Restablecer| ![](media/reset.png)| | |
| Versión de mouse| ![](media/ctrlaltdel.png)| CTRL + ALT + flecha izquierda| |
| Enviar CTRL + ALT + SUPR a la máquina virtual| | CTRL + ALT + FIN| |
| Cambiar del modo de pantalla completa al modo de ventana| | CTRL + ALT + INTER| |
| Use el modo de sesión mejorada| ![](media/basic.png)| | |
| Abra la configuración de la máquina virtual| | CTRL+O| |
| Crear un punto de control| ![](media/checkpoint.png)| CTRL + N o seleccione **acción** > **Checkpoint**| |
| Revertir a un punto de control| ![](media/revert.png)| CTRL + E| |
| Realice una captura de pantalla| | CTRL + C| |
| Devolver los clics del mouse o del teclado al equipo físico| | Presione CTRL + ALT + flecha izquierda y, a continuación, mueva el puntero del mouse fuera de la ventana de la máquina virtual.Se trata de la **versión combinación de teclas de mouse** y se puede cambiar en el **configuración de Hyper-V** en **Administrador de Hyper-V**.| |
| Enviar clics del mouse o teclado a la máquina virtual| | Haga clic en la ventana de la máquina virtual.El puntero del mouse puede aparecer como un pequeño punto al conectarse a una máquina virtual.| |
| Cambiar la configuración de la máquina virtual| | Seleccione **archivo** > **configuración**.| |
| Conectarse a una imagen de DVD (archivo .iso) o un disquete virtual (.vfd archivo)| | Haga clic en **Media** en el menú.Disquetes virtuales no se admiten para las máquinas virtuales de generación 2.| |


##Paso siguiente:

[Paso 6: Experimentar con los puntos de control](walkthrough_checkpoints.md)




