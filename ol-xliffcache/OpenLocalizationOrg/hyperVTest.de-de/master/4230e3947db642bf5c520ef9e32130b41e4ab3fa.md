MS. ContentId: 34D5925A-D724-4552-9403-C2703A973234 
Titel: Migrieren und Aktualisieren von virtuellen Maschinen

#Migration und Aktualisierung von virtuellen Maschinen

Wenn Sie virtueller Maschinen auf Ihren Windows-10-Host, die ursprünglich mit Hyper-V in Windows 8.1 oder früher erstellt wurden verschieben, können Sie nicht die neuen Features von virtuellen Computern zu verwenden, bis Sie die Version von Virtual Machine-Konfiguration manuell aktualisieren.


Zum Aktualisieren der Version der Konfiguration der virtuellen Computer herunterfahren Sie, und wählen Sie Upgrade Konfiguration des virtuellen Computers im Hyper-V-Manager.
Sie können auch einen erhöhten Berechtigungen öffnen Windows PowerShell-Befehlszeile, und geben:


 '''PowerShell
Update-VmVersion <vmname> | <vmobject>
```



## How do I check the configuration version of the virtual machines running on Hyper-V? 

To find the configuration version, open an elevated Windows PowerShell command prompt, and run the following command:

**Get-VM * | Format-Table Name, Version**

The PowerShell command produces the following sample output:
```
Name Status CPUUsage(%) MemoryAssigned(M) Betriebszeit Status Version

Atlantis ausführen 0 1024 00:04:20.5910000 ordnungsgemäß 5.0

SGC VM ausführen 0 538 00:02:44.8350000 ordnungsgemäß 6.2
```


##Was geschieht, wenn ich nicht die Konfigurationsversion aktualisiere?

Wenn Sie virtuelle Computer, die Sie mit einer früheren Version von Hyper-V erstellt haben verfügen, funktionieren einige Funktionen nicht mit diesen virtuellen Computern, erst die VM-Version zu aktualisieren.

VM-Konfiguration Mindestversion für neue Features von Hyper-V:

| **Featurename**| **Mindestversion des virtuellen Computers**| |
| :------------------------------------- | -----------------: ||
| Speicher im laufenden Systembetrieb hinzufügen/entfernen| 6.0| |
| Hot-Hinzufügen/Entfernen von Netzwerkadaptern| 5.0| |
| Sicherer Start für virtuelle Linux-Computer| 6.0| |
| Produktion Prüfpunkte| 6.0| |
| PowerShell-Direct| 6.2| |
| Virtuelle Trusted Platform Module (vTPM)| 6.2| |
| Virtual Machine-Gruppierung| 6.2| |


##Version der VM-Konfiguration

Beim Verschieben oder importieren ein virtuellen Computers auf einen Host mit Hyper-V auf Windows 10 von Windows 8.1-Host ist nicht die Konfigurationsdatei des virtuellen Computers automatisch aktualisiert.
Dadurch wird die virtuelle Maschine auf einem Host mit Windows 8.1 zurück verschoben werden soll.
Haben Sie keinen Zugriff auf neue Funktionen für virtuelle Computer, bis Sie die Version von Virtual Machine-Konfiguration manuell aktualisieren.


Konfigurationsversion der virtuellen Maschine darstellt, welche Version von Hyper-V-Konfiguration des virtuellen Computers gespeicherten Zustand und snapshot-Dateien, die mit kompatibel ist.
Virtuelle Computer mit Version 5 der Konfiguration sind kompatibel mit Windows 8.1 und kann unter Windows 8.1 und Windows 10 ausgeführt wird.
Virtuelle Computer mit Version 6 der Konfiguration sind kompatibel mit Windows 10 und nicht unter Windows 8.1 ausgeführt.

Es ist nicht notwendig, alle virtuellen Computer gleichzeitig aktualisieren.
Sie können auch bestimmte virtuelle Computer bei Bedarf zu aktualisieren.
Sie wird nicht jedoch Zugriff auf neue virtuelle Maschine Funktionen haben, bis Sie die Version der Konfiguration für jeden virtuellen Computer manuell aktualisieren.




----------------

** Wichtige **

• Nach dem upgrade von der Version von Virtual Machine Configuration, nicht der virtuellen Maschine auf einem Host verschieben, die Windows 8.1 ausgeführt wird.

• Die Version von Virtual Machine-Konfiguration von Version 6 auf Version 5 heruntergestuft werden kann nicht.

• Sie müssen die virtuelle Maschine so aktualisieren Sie die Konfiguration des virtuellen Computers deaktivieren.

• Nach der Aktualisierung der virtuellen Maschine verwendet das neue Dateiformat für die Konfiguration.
Weitere Informationen finden Sie unter neue virtuelle Maschine Konfigurationsdateiformat.

--------






##Was geschieht, wenn ich eine virtuelle Maschine aktualisieren?

Wenn Sie manuell ein upgrade die Konfigurationsversion eines virtuellen Computers auf Version 6.x, ändern Sie die Dateistruktur, die zum Speichern der virtuellen Maschinen Konfigurations- und Prüfpunkt-Dateien verwendet wird.


Aktualisierte virtuelle Computer verwenden Sie ein neues Configuration-Dateiformat, das entwickelt wurde, um die Effizienz des lesen und Schreiben von Konfigurationsdaten für die virtuelle Maschine zu erhöhen.
Das Upgrade wird auch potenzielle Datenverluste im Falle eines Speicherausfalls reduziert.


Die folgende Tabelle enthält die Speicherorte der Binärdatei und Erweiterungsinformationen für einen aktualisierten virtuellen Computer.



| **Konfiguration und Prüfpunkt-Dateien für virtuelle Maschinen (Version 6.x)**| **Beschreibung**| |
|:---------------|:----------------||
| **Konfiguration des virtuellen Computers**| Konfigurationsinformationen werden in einem binären Format gespeichert, die die Erweiterung .vmcx verwendet.| |
| **Laufzeitstatus des virtuellen Computers**| Daten über den Laufzeitzustand werden in einem binären Format gespeichert, die die Erweiterung .vmrs verwendet.| |
| **Virtuelle Festplatte in Virtual machine**| Die Dateien der virtuellen Festplatte für die virtuelle Maschine.Sie verwenden die VHD- oder vhdx-Datei-Erweiterungen.| |
| **Automatische virtuelle Festplattendateien**| Die differenzierende Datenträgerdateien für die Prüfpunkte für virtuelle Maschinen verwendet.Sie verwenden die .avhdx Dateierweiterungen.| |
| **Prüfpunktdateien**| Prüfpunkte werden in mehreren Prüfpunktdateien gespeichert.Jedem Prüfpunkt erstellt eine Konfigurationsdatei und die Datei der Common Language Runtime-Zustand.Prüfpunktdateien verwenden die Dateierweiterungen .vmrs und .vmcx.Diese neue Dateiformate sind auch für die Produktion Prüfpunkte und standard-Prüfpunkte verwendet.| |
Nach dem upgrade der Konfigurations des virtuellen Computers nach Version 6.x, es ist nicht möglich, downgrade von Version 6.x zur Version 5.


So aktualisieren Sie die Konfiguration des virtuellen Computers muss der virtuelle Computer deaktiviert werden.

Die folgende Tabelle enthält die standardmäßigen Dateispeicherorte für neue oder aktualisierte virtuelle Computer.

| **Dateien für virtuelle Maschinen (Version 6.x)**| **Beschreibung**| |
|:-----|:-----||
| **Konfigurationsdatei der virtuellen Maschine**| C:\ProgramData\Microsoft\Windows\Hyper-V\Virtual Computer| |
| **Datei des virtuellen Computers Runtime Status**| C:\ProgramData\Microsoft\Windows\Hyper-V\Virtual Computer| |
| **Prüfpunktdateien (.vmrs, .vmcx)**| C:\ProgramData\Microsoft\Windows\Snapshots| |
| **Virtuelle Festplattendatei (.vhd/.vhdx)**| C:\Users\Public\Documents\Hyper-V\Virtual-Festplatten| |
| **Automatische virtuelle Festplattendateien (.avhdx)**| C:\Users\Public\Documents\Hyper-V\Virtual-Festplatten| |







