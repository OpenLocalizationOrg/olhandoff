MS. ContentId: 3C63F9A8-30E4-40F4-BC7B-A001C1E90779
Titel: Schritt 4: erstellen eine virtuellen Windows-Maschine aus einer ISO-Datei

#Schritt 4: Erstellen einer virtuellen Windows-Maschine aus einer ISO-Datei

Für diesen Schritt Wenn bereits eine .iso-Datei für einen unterstützten 64-Bit-Betriebssystem können, das Sie.
Wenn nicht, Sie, die ISO für herunterladen können [Windows 8.1 Enterprise](http://www.microsoft.com/en-us/evalcenter/evaluate-windows-8-1-enterprise) und wählen Sie die 64-Bit-Edition.


1. Klicken Sie im Hyper-V-Manager auf den **Aktion** Menü > **Neu** > **Virtual Machine**.
    
2. Stellen Sie in der Virtual Machine-Assistenten die folgenden Optionen:
    
    <table>
    <tr><th>erweitert?“</th><th>Eintrag</th></tr>
    <tr><td>Name:</td><td>Geben Sie im <b>Exemplarische Vorgehensweise Windows-VM</b></td></tr>
    <tr><td>Generation:</td><td><b>Zweite Generation</b></td></tr>
    <tr><td>Arbeitsspeicher beim Start:</td><td><b>1024</b> und lassen Sie dynamischen Arbeitsspeicher aktiviert</td></tr>
    <tr><td>Konfigurieren Sie Netzwerk:</td><td><b>Extern</b> (Dies ist der virtuelle Switch, den Sie in Schritt 3 erstellt haben.)</td></tr>
    <tr><td>Verbinden Sie virtuelle Festplatte:</td><td><b>Erstellen einer virtuellen Festplatte</b> (halten Sie die anderen Standardwerte) </td></tr>
    <tr><td>Installationsoptionen:</td><td><b>Installieren Sie ein Betriebssystem von einer startbaren CD/DVD-ROM</b>. Klicken Sie unter <b>Medien</b>, wählen Sie <b>Abbilddatei (Iso)</b> und klicken Sie dann auf <b>Durchsuchen</b> die ISO-Datei auf.</td></tr>
    </table>
    
3. Wenn alles wie gewünscht aussieht, klicken Sie auf **Fertig stellen**.
    

> **Hinweis:** Wenn Sie nur 32-Bit-Version von Windows haben, müssen Sie auf Generation 1 in der **Generation** Abschnitt des Assistenten.
> VMs Generation 2 unterstützen nur 64-Bit-Betriebssysteme.

##Nächster Schritt:

[Schritt 5: Herstellen einer Verbindung mit dem virtuellen Computer, und schließen Sie die installation](walkthrough_vmconnect.md)





