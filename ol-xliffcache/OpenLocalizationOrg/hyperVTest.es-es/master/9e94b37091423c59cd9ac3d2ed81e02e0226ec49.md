MS. ContentId: 8D89E9D8-2501-46A7-9304-2F19F37AFC85
título: trabajar con puntos de control

#Usar puntos de comprobación para revertir las máquinas virtuales a un estado anterior

Agregar esta frase para probar el proceso de HO HB.
Puntos de comprobación proporcionan una manera rápida y fácil de revertir la máquina virtual a un estado anterior.
Esto es especialmente útil cuando se va a realizar un cambio en una máquina virtual y desea poder volver al estado presente si causa problemas de cambio.


##Habilitar o deshabilitar los puntos de control

1.  En **Administrador de Hyper-V**, haga clic en el nombre de la máquina virtual y haga clic en **configuración**.
2.  En el **administración** sección, seleccione **puntos de comprobación**.
3.  Para permitir que los puntos de comprobación retirar esta máquina virtual, asegúrese de que habilitar los puntos de control está seleccionado, este es el comportamiento predeterminado.
   Para desactivar los puntos de comprobación, desactive el **Habilitar puntos de comprobación** casilla de verificación.
4.  Haga clic en **aplicar** para aplicar los cambios.
   Cuando haya terminado, haga clic en **Aceptar** para cerrar el cuadro de diálogo.


##Elija los puntos de control estándar o de producción

Hay dos tipos de puntos de comprobación:
*  **Los puntos de control de producción** --se utiliza principalmente en los servidores en entornos de producción como una forma de copia de seguridad.
*  **Los puntos de control estándar** --utilizados en el desarrollo o entornos de prueba para permitir la reversión si se produce un error en un cambio.

Ambos tipos de puntos de comprobación restauración una máquina virtual a un estado anterior.

Los puntos de control de producción creación un punto de comprobación coherentes con la aplicación de una máquina virtual.
Esto significa que el equipo virtual guardado se reanudará con ningún estado de la aplicación.

Los puntos de control estándar (anteriormente conocidos como instantáneas) capturan el estado de memoria exacto de la máquina virtual.
Esto significa que la máquina virtual se restaurará con **exactamente** el mismo estado en el que el punto de comprobación se bajan al estado de la aplicación exacta.
Los puntos de control estándar pueden contener información acerca de las conexiones de cliente, las transacciones y el estado de la red externa.
Esta información no sea válida cuando se aplica el punto de comprobación.
Además, si un punto de comprobación se realiza durante un bloqueo de aplicación, restaurar dicho punto de comprobación estará en el centro de dicho bloqueo.

La presencia de un punto de control estándar para una máquina virtual puede afectar al rendimiento de disco de la máquina virtual.
No se recomienda usar puntos de control estándar en máquinas virtuales al rendimiento o la disponibilidad de espacio de almacenamiento es crítica.


Aplicar un punto de control de producción implica arrancar el sistema operativo invitado desde un estado sin conexión.
Esto significa que no se captura ninguna información de estado o la seguridad de la aplicación como parte del proceso de punto de comprobación.

La siguiente tabla muestra cuándo usar puntos de control de producción o los puntos de control estándar, según el estado de la máquina virtual.

| **Estado de la máquina virtual**| **Punto de control de producción**| **Punto de control estándar**|
|:-----|:-----|:-----|
| **Ejecución con Integration Services**| Sí| Sí|
| **Ejecutar sin Integration Services**| No| Sí|
| **Sin conexión: ningún estado guardado**| Sí| Sí|
| **Sin conexión: con el estado guardado**| No| Sí|
| **En pausa**| No| Sí|
Para ver la diferencia entre los puntos de control estándar y de producción, observe el [Tutorial de puntos de comprobación](../quick_start/walkthrough_checkpoints.md).

##Establecer un tipo de punto de comprobación predeterminado

1.  En **Administrador de Hyper-V**, haga clic en el nombre de la máquina virtual y haga clic en **configuración**.
2.  En el **administración** sección, seleccione **puntos de comprobación**.
3.  Seleccione los puntos de control de producción o los puntos de control estándar.
   Si elige los puntos de control de producción, también puede especificar si el host debe tener un punto de control estándar si no se puede tomar un punto de control de producción.
   Si desactiva esta casilla de verificación y no se puede tomar un punto de control de producción, no se seleccionará ningún punto de comprobación.
