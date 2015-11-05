MS. ContentId: 4981828d-1a08-4d8c-a99d-874a926a153f
título: PowerShell para comparación Docker

#Comparación de Docker para administrar contenedores de servidores de Windows PowerShell

Actualizar contenido en el 27 de octubre para pruebas, ver2.
Hay muchas maneras de administrar contenedores de Windows Server con herramientas de Windows en el equipo (en esta versión preliminar, PowerShell) y herramientas de administración de código abierto como Docker.
Guías de esquematización individualmente disponibles aquí:
* <g id="73c50499-9d65-4e27-adfc-a10546869e23CapsExtId1" ctype="x-linkText">Administrar contenedores de Windows Server con Docker</g><g id="73c50499-9d65-4e27-adfc-a10546869e23CapsExtId2" ctype="x-title"></g>
* <g id="ec013f98-7928-4f72-993e-6c157e2d0577CapsExtId1" ctype="x-linkText">Administrar contenedores de servidor de Windows con PowerShell</g><g id="ec013f98-7928-4f72-993e-6c157e2d0577CapsExtId2" ctype="x-title"></g>

Esta página es ampliar la comparación de las herramientas de Docker y herramientas de administración de PowerShell de referencia de profundidad.

##PowerShell para contenedores frente a las máquinas virtuales de Hyper-V

Puede crear, ejecutar e interactuar con Windows Server contenedores mediante cmdlets de PowerShell.
Todo lo que necesita para empezar a trabajar está disponible en el equipo.

Si ha usado PowerShell de Hyper-V, el diseño de los cmdlets debe ser bastante familiar.
Una gran parte del flujo de trabajo es similar a cómo se podría administrar una máquina virtual mediante el módulo de Hyper-V.
En lugar de <g id="b6f725e3-e5ea-45de-bfa1-53fe5ef4effa" ctype="x-code">New-VM</g>, <g id="c7f3ced7-00a5-4c67-8fb3-8586469d4b50" ctype="x-code">Get-VM</g>, <g id="f9b945e1-e0cd-436b-8bbe-a656096b1d7e" ctype="x-code">Start-VM</g>, <g id="0a42a87b-ed73-44bb-b828-a5a7c94c440c" ctype="x-code">Stop-VM</g>, tiene <g id="91e20bda-08d5-4f62-948e-b9fc0131849b" ctype="x-code">nuevo contenedor</g>, <g id="c1eb5ba3-4a57-414c-9d7b-99a37228b4d6" ctype="x-code">Get Container</g>, <g id="76987b14-6de2-4c69-8168-f6071d336b35" ctype="x-code">Inicio contenedor</g>, <g id="befbcf72-cb9b-4f49-b756-edcb2617279f" ctype="x-code">Stop contenedor</g>.
Hay bastantes cmdlets específicos del contenedor y los parámetros, pero el ciclo de vida general y administración de un contenedor de Windows es más o menos como el de una máquina virtual de Hyper-V.

##¿Cómo se comparan la administración de PowerShell con Docker?

Los cmdlets de PowerShell de contenedores exponer una API que no es exactamente lo mismo que Docker; como regla general, los cmdlets son más granulares en operación.
Algunos comandos Docker tengan bastante sencillos paralelos en PowerShell:

