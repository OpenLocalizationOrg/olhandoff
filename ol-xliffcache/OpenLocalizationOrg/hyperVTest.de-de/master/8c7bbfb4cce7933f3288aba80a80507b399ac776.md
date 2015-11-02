MS. ContentId: 93EDAAF5-E4FC-4F3F-AB55-669D2BF47D78
Titel: Einführung in Hyper-V auf Windows-10


#Einführung in Hyper-V auf Windows-10-test

Hinzufügen von diesem Satz für HO Kont Testverfahren.
Sind Sie Software-Entwickler, ein IT-Experten oder eine Technologie-Enthusiast, müssen viele von Ihnen mehrere Betriebssysteme, gelegentlich auf vielen verschiedenen Computern ausgeführt werden.
Nicht alle von uns haben Zugriff auf ein umfassendes Labs untergebracht werden alle diese Computer und Virtualisierung kann daher einen Platz und Zeit sparen.

##Verwendet für die Virtualisierung

Virtualisierung kann jeder Umgebung mit mehreren Test bestehend aus vielen Betriebssystemen, Software-Konfigurationen und Hardwarekonfigurationen problemlos zu verwalten.
Hyper-V bietet Virtualisierung auf Windows sowie einen einfachen Mechanismus, wechseln Sie schnell zwischen diesen Umgebungen, ohne dass zusätzliche Hardwarekosten anfallen.
  


Hyper-V kann z. B. in vielerlei Hinsicht verwendet werden:
- Eine Umgebung bestehend aus mehreren virtuellen Computern kann auf einem einzelnen Desktop oder Laptop-Computer erstellt werden.
    Nachdem die Tests abgeschlossen sind, können diese virtuellen Computer exportiert und anschließend in einem anderen Hyper-V-System importiert.
    
- Entwickler können Hyper-V auf dem Computer zum Testen von Software auf mehreren Betriebssystemen verwenden.
    Wenn Sie eine Anwendung, auf denen Windows 8, Windows 7 oder Linux-Betriebssystem getestet werden müssen verfügen, können z. B. mehrere virtuelle Computer auf Ihrem Entwicklungssystem, enthält jedes dieser Betriebssysteme erstellt werden.
    
- Hyper-V können virtuelle Computer von Hyper-V-Bereitstellung zu beheben.
    Sie können exportieren ein virtuellen Computers von der produktionsumgebung, auf dem Desktop mit Hyper-V zu öffnen, führen Sie die Problembehandlung erforderlich und dann wieder in die produktionsumgebung zu exportieren.
    

- Virtuelle Netzwerke können Sie eine Umgebung mit mehreren Computern Umgebung für Entwicklungs-/Test/Demo erstellen, die im Produktionsnetzwerk beeinflussen sicher ist.
    
- Enthusiasten können sie zum Experimentieren mit anderen Betriebssystemen.
    Hyper-V erleichtert und Beenden von verschiedenen Betriebssystemen.
    
- Hyper-V können auf einem Laptop für ältere Versionen von Windows oder nicht-Windows-Betriebssystemen zu veranschaulichen.
    


##System requirements (Systemanforderungen)

Hyper-V ist ein 64-Bit-System, Second Level Address Translation (SLAT) ist, erforderlich. SLAT ist eine Funktion, die in die aktuelle Generation von 64-Bit-Prozessoren von Intel und AMD vorhanden. Sie benötigen auch einen 64-Bit-Version von Windows 8 oder höher und mindestens 4 GB RAM. Hyper-V unterstützt die Erstellung von 32-Bit- und 64-Bit-Betriebssysteme auf VMs.

Hyper-V dynamic Memory kann erforderlichen Arbeitsspeichers durch den virtuellen Computer reserviert und dynamisch aufgehoben werden (Sie geben ein Minimum und Maximum) und Freigeben von ungenutztem Speicher zwischen virtuellen Computern.
Sie können 3 oder 4 virtuellen Computer ausführen, auf einem Computer mit 4 GB RAM, jedoch benötigen Sie mehr RAM für 5 oder mehr virtuelle Computer.
Am anderen Ende des Spektrums können Sie auch große virtuelle Computer mit 32 Prozessoren und 512 GB RAM, abhängig von der physischen Hardware erstellen.

