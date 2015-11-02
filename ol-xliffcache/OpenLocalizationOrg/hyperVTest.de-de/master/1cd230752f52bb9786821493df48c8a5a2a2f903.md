MS. ContentId: 526e4f1a-2936-4c61-b3be-d41b4cf9d10f
Titel: zu Windows Server-Container

#Windows Server-Container

Applikationen Kraftstoff Innovation in der Cloud und mobile Zeitraum.
Container und das Ökosystem, das gezogen, entwickelt werden Softwareentwickler Applications-Erlebnis die nächste Generation erstellen können.

Sehen Sie sich einen kurzen Überblick: [Windows-basierte Container: moderne app-Entwicklung mit einer unternehmenstauglichen Steuerelement](https://youtu.be/Ryx3o0rD5lY).

##Was sind Container?

Es handelt sich um eine isolierte, Ressource gesteuerte und portable operating Umgebung.

Im Grunde ist ein Container einer isolierten Stelle, wo eine Anwendung ohne den Rest des Systems und ohne das System, das sich auf die Anwendung ausgeführt werden kann.
Container sind der nächste Entwicklungsschritt bei der Virtualisierung.

Wenn Sie innerhalb eines Containers würden, sieht es sehr viel, wie Sie in einem neu installierten physischen Computer oder einen virtuellen Computer wurden.
Und zu [Docker](https://www.docker.com/), einen Windows Server-Container kann auf die gleiche Weise wie jede andere Container verwaltet werden.

##Container-Grundlagen

Beim Arbeiten mit Containern bemerken Sie viele ähnlichkeiten zwischen einem Container und einer virtuellen Maschine.
Ein Container ein Betriebssystem ausgeführt wird, verfügt über ein Dateisystem und kann über ein Netzwerk zugegriffen werden, als ob es sich um eine physische oder virtuelle Computersystem war.
Dies bedeutet, dass die Technologie und die Konzepte hinter Container sehr von dem der virtuelle Computer unterscheiden.
[In diesem Blogbeitrag](http://azure.microsoft.com/blog/2015/08/17/containers-docker-windows-and-trends/) von Mark Russinovich erklärt auch zu Containern.

Die folgenden grundlegenden Konzepte können nützlich sein, Sie zu Beginn erstellen und Arbeiten mit Windows Server-Containern.


**Container Host:** physische oder virtuelle Computersystem mit der Funktion für die Windows Server-Container konfiguriert.
Der Container-Host führt einen oder mehrere Windows Server-Container.

**Container-Image:** wie Änderungen an einer Container-Dateisystems oder der Registrierung vorgenommen werden, wie z. B. mit der Softwareinstallation in der Sandbox erfasst werden.
In vielen Fällen diesen Zustand erfassen empfiehlt, neuer Container erstellt werden können, die diese Änderungen vererbt.
Was ist ein Image ist – nach der Container, die Sie beendet wurde, kann entweder diese Sandbox verwerfen oder können Sie es in ein neues Container-Bild konvertieren.
Nehmen wir z. B., dass Sie einen Container aus dem Windows Server Core-Betriebssystem-Image bereitgestellt haben.
Anschließend installieren Sie MySQL in diesem Container.
Erstellen ein neues Bild aus diesem Container würde als bereitstellbar Version des Containers fungieren.
Dieses Bild enthält nur die Änderungen (MySQL), jedoch als eine Schicht über das Betriebssystemabbild Container arbeiten würden.

**Sandbox:** nach ein Container gestartet wurde, können alle Aktionen bereitstellen, wie z. B. Datei Systemmodifikationen, Änderungen an der Registrierung oder Softwareinstallationen auf dieser Ebene "Sandbox" erfasst werden.



**Container BS-Image:** Container von Abbildern bereitgestellt werden.
Das Betriebssystemabbild Container ist möglicherweise viele Bildebenen, aus denen ein Container der ersten Ebene.
Grafik für das Betriebssystem.
Ein Container-Betriebssystemabbild ist unveränderlich, kann nicht geändert werden.

**Container Repository:** jedes Mal ein Container-Image, das Container-Image erstellt wird und die abhängigen Elemente in einem lokalen Repository gespeichert werden.
Diese Bilder können oft auf dem Host Container wiederverwendet werden.
Die Container-Bilder können auch in einem öffentlichen oder privaten Repository wie z. B. DockerHub gespeichert werden, damit sie über viele verschiedene Container-Host verwendet werden können.

**Container-Management-Technologie:** Windows Server-Container kann mithilfe von PowerShell und Docker verwaltet werden.
Mit einem dieser Tools können Sie Erstellen neuer Container Container Bilder sowie den Lebenszyklus der Container verwalten.

<center>![](media/containerfund.png)</center>

##Container für Entwickler

Ein Entwickler den Desktop an einen Computer testen, auf einen Satz von Produktionscomputer, ein Docker Bild erstellt werden kann, die in Sekunden genauso wie in jeder Umgebung bereitgestellt wird.
Dieser Artikel hat eine massive erstellt und wachsenden Ökosystem Anwendungstypen in Docker-Containern mit DockerHub, öffentliche Containern Anwendung Registrierung, die Docker derzeit mehr als 180.000 Applications im öffentlichen Community-Repository veröffentlichen verwaltet, verpackt.



Wenn Sie eine app containerize, werden nur die app und zum Ausführen der Anwendung erforderlichen Komponenten "Abbild" zusammengefasst.
Container werden aus diesem Bild nach Bedarf erstellt.
Sie können auch ein Bild als Basislinie verwenden, um ein anderes Bild zu erstellen, wodurch schnellere Erstellung von Abbildern.
Mehrere Container können dasselbe Image, freigeben, d. h. Container sehr schnell starten und weniger Ressourcen.
Beispielsweise können Sie Container ein leicht Hochfahren und portable app Komponenten – oder "Micro-Dienste" – für apps verteilt und schnell skalieren, jeden Dienst einzeln.

Da dem Container alles zum Ausführen der Anwendung benötigt ist, sie sind sehr leicht portieren und können auf jedem Computer, auf Windows Server 2016 ausführen.
Sie können erstellen Testcontainer lokal, und, dasselbe Abbild für den Container für private Clouds, öffentliche Cloud oder Dienstanbieter Ihres Unternehmens bereitstellen.
Die natürliche Flexibilität von Containern moderne app Entwicklungsmustern in großem Maßstab unterstützt, virtualisiert und cloud-Umgebungen.

Mit Containern können Entwickler eine Anwendung in jeder Sprache erstellen.
Diese apps sind vollständig portabel und können überall - Laptop, Desktop, Server, private Clouds, öffentliche Cloud oder Dienstanbieter - Code unverändert ausgeführt werden.



Container können Entwickler erstellen und höherer Qualität Applications schneller anzubieten.

##Container für IT-Experten

Container können IT-Experten standardisierte Umgebung für ihre Entwicklung, QA und Produktions-Teams bereitstellen.
Sie müssen nicht mehr über komplexe Installations- und Konfigurationsschritte erforderlich machen.
Mithilfe von Containern abstrahieren Systemadministratoren abwesend Unterschiede in Betriebssysteminstallationen versorgen und zugrunde liegende Infrastruktur.

Container können Administratoren eine Infrastruktur zu erstellen, die einfacher zu aktualisieren und zu warten ist.

##Video-Überblick

<iframe src="https://channel9.msdn.com/Blogs/containers/Containers-101-with-Microsoft-and-Docker/player" width="960" height="540" allowFullScreen="true" frameBorder="0" scrolling="no"></iframe>


##Wiederholen Sie den Windows Server-Container

[Erste Schritte mit Windows Server-Container in Windows Azure](../quick_start/azure_setup.md)  
[Erste Schritte mit Windows Server-Containern lokal](../quick_start/container_setup.md)

-------------------

[Zurück zur Startseite von Container](../containers_welcome.md)