| Comando docker| PowerShell Cmdlet|
|----|----|
| <g id="11858176-e7a8-40b4-a8a3-3a049a0b994d" ctype="x-code">docker ps - a</g>| <g id="019baa5a-b63e-4328-a429-4aa52817af46" ctype="x-code">Get-Container</g>|
| <g id="a9ef4bd6-866f-49e0-a884-cbd45a0cd74f" ctype="x-code">imágenes docker</g>| <g id="8550f186-4f4b-4947-a6fd-fe139cf2d0c6" ctype="x-code">Get-ContainerImage</g>|
| <g id="2ce64bfe-e95f-4a22-a02a-84b91d3487c0" ctype="x-code">rm docker</g>| <g id="effd6f72-6750-4a7c-85f1-e3952d320aa2" ctype="x-code">Quitar contenedores</g>|
| <g id="e4073cd3-3928-4bd5-b2c1-c9fcbdbb9851" ctype="x-code">rmi docker</g>| <g id="393891d5-c6fd-463a-9cc7-fc89e97686c5" ctype="x-code">Quitar ContainerImage</g>|
| <g id="d84e8c9d-9148-4dc2-bd25-4feaf0f9da7b" ctype="x-code">crear docker</g>| <g id="3515f8e9-9833-407d-aa29-129f75ab3f66" ctype="x-code">Nuevo contenedor</g>|
| <g id="c0883de6-3a75-4f73-9e3d-b5fc6c7ed4d9" ctype="x-code">confirmación de docker < Id. de contenedor ></g>| <g id="76daaa83-d330-466d-a2ea-d61acfd6aaef" ctype="x-code">Nueva ContainerImage-contenedor < contenedor ></g>|
| <g id="f8ae7a90-dfc1-492f-8f6a-f904ecb348de" ctype="x-code">carga docker < tarball ></g>| <g id="79b7cd3d-d9c0-4fdb-bb2a-e80cb8f9ad20" ctype="x-code">Importación-ContainerImage < paquete AppX ></g>|
| <g id="6fa6a633-578a-4ecd-a168-ce0308142c54" ctype="x-code">docker guardar</g>| <g id="c306911c-0b5d-4690-801c-dddd5c3a4402" ctype="x-code">ContainerImage de exportación</g>|
| <g id="832ebe0b-8809-4a17-9c4a-5698d0c1c440" ctype="x-code">inicio de docker</g>| <g id="5e1c094e-81cc-4ebb-b706-a5d298b74ca7" ctype="x-code">Contenedor de inicio</g>|
| <g id="10bab149-2659-4f98-babd-5bff8de0f74a" ctype="x-code">Detener docker</g>| <g id="a07655c0-2f24-464b-9120-19baffb0220b" ctype="x-code">Contenedor de detención</g>|
Los cmdlets de PowerShell no son una paridad perfecto exacta y hay un número razonable de comandos que no estamos proporcionando reemplazos de PowerShell para * (en particular <g id="5043c21f-0b58-47c6-8612-38e9d9ecd56d" ctype="x-code">compilación docker</g> y <g id="c20d9d8d-d472-415b-b50e-2884ba20d7b2" ctype="x-code">docker cp</g>).
Pero ¿qué puede llamarle la atención es que no hay ningún sustituto de una línea única de <g id="453bcf7e-9eec-4d18-a511-8b64b7e47a08" ctype="x-code">docker ejecutar</g>.

\ * Sujeta a cambios.

###Pero necesito docker ejecutar! ¿Qué está ocurriendo?

Estamos haciendo un par de cosas aquí para proporcionar un modelo de interacción ligeramente más familiar para los usuarios que conocen bien PowerShell ya.
Por supuesto, si está acostumbrado a la manera en que opera docker, se trata de un poco de un cambio mental.

1.  El ciclo de vida de un contenedor en el modelo de PowerShell es ligeramente diferente.
   En el módulo de PowerShell de contenedores, exponemos las operaciones más granulares de <g id="a2554f1d-5240-4b29-8d8c-f09074e8a53b" ctype="x-code">nuevo contenedor</g> (que crea un nuevo contenedor detenido) y <g id="b970640a-b138-4665-8020-d159e9f00c74" ctype="x-code">Inicio contenedor</g>.
   
   Entre crear e iniciar el contenedor, también puede configurar la configuración del contenedor; para TP3, la otra configuración que estamos planeando exponer es la capacidad para establecer la conexión de red para el contenedor.
   mediante el (Agregar/quitar/conectar/desconectar/Get/Set)-ContainerNetworkAdapter cmdlets.
   
