MS. ContentId: 4981828d-1a08-4d8c-a99d-874a926a153f
Titel: PowerShell Docker Vergleich

#PowerShell zum Vergleich der Docker für die Verwaltung von Windows Server-Container

Es gibt viele Verfahren zum Verwalten von Windows Server-Container mit integrierten Windows-Tools (in dieser Vorschau PowerShell) und Open-Source-Verwaltungstools, wie z. B. Docker.
Führungslinien Gliedern beide einzeln erhältlich hier:
* [Verwalten von Windows Server-Container mit Docker](../quick_start/manage_docker.md)
* [Verwalten von Windows Server-Container mit PowerShell](../quick_start/manage_powershell.md)
    

Diese Seite ist einem mehr Tiefe Referenz Vergleich von Docker-Tools und PowerShell-Verwaltungstools.

##PowerShell für Container im Vergleich zu Hyper-V-Computern

Erstellen können, ausführen und mit Windows Server-Container mit PowerShell-Cmdlets interagieren.
Alles, was Sie benötigen den Einstieg wird im Feld verfügbar.

Wenn Sie Hyper-V-PowerShell verwendet haben, sollte das Design der Cmdlets Recht vertraut sein.
Ein Großteil der Workflow ist ähnlich wie eine virtuelle Maschine mit dem Hyper-V-Modul verwaltet.
Anstelle von `New-VM`, `Get-VM`, `Start-VM`, `Stop-VM`, stehen Ihnen `New-Container`, `Get-Container`, `Start-Container`, `Stop-Container`.
Es gibt einige Container-spezifische Cmdlets und Parameter, aber die allgemeine Lebenszyklus und Verwaltung von Windows-Container sieht in etwa wie eine Hyper-V-VM.

##Wie Vergleich PowerShell Management im zu Docker?

Die Container-PowerShell-Cmdlets verfügbar machen eine API, die nicht ganz identisch mit der Docker ist. die Cmdlets sind in der Regel genauer Vorgang.
Einige Befehle Docker sind unkompliziert Parallels in PowerShell:

| Docker-Befehl| PowerShell-Cmdlets|
|----|----|
| `Docker Ps - ein`| `Get-Container`|
| `Docker Bilder`| `Get-ContainerImage`|
| `Docker rm`| `Entfernen eines Containers`|
| `Docker rmi`| `Remove-ContainerImage`|
| `Docker erstellen`| `Neuen Container`|
| `Docker Commit < Container-ID >`| `Neue ContainerImage-Container < Container >`|
| `Docker laden < Tarball >`| `Import-ContainerImage < AppX-Paket >`|
| `Docker speichern`| `Export-ContainerImage`|
| `Docker starten`| `Start-Container`|
| `Docker beenden`| `Stop-Container`|
Die PowerShell-Cmdlets sind keine genaue perfekte Parität, und es gibt eine große Anzahl von Befehlen, die wir nicht PowerShell Ersatz für bereitstellen * (insbesondere `Docker Build` und `Docker cp`).
Aber was Ihnen sofort auffallen möglicherweise darin, dass es kein einzelnes einzeilige Ersatz für `Docker ausführen`.

\ * Vorbehalten.

###Aber ich Docker ausführen! Was ist passiert?

Wir machen, ein paar Dinge, die eine etwas vertrauter Interaktionsmodell für Benutzer bereitstellen, die ihre PowerShell bereits vertraut sind.
Wenn Sie die Art und Weise Docker arbeitet verwendet, wird dies natürlich etwas ein Umdenken sein.

1.  Der Lebenszyklus eines Containers im PowerShell-Modell ist etwas anders.
    Im Container PowerShell-Modul, wir die präzisere Vorgänge verfügbar machen `New-Container` (wodurch erstellt einen neuen Container, der beendet wurde) und `Start-Container`.
    
    Zwischen erstellen, und starten den Container, können Sie auch den Container Einstellungen konfigurieren. für TP3 ist nur anderen Konfigurationen, die wir bereitstellen möchten die Möglichkeit, die Netzwerkschnittstelle für den Container festlegen.
    verwenden die (hinzufügen/entfernen/Verbindung herstellen/trennen/Get/Set)-ContainerNetworkAdapter-Cmdlets.
    