4.  Si desea cambiar la ubicación donde se almacenan los archivos de configuración del punto de control, cambie la ruta de acceso en la **ubicación del archivo de punto de comprobación** sección.
5.  Haga clic en **aplicar** para aplicar los cambios.
   Cuando haya terminado, haga clic en **Aceptar** para cerrar el cuadro de diálogo.

Es el comportamiento predeterminado de Windows 10 para nuevas máquinas virtuales crear puntos de comprobación de producción con reserva de puntos de control estándar


##Crear un punto de control

Para crear un punto de control
1.  En **Administrador de Hyper-V**, en **máquinas virtuales**, seleccione la máquina virtual.
2.  Haga clic en el nombre de la máquina virtual y, a continuación, haga clic en **Checkpoint**.
3.  Una vez completado el proceso, aparecerá el punto de comprobación en **puntos de comprobación** en el **Administrador de Hyper-V**.


##Aplicar un punto de control

Si desea revertir la máquina virtual a un momento anterior, puede aplicar un punto de comprobación existente.

1.  En **Administrador de Hyper-V**, en **máquinas virtuales**, seleccione la máquina virtual.
2.  En la sección de puntos de control, haga clic en el punto de control que desea utilizar y haga clic en **aplicar**.
3.  Aparece un cuadro de diálogo con las siguientes opciones:

``` 
**Create Checkpoint and Apply**: Creates a new checkpoint of the virtual machine before it applies the earlier checkpoint. 

**Apply**: Applies only the checkpoint that you have chosen. You cannot undo this action.

**Cancel**: Closes the dialog box without doing anything.
```

##Eliminar un punto de control

Para eliminar correctamente un punto de comprobación:

1.  En **Administrador de Hyper-V**, seleccione la máquina virtual.
2.  En el **puntos de comprobación** sección, haga clic en el punto de control que desea eliminar y haga clic en eliminar.
   También puede eliminar un punto de control y todos los puntos de comprobación posteriores.
   Para ello, haga clic en el punto de comprobación más antiguo que desea eliminar y, a continuación, haga clic en **** Eliminar punto de comprobación** subárbol **.
3.  Que se le pida confirmación eliminar el punto de comprobación.
   Confirme que es el punto de comprobación correcto y, a continuación, haga clic en **Eliminar**.
4.  Combinarán los archivos .avhdx y .vhdx, y cuando haya finalizado, se eliminará el archivo .avhdx del sistema de archivos.

> **Sugerencia:** se puede usar Windows Powershell para eliminar un punto de comprobación mediante la **Remove-VMSnapshot** cmdlet.

Los puntos de control se almacenan como archivos .avhdx en la misma ubicación que los archivos .vhdx para la máquina virtual.
No debe eliminar los archivos de .avhdx directamente.


##Cambiar el lugar donde la configuración de punto de comprobación y guardar el estado de los archivos se almacenan

Si la máquina virtual no tiene puntos de comprobación, puede cambiar dónde se almacenan los archivos de estado guardado y configuración de punto de comprobación.

1.  En **Administrador de Hyper-V**, haga clic en el nombre de la máquina virtual y haga clic en **configuración**.
   
2.  En el **administración** sección, seleccione **puntos de comprobación** o **ubicación del archivo de punto de comprobación**.
   
4.  En **ubicación del archivo de punto de comprobación**, escriba la ruta de acceso a la carpeta donde desea almacenar los archivos.
   
5.  Haga clic en **aplicar** para aplicar los cambios.
   Cuando haya terminado, haga clic en **Aceptar** para cerrar el cuadro de diálogo.

La ubicación predeterminada para almacenar archivos de configuración de punto de comprobación es: % systemroot%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots.




##Cambiar el nombre de un punto de control

1.  En **Administrador de Hyper-V**, seleccione la máquina virtual.
2.  Haga clic en el punto de control y, a continuación, seleccione **cambiar el nombre de**.
3.  Escriba el nuevo nombre del punto de control.
   Debe ser inferior a 100 caracteres y el campo no puede estar vacío.
4.  Haga clic en **ENTRAR** cuando haya terminado.

De forma predeterminada, el nombre de un punto de comprobación es el nombre de la máquina virtual que se combina con la fecha y hora que se tomó el punto de comprobación.
Este es el formato estándar:

```
virtual_machine_name (MM/DD/YYY –hh:mm:ss AM\PM)
```

Los nombres están limitados a 100 caracteres o menos y el nombre no puede estar en blanco.






