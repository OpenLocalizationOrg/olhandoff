MS. ContentId: F0D47E70-0BA1-4A06-B2F3-0232C496709D
título: preguntas más frecuentes

#Preguntas más frecuentes

Última actualización: 1 de mayo de 2015

##¿Qué es un contenedor de Windows Server?

Contenedores de Windows Server son un método de virtualización del sistema operativo ligero utilizado para separar las aplicaciones o servicios de otros servicios que se ejecutan en el mismo host del contenedor.
Para habilitar esta opción, cada contenedor tiene su propia vista del sistema operativo, procesos, sistema de archivos, registro y direcciones IP.

##¿Cuál es la diferencia entre los contenedores de Windows Server y Linux?

Contenedores de Windows Server y Linux son similares, ambas implementan tecnologías similares dentro de su sistema operativo básico y kernel.
La diferencia proviene de la plataforma y las cargas de trabajo que se ejecutan dentro de los contenedores.
Cuando un cliente utiliza contenedores de Windows Server, puede integrar con las tecnologías existentes de Windows como. NET, ASP.NET, PowerShell y mucho más.

##¿Qué es un contenedor de Hyper-V?

Puede pensar en un contenedor de Hyper-V como un contenedor de servidores de Windows ejecutando dentro de una partición de Hyper-V.

Contenedores de Hyper-V ofrecen una opción de implementación adicionales entre el contenedor del servidor Windows muy eficaz, alta densidad y máquina virtuales aislada Hyper-V virtualizada de hardware.
Para entornos donde las aplicaciones de diferentes límites en el mismo host de confianza, puede requerirse aislamiento adicionales.
Contenedores de Hyper-V proporcionará más alto de aislamiento mediante una virtualización optimizada y el sistema operativo Windows Server que separa los contenedores entre sí y desde el sistema operativo host.
Ambas opciones de implementación de contenedor usan las misma administración API, herramientas e image formatos, durante la implementación, los clientes simplemente pueden elegir el modo de implementación que mejor cumpla sus requisitos.


##¿Cuándo estará disponible para su uso contenedores de Hyper-V?

Esperamos que ofrecen una vista previa de los contenedores de Hyper-V de este año natural.


##¿Contenedores de Hyper-V también estará disponible para el ecosistema de Docker?

Sí: contenedores de Hyper-V proporcionará el mismo nivel de integración y administración con Docker como contenedores de Windows Server.
El objetivo es tener una experiencia multiplataforma, coherente y abierta.
La plataforma Docker simplifica enormemente y mejorar la experiencia de trabajo a través de las opciones del contenedor.
Una aplicación desarrollada con contenedores de Windows Server puede implementarse como un contenedor de Hyper-V sin cambios.

##¿Por qué es necesario elegir entre la administración Docker y PowerShell para el contenedor de Windows Server

**Esto no es el comportamiento deseado ni nuestro plan a largo plazo.**  Herramientas de administración de contenedor de PowerShell y herramientas de administración de contenedor Docker funcionará en paralelo en el futuro.

Dicho esto, puede resultar difícil usando varias interfaces de administración para administrar el mismo contenedor.

Por ejemplo, tome la creación de un contenedor con PowerShell y el nombre de la imagen con caracteres en mayúscula.
Docker no es compatible con límites, no de PowerShell.
Aunque ese ejemplo concreto es muy fácil, qué obtiene mucho más difícil entregar los cambios de estado (condiciones de carrera y expectativas diferentes), el conjunto de características diferencias o versiones...

A corto plazo decidimos que interfaces de administración (en este caso Docker y PowerShell) sólo contenedores vea crearon: crear un contenedor con Docker y PowerShell no lo ve, créelo con PowerShell y Docker no lo ve.


##Como desarrollador, ¿tengo que volver a escribir la aplicación para cada tipo de contenedor?

No, las imágenes de Windows contenedor son comunes a los contenedores de Windows Server y Hyper-V.
La elección del tipo de contenedor se realiza cuando se inicia el contenedor.
Desde la perspectiva del desarrollador, contenedores de Windows Server y Hyper-V son dos versiones de la misma entidad.
Ofrecen la misma experiencia de desarrollo, programación y administración, está abierta y extensible e incluirá el mismo nivel de integración y compatibilidad a través de Docker.

Un desarrollador puede crear una imagen de contenedor con un contenedor de Windows Server e implementarlo como un contenedor de Hyper-V o viceversa, sin ningún cambio aparte de especificar la marca de tiempo de ejecución adecuados.

Contenedores de Windows Server ofrece mayor densidad y el rendimiento (por ejemplo, número inferior el rendimiento en tiempo de ejecución de tiempo, más rápido en comparación con las configuraciones anidadas) para cuando la velocidad es clave.
Contenedores de Hyper-V ofrecen mayor aislamiento, asegurarse de que el código que se ejecuta en un contenedor no se puede poner en peligro o afectar al sistema operativo host u otros contenedores que se ejecutan en el mismo host.
Esto es útil para escenarios de varios inquilinos (con requisitos de hospedaje de código no seguro) incluidas las aplicaciones de SaaS y el proceso de hospedaje.


##¿Son un complemento de contenedores de Hyper-V o Windows Server, o bien se que integra dentro de Windows Server?

Las funciones de contenedor se integrará en Windows Server 2016.
Permanezca atento para obtener más información acerca de la disponibilidad general.


##¿Cuáles son los requisitos previos para contenedores de Windows Server y Hyper-V?

Ventana Server contenedores y los contenedores de Hyper-V requieren Windows Server 2016.
Estas tecnologías no funcionará con versiones anteriores de Windows.

##¿Son contenedores de servidor Nano basado compatibles?

Para la versión TP3, no no son.
Contenedores de Server Core basándose solo se admiten actualmente.

##¿Puedo ejecutar Windows Server contenedores en ESXi u otro hipervisor de Hyper-V no?

Sí, ejecutar el contenedor de Windows Server en cualquier instalación TP3 Server Core.
Siga las instrucciones para [Habilitar los contenedores en lugar de características](../quick_start/inplace_setup.md).


##¿Microsoft participa en la iniciativa de contenedor abierto (OCI)?

Para garantizar que el formato de empaquetado permanece universal, Docker recientemente organiza la iniciativa de contenedor de abrir (OCI), para garantizar el empaquetado de contenedor sigue siendo un formato abierto y guiada foundation con Microsoft como uno de los miembros fundadores.

##¿Es Microsoft realmente asocia Docker?

Sí.
Nuestra asociación con Docker permite a los desarrolladores crear, administrar e implementar Windows Server y Linux contenedores con el mismo conjunto de herramienta Docker.
Desarrolladores orientadas a Windows Server ya no tendrá que elegir entre el uso de las tecnologías de la amplia gama de Windows Server y crear aplicaciones de contenido.

Docker es dos cosas, el grupo de código abierto de proyectos y Docker la empresa.
Consideramos que esta asociación para incluir ambas.
Docker es correcta, en parte, debido al vibrante ecosistema que haya elaborado en torno a la tecnología de contenedor Docker.
Microsoft está contribuyendo al proyecto Docker, habilitando la compatibilidad para los contenedores de Windows Server y Hyper-V.

Para obtener más información, consulte el [compatibilidad con contenedores de nuevo Windows Server y Azure para Docker](http://azure.microsoft.com/blog/2014/10/15/new-windows-server-containers-and-azure-support-for-docker/?WT.mc_id=Blog_ServerCloud_Announce_TTD) entrada de blog.

-------------------

[Volver a la página principal de contenedor](../containers_welcome.md)



