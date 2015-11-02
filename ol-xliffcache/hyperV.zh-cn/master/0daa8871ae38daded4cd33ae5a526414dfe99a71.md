#Step 4: Create a Windows virtual machine from an .iso file

For this step, if you already have a .iso file for a supported 64-bit operating system, you can use that.
If not, you can download the .iso for [Windows 8.1 Enterprise](http://www.microsoft.com/en-us/evalcenter/evaluate-windows-8-1-enterprise) and choose the 64-bit edition.

1.  In Hyper-V Manager, click on the **Action** menu > **New** > **Virtual machine**.
2.  In the virtual machine wizard, make the following choices:
    
    <table>
      <tr>
        <th caps_internal_Id="fd5bf520-ef20-4a9c-a8e6-b91355e179ca">Page</th>
        <th caps_internal_Id="d597e9da-57f1-40fe-bb9e-f792b49b549e">Entry</th>
      </tr>
      <tr>
        <td caps_internal_Id="6d6b261f-036f-4efd-9e63-fce491365e0d">Name:</td>
        <td>Type in <b caps_internal_Id="826c30e6-841e-4b73-a61d-49034a3ddaed">Windows Walkthrough VM</b></td>
      </tr>
      <tr>
        <td caps_internal_Id="43f2780e-c247-4e13-948e-f4585aca4aa4">Generation:</td>
        <td>
          <b caps_internal_Id="b2df3e15-315e-4cca-949e-06fe4bd54521">Generation 2</b>
        </td>
      </tr>
      <tr>
        <td caps_internal_Id="d92fd918-de18-4a3b-a1af-e89ccaa04a5b">Startup Memory:</td>
        <td>
          <b caps_internal_Id="f52b9094-d83f-433c-bb1d-42371e7f6728">1024</b> and leave dynamic memory selected</td>
      </tr>
      <tr>
        <td caps_internal_Id="f8b823cf-c5c3-449a-bac0-4620677860e6">Configure Networking:</td>
        <td>
          <b caps_internal_Id="7080bf45-3203-4783-b8f8-ac9b317c27b3">External</b> (this is the virtual switch you created in Step 3)</td>
      </tr>
      <tr>
        <td caps_internal_Id="0a9c9291-c2bd-4633-89ca-6d5eea8b134f">Connect virtual hard disk:</td>
        <td>
          <b caps_internal_Id="72c51616-e140-460c-834a-38a661fbe173">Create a virtual hard disk</b> (keep the other default values) </td>
      </tr>
      <tr>
        <td caps_internal_Id="c4c7efcc-09f3-4dab-a749-7dd89ad1b387">Installation Options:</td>
        <td>
          <b caps_internal_Id="e78212ee-806a-4324-b54a-404e1d2614d7">Install an operating system from a bootable CD/DVD-ROM</b>. Under <b caps_internal_Id="b4952826-4107-4cdd-8add-ea9c67b6679d">Media</b>, select <b caps_internal_Id="27270b1a-e640-40f1-8b24-4295f9aeb831">Image file (iso)</b> and then click <b caps_internal_Id="e10c071a-3d79-4cb5-8f76-eb8ef356132d">Browse</b> to point to the .iso file.</td>
      </tr>
    </table>
3.  When everything looks right, click **Finish**.

> **Note:** If you only have 32-bit version of Windows, you need to choose Generation 1 in the **Generation** section of the wizard.
> Generation 2 VMs only support 64-bit operating systems.
> 

##Next Step:

[Step 5: Connect to the virtual machine and finish the installation](walkthrough_vmconnect.md)


