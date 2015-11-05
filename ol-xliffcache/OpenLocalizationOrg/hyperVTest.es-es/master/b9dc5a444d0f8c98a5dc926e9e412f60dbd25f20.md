Bienvenido al abrir documentos de diseño de publicación
=======================================================

Esto es el repositorio Abrir publicación de documentos de diseño con la tecnología de publicación abierta de MSDN.

Inicio rápido
-------------

Comenzar a contribuir a documentos abiertos publicación siguiendo estos pasos:

1. Clonar el repositorio:
   ```
   git clone https://github.com/openpublish/docs.git
   ```

2. Edite los archivos de descuento con su editor favorito de descuento.
3. Confirme e inserte los cambios:
   ```
   git add -u
   git commit -m "update doc"
   git push
   ```

4. Espere un momento y los cambios se publicará automáticamente en:
   
   -   Docset 1: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/community
   -   Docset 2: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/hyperv<g id="7607f36f-a92e-4df1-bf16-5b5e58bddfd5" ctype="x-em">en</g>windows
   -   Docset 3: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/windowscontainers


> Si no tiene el permiso para insertar en este repositorio, bifurcar a su propia cuenta y usar la solicitud de extracción para enviar los cambios de vuelta.

Validación y vista previa
-------------------------

Antes de enviar los cambios a remoto, puede crear y obtener una vista previa de su documento local para detectar problemas al principio:

1. Para validar los cambios, sólo tiene que ejecutar <g id="fa183a09-8254-43a4-bc8a-420f60fc2238" ctype="x-code">msbuild</g> bajo la raíz del repositorio.
2. Para obtener una vista previa de los cambios:
   1. Ejecutar <g id="f9fb34b8-ea6d-4489-8027-38128c9f1580" ctype="x-code">/t:serve de msbuild</g> bajo la raíz del repositorio.
   2. Abra <g id="584d2773-6560-47b0-a04e-6731e6b247a8" ctype="x-code">http://localhost: 8000</g> en el explorador.





