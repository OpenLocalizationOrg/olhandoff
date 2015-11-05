MS. ContentId: 7561B149-A147-4F71-9840-6AE149B9DED5
título: admite los sistemas operativos Windows invitados


#Invitados de Windows admitidos

En este artículo se enumeran los sistemas operativos de Windows compatibles como invitados en Hyper-V en Windows, también se proporciona información acerca de los servicios de integración.

> 10 de Windows se ejecuta como un sistema operativo invitado en Windows 8.1 y Windows Server 2012 R2 Hyper-V hosts.

##¿Qué significa "compatibilidad"?

La compatibilidad significa que Microsoft ha probado estas combinaciones de host o invitado.
Problemas con estas combinaciones pueden recibir atención de los servicios de soporte técnico.

Microsoft proporciona compatibilidad para sistemas operativos invitados de la siguiente manera:
* Los problemas encuentran en sistemas operativos de Microsoft y en la integración de servicios son compatibles con Microsoft admiten.
* Para los problemas encontrados en otros sistemas operativos que han sido certificados por el proveedor de sistema operativo para que se ejecute en Hyper-V, se proporciona compatibilidad con el proveedor.
* Para los problemas encontrados en otros sistemas operativos, Microsoft envía la salida a la Comunidad de soporte de múltiples proveedores, <g id="e3b7d9a3-c106-4330-9234-2f92a1909f44CapsExtId1" ctype="x-linkText">TSANet</g><g id="e3b7d9a3-c106-4330-9234-2f92a1909f44CapsExtId2" ctype="x-title"></g>.

##¿Cuáles son los servicios de integración y por qué son importantes?

Hyper-V incluye servicios de integración para sistemas operativos invitados admitidos.
Servicios de integración de mejoran la interacción entre el sistema host y la máquina virtual.

Algunos sistemas operativos (incluidas las diferentes versiones de Windows) tiene los servicios de integración integrados, mientras que otros proveedores ofrecen servicios de integración a través de Windows Update.

##Sistemas de operativos de invitado de Windows Server

Para los Hosts de Hyper-V de Windows 10:


| Sistema operativo invitado| Número máximo de procesadores virtuales| Servicios de integración| Notas| |
| -----                                | -----                                     | -----                     | -----     | ----- |
| Vista previa técnica de Windows Server| 64| Integrada| | | |
| Windows Server 2012 R2| 64| Integrada| | | |
| Windows Server 2012| 64| Integrada| | | |
| Windows Server 2008 R2 con Service Pack 1 (SP 1)| 64| Instalar los servicios de integración después de configurar el sistema operativo en la máquina virtual.| Ediciones Datacenter, Enterprise, Standard y Web.| |
| Windows Server 2008 con Service Pack 2 (SP 2)| 4| Instalar los servicios de integración después de configurar el sistema operativo en la máquina virtual.| Ediciones Datacenter, Enterprise, Standard y Web (32 bits y 64 bits).| |
| Windows Home Server 2011| 4| Instalar los servicios de integración después de configurar el sistema operativo en la máquina virtual.| |
| Windows Small Business Server 2011| Edición Essentials - 2, edición Standard - 4| Instalar los servicios de integración después de configurar el sistema operativo en la máquina virtual.| Essentials y Standard editions.| |

##Sistemas operativos invitados a Windows admitidos

Para los Hosts de Hyper-V de Windows 10:

| Sistema operativo invitado| Número máximo de procesadores virtuales| Servicio de integración| Notas| |
| ----- | ----- | ----- | ----- | ----- |
| 10 de Windows| 32| Integrada| | |
| Windows 8.1| 32| Integrada| | |
| Windows 8| 32| Actualice los servicios de integración después de configurar el sistema operativo en la máquina virtual.| | |
| Windows 7 con Service Pack 1 (SP 1)| 4| Actualice los servicios de integración después de configurar el sistema operativo en la máquina virtual.| Ultimate, Enterprise y ediciones Professional (32 bits y 64 bits).| |
| Windows 7| 4| Actualice los servicios de integración después de configurar el sistema operativo en la máquina virtual.| Ultimate, Enterprise y ediciones Professional (32 bits y 64 bits).| |
| Windows Vista con Service Pack 2 (SP2)| 2| Instalar los servicios de integración después de configurar el sistema operativo en la máquina virtual.| Business, Enterprise y Ultimate, incluidas las ediciones N y KN.| |
10 de Windows es un sistema operativo en Windows 8.1 y Windows Server 2012 R2 Hyper-V hosts.

##Linux y BSD gratuito

Para los Hosts de Hyper-V de Windows 10:

| Sistema operativo invitado| |
| -----|------|
| <g id="178a2cc6-fe88-4651-8ab5-88343cb8d87dCapsExtId1" ctype="x-linkText">CentOS y Red Hat Enterprise Linux </g><g id="178a2cc6-fe88-4651-8ab5-88343cb8d87dCapsExtId2" ctype="x-title"></g>| |
| <g id="ff9f2024-f45c-4c6c-b3bc-6155362b01a5CapsExtId1" ctype="x-linkText">Debian máquinas virtuales en Hyper-V</g><g id="ff9f2024-f45c-4c6c-b3bc-6155362b01a5CapsExtId2" ctype="x-title"></g>| |
| <g id="f5600042-8707-4e38-a626-c8bfb122a337CapsExtId1" ctype="x-linkText">SUSE</g><g id="f5600042-8707-4e38-a626-c8bfb122a337CapsExtId2" ctype="x-title"></g>| |
| <g id="5765673b-779b-4dea-b2ba-15519de690a1CapsExtId1" ctype="x-linkText">Oracle Linux</g><g id="5765673b-779b-4dea-b2ba-15519de690a1CapsExtId2" ctype="x-title"></g>| |
| <g id="e04af310-912d-4c0b-8bfb-52b218bfc417CapsExtId1" ctype="x-linkText">Ubuntu</g><g id="e04af310-912d-4c0b-8bfb-52b218bfc417CapsExtId2" ctype="x-title"></g>| |
| <g id="4fddd28d-866e-488c-812a-3ebde0d2447aCapsExtId1" ctype="x-linkText">FreeBSD</g><g id="4fddd28d-866e-488c-812a-3ebde0d2447aCapsExtId2" ctype="x-title"></g>| |
Existen consideraciones respecto de las versiones de kernel específico.
Para obtener más información, incluida la información de soporte técnico en las versiones anteriores de Hyper-V, vea <g id="d8eb7793-ffaf-4ecb-aa58-18b7df10a454CapsExtId1" ctype="x-linkText">Linux y FreeBSD máquinas virtuales Hyper-V</g><g id="d8eb7793-ffaf-4ecb-aa58-18b7df10a454CapsExtId2" ctype="x-title"></g>.




