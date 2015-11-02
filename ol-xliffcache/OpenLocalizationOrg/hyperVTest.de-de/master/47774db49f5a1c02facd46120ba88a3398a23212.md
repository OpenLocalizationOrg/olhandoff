MS-TEST:::ms.ContentId: 95FE9554-3968-4EED-B65D-E03F06A7598D
title: Step 3: Create a virtual switch

#MS-TEST:::Step 3: Create a virtual switch

MS-TEST:::A virtual switch allows you to create a network connection for your virtual machine.
MS-TEST:::They are used just like the network adapter (NIC) on your physical computer.

MS-TEST:::For this example, we are going to create an External switch.
MS-TEST:::The external switch will allow your virtual machine to access the host machine's network adapter.
MS-TEST:::If your host machine is connected to the internet, your virtual machine will be as well.

MS-TEST:::We'll also set the switch to allow the host to share this network adapter.
MS-TEST:::This makes it so both the virtual machines and the host can use the same network.



1. MS-TEST:::In Hyper-V manager, click **Virtual Switch Manager**.
    
    MS-TEST:::![](media/virtual_switch_manager1.png)
    
2. MS-TEST:::Select **New virtual network switch**.
    
    MS-TEST:::![](media/new_switch.png)
    
3. MS-TEST:::Select **External** and **Create Virtual Switch**.
    
    MS-TEST:::![](media/new_switch_createbutton.png)
    
4. MS-TEST:::Under **Name**, type **External**.
5. MS-TEST:::Under **External network**, select the correct network adapter (there will probably only be one option).
6. MS-TEST:::Select **Allow management operating system to share this network adapter** and click **OK**.
    
    MS-TEST:::![](media/share_nic.png)
    
7. MS-TEST:::You'll get a message warning you that your network might disconnect while the virtual switch is created.
    MS-TEST:::Just click **Yes**.
    MS-TEST:::Your network will be unavailable for a short time.
    
    MS-TEST:::![](media/network_warning.png)

##MS-TEST:::Next step:

MS-TEST:::[Step 4: Create a Windows virtual machine from an .iso file](walkthrough_create_vm.md)




