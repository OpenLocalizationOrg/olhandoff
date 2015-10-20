テストms.ContentId: 1ab7bfe1-da35-4ff1-916f-936fedf536a0
title: Setup Windows Containers in Azureテスト終わり

#テストPreparing Microsoft Azure for Windows Server Containersテスト終わり

テストThis is a test edit!!!テスト終わり
テストBefore creating and managing Windows Server Containers in Azure you will need to deploy a Windows Server 2016 Technical Preview image which has been pre-configured with the Windows Server Containers feature.テスト終わり
テストThis guide will walk you through this process.テスト終わり

> テストOther getting started guides:テスト終わり
* テストRun Windows Server Containers in [a new Hyper-V virtual machine](./container_setup.md).テスト終わり
* テストRun Windows Server Containers in [an existing virtual machine](./inplace_setup.md)テスト終わり
* テストSetup Windows Server Containers [on a physical Windows Server Core installation](./inplace_setup.md)テスト終わり

##テストStart Using Azure Portalテスト終わり

テストIf you have an Azure account, skip straight to [Create a Container Host VM](#CreateacontainerhostVM).テスト終わり

1. テストGo to [azure.com](https://azure.com) and follow the steps for an [Azure Free Trial](https://azure.microsoft.com/en-us/pricing/free-trial/).テスト終わり
2. テストSign in with your Microsoft account.テスト終わり
3. テストWhen your account is ready to go, sign into the [Azure Management Portal](https://portal.azure.com).テスト終わり

##テストCreate a Container Host VMテスト終わり

テストClick on the following link to start the VM creation process – [New Windows Server Container Host in Azure](https://portal.azure.com/#gallery/Microsoft.WindowsServer2016TechnicalPreviewwithContainers).テスト終わり


テストYou can also search for the image in the Azure gallery.テスト終わり

テストClick on the `create` button.テスト終わり

テスト![](./media/newazure1.png)テスト終わり

テストGive the Virtual Machine a name, select a user name and a password.テスト終わり

テスト![](media/newazure2.png)テスト終わり

テストSelect Optional Configuration > Endpoints > and enter an HTTP endpoint with a private and public port of 80 as seen below.テスト終わり
テストWhen completed click ok two times.テスト終わり

テスト![](./media/newazure3.png)テスト終わり

テストSelect the `create` button to start the Virtual Machine deployment process.テスト終わり

テスト![](media/newazure2.png)テスト終わり

テストWhen the VM deployment is complete, select the connect button to start an RDP session with the Windows Server Container Host.テスト終わり

テスト![](media/newazure6.png)テスト終わり

テストLog into the VM using the username and password specified during the VM creation wizard.テスト終わり
テストOnce logged in you will be looking at a Windows command prompt.テスト終わり

テスト![](media/newazure7.png)テスト終わり


##テストVideo Walkthroughテスト終わり

<iframe src="https://channel9.msdn.com/Blogs/containers/Quick-Start-Configure-Windows-Server-Containers-in-Microsoft-Azure/player" width="800" height="450" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##テストNext Steps - Start Using Containersテスト終わり

テストNow that you have a Windows Server 2016 system running the Windows Server Container feature jump to the following guides to begin working with Windows Server Containers and Windows Server Container images.テスト終わり


テスト[Quick Start: Windows Server Containers and Docker](./manage_docker.md)  
[Quick Start: Windows Server Containers and PowerShell](./manage_powershell.md)テスト終わり


-------------------

テスト
[Back to Container Home](../containers_welcome.md)  
[Known Issues for Current Release](../about/work_in_progress.md)テスト終わり