2.  Actualmente no se puede pasar un comando para ejecutarlo dentro del contenedor en el inicio. Sin embargo, puede obtener una sesión de PowerShell interactiva en un contenedor mediante ejecución <g id="cc41f26f-60bd-4948-8145-6b921164f42d" ctype="x-code">Enter-PSSession - valor de ContainerId < identificador de un contenedor de ejecución ></g>, y se puede ejecutar un comando dentro de un contenedor de ejecución mediante <g id="8b08e1e4-a5bf-400b-9c05-d3920a95542d" ctype="x-code">Invoke-Command - valor de ContainerId < Id. de contenedor > - ScriptBlock {código para que se ejecute dentro del contenedor}</g> o <g id="65f32128-73ee-4b76-8c3f-d8cf90d3eac6" ctype="x-code">Invoke-Command - valor de ContainerId < Id. de contenedor > FilePath: < ruta de acceso al script ></g>.  
Dos de estos comandos permiten opcional <g id="c2ebf343-b4c2-44c4-b589-267198e77937" ctype="x-code">- RunAsAdministrator</g> indicador para las acciones de alta privilige.


##Advertencias y problemas conocidos

1.  En este momento, los cmdlets de contenedores no tienen conocimiento sobre los contenedores o imágenes creadas a través de Docker y Docker no sabe nada acerca de los contenedores y las imágenes creadas mediante el PowerShell.
   Si se creó en Docker, administrar con Docker; Si se ha creado a través de PowerShell, puede administrar a través de PowerShell.
   
2.  Tenemos bastantes trabajo que nos gustaría hacer para mejorar la experiencia del usuario final: mensajes de error mejorados, mejores informes de progreso, cadenas de evento no válido y así sucesivamente.
   Si por accidente para que se ejecute en una situación donde desee que recibían más o mejores info, no dude en enviar sus sugerencias a los foros.

##Un rápido runthrough

Este es un recorrido a través de algunos flujos de trabajo comunes.

Se supone que ha instalado una imagen de contenedor de sistema operativo llamada "ServerDatacenterCore" y crea un conmutador virtual denominado "Conmutador Virtual" (con New-VMSwitch).

``` PowerShell
### 1. Enumerating images
# At this point, you can enumerate the images on the system:
Get-ContainerImage

# Get-ContainerImage also accepts filters.
# For example, this will return all container images whose Name starts with S (case-insensitive):
Get-ContainerImage -Name S*

# You can save the results of this to a variable.
# (If you're not familiar with PowerShell, the "$" denotes a variable.)
$baseImage = Get-ContainerImage -Name ServerDatacenterCore
$baseImage

### 2. Creating and enumerating containers
# Now, we can create a new container using this image:
New-Container -Name "MyContainer" -ContainerImage $baseImage -SwitchName "Virtual Switch"

# Now we can enumerate all containers.
Get-Container

# Similarly, we can save this container to a variable:
$container1 = Get-Container -Name "MyContainer"

### 3. Starting containers, interacting with running containers, and stopping containers
# Now let's go ahead and start the container.
Start-Container -Name "MyContainer"

# (We could've also started this container using "Start-Container -Container $container1".)

# With the container now running, let's go ahead and enter an interactive PowerShell session:
Enter-PSSession -ContainerId $container1.Id

# This should eventually bring up a PowerShell prompt from inside the container.
# You can try all the things that you did in the interactive cmd prompt given by "docker run -it".
# For now, just to prove we've been here, we can create a new file:
cd \
mkdir Test
cd Test
echo "hello world" > hello.txt
exit

# Now we should be back in the outside world. Even though we've exited the PowerShell session,
# the container itself is still running, as you can see by printing out the container again:
$container1

# Before we can commit this container to a new image, we need to stop the container.
# Let's do that now.
Stop-Container -Container $container1

### 4. Creating a new container image
# And now let's commit it to a new image.
$image1 = New-ContainerImage -Container $container1 -Publisher Test -Name Image1 -Version 1.0

# Enumerate all the images again, for sanity's sake:
Get-ContainerImage

# Rinse and repeat! Make another container based on the new image.
$container2 = New-Container -Name "MySecondContainer" -ContainerImage $image1 -SwitchName "Virtual Switch"

# (If you like, you can start the second container and verify that the new file
# "\Test\hello.txt" is there as expected.)

### 5. Removing a container
# The first container we created is now stopped. Let's get rid of it:
Remove-Container -Container $container1

# And confirm that it's gone:
Get-Container

### 6. Exporting, removing, and importing images
# For images that aren't the base OS image, we can export them into an .appx package file.
Export-ContainerImage -Image $image1 -Path "C:\exports"
# This should create a .appx file in the C:\exports folder.
# If you've given your image the same publisher, name, and version we used earlier,
# you'd expect the resulting .appx to be named "CN=Test_Image1_1.0.0.0.appx".

# Before we can try importing the image again, we need to remove the image.
# (If you have any running containers that depend on this image, you'll want to stop them first.)
Remove-ContainerImage -Image $image1

# Now let's import the image again:
Import-ContainerImage -Path C:\exports\CN=Test_Image1_1.0.0.0.appx

# We'd previously created a container dependent on this image. You should be able to start it:
Start-Container -Container $container2 
```

