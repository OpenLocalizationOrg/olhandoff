MS. ContentId: FBBAADE6-F1A1-4B5C-8FD2-BDCA3FCF81CA
título: paso 6: experimento con puntos de control

#Paso 6: Experimentar con los puntos de control

Los puntos de control son una herramienta útil si desea guardar el estado actual de una máquina virtual antes de realizar un cambio como aplicar una actualización, instalar software o cambiar una configuración.
Si el cambio causa problemas, puede restaurar el punto de comprobación y volver atrás.

Hay dos tipos de puntos de comprobación:  
<g id="ce7d807b-8555-41e5-837f-33eee5c0c1cc" ctype="x-strong">Los puntos de control de producción</g>: usa principalmente en los servidores en entornos de producción.
<g id="269c4598-33f2-48fc-b208-e7cb1cf11efe" ctype="x-strong">Los puntos de control estándar</g>: usados en el desarrollo o entornos de prueba

Los puntos de control de producción son el valor predeterminado para Hyper-V en Windows 10.


##Cambiar el tipo de punto de comprobación

Para comenzar, pruebe el estilo anterior de puntos de comprobación, <g id="78f1eca8-9ee3-40c7-a2e8-da610517d04b" ctype="x-strong">puntos de control estándar</g>.
Puesto que los puntos de control de producción son el valor predeterminado, tenemos que ir a la configuración de la máquina virtual y cambie el tipo de punto de comprobación.

1. Haga doble clic en <g id="4f111d07-43f1-4ab8-be11-aeccada1f75c" ctype="x-strong">máquina virtual del tutorial de Windows</g> y seleccione <g id="ad112fa7-e90b-4b8f-8be5-967244720299" ctype="x-strong">configuración</g>.
2. En el <g id="f790007e-b356-41ba-acad-5dbbed5a9996" ctype="x-strong">administración</g> sección, seleccione <g id="dc785ccd-1562-45e3-8c40-8953a4309c92" ctype="x-strong">puntos de comprobación</g>.
3. Seleccione <g id="447a3ec3-4a32-4d0a-9fde-ea39d476b31b" ctype="x-strong">puntos de control estándar</g>.
   El cuadro de diálogo debería tener este aspecto:
   
   <g id="8915684f-c369-4ec3-9efa-2806e6c963c5" ctype="x-linkText"></g>
4.  Haga clic en <g id="c0715328-68e8-45cf-bfd8-bf507ad7e055" ctype="x-strong">Aceptar</g> para cerrar el cuadro de diálogo.

##Abra el Bloc de notas para probar los puntos de control

Para ver lo que ocurre con cada tipo de punto de comprobación, se ejecutará una aplicación en la máquina virtual.
1. Haga doble clic en <g id="26d94e86-3a3a-4862-a61b-3e071a5aee5a" ctype="x-strong">máquina virtual del tutorial de Windows</g> y seleccione <g id="f9c31022-360f-49cc-8479-c21756c884cf" ctype="x-strong">Conectar</g>.
2. En la máquina virtual, abra <g id="752da92e-e38a-4249-86c1-87d05b45cbe2" ctype="x-strong">el Bloc de notas</g> haciendo clic en el <g id="e0168d09-e6f2-4a46-84d6-fadf55a95965" ctype="x-strong">iniciar</g> menú y escriba <g id="7443a0ec-b5b6-4ed1-97fc-64bc7a415da6" ctype="x-strong">el Bloc de notas</g> y, a continuación, selecciónelo en los resultados.
3. En el Bloc de notas, escriba <g id="99d929f3-797a-413b-9c19-cfdd73b7cbcc" ctype="x-strong">Esto es una prueba de puntos de comprobación.</g> El archivo debe tener este aspecto:
   
   <g id="6beddc9d-6949-4f3c-b840-ff0d503ed2cf" ctype="x-linkText"></g>
4. Guarde el archivo como <g id="15955be0-bc70-41e6-8e7d-7f45f4c5d71a" ctype="x-strong">test.txt</g>, pero no cierre el Bloc de notas.
   Deje ejecutándose en la máquina virtual.

##Crear un punto de control estándar