2.  Derzeit kann keinen auszuführenden Befehl innerhalb des Containers auf "Start" übergeben werden. Allerdings weiterhin erhalten Sie eine interaktive PowerShell-Sitzung mit einem ausgeführten Container `Enter-PSSession - des Elements < ID eines laufenden Containers >`, und Sie können einen Befehl innerhalb einer ausgeführten Container mit ausführen `Invoke-Command - des Elements < Container-Id > - ScriptBlock {Code innerhalb des Containers ausgeführt werden soll.}` oder `Invoke-Command - des Elements < Container-Id > - FilePath < Pfad >`.  
    Beide Befehle ermöglichen das optionale `- RunAsAdministrator` für hohe Privilige Aktionen kennzeichnen.
    



##Vorbehalte und bekannte Probleme

1.  Jetzt, die Container-Cmdlets haben keine Kenntnis über Container oder Bilder, die durch Docker erstellt und Docker weiß nicht, alles zu Containern und Images, die über die PowerShell erstellt.
    Wenn Sie in der Docker erstellt, mit der Docker verwalten; Wenn Sie es über PowerShell erstellt haben, können verwalten Sie sich über PowerShell.
    
2.  Wir haben eine ziemlich viel Arbeit, die wir tun, damit um der Endbenutzer – verbesserte Fehlermeldungen, bessere Fortschrittsberichte, ungültiges Ereigniszeichenfolgen usw. zu optimieren möchten.
    Wenn Sie eine Situation auftreten versehentlich, wo sollen Sie waren Weitere erste, oder Informationen besser, wir gerne Vorschläge zu den Foren zu senden.

##Eine schnelle runthrough

Im folgenden wird erörtert einige allgemeine Workflows.

Dabei wird vorausgesetzt, Sie ein Betriebssystemabbild-Container mit dem Namen "ServerDatacenterCore" installiert haben, und erstellt einen virtuellen Switch mit dem Namen "Virtueller Switch" (mit dem New-VMSwitch).

``` PowerShell
### 1. Enumerating images
# At this point, you can enumerate the images on the system:
Get-ContainerImage

# Get-ContainerImage also accepts filters.
# For example, this will return all container images whose Name starts with S (case-insensitive):
Get-ContainerImage -Name S*

# You can save the results of this to a variable.
# (If you're not familiar with PowerShell, the "$" denotes a variable.)
$baseImage = Get-ContainerImage -Name ServerDatacenterCore
$baseImage

### 2. Creating and enumerating containers
# Now, we can create a new container using this image:
New-Container -Name "MyContainer" -ContainerImage $baseImage -SwitchName "Virtual Switch"

# Now we can enumerate all containers.
Get-Container

# Similarly, we can save this container to a variable:
$container1 = Get-Container -Name "MyContainer"

### 3. Starting containers, interacting with running containers, and stopping containers
# Now let's go ahead and start the container.
Start-Container -Name "MyContainer"

# (We could've also started this container using "Start-Container -Container $container1".)

# With the container now running, let's go ahead and enter an interactive PowerShell session:
Enter-PSSession -ContainerId $container1.Id

# This should eventually bring up a PowerShell prompt from inside the container.
# You can try all the things that you did in the interactive cmd prompt given by "docker run -it".
# For now, just to prove we've been here, we can create a new file:
cd \
mkdir Test
cd Test
echo "hello world" > hello.txt
exit

# Now we should be back in the outside world. Even though we've exited the PowerShell session,
# the container itself is still running, as you can see by printing out the container again:
$container1

# Before we can commit this container to a new image, we need to stop the container.
# Let's do that now.
Stop-Container -Container $container1

### 4. Creating a new container image
# And now let's commit it to a new image.
$image1 = New-ContainerImage -Container $container1 -Publisher Test -Name Image1 -Version 1.0

# Enumerate all the images again, for sanity's sake:
Get-ContainerImage

# Rinse and repeat! Make another container based on the new image.
$container2 = New-Container -Name "MySecondContainer" -ContainerImage $image1 -SwitchName "Virtual Switch"

# (If you like, you can start the second container and verify that the new file
# "\Test\hello.txt" is there as expected.)

### 5. Removing a container
# The first container we created is now stopped. Let's get rid of it:
Remove-Container -Container $container1

# And confirm that it's gone:
Get-Container

### 6. Exporting, removing, and importing images
# For images that aren't the base OS image, we can export them into an .appx package file.
Export-ContainerImage -Image $image1 -Path "C:\exports"
# This should create a .appx file in the C:\exports folder.
# If you've given your image the same publisher, name, and version we used earlier,
# you'd expect the resulting .appx to be named "CN=Test_Image1_1.0.0.0.appx".

# Before we can try importing the image again, we need to remove the image.
# (If you have any running containers that depend on this image, you'll want to stop them first.)
Remove-ContainerImage -Image $image1

# Now let's import the image again:
Import-ContainerImage -Path C:\exports\CN=Test_Image1_1.0.0.0.appx

# We'd previously created a container dependent on this image. You should be able to start it:
Start-Container -Container $container2 
```

