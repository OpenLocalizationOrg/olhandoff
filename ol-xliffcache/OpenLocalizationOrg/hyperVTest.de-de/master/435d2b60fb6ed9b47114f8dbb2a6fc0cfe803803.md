MS-TEST:::ms.ContentId: 6C7EB25D-66FB-4B6F-AB4A-79D6BB424637
title: Make a new management service

#MS-TEST:::Make a new management service

MS-TEST:::This is a test.
MS-TEST:::This document introduces VM Services built on Hyper-V sockets and how to get started using them.

##MS-TEST:::What is a VM Service?

MS-TEST:::Adding this sentence for testing HO-HB process.
MS-TEST:::VM Services are services that span the Hyper-V host and virtual machines running on the host.

MS-TEST:::Hyper-V now (Windows 10 and Server 2016+) provides a non-network connection which allows you to create services spanning the host/virtual machine boundary while preserving Hyper-V’s fundamental requirements around tenant/hoster isolation, control, and diagnosable.

MS-TEST:::Hyper-V will continue to provide a base set of in-box services (integration services) for basics (such as time sync) and for common requests we receive, but now anyone can write and deploy a VM service as needed.

MS-TEST:::PowerShell Direct is an in-box example of a VM Service.

##MS-TEST:::What is a Hyper-V socket?

MS-TEST:::Hyper-V sockets are TCP-like sockets with no dependence on networking.
MS-TEST:::Using Hyper-V sockets, services can run independently of the networking stack and all data flow stays on host memory.

##MS-TEST:::System Requirements

MS-TEST:::**Supported Host OS**
*   MS-TEST:::Windows 10
*   MS-TEST:::Windows Server Technical Preview 3
*   MS-TEST:::Future releases (Server 2016 +)

MS-TEST:::**Supported Guest OS**
*   MS-TEST:::Windows 10
*   MS-TEST:::Windows Server Technical Preview 3
*   MS-TEST:::Future releases (Server 2016 +)
*   MS-TEST:::Linux

##MS-TEST:::Capabilities and Limitations

MS-TEST:::Kernel mode or user mode  
Data stream only    
No block memory so not the best for backup/video

##MS-TEST:::Getting started

MS-TEST:::This guide assumes you're familiar with socket programming in C/C++.

###MS-TEST:::Step 1 - Register your service on the Hyper-V host

MS-TEST:::In order to use a custom service integrated with Hyper-V, the new service must be registered with the Hyper-V Host's registry.

MS-TEST:::By registering the service in the registry, you get:
*  MS-TEST:::WMI management for enable, disable, and listing available services
*  MS-TEST:::Onto the list of services allowed to communicate with virtual machines directly.

MS-TEST:::** Registry location and information **

``` 
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\VirtualDevices\6C09BB55-D683-4DA0-8931-C9BF705F6480\GuestCommunicationServices\
```
MS-TEST:::In this registry location, you'll see several GUIDS.
MS-TEST:::Those are our in-box services.

MS-TEST:::Information in the registry per service:
* MS-TEST:::`Service GUID`
    * MS-TEST:::`ElementName (REG_SZ)` -- this is the service's friendly name

MS-TEST:::To register your own service, create a new registry key using your own GUID and friendly name.

MS-TEST:::The registry entry will look like this:
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Virtualization\GuestCommunicationServices\
    999E53D4-3D5C-4C3E-8779-BED06EC056E1\
        ElementName REG_SZ  VM Session Service
    YourGUID\
        ElementName REG_SZ  Your Service Friendly Name
```

> MS-TEST:::** Tip: **  To generate a GUID in PowerShell and copy it to the clipboard, run:
``` PowerShell
[System.Guid]::NewGuid().ToString() | clip.exe
```



###MS-TEST:::Step 2 - Create a simple host-side service

###MS-TEST:::Step 3 - Create a simple guest-side service

##MS-TEST:::More information about AF_HYPERV

MS-TEST:::Since Hyper-V sockets do not depend on a networking stack, TCP/IP, DNS, etc. the socket end point needed a non-IP, not hostname, format that still describes the connection.
MS-TEST:::In lieu of an IP or hostname, AF_HYPERV endpoints rely heavily on two GUIDS:
* MS-TEST:::VM ID – this is the unique ID assigned per VM.
    MS-TEST:::A VM’s ID can be found using the following PowerShell snippet.
```PowerShell
(Get-VM -Name vmname).Id
```
* MS-TEST:::Service ID – GUID under which the service is registered in the Hyper-V host registry.
    MS-TEST:::See [Registering a New Service](#GettingStarted).

MS-TEST:::For connections from a service on the host to the service on a VM:  
VMID and Service ID
For connections from a service on a VM to the service on the host:  
Zero GUID and Service ID

##MS-TEST:::Supported socket commands

MS-TEST:::Socket()
Bind()
Connect ()
Send()
Listen()
Accept()