1. Para crear el punto de control, haga clic en el <g id="94004a9c-953d-45cc-9eb6-50efdd08da15" ctype="x-linkText"></g> <g id="b737418f-0bfd-49e6-9163-a906241b116e" ctype="x-strong">punto de comprobación</g> botón en la barra de menús.
2. En el cuadro de diálogo de nombre de punto de comprobación, escriba <g id="ff98428a-933d-4522-b039-e9326ae91499" ctype="x-strong">estándar</g>.
   El cuadro de diálogo debería tener este aspecto:
   
   <g id="eaab4508-5d04-41b3-af7b-d4edadcc08a9" ctype="x-linkText"></g>
3. Una vez completado el proceso, aparecerá el punto de comprobación en <g id="a8b96699-5d5f-4ad4-89c3-06ffea099955" ctype="x-strong">puntos de comprobación</g> en el <g id="36055983-12fa-4592-ae9a-74877899834a" ctype="x-strong">Administrador de Hyper-V</g>.
   
   <g id="4f88a8a0-3d8a-4610-874d-5b8ffdb749cd" ctype="x-linkText"></g>

##Crear un punto de control de producción

Ahora, necesitamos cambiar cambiar el tipo de punto de comprobación que se va a aplicar en <g id="87377e2b-320c-497f-bd98-c796546d99e7" ctype="x-strong">puntos de comprobación de producción</g> antes de realizar un segundo punto de control.

1.  Haga la máquina virtual y a continuación, haga clic en <g id="d85b8259-f9a5-48dc-8f06-ec567d360f6b" ctype="x-strong">configuración</g>.
2.  En el <g id="1deddb76-2d82-4d3e-be1e-dec56f3c875b" ctype="x-strong">administración</g> sección, seleccione <g id="65f18bd3-c88b-4a12-9d30-ec709e6481be" ctype="x-strong">puntos de comprobación</g>.
3.  Seleccione <g id="28d89de5-b226-4714-be6b-e655b0928d96" ctype="x-strong">puntos de comprobación de producción</g>.
4.  Desactive la opción de reserva.
   Si el sistema no puede tener un punto de control de producción, queremos que producirá un error en lugar de realizar un punto de control estándar.
   
   <g id="4587babd-490d-4771-bcca-9e5608310016" ctype="x-linkText"></g>
5.  Haga clic en <g id="b775a591-c63e-4925-838a-0c2095c5d86b" ctype="x-strong">Aceptar</g> para cerrar el cuadro de diálogo.
6.  Haga doble clic en la máquina virtual nuevo y seleccione <g id="14090719-e473-4441-b224-8849889d49df" ctype="x-strong">Conectar</g>.
7.  En el Bloc de notas en la máquina virtual, escriba otra línea lee <g id="3f67f78b-c348-4b60-a775-292659680b50" ctype="x-strong">Esto es una prueba de un punto de control de producción</g> y vuelva a guardar el archivo.
8.  Haga clic en el <g id="c3075aaf-2a1b-4e24-a12e-be7686db3875" ctype="x-linkText"></g> <g id="89656103-968f-4fb1-a052-629998e25c38" ctype="x-strong">punto de comprobación</g> botón en la barra de menús.
9.  Cuando se le pida, asígnele el nombre <g id="a3c2997a-fe30-46ae-b597-a7192ca32cb4" ctype="x-strong">producción</g> y, a continuación, haga clic en <g id="a45e67e9-c387-45f3-ac0d-a86660e273c6" ctype="x-strong">Sí</g>.
   
   <g id="dd750d26-9654-4f1b-a2b2-d65715595f97" ctype="x-linkText"></g>
10. Cerrar VMConnect.
   La máquina virtual seguirá ejecutándose, puede simplemente no esté conectado a él ya.
11. En el Administrador de Hyper-V, la lista de puntos de control tendrá ahora este aspecto:
   
   <g id="73ecd4fa-d1d3-48e8-a43e-5a830fed9748" ctype="x-linkText"></g>



##Aplicar el punto de control estándar

1.  En <g id="569baf6b-6c1f-4eb3-a885-08f66e2a5a90" ctype="x-strong">Administrador de Hyper-V</g>, en el <g id="ad462c91-660a-42d8-8996-19c757a567bd" ctype="x-strong">puntos de comprobación</g> sección, haga clic en el título de uno <g id="44faa753-3e4a-4272-8fb8-7d6333b78303" ctype="x-strong">estándar</g> y haga clic en <g id="cc1c6506-e59b-4994-8678-a09806a7943c" ctype="x-strong">aplicar</g>.
2.  En el cuadro de diálogo emergente, haga clic en <g id="4e2d084b-072a-43fa-82bb-ef5ba597d32f" ctype="x-strong">Crear punto de comprobación y aplicar</g>.
   
   <g id="c3fb8e38-683e-4c9d-bc60-e245a0c15e0c" ctype="x-linkText"></g>
