ms.ContentId: 95FE9554-3968-4EED-B65D-E03F06A7598D
タイトル: ステップ 3: バーチャルスウィッチの作成

#ステップ 3: バーチャルスウィッチの作成

テストA virtual switch allows you to create a network connection for your virtual machine.テスト終わり
テストThey are used just like the network adapter (NIC) on your physical computer.テスト終わり



テストFor this example, we are going to create an External switch.テスト終わり
テストThe external switch will allow your virtual machine to access the host machine's network adapter.テスト終わり
テストIf your host machine is connected to the internet, your virtual machine will be as well.テスト終わり


テストWe'll also set the switch to allow the host to share this network adapter.テスト終わり
テストThis makes it so both the virtual machines and the host can use the same network.テスト終わり



1. テストIn Hyper-V manager, click **Virtual Switch Manager**.テスト終わり
    
    テスト![](media/virtual_switch_manager1.png)テスト終わり
    
2. テストSelect **New virtual network switch**.テスト終わり
    
    テスト![](media/new_switch.png)テスト終わり
    
3. テストSelect **External** and **Create Virtual Switch**.テスト終わり
    
    テスト![](media/new_switch_createbutton.png)テスト終わり
    
4. テストUnder **Name**, type **External**.テスト終わり
5. テストUnder **External network**, select the correct network adapter (there will probably only be one option).テスト終わり
    

6. テストSelect **Allow management operating system to share this network adapter** and click **OK**.テスト終わり
    

    テスト![](media/share_nic.png)テスト終わり
    


7. テストYou'll get a message warning you that your network might disconnect while the virtual switch is created.テスト終わり
    テストJust click **Yes**.テスト終わり
    テストYour network will be unavailable for a short time.テスト終わり
    
    テスト![](media/network_warning.png)テスト終わり

##テストNext step:テスト終わり

テスト[Step 4: Create a Windows virtual machine from an .iso file](walkthrough_create_vm.md)テスト終わり




