MS. ContentId: 93EDAAF5-E4FC-4F3F-AB55-669D2BF47D78
título: Introducción a Hyper-V en Windows 10


#Introducción a Hyper-V en Windows 10 pruebas

Agregar esta frase para probar el proceso de HO HB.
Tanto si es un desarrollador de software, un ITPro o un aficionado a la tecnología, muchos de ustedes que deba ejecutar varios sistemas operativos, ocasionalmente en muchos equipos diferentes.
No todos nosotros tenemos acceso a una serie completa de laboratorios para albergar todas estas máquinas y, por lo que la virtualización puede representar un ahorro de espacio y tiempo.

##Usos de virtualización

La virtualización permite que cualquier persona mantener fácilmente varios entornos de prueba formado por muchos sistemas operativos, las configuraciones de software y las configuraciones de hardware.
Hyper-V proporciona virtualización en Windows como un mecanismo sencillo para cambiar rápidamente entre los entornos sin incurrir en costos de hardware adicional.

Hyper-V se puede utilizar en muchos sentidos, por ejemplo:
- Un entorno de prueba que consta de varias máquinas virtuales puede crearse en un único equipo de escritorio o portátil.
   Una vez completadas las pruebas, estas máquinas virtuales se puede exportar y, a continuación, se importan en cualquier otro sistema de Hyper-V.
   
- Los programadores pueden utilizar Hyper-V en su equipo para probar el software en varios sistemas operativos.
   Por ejemplo, si tiene una aplicación que debe probarse en un sistema operativo Linux, Windows 7 y Windows 8, se pueden crear varias máquinas virtuales en el sistema de desarrollo, uno que contenga cada uno de estos sistemas operativos.
   
- Puede utilizar Hyper-V para máquinas virtuales desde cualquier implementación de Hyper-V de solución de problemas.
   Puede exportar una máquina virtual del entorno de producción, abra en el escritorio que ejecuta Hyper-V, realizar la solución de problemas necesaria y, a continuación, exportarlo en el entorno de producción.
   
- Con una red virtual, puede crear un entorno con varios equipos de prueba y desarrollo y de demostración que es seguro afecte a la red de producción.
   
- Entusiastas sirven para experimentar con otros sistemas operativos.
   Hyper-V hace muy fácil aparezca y destruir sistemas operativos diferentes.
   
- Puede usar Hyper-V en un equipo portátil para demostrar las versiones anteriores de Windows o sistemas operativos que no sean Windows.


##Requisitos del sistema

Hyper-V requiere un sistema de 64 bits que tiene la traducción de direcciones de segundo nivel (SLAT). SLAT es una característica presente en la generación actual de procesadores de 64 bits con Intel y AMD. También necesitará una versión de 64 bits de Windows 8 o posterior y al menos 4GB de RAM. Hyper-V es compatible con la creación de sistemas operativos de 32 bits y 64 bits en las máquinas virtuales.

Memoria dinámica de Hyper-V permite la memoria que necesita la máquina virtual para asignar y desasignar dinámicamente (especifique un mínimo y máximo) y compartir la memoria no utilizada entre máquinas virtuales.
Puede ejecutar máquinas virtuales de 3 o 4 en un equipo que tiene 4GB de RAM, pero necesitará más memoria RAM para 5 o más máquinas virtuales.
En el otro extremo del espectro, también puede crear máquinas virtuales grandes con 32 procesadores y 512GB de RAM, según el hardware físico.

##Sistemas operativos que puede ejecutar en una máquina virtual

El término "Invitado" hace referencia a una máquina virtual y "host" se refiere al equipo que ejecuta la máquina virtual.
Hyper-V en Windows admite muchos diferentes sistemas operativos invitados incluidos diversas versiones de Linux, FreeBSD y Windows.
Para obtener información sobre qué sistemas operativos son compatibles como invitados en Hyper-V en Windows, vea [admite sistemas operativos Windows invitados](supported_guest_os.md) y [Linux y FreeBSD máquinas virtuales Hyper-V](https://technet.microsoft.com/library/dn531030.aspx).


##Diferencias entre Hyper-V en Windows e Hyper-V en Windows Server

Hay algunas características que funcionan de manera diferente en Hyper-V en Windows que cuando se ejecuta en Windows Server Hyper-V.
Estos son los siguientes:

- El modelo de administración de memoria es diferente para Hyper-V en Windows.
   En un servidor, la memoria de Hyper-V se administra con la suposición de que solo las máquinas virtuales se ejecutan en el servidor.
   En Hyper-V en Windows, la memoria se administra con la descripción en la que mayoría de los equipos cliente está ejecutando software además de máquinas virtuales en ejecución.
   Por ejemplo, es posible ejecutar un desarrollador Visual Studio, así como varias máquinas virtuales en el mismo equipo.
   
- SR-IOV en un invitado de 64 bits funciona con normalidad, pero no es de 32 bits y no se admiten.


###Características no disponibles en Windows Hyper-V de Windows Server

Existen algunas características incluidas en Hyper-V en el servidor que no están incluidos en Hyper-V en Windows.
Estos son los siguientes:

- La capacidad de FX remoto virtualizar GPU
   
- Migración en vivo de máquinas virtuales desde un host a otro
   
- Réplica de Hyper-V
   
- Canal de fibra virtual
   
- Redes de SR-IOV
   
- Compartir. VHDX


> **Advertencia**: máquinas virtuales que ejecutan Hyper-v no controlan automáticamente pasar de una red cableada para una conexión inalámbrica.
> Debe cambiar la configuración del adaptador de red de máquinas virtuales manualmente.

##Limitaciones

Usar la virtualización tiene limitaciones.
Las características o las aplicaciones que dependen de hardware no funcionará bien en una máquina virtual.
Por ejemplo, juegos o aplicaciones que requieren un procesamiento con GPU (sin entregar el software de reserva) podrían no funcionar bien.
Además, las aplicaciones basadas en los temporizadores de 10ms sub, como aplicaciones de alta precisión sensible a la latencia, como música mezcla de aplicaciones, etc. podría tener problemas al ejecutar en una máquina virtual.
El SO raíz también se ejecuta por encima de la capa de virtualización Hyper-V, pero es especial en que tiene acceso directo a todo el hardware.
Se trata de por qué las aplicaciones con requisitos de hardware especial continuarán funcionando sin obstáculos en la raíz del sistema operativo, pero las aplicaciones sensibles a la latencia y de gran precisión todavía podrían tener problemas al ejecutar en el SO raíz.

Como recordatorio, deberá tener una licencia válida para los sistemas operativos en que uso en las máquinas virtuales.

##Paso siguiente:

[Tutorial Hyper-V en Windows 10](..\quick_start\walkthrough.md)

Desproteger [What's New](whats_new.md) en Hyper-V en Windows 10.





