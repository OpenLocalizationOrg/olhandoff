MS. ContentId: C2593EA1-B182-4C71-8504-49691F619158
título: paso 1: asegúrese de que su equipo es compatible

##Compatibilidad de sistema operativo

El rol de Hyper-V sólo puede instalarse en las ediciones Pro, Enterprise y educación de 10 de Windows.
Si está usando la edición principal, Mobile o Mobile Enterprise del 10 de Windows, no se puede usar el rol Hyper-V.
10 de Windows Home edition se puede actualizar a Windows Professional de 10.
Hacer así que abra la configuración > seguridad y actualización > activación.
Aquí puede visitar la tienda y comprar una actualización.

##Compatibilidad de hardware

Aunque este documento no proporciona una lista completa de hardware compatible de Hyper-V son necesarios los siguientes elementos:

- Procesador de 64 bits con traducción de direcciones de nivel de segundo (SLAT).
- Extensión del modo de Monitor de máquina virtual debe estar presente.
- Mínimo de 4 GB de memoria, sin embargo, dado que las máquinas virtuales se comparten esta memoria con el host de Hyper-V, desea proporcionar memoria suficiente para controlar la carga de trabajo esperada virtual.

Los siguientes elementos debe estar habilitado en los BIOS del sistema:
- Virtualización
- Prevención de ejecución de datos

##Comprobar la compatibilidad de Hardware

Para comprobar la compatibilidad, abra PowerShell o un símbolo del sistema (cmd.exe) y un tipo <g id="1ddb5bbd-a4c8-42ee-a8d3-b7577a93182b" ctype="x-code">systeminfo.exe</g>.
Esto devolverá información sobre la compatibilidad de Hyper-V.
Si todos los elementos enumerados tienen un valor de 'Sí' su sistema puede ejecutar el rol Hyper-V.
Si cualquier elemento devuelve 'No', compruebe los requisitos enumerados en el documento y realizar ajustes siempre que sea posible.

<g id="ffc6182b-963d-4f20-a919-38ecd0cace8f" ctype="x-linkText"></g>

##Host de Hyper-V existente

Si ejecuta systeminfo.exe en un host de Hyper-V existente, la sección requisitos de Hyper-V leerá:

''' Requisitos de Hyper-V: se ha detectado un hipervisor.
Características necesarias para Hyper-V no se mostrarán.'' '

##Paso siguiente:

<g id="a0313845-0e4f-4768-8cee-635e47aa23fdCapsExtId1" ctype="x-linkText">Paso 2: Instalar Hyper-V</g><g id="a0313845-0e4f-4768-8cee-635e47aa23fdCapsExtId2" ctype="x-title"></g>