##Betriebssysteme, die auf einem virtuellen Computer ausgeführt werden kann

Der Begriff "Gast" bezieht sich auf einer virtuellen Maschine und "Host" bezieht sich auf den Computer, auf dem virtuellen Computer ausgeführt wird.
Hyper-V auf Windows unterstützt viele verschiedene Gastbetriebssysteme einschließlich verschiedener Versionen von Linux, FreeBSD und Windows.
Informationen darüber, welche Betriebssysteme als Gäste in Hyper-V unter Windows unterstützt werden, finden Sie unter [unterstützten Windows-Gastbetriebssysteme](supported_guest_os.md) und [Linux und FreeBSD virtuellen Maschinen auf Hyper-V-](https://technet.microsoft.com/library/dn531030.aspx).



##Unterschiede zwischen Hyper-V auf Windows und Hyper-V auf WindowsServer

Es gibt einige Features, die unterschiedlich in Hyper-V auf Windows als bei Hyper-V auf Windows Server ausgeführt wird.
Diese umfassen Folgendes:

- Das Speicher-Management-Modell unterscheidet sich für Hyper-V unter Windows.
    Hyper-V-Speicher erfolgt auf einem Server unter der Annahme, die nur die virtuellen Maschinen auf dem Server ausgeführt werden.
    In Hyper-V unter Windows wird Arbeitsspeicher verwaltet, unter der Voraussetzung, dass die meisten Clientcomputer ausgeführte Software sowie virtuelle Computer ausgeführt werden.
    Beispielsweise kann ein Entwickler Visual Studio als auch mehrere virtuelle Maschinen auf dem gleichen Computer ausgeführt werden.
    
- SR-IOV auf einem 64-Bit-Gast funktioniert normal, aber die 32-Bit nicht und wird nicht unterstützt.


###Windows Server-Features nicht die Berechtigung in Windows Hyper-V

Es gibt einige Funktionen in Hyper-V auf Server enthalten, die in Hyper-V unter Windows nicht enthalten sind.
Diese umfassen Folgendes:

- Die Funktion Remote FX GPUs virtualisieren
    

- Live-Migration virtueller Maschinen von einem Host zum anderen
    
- Hyper-V-Replikat
    
- Virtueller Fibre Channel
    
- SR-IOV-Netzwerke
    
- Gemeinsam genutzt. VHDX


> **Warnung**: virtuelle Computer auf Hyper-V nicht automatisch behandelt Umstellung von einem drahtgebundenen zu einer drahtlosen Verbindung.
> Sie müssen die Einstellungen für virtuelle Maschinen des Netzwerkadapters ändern manuell.

##Einschränkungen

Mithilfe der Virtualisierung begrenzt ist.
Features oder Apps, die auf bestimmte Hardware abhängig sind funktioniert ebenfalls auf einem virtuellen Computer nicht.
Z. B. Spiele oder Programme, die Verarbeitung mit GPUs erfordern (ohne Software fallback) funktionieren möglicherweise nicht gut.
Außerdem konnte Anträge auf Sub 10 ms Zeitgeber verlassen, wie latenzempfindliche Präzisions-apps, z. B. live Musik mischen von apps usw. Probleme, die auf einem virtuellen Computer ausgeführt haben.
Rootbetriebssystem auch über der Virtualisierungsebene Hyper-V ausgeführt wird, ist es jedoch spezielle, da er direkten Zugriff auf die gesamte Hardware hat.
Deshalb wird mit besonderen hardwareanforderungen weiterhin im Stammverzeichnis OS ungehindert jedoch latenzempfindliche, Präzisions-apps können immer noch Probleme im Stammverzeichnis Betriebssystem ausgeführt.

Zur Erinnerung müssen Sie eine gültige Lizenz für alle Betriebssysteme verfügen, die in den virtuellen Computern verwendet.

##Nächster Schritt:

[Exemplarische Vorgehensweise Hyper-V auf Windows 10](..\quick_start\walkthrough.md)


Auschecken [Neues](whats_new.md) in Hyper-V auf Windows-10.





