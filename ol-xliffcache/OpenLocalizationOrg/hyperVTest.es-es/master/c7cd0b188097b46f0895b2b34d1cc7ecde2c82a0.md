MS. ContentId: B971C429-CEF0-4DAB-8456-3B08AEC0C233
título: paso 7: exportar e importar una máquina virtual

#Paso 7: Exportar e importar una máquina virtual

Rápidamente puede copiar una máquina virtual o mover una máquina virtual mediante la exportación y la funcionalidad de importación.

##Exportar la VM

Exportar una máquina virtual exporta todas las piezas de la máquina virtual, incluidos los puntos de control.

1. En el Administrador de Hyper-V, haga clic en la máquina virtual y seleccione **exportar**.
   
   ![](media/select_export1.png)
2. Haga clic en **Examinar** en el cuadro de diálogo cuadro, navegue a C:\Users\Public y, a continuación, haga clic en **Seleccionar la carpeta**.
   
3. En el **Exportar Máquina Virtual** cuadro de diálogo, asegúrese de que la ruta de acceso parece correcto y, a continuación, haga clic en **exportar**.
   
   ![](media/click_export.png)
4. Mientras la máquina virtual que se va a exportar, puede ver el progreso en la sección Estado:
   
   ![](media/export_progress.png)

##¿Funcionaba la exportación?

Para comprobar que la máquina virtual se ha exportado, haga doble clic en el **iniciar** menú y seleccione **Explorador de archivos**.
1. Navegue a la máquina virtual del tutorial de C:\Users\Public\Windows.
2. Debe ver otra carpeta denominada VM del tutorial de Windows y dentro de esa carpeta debe ser tres carpetas con los archivos de la máquina virtual exportado:
   - Instantáneas
   - Discos duros virtuales
   - Máquinas virtuales
   
   ![](media/export_confirm.png)

##Importar la máquina virtual

Antes de que se importe la máquina virtual, vamos a eliminar la máquina virtual original.
Haga doble clic en la máquina virtual y seleccione **Eliminar**.
1. En **Administrador de Hyper-V**, en el **acción** menú, haga clic en **Importar máquina Virtual**.
2. En el **Buscar carpeta** sección, haga clic en Examinar y navegue a la máquina virtual del tutorial de C:\Users\Public\Windows y, a continuación, haga clic en **siguiente**.
3. En el **Seleccione la máquina virtual para importar** clic en la pantalla **siguiente**.
4. En el **Elegir un tipo de importación** sección, seleccione **registrar la máquina virtual en su lugar** y, a continuación, haga clic en **siguiente**.
6. En el **Elegir destino** sección, deje el valor predeterminado y haga clic en **siguiente**.
7. En carpetas de almacenamiento elija, deje la ruta de acceso predeterminada y haga clic en **siguiente**.
8. En la página Resumen, verá una lista de las rutas de acceso donde se ubicarán los nuevos archivos de máquina virtual.
   Haga clic en **Finalizar** para iniciar la importación.


##¿Funcionaba la importación?

Para asegurarse de que la importación trabajada, simplemente haga doble clic en la máquina virtual en **Administrador de Hyper-V** e inicie VMConnect para comprobar la máquina virtual.

##Paso siguiente:

[Paso 8: Experimentar con Windows Powershell](walkthrough_powershell.md)



