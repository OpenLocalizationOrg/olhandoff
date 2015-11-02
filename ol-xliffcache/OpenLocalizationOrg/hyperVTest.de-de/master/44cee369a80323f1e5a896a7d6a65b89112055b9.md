MS. ContentId: C2593EA1-B182-4C71-8504-49691F619158
Titel: Schritt 1: Stellen Sie sicher, dass Ihr Computer kompatibel ist

##Betriebssystemkompatibilität

Hyper-V-Rolle kann nur in den Editionen Pro, Enterprise und Ausbildung von 10 für Windows installiert werden.
Wenn Sie die Homepage, Mobil oder Mobile Enterprise Edition von Windows 10 verwenden, kann Hyper-V-Rolle verwendet werden.
10 Home Edition kann auf Windows 10 Professional aktualisiert werden.
Dazu öffnen Sie die Einstellungen > Update und Sicherheit > Aktivierung.
Hier können Sie den Store besuchen und ein Upgrade erwerben.

##Hardwarekompatibilität

Während dieses Dokuments keine vollständige Liste der Hyper-V-kompatible Hardware bereitstellen, sind die folgenden Elemente erforderlich:

- 64-Bit-Prozessor mit Second Level-Adressübersetzung (SLAT).
- VM-Monitor-Modus-Erweiterung muss vorhanden sein.
- Mindestens 4 GB Arbeitsspeicher, doch da virtuelle Computer mit Hyper-V-Hosts dieser Arbeitsspeicher freigibt, Bereitstellen von ausreichend Arbeitsspeicher, um die erwartete virtuellen Arbeitslast zu bewältigen.

Die folgenden Elemente müssen im Bios aktiviert sein:
- Virtualisierung
    
- Datenausführungsverhinderung

##Prüfen der Hardwarekompatibilität

Um die Anwendungskompatibilität zu überprüfen, Öffnen von PowerShell oder eine Befehlszeile (cmd.exe), geben `systeminfo.exe`.
Dies gibt Informationen zur Kompatibilität von Hyper-V zurück.
Wenn alle Artikel aufgeführten Wert "Yes" kann Hyper-V-Rolle auf Ihrem System ausgeführt.
Wenn ein Element auf "Nein" zurückgibt, überprüfen Sie die in diesem Dokument aufgeführten Anforderungen und nehmen Sie Anpassungen vor, soweit möglich.

![](media/SystemInfo_upd.png)

##Vorhandene Hyper-V-Host

Wenn systeminfo.exe über einen vorhandenen Hyper-V-Host ausgeführt wird, liest der Anforderungen für Hyper-V-Abschnitt:

'''Hyper-V-Anforderungen: ein Hypervisor erkannt wurde.
Features erforderlich für Hyper-V nicht angezeigt werden. ""

##Nächster Schritt:

[Schritt 2: Installieren der Hyper-V](walkthrough_install.md)



