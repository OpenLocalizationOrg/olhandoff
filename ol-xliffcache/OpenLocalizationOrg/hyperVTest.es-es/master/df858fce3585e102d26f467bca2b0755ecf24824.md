MS. ContentId: 3C63F9A8-30E4-40F4-BC7B-A001C1E90779
título: paso 4: crear una máquina virtual de Windows desde un archivo .iso

#Paso 4: Crear una máquina virtual de Windows desde un archivo .iso

Para este paso si ya tiene un archivo .iso de un sistema operativo de 64 bits compatible, puede usarlo.
Si no es así, puede descargar el ISO para <g id="62e3d36d-84b3-40c6-ab9f-811be48650c5CapsExtId1" ctype="x-linkText">Windows 8.1 Enterprise</g><g id="62e3d36d-84b3-40c6-ab9f-811be48650c5CapsExtId2" ctype="x-title"></g> y elija la edición de 64 bits.

1. En el Administrador de Hyper-V, haga clic en el <g id="c4b7bc56-3147-4c0b-af48-cdab893b504b" ctype="x-strong">acción</g> menú > <g id="8997b1e0-c230-40cc-a0a9-d1c14682f75f" ctype="x-strong">nuevo</g> > <g id="d68fe7ab-b0b8-4112-8af2-ac2f472c6c26" ctype="x-strong">Máquina Virtual</g>.
2. En el Asistente para la máquina virtual, realice las siguientes opciones:
   
   <table>
   <tr><th>Página</th><th>Entrada</th></tr>
   <tr><td>Nombre:</td><td>Escriba en <b>Máquina virtual del tutorial de Windows</b></td></tr>
   <tr><td>Generación:</td><td><b>Generación 2</b></td></tr>
   <tr><td>Memoria de inicio:</td><td><b>1024</b> y deje activada la memoria dinámica</td></tr>
   <tr><td>Configurar la red:</td><td><b>Externo</b> (es decir, el conmutador virtual que creó en el paso 3)</td></tr>
   <tr><td>Conectar disco duro virtual:</td><td><b>Crear un disco duro virtual</b> (mantenga los demás valores predeterminados) </td></tr>
   <tr><td>Opciones de instalación:</td><td><b>Instalar un sistema operativo desde un CD, DVD-ROM arranque</b>. Bajo <b>Media</b>, seleccione <b>Archivo de imagen (iso)</b> y, a continuación, haga clic en <b>Examinar</b> Para seleccionar el archivo .iso.</td></tr>
   </table>
   
3. Cuando todo parezca correcto, haga clic en <g id="be021aa4-7453-4043-9737-048308636eb6" ctype="x-strong">Finalizar</g>.

> <g id="62c6347a-a15f-4328-848e-1b2de5a88f29" ctype="x-strong">Nota:</g> si sólo tiene la versión de 32 bits de Windows, debe elegir la generación 1 en el <g id="b92dbeae-0a4f-418a-8e2b-165c3a9136fc" ctype="x-strong">generación</g> sección del asistente.
> Máquinas virtuales de generación 2 solo admiten los sistemas operativos de 64 bits.

##Paso siguiente:

<g id="0146a846-541a-44fc-9d57-dffead464145CapsExtId1" ctype="x-linkText">Paso 5: Conectarse a la máquina virtual y finalizar la instalación</g><g id="0146a846-541a-44fc-9d57-dffead464145CapsExtId2" ctype="x-title"></g>