34. Cuando termine, la lista de puntos de comprobación le ahora el siguiente aspecto:
   
   <g id="b26a53b1-053d-47c9-9fc1-f09c867ea934" ctype="x-linkText"></g>
4. Cuando éste finalice, haga clic en la máquina virtual y haga clic en <g id="52694321-ed6a-4e23-837b-41032c884e41" ctype="x-strong">Conectar</g> para conectarse a la máquina virtual.
5. Cuando se conecta a la máquina virtual, la máquina virtual debe estar en ejecución, con el Bloc de notas abierto, pero se perderá la línea acerca de los puntos de control de producción:
   
   <g id="86fea0d4-f601-412b-a446-081fb70213c4" ctype="x-linkText"></g>
6. Cerrar VMConnect, pero deje la máquina virtual que se ejecuta.


##Aplicar el punto de control de producción

Ahora, volvamos al administrador de Hyper-V y aplicar el punto de control de producción y ver el aspecto después de la máquina virtual.

1.  En la sección de puntos de control, haga clic en el título de uno <g id="8bb20d90-ec79-46c6-8dbd-6a1c1ad3f0e5" ctype="x-strong">punto de comprobación de producción</g> y haga clic en <g id="242fe52a-b8b7-4820-9999-0ae55e80b948" ctype="x-strong">aplicar</g>.
2.  En el cuadro de diálogo emergente, seleccione <g id="004d7388-3477-44c4-85f3-e088dcaee2e2" ctype="x-strong">Crear punto de comprobación y aplicar</g>.
3. Cuando éste finalice, haga clic en la máquina virtual y haga clic en <g id="aa42e686-ad37-4052-802f-1be9243e5719" ctype="x-strong">Conectar</g> para iniciar la máquina virtual.
4. Observará que no se está ejecutando la máquina virtual.
   Haga clic en el <g id="716bdb82-82cf-4c2b-a995-e4169b88a298" ctype="x-linkText"></g> botón de inicio en la barra de menús para iniciar la máquina virtual.
5. Abrir Abrir test.txt en el Bloc de notas.
   Debería ver la línea en el archivo sobre las pruebas de los puntos de control de producción:
   
   <g id="4db84606-f178-4550-8635-930deb30b8b7" ctype="x-linkText"></g>


##Cambiar el nombre de un punto de control

1. Haga clic en el último punto de comprobación en el árbol y haga clic en Cambiar nombre.
2. Nombre del punto de control <g id="5bf22d29-bdac-47ee-9274-64aae9f4c5e8" ctype="x-strong">Eliminar me</g>.
   
   <g id="763bcf21-0360-4408-914b-1f97646eab0c" ctype="x-linkText"></g>

##Eliminar un punto de control

El paso anterior probablemente ha proporcionado una sugerencia sobre lo que haremos a continuación.
Vamos a eliminar el punto de control que acaba de cambiar.

1. Haga doble clic en el punto de control denominado <g id="7f6161e2-c7f9-4414-9a66-4e96dadef579" ctype="x-strong">Eliminar me</g> y haga clic en <g id="099d3a5c-12d0-4a60-8a1b-32430bd42f84" ctype="x-strong">Delete checkpoint</g>.
   
   <g id="46a9d18b-cfa4-42f7-9e87-99e04b7e98ca" ctype="x-linkText"></g>
2. En el cuadro de diálogo de advertencia, haga clic en <g id="532965bf-04f4-4b45-9ca3-845410d82c2b" ctype="x-strong">Eliminar</g>.
   
   <g id="e6a5772b-6b04-40b0-9bf9-7b3ff8b4ebc3" ctype="x-linkText"></g>
3. Después de elimina el punto de control, la lista debe tener un aspecto similar al siguiente:
   
   <g id="61ae0f70-c3bf-468d-90ed-8a788e67f059" ctype="x-linkText"></g>


##Paso siguiente:

<g id="ac38fc69-a267-42dc-85ef-d29df00d2339CapsExtId1" ctype="x-linkText">Paso 7: Exportar e importar una máquina virtual</g><g id="ac38fc69-a267-42dc-85ef-d29df00d2339CapsExtId2" ctype="x-title"></g>






