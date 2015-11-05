MS. ContentId: 95FE9554-3968-4EED-B65D-E03F06A7598D
título: paso 3: crear un conmutador virtual

#Paso 3: Crear un conmutador virtual

Un conmutador virtual le permite crear una conexión de red para la máquina virtual.
Se utilizan al igual que el adaptador de red (NIC) en el equipo físico.

En este ejemplo, vamos a crear un conmutador externo.
El conmutador externo le permitirá la máquina virtual para tener acceso al host del adaptador de red del equipo.
Si su equipo host está conectado a internet, también será la máquina virtual.

También estableceremos el conmutador para permitir que el host comparta este adaptador de red.
Esto hace que sea así tanto las máquinas virtuales y el host puede utilizar la misma red.



1. En el Administrador de Hyper-V, haga clic en **Administrador de conmutadores virtuales**.
   
   ![](media/virtual_switch_manager1.png)
   
2. Seleccione **nuevo conmutador de red virtual**.
   
   ![](media/new_switch.png)
   
3. Seleccione **externo** y **crear conmutador Virtual**.
   
   ![](media/new_switch_createbutton.png)
   
4. Bajo **nombre**, tipo **externo**.
5. Bajo **red externa**, seleccione el adaptador de red correctos (probablemente habrá sólo sea una opción).
6. Seleccione **Permitir que el sistema operativo de administración comparta este adaptador de red** y haga clic en **Aceptar**.
   
   ![](media/share_nic.png)
   
7. Obtendrá un mensaje que le advierte de que la red podría desconectar mientras se crea el conmutador virtual.
   Haga clic en **Sí**.
   La red no estará disponible durante un breve período.
   
   ![](media/network_warning.png)

##Paso siguiente:

[Paso 4: Crear una máquina virtual de Windows desde un archivo .iso](walkthrough_create_vm.md)




