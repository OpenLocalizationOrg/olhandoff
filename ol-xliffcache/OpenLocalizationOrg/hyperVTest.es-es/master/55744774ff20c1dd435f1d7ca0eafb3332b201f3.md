MS. ContentId: 040B1B51-0F25-4295-B317-8CC4DE0A1AFF
título: exportar e importar máquinas virtuales




#Las máquinas virtuales de importación y exportación

Puede usar la exportación e importar funcionalidad para duplicar rápidamente máquinas virtuales o moverlas de un host a otro.
No es necesario exportar una máquina virtual para poder importarlo.
Puede copiar simplemente una máquina virtual y sus archivos asociados en el nuevo host y, a continuación, utilice la **Importar máquina Virtual** Asistente para especificar la ubicación de los archivos.
Esto registra la máquina virtual con Hyper-V y hace que esté disponible para usarse.

##Exportar las máquinas virtuales

Una forma sencilla para preparar las máquinas virtuales que desea importar es el **Exportar Máquina Virtual** asistente.

1. En el Administrador de Hyper-V, seleccione una o varias máquinas virtuales, haga doble clic en la selección y seleccione **exportar**.
2. Haga clic en **Examinar** en el cuadro de diálogo y elija dónde desea colocar las VM exportadas y, a continuación, haga clic en **Seleccionar la carpeta**.
3. En el **Exportar Máquina Virtual** cuadro de diálogo, haga clic en **exportar**.

Para obtener información sobre cómo usar Windows PowerShell para exportar máquinas virtuales, vea [Export-VM](https://technet.microsoft.com/library/hh848491.aspx)

##Importar máquinas virtuales

1. En **Administrador de Hyper-V**, en el **acción** menú, haga clic en **Importar máquina Virtual**.
2. En la sección Buscar carpeta, haga clic en Examinar y navegue a la ubicación de los archivos de máquina virtual.
   Tenga en cuenta que con el Asistente para puede importar una máquina virtual a la vez y tiene que seleccionar la carpeta de la máquina virtual en lugar de la carpeta de exportación general.
   Haga clic en **siguiente** finalizada.
3. Seleccione la máquina virtual para importar y, a continuación, haga clic en **siguiente**.
4. En la sección Seleccionar tipo de importación, puede elegir cómo importar la máquina virtual:
   -  **Registrar** : utiliza el identificador único existente de la máquina virtual y lo registra en contexto.
      Elija esta opción si los archivos de las máquinas virtuales ya están en la ubicación correcta.
   - **Restaurar** : utiliza el identificador único de la máquina virtual original y también copia los archivos de máquina virtual en la ubicación predeterminada especificada para el host.
   - **Copia** : crea un nuevo identificador único para la máquina virtual y también copia los archivos de máquina virtual en la ubicación predeterminada especificada para el host.
   
5. Después de seleccionar cómo importar la máquina virtual, haga clic en **siguiente**.
6. En la sección Seleccionar destino, puede elegir dónde almacenar los archivos de la máquina virtual o dejarlos en su ubicación actual.
   Cuando haya terminado, haga clic en **siguiente**.
7. En carpetas de almacenamiento elija, puede seleccionar otro lugar para almacenar el archivo .vhdx o dejarlos donde están.
   Cuando haya terminado, haga clic en **siguiente**.
8. Cuando haya terminado de importar la máquina virtual, verá la página de resumen que describe dónde se encuentran los nuevos archivos de máquina virtual.

El Asistente Importar máquina Virtual también le guía por los pasos para abordar las incompatibilidades al importar la máquina virtual al nuevo host, por lo que este asistente puede ayudarle con la configuración que está asociada con el hardware físico, como memoria, los conmutadores virtuales y los procesadores virtuales.

Para importar una máquina virtual, el asistente hace lo siguiente:
1. Crea una copia del archivo de configuración de máquina virtual.
   Esto sirve como medida de precaución produce un reinicio inesperado del host como de un corte del suministro eléctrico.
2. Valida el hardware.
   Información en el archivo de configuración de máquina virtual se compara con el hardware en el nuevo host.
3. Compila una lista de errores.
   Esta lista identifica qué debe configurarse y determina las páginas que aparecen siguiente en el asistente.
4. Muestra las páginas pertinentes, una categoría a la vez.
   El asistente explica cada incompatibilidad que le ayudará a volver a configurar la máquina virtual para que sean compatibles con el nuevo host.
5. Quita la copia del archivo de configuración.
   Después de que el asistente hace esto, la máquina virtual está lista para iniciarse.

Además del asistente, el módulo de Hyper-V para Windows PowerShell incluye cmdlets para importar las máquinas virtuales.
Para obtener más información, vea [Import-VM](https://technet.microsoft.com/library/hh848495.aspx).