###Generar su propio ejemplo

Puede ver todos los contenedores cmdlets usados <g id="cdf42705-18f6-4fec-93b4-e26a6935560c" ctype="x-code">Get-Command - módulo contenedores</g>.
Existen varios otros cmdlets que no se describen aquí, que dejaremos que conozca por su cuenta.
<g id="4976e835-ef7b-4e57-85ff-2143b8321d45" ctype="x-strong">Nota</g> esto no devolverá el <g id="9d570ddd-76a4-43a8-927f-70d5ffc17390" ctype="x-code">Enter-PSSession</g> y <g id="16a5c7f3-b8d5-46c2-af7c-55072a5e5edc" ctype="x-code">Invoke-Command</g> cmdlets, que forman parte del núcleo de PowerShell.

También puede obtener ayuda sobre el uso de cualquier cmdlet <g id="290dbdf2-8e8b-46d2-83ef-4e65ee21556a" ctype="x-code">Get-Help [nombre de cmdlet]</g>, o de manera equivalente <g id="a58359e0-ca23-490f-9d40-0a7c646d1614" ctype="x-code">[nombre de cmdlet]-?</g>.
Hoy en día, el resultado de la Ayuda se genera automáticamente y sólo explica la sintaxis de comandos; iremos añadiendo más documentación conforme nos acercamos a finalizar el diseño del cmdlet.

Una forma mejor para descubrir la sintaxis es PowerShell ISE, puede no ha examinado antes si no has utilizado PowerShell mucho.
Si está ejecutando en un SKU que lo permita, intente iniciar el ISE, abra el panel de comandos y elija el módulo "Contenedores", que mostrará una representación gráfica de los cmdlets y sus conjuntos de parámetros.

PS: Sólo para probar que puede llevar a cabo, aquí es una función de PowerShell que se compone de algunos de los cmdlets que vimos anteriormente en un sustituto <g id="803e675f-665b-44fd-8654-6ee59381f7b3" ctype="x-code">docker ejecutar</g>.
(Para ser más precisos, esto es una prueba de concepto, no en desarrollo activo).

``` PowerShell
function Run-Container ([string]$ContainerImageName, [string]$Name="fancy_name", [switch]$Remove, [switch]$Interactive, [scriptblock]$Command) {
    $image = Get-ContainerImage -Name $ContainerImageName
    $container = New-Container -Name $Name -ContainerImage $image
    Start-Container $container

    if ($Interactive) {
         Start-Process powershell ("-NoExit", "-c", "Enter-PSSession -ContainerId $($container.Id)") -Wait
    } else {
        Invoke-Command -ContainerId $container.Id -ScriptBlock $Command
    }

    Stop-Container $container

    if ($Remove) {
        Remove-Container $container -Force
    }
} 
```

##Docker

Contenedores de servidores de Windows se pueden administrar con comandos de Docker.
Aunque la experiencia en Windows contenedores deben ser comparable a sus homólogos de Linux y tienen la misma administración a través de Docker, hay algunos comandos Docker que simplemente no tienen sentido con un contenedor de Windows.
Otros simplemente no han sido probadas (estamos obteniendo existe).

En un esfuerzo para no duplicar la documentación de API disponible en Docker, éste es un vínculo a la API de administración.
Los tutoriales son fantásticas.

Nos estamos realizando el seguimiento de las cosas que y no funcionan en las API Docker en nuestro documento de trabajo en curso.




