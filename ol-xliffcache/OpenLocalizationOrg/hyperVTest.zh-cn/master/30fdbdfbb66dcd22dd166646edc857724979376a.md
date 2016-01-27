ms.ContentId: 7561B149-A147-4F71-9840-6AE149B9DED5
title: Supported Windows Guest Operating Systems


# Supported Windows guests 
26-Jan update. This article lists the Windows operating systems supported as guests in Hyper-V on Windows, as well provides information about integration services. 

> Windows 10 runs as a guest operating system on Windows 8.1 and Windows Server 2012 R2 Hyper-V hosts.

## What does support mean? 
Support means Microsoft has tested these host/guest combinations.  Issues with these combinations may receive attention from Product Support Services.
 
Microsoft provides support for guest operating systems in the following manner:
* Issues found in Microsoft operating systems and in integration services are supported by Microsoft support.
* For issues found in other operating systems that have been certified by the operating system vendor to run on Hyper-V, support is provided by the vendor.
* For issues found in other operating systems, Microsoft submits the issue to the multi-vendor support community, <bpt id="p0">[</bpt>TSANet<ept id="p1">](http://www.tsanet.org/)</ept>.

## What are integration services and why do they matter?
Hyper-V includes integration services for supported guest operating systems.  Integration services improve interaction between the host system and the virtual machine.  

Some operating systems (including different versions of Windows) have the integration services built-in, while others provide integration services through Windows Update.

## Supported Windows Server guest operating systems

For Windows 10 Hyper-V Hosts:


 |  Guest operating system              |  Maximum number of virtual processors     |  Integration Services     |  Notes    |       | 
 | -----                                | -----                                     | -----                     | -----     | ----- |
 |  Windows Server Technical Preview    | 64                                        | Built-in |                |           |       |
 |  Windows Server 2012 R2              | 64                                        | Built-in |                |           |       |
 |  Windows Server 2012                 | 64                                        | Built-in |                |           |       | 
 |  Windows Server 2008 R2 with Service Pack 1 (SP 1)   | 64                            | Install the integration services after you set up the operating system in the virtual machine.                                                                        | Datacenter, Enterprise, Standard and Web editions.                                                                                                              |       | 
 |  Windows Server 2008 with Service Pack 2 (SP 2)      | 4                         | Install the integration services after you set up the operating system in the virtual machine.                                                                                | Datacenter, Enterprise, Standard and Web editions (32-bit and 64-bit).                                                                                          |        | 
 |  Windows Home Server 2011            | 4                                         | Install the integration services after you set up the operating system in the virtual machine.                                                                                             |       | 
 |  Windows Small Business Server 2011  |  Essentials edition - 2, Standard edition - 4  |  Install the integration services after you set up the operating system in the virtual machine.                                                                        |  Essentials and Standard editions.                                                                                                                  |        | 
 
 
## Supported Windows guest operating systems

For Windows 10 Hyper-V Hosts:

 |  Guest operating system |  Maximum number of virtual processors |  Integration Service  |  Notes  |  |
 | ----- | ----- | ----- | ----- | ----- |
 | Windows 10 | 32 | Built-in |  |  |
 | Windows 8.1 | 32 | Built-in |  |     |
 | Windows 8 | 32 | Upgrade the integration services after you set up the operating system in the virtual machine. |     |  |
 | Windows 7 with Service Pack 1 (SP 1) | 4 | Upgrade the integration services after you set up the operating system in the virtual machine. | Ultimate, Enterprise, and Professional editions (32-bit and 64-bit). |   |
 | Windows 7 | 4 | Upgrade the integration services after you set up the operating system in the virtual machine. | Ultimate, Enterprise, and Professional editions (32-bit and 64-bit). |  |
 | Windows Vista with Service Pack 2 (SP2) | 2 | Install the integration services after you set up the operating system in the virtual machine. | Business, Enterprise, and Ultimate, including N and KN editions. |    |
 
 Windows 10 is a guest operating system on Windows 8.1 and Windows Server 2012 R2 Hyper-V hosts.

## Linux and Free BSD

For Windows 10 Hyper-V Hosts:

| Guest operating system |  |
| -----|------|
| <bpt id="p2">[</bpt>CentOS and Red Hat Enterprise Linux <ept id="p3">](https://technet.microsoft.com/library/dn531026.aspx)</ept> | |
| <bpt id="p4">[</bpt>Debian virtual machines on Hyper-V<ept id="p5">](https://technet.microsoft.com/library/dn614985.aspx)</ept> | |
| <bpt id="p6">[</bpt>SUSE<ept id="p7">](https://technet.microsoft.com/en-us/library/dn531027.aspx)</ept> | |
| <bpt id="p8">[</bpt>Oracle Linux<ept id="p9">](https://technet.microsoft.com/en-us/library/dn609828.aspx)</ept>  | |
| <bpt id="p10">[</bpt>Ubuntu<ept id="p11">](https://technet.microsoft.com/en-us/library/dn531029.aspx)</ept> | |
| <bpt id="p12">[</bpt>FreeBSD<ept id="p13">](https://technet.microsoft.com/library/dn848318.aspx)</ept> | |

There are caveats around specific kernel versions. For more information, including support information on past versions of Hyper-V, see <bpt id="p14">[</bpt>Linux and FreeBSD Virtual Machines on Hyper-V<ept id="p15">](https://technet.microsoft.com/library/dn531030.aspx)</ept>.
<!--HONumber=Jan16_HO4-->
