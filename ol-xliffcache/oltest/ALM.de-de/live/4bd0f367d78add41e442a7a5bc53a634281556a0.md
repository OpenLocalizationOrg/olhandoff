Title: Publish build artifacts
Description: Publish build artifacts
ms.TocTitle: Publish build artifacts
ms.ContentId: 1BB6BB93-5749-438F-B0BD-B8DB61141D9A

# Publish build artifacts

Copy binaries and other files you need from your build process into an artifact on your server or file share so your team can download them.

## Demands

None

## Arguments

<table>
<thead>
<tr>
<td>Argument</td>
<td>Description</td>
</tr>
</thead>
<tr>
<td>Copy Root</td>
<td>
<p>Specify the root folder that contains the files you want to copy.</p>
<p>Leave it empty to copy from the root folder of the repo. For example ```C:\a\```&lt;randomid&gt;```\OurRepo```</p>
<p>Specify $(Agent.BuildDirectory) if your build produces artifacts outside of the sources directory. This will copy files from the build agent working directory. For example ```C:\a\```&lt;randomid&gt;</p>
</td>
</tr>
<tr>
<td>Contents</td>
<td><p>Specify minimatch pattern filters (one on each line) that you want to apply to the list of files to be copied. For example, specify ```**\bin``` to copy files in any sub-folder named bin.</p>
</td>
</tr>
<tr>
<td>Artifact Name</td>
<td>Specify the name of the artifact.</td>
</tr>
<tr>
<td>Artifact Type</td>
<td>
<p>Choose server to store the artifact on your Team Foundation Server. This is the best and simplest option in most cases.</p>
<p>Choose file share to copy the artifact to a file share. Some common reasons to do this:</p>
<ul>
<li>The size of your drop is large and consumes too much time and bandwidth to copy.</li>
<li>You need to run some custom scripts or other tools against the artifact.</li>
</ul>
<p>
If you use a file share, specify the UNC file path to the folder. You can control how the folder is created for each build using variables. For example ```\\my\share\$(Build.DefinitionName)\$(Build.BuildNumber)```. 
</p>
<p>**Note:** You cannot use a file share if you are using the [hosted pool](https://www.visualstudio.com/get-started/build/hosted-agent-pool).</p>
</td>
</tr>
</table>

## Examples

### Copy executables and readme file

#### Goal

You want to copy just the read me and the files needed to run this C# console app:

 * Solution 'ConsoleApplication1' (3 projects)

  - C# ClassLibrary1

  - C# ClassLibrary2

  - C# ConsoleApplication1   

#### Arguments

 * Copy Root: $(Build.SourcesDirectory)

 * Contents example 1: 

   ```
   ConsoleApplication1\bin\**\*.exe
   ConsoleApplication1\bin\**\*.dll
   readme.txt
   ```

 * Content example 2:

   ```
   ConsoleApplication1\bin\**\?(*.exe|*.dll)
   readme.txt
   ```

 * Artifact Name: drop

#### Results

The *drop* artifact is published and contains these files:

 * ConsoleApplication1

  - bin

    * Release

      - ClassLibrary1.dll

      - ClassLibrary2.dll

      - ConsoleApplication1.exe

 * readme.txt

## Q & A

<!-- BEGINSECTION class="md-qanda" -->

### Q: I'm having problems. How can I troubleshoot them?

A: Try this:

 0. On the variables tab, add ```system.debug``` and set it to ```true```. Select to allow at queue time.

 0. In the explorer tab, view your completed build and click the publish artifact step to view the output.

### Q: What's a minimatch pattern? How does it work?

See https://github.com/isaacs/minimatch and https://realguess.net/tags/minimatch/.

### Q: What variables can I use? 

A: [Predefined variables](/library/vs/alm/build/scripts/variables.md)

<!-- ENDSECTION -->