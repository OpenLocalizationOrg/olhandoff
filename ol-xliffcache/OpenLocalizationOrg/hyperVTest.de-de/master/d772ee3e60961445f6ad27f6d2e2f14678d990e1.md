MS. ContentId: D1D4969F-52FD-43A2-982B-B531B0343D2B 
Titel: Problembehandlung

#Problembehandlung bei Hyper-V auf Windows 10

##Ich 10 für Windows aktualisiert, und jetzt kann ich keine Verbindung zu meiner Downlevel-Host (Windows 8.1 oder Server 2012 R2)

In Windows-10 verschoben Hyper-V-Manager WinRM für die Remoteverwaltung.
Was also ist jetzt die Remoteverwaltung muss auf dem Remotehost aktiviert werden, um die Hyper-V-Manager verwenden, um ihn zu verwalten.

Weitere Informationen finden Sie unter [Remote Hyper-V-Hosts verwalten](remote_host_management.md)

##Den prüfpunkttyp geändert, aber dauert noch den falschen Typ des Prüfpunkts

Wenn den Prüfpunkt aus VMConnect werden, und Sie den Prüfpunkt in Hyper-V-Manager den Prüfpunkt ändern, werden Sie unabhängig Prüfpunkt beim Öffnen des VMConnect angegeben wurde.

Schließen Sie VMConnect und erneut öffnen Sie, damit er den richtigen Typ des Prüfpunkts ausführen wird.

##Wenn ich versuche, eine virtuelle Festplatte auf einem Flashlaufwerk erstellen, wird eine Fehlermeldung angezeigt.

Hyper-V unterstützt keine FAT/FAT32-formatierten Laufwerke, da diese Dateisysteme keine Zugriffssteuerungslisten (ACLs bieten) und Dateien, die größer als 4GB nicht unterstützt.
ExFAT formatierte Datenträgern nur begrenzte ACL-Funktionen bereitstellen und daher auch nicht unterstützt aus Sicherheitsgründen.
Die Fehlermeldung angezeigt, die in PowerShell ist "Fehler beim Erstellen ' \[path, VHD\]': der angeforderte Vorgang konnte aufgrund einer Beschränkung der Datei System (0x80070299) nicht abgeschlossen werden."

Verwenden einer NTFS formatierten Laufwerk stattdessen.


##Diese Meldung wird beim Versuch, zu installieren: "Hyper-V nicht installiert werden: der Prozessor second Level-Adressübersetzung (SLAT) nicht unterstützt."

Hyper-V erfordert SLAT, um die virtuellen Computer ausgeführt werden.
Wenn Sie den Computer SLAT nicht unterstützt, kann nicht es einem Host für virtuelle Mahchines sein.

Wenn Sie nur die Verwaltungstools installieren möchten, deaktivieren Sie **Hyper-V-Plattform** in **Programme und Funktionen** > **Windows-Funktionen ein- oder ausschalten**.