###Erstellen Sie Ihre eigenen Beispiel

Sie sehen, dass der Container Cmdlets mithilfe einer `Get-Command - Modul Container`.
Es gibt mehrere andere Cmdlets, die hier nicht beschrieben werden, die wir Ihnen Informationen auf Ihren eigenen lassen.
**Hinweis** Dadurch wird nicht zurückgegeben, die `Enter-PSSession` und `Invoke-Command` Bestandteil des Kerns PowerShell-Cmdlets.

Erhalten Sie Hilfe zur Verwendung von jedem Cmdlet auch `Get-Help [CmdletName]`, bzw. die Referenzdatenbank `[CmdletName]-?`.
Heute Hilfe wird automatisch generiert und teilt Ihnen nur die Syntax für Befehle. Wir werden weitere Dokumentation hinzufügen werden wie wir näher erhalten an das Cmdlet-Design abschließen.

Eine nützlicher Möglichkeit, die Syntax zu ermitteln ist PowerShell ISE, die Sie nicht vor dem besprochen haben können, wenn Sie PowerShell sehr viel verwendet haben.
Wenn Sie auf eine SKU, die es ermöglicht ausgeführt, starten Sie das Befehlsfenster zu öffnen, und wählen im Modul "Container" der grafisch dargestellt, die Cmdlets und ihren Parameter angezeigt, für die ISE.

PS: Nur um zu beweisen, es ist möglich, hier ist eine PowerShell-Funktion, die einige der Cmdlets verfasst, wir bereits, in einem ersatz gesehen haben `Docker ausführen`.
(Klar gesagt werden, ist dies eine Machbarkeitsstudie nicht in der aktiven Entwicklung.)

``` PowerShell
function Run-Container ([string]$ContainerImageName, [string]$Name="fancy_name", [switch]$Remove, [switch]$Interactive, [scriptblock]$Command) {
    $image = Get-ContainerImage -Name $ContainerImageName
    $container = New-Container -Name $Name -ContainerImage $image
    Start-Container $container

    if ($Interactive) {
         Start-Process powershell ("-NoExit", "-c", "Enter-PSSession -ContainerId $($container.Id)") -Wait
    } else {
        Invoke-Command -ContainerId $container.Id -ScriptBlock $Command
    }

    Stop-Container $container

    if ($Remove) {
        Remove-Container $container -Force
    }
} 
```

##Docker

Windows Server-Container können mit Docker-Befehlen verwaltet werden.
Während Windows Container ihren Gegenstücken Linux vergleichbar sein und sollte die gleiche Verwaltung über Docker auftreten, stehen einige Docker-Befehle, die einfach mit einem Windows-Container nicht sinnvoll sind.
Andere einfach noch nicht getestet wurden (wir gehen vorhanden).

In dem Bestreben, die API-Dokumentation Docker nicht duplizieren ist hier ein Link zu ihrer Verwaltungs-APIs.
Die exemplarischen Vorgehensweisen sind fantastisch.

Wir überwachen die Dinge, die funktionieren und nicht in die Docker-APIs in unser Dokument In Bearbeitung.



