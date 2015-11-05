MS. ContentId: 526e4f1a-2936-4c61-b3be-d41b4cf9d10f
título: acerca de los contenedores de servidores Windows

#Contenedores de Windows Server

Probar las actualizaciones para la demostración de la mañana!
Las aplicaciones de combustible innovación en la nube y era móvil.
Contenedores y el ecosistema que está desarrollando en torno a ellas, en el que se va a conceder a los desarrolladores de software para crear la próxima generación de experiencias de aplicaciones.

Ver una breve introducción: [contenedores basados en Windows: desarrollo de aplicaciones modernas con control de nivel empresarial](https://youtu.be/Ryx3o0rD5lY).

##¿Cuáles son los contenedores?

Son un, recursos controlados y portátil entorno operativo aislado.

Básicamente, un contenedor es un lugar aislado donde una aplicación puede ejecutarse sin afectar al resto del sistema y sin el sistema de la aplicación.
Los contenedores son la evolución de la virtualización.

Si estaba dentro de un contenedor, tendría el aspecto muy similar como estaba dentro de una máquina virtual o de un equipo físico recién instalado.
Y, a [Docker](https://www.docker.com/), un contenedor de servidores de Windows se pueden administrar en la misma forma que cualquier otro contenedor.

##Aspectos básicos de contenedor

Al comenzar a trabajar con contenedores observará muchas similitudes entre un contenedor y una máquina virtual.
Un contenedor ejecuta un sistema operativo, tiene un sistema de archivos y puede tener acceso a través de una red como si fuese un sistema físico o virtual.
Dicho esto, la tecnología y los conceptos de los contenedores son muy diferentes de las máquinas virtuales.
[Esta entrada de blog](http://azure.microsoft.com/blog/2015/08/17/containers-docker-windows-and-trends/) por Mark Russinovich explica también contenedores.

Los siguientes conceptos claves será útiles cuando empiece a crear y trabajar con contenedores de Windows Server.

**Contenedor Host:** sistema de equipo físico o Virtual configurada con la característica de contenedor de Windows Server.
El host del contenedor ejecutará uno o varios contenedores de servidor de Windows.

**Contenedor de imagen:** como se realizan modificaciones en un sistema de archivos contenedores o del registro, como con instalación de software se capturan en el recinto de seguridad.
En muchos casos, puede que desee capturar este estado tal que se pueden crear nuevos contenedores que heredan estos cambios.
Eso es lo que es de una imagen, una vez que ha detenido el contenedor puede descartar en ese espacio aislado o puede convertirlo en una nueva imagen de contenedor.
Por ejemplo, imaginemos que ha implementado un contenedor de la imagen de sistema operativo de Windows Server Core.
A continuación, instalar MySQL en este contenedor.
Crear una nueva imagen de este contenedor actuará como una versión que se pueden implementar del contenedor.
Esta imagen sólo contendría los cambios realizados (MySQL), sin embargo funcionaría como una capa encima de la imagen de sistema operativo del contenedor.

**Recinto de seguridad:** una vez que se ha iniciado un contenedor, todas las acciones de escritura como modificaciones del sistema de archivos, las modificaciones del registro o las instalaciones de software se capturan en este nivel de 'recinto'.

**Contenedor de imagen del sistema operativo:** se implementan contenedores de imágenes.
La imagen de sistema operativo del contenedor es la primera capa de potencialmente muchos niveles de la imagen que componen un contenedor.
Esta imagen proporciona el entorno de sistema operativo.
Una imagen de sistema operativo del contenedor es inmutable, no se puede modificar.

**Repositorio de contenedor:** cada vez que se crea la imagen de contenedor en una imagen de contenedor y sus dependencias se almacenan en un repositorio local.
Estas imágenes se pueden reutilizar muchas veces en el host del contenedor.
Las imágenes de contenedor también pueden almacenarse en un repositorio público o privado, como DockerHub para que se pueden utilizar en muchos host contenedor diferente.

**Tecnología de administración de contenedor:** Windows Server contenedores pueden administrarse mediante PowerShell y Docker.
Con cualquiera de estas herramientas se pueden crear nuevos contenedores, imágenes de contenedor como así como administrar el ciclo de vida del contenedor.

<center>![](media/containerfund.png)</center>

##Contenedores para desarrolladores

Desde el escritorio de un desarrollador a una máquina de pruebas para un conjunto de equipos de producción, se puede crear imagen un Docker que implementa en cualquier entorno de forma idéntica en segundos.
Este artículo ha creado un gran y crecimiento ecosistema de aplicaciones empaquetadas en contenedores de Docker, con DockerHub, el registro de aplicación en contenedor público que mantiene Docker, actualmente publicar más de 180.000 aplicaciones en el repositorio de comunidad pública.

Cuando containerize una aplicación, sólo la aplicación y los componentes necesarios para ejecutar la aplicación se combinan en una "imagen".
En esta imagen, a continuación, se crean los contenedores según sea necesario.
También puede utilizar una imagen como una línea de base para crear otra imagen, hacer que la creación de imágenes aún más rápida.
Varios contenedores pueden compartir la misma imagen, lo que significa contenedores inician muy rápidamente y utilizan menos recursos.
Por ejemplo, puede utilizar contenedores de poner en marcha ligera y componentes de aplicación portátil – o servicios micro – para aplicaciones distribuyen y escalación rápidamente cada servicio por separado.

Puesto que el contenedor tiene todo que lo necesario para ejecutar la aplicación, son muy portátiles y se puede ejecutar en cualquier equipo que ejecute Windows Server 2016.
Puede crear y probar contenedores localmente y luego implementar esa misma imagen de contenedor en la nube privada, nube pública o proveedor de servicios de su empresa.
La agilidad natural de contenedores admite patrones de desarrollo de aplicaciones modernas de gran escala, virtualizados y entornos en la nube.

Contenedores, los desarrolladores pueden crear una aplicación en cualquier lenguaje.
Estas aplicaciones son totalmente portables y pueden ejecutar en cualquier lugar - equipo portátil, escritorio, servidor, nube privada, nube pública o proveedor de servicios: sin realizar ningún cambio en el código.

Contenedores de ayuda a los desarrolladores crear y distribuir las aplicaciones de mayor calidad, más rápido.

##Contenedores para los profesionales de TI

Los profesionales de TI pueden utilizar contenedores para proporcionar entornos estandarizados para su desarrollo, control de calidad y los equipos de producción.
Ya no tienen que preocuparse de instalación complejos y pasos de configuración.
Mediante el uso de contenedores, los administradores de sistemas abstraen ubicación diferencias en las instalaciones de sistema operativo y la infraestructura subyacente.

Contenedores ayudan a los administradores crear una infraestructura que es más fácil de actualizar y mantener.

##Información general en vídeo

<iframe src="https://channel9.msdn.com/Blogs/containers/Containers-101-with-Microsoft-and-Docker/player" width="960" height="540" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##Pruebe Windows Server contenedores

[Introducción a los contenedores de Windows Server en Windows Azure](../quick_start/azure_setup.md)  
[Introducción a Windows Server contenedores localmente](../quick_start/container_setup.md)

-------------------

[Volver a la página principal de contenedor](../containers_welcome.md)




