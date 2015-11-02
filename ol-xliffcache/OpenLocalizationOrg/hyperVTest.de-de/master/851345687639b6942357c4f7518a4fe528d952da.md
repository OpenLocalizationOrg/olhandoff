MS. ContentId: 52DAFFBE-40F5-46D2-96F3-FB8659581594 
Titel: Neues in Hyper-V für Windows 10

#Was ist neu in Hyper-V auf Windows 10

Dieses Thema erläutert die neue und geänderte Funktionen in Hyper-V auf 10 für Windows ®.

##Windows PowerShell Direct

Es ist nun eine einfache und zuverlässige Möglichkeit zum Ausführen von Windows PowerShell-Befehle in einem virtuellen Computer aus dem Hostbetriebssystem.
Es gibt keine Netzwerk- oder Firewall-Anforderungen oder eine spezielle Konfiguration.
Dies funktioniert unabhängig von der Konfiguration der remote-Verwaltung.
Verwenden möchten, müssen Sie Windows 10 oder Technical Preview für Windows Server, auf dem Host und das Gastbetriebssystem des virtuellen Computers ausführen.

Verwenden Sie zum Erstellen einer PowerShell-Direct-Sitzungs einen der folgenden Befehle aus:

``` PowerShell
Enter-PSSession -VMName VMName
Invoke-Command -VMName VMName -ScriptBlock { commands }
```

Heute verlassen sich Hyper-V-Administratoren auf zwei Kategorien von Tools für die Verbindung mit einer virtuellen Maschine auf dem Hyper-V-Host ein:
- Remote-Management-Tools wie PowerShell oder Remotedesktop
- Verbindung mit Hyper-V-Computer (VM-Verbindung)

Beide dieser Technologien funktionieren gut, aber jeder haben vor-und Nachteile, mit zunehmender Größe die Hyper-V-Bereitstellung.
VMConnect ist zuverlässig, aber es nur schwer zu automatisieren.
Remote-PowerShell ist leistungsstark, kann aber schwierig sein, Setup und verwalten.


Windows PowerShell Direct bietet eine leistungsfähige Skripting und Automatisierung mit der Einfachheit des VMConnect auftreten.
Da Windows PowerShell direkt zwischen dem Host und dem virtuellen Computer ausgeführt wird, braucht man nicht für eine Netzwerkschnittstelle oder remote-Verwaltung zu ermöglichen.
Sie benötigen die Gast-Anmeldeinformationen für den virtuellen Computer anzumelden.

####Anforderungen

- Sie müssen verbunden sein, zu einem Windows-10 oder Technical Preview für Windows Server-Host mit virtuellen Computern, die Windows-10 oder Technical Preview für Windows Server als Gäste ausgeführt werden.
- Sie müssen mit Hyper-V-Administratoranmeldeinformationen auf dem Host angemeldet sein.
- Benutzeranmeldeinformationen erforderlich für den virtuellen Computer.
- Der virtuelle Computer, die Sie herstellen möchten muss ausgeführt werden und gestarteten sein.


##Im laufenden Systembetrieb hinzufügen und Entfernen von für Netzwerkadapter und Speicher

Sie können jetzt hinzufügen oder Entfernen eines Netzwerkadapters, während der virtuelle Computer, ohne Ausfallzeiten ausgeführt wird.
Dies funktioniert für virtuelle Maschinen der Generation 2 unter Windows und Linux-Betriebssystemen.


Sie können auch anpassen, dass die Größe des Arbeitsspeichers zugewiesen an einen virtuellen Computer, während er ausgeführt wird, selbst wenn Sie Dynamic Memory aktiviert haben.
Dies funktioniert für die Generation 1 und Generation 2 virtuelle Computer.

##Produktion Prüfpunkte

Erzeugung von Prüfpunkten können Sie die einfache Erstellung von "point-in-Time" Images eines virtuellen Computers, die später so wiederhergestellt werden können, die für alle Produktionsarbeitslasten vollständig unterstützt wird.
Dies erfolgt mithilfe von backup im Gast-Technologie zum Erstellen des Prüfpunkts, anstelle von gespeicherten Zustand-Technologie.
Für die Erzeugung von Prüfpunkten wird der Volume Snapshot-Dienst (VSS) in Windows Virtual Machines verwendet.
Virtuelle Linux-Computer leeren ihre Dateisystem-Puffer um eine konsistente Datei System-Prüfpunkt zu erstellen.
Wenn Sie mithilfe der gespeicherten Zustand Technologie Prüfpunkte erstellen möchten, können Sie immer noch zur Verwendung von standard-Prüfpunkten für den virtuellen Computer auswählen.



> **Wichtig:** die Standardeinstellung für neue virtuelle Computer Produktion Prüfpunkte mit Fallback standard Prüfpunkte erstellt werden.
> 


##Verbesserung der Hyper-V-Manager

- **Alternative Anmeldeinformationen Unterstützung** – Sie können jetzt einen anderen Satz von Anmeldeinformationen im Hyper-V-Manager verwenden, beim Herstellen einer Verbindung mit einer anderen Windows 10 Technical Preview-Remotehost.
    Daher ist es einfacher, später anmelden, können Sie auch diese Anmeldeinformationen speichern.
    

- **Niedrigeren** – Sie können nun Hyper-V-Manager weitere Versionen von Hyper-V verwaltet werden.
    Mit Hyper-V-Manager in Windows 10: Technische Vorschau können Sie Computer mit Hyper-V auf Windows Server 2012, Windows 8, Windows Server 2012 R2 und Windows 8.1 verwalten.
    
- **Management-Protokoll aktualisiert** -Hyper-V-Manager wurde aktualisiert, um die Kommunikation mit remote Hyper-V-Hosts mithilfe des Protokolls WS-MAN, CredSSP, Kerberos oder NTLM-Authentifizierung erlaubt.
    Wenn Sie CredSSP für die Verbindung zu einem Remotehost für Hyper-V verwenden, können Sie eine live Migration ohne ersten Aktivierung eingeschränkte Delegierung in Active Directory durchzuführen.
    WS-MAN-basierten Infrastruktur vereinfacht außerdem die Konfiguration einen Host für die Remoteverwaltung aktivieren.
    WS-MAN eine Verbindung über Port 80, die standardmäßig geöffnet wird.


##Standby-Works verbunden

Wenn Hyper-V auf einem Computer aktiviert ist, das immer On/Always verbunden (AOAC) Power verwendet, ist der verbundenen Standbymodus Energiezustand jetzt verfügbar.

In Windows 8 und 8.1 verursacht Hyper-V-Computer, auf denen das immer On/Always verbunden (AOAC) Power-Modell (auch bekannt als InstantON) verwendet wird, niemals in den Ruhezustand.
Finden Sie unter diesem () [KB-Artikel]
https://support.Microsoft.com/en-US/KB/2973536) für eine vollständige Beschreibung.


##Sicherer Start Linux

Weitere Linux-Betriebssysteme auf virtuellen Maschinen der Generation 2, kann mit der sicheren Boot-Option aktiviert jetzt gestartet werden.
Ubuntu 14.04 und höher und SUSE Linux Enterprise Server 12 sind für den sicheren Start auf Hosts aktiviert, die die Technical Preview ausgeführt.
Bevor Sie den virtuellen Computer zum ersten Mal starten, müssen Sie angeben, dass der virtuelle Computer die Microsoft UEFI-Zertifizierungsstelle verwendet werden soll.
Geben Sie an einer Eingabeaufforderung mit Windows Powershell:

    Set-VMFirmware vmname -SecureBootTemplate MicrosoftUEFICertificateAuthority

Weitere Informationen zu virtuellen Linux-Computern auf Hyper-V ausgeführt wird, finden Sie unter [Linux und FreeBSD virtuellen Maschinen auf Hyper-V-](http://technet.microsoft.com/library/dn531030.aspx).


##Version der VM-Konfiguration

Beim Verschieben oder importieren ein virtuellen Computers auf einen Host mit Hyper-V auf Windows 10 von Windows 8.1-Host ist nicht die Konfigurationsdatei des virtuellen Computers automatisch aktualisiert.
Dadurch wird die virtuelle Maschine auf einem Host mit Windows 8.1 zurück verschoben werden soll.
Haben Sie keinen Zugriff auf neue Funktionen für virtuelle Computer, bis Sie die Version von Virtual Machine-Konfiguration manuell aktualisieren.


Konfigurationsversion der virtuellen Maschine darstellt, welche Version von Hyper-V-Konfiguration des virtuellen Computers gespeicherten Zustand und snapshot-Dateien, die mit kompatibel ist.
Virtuelle Computer mit Version 5 der Konfiguration sind kompatibel mit Windows 8.1 und kann unter Windows 8.1 und Windows 10 ausgeführt wird.
Virtuelle Computer mit Version 6 der Konfiguration sind kompatibel mit Windows 10 und nicht unter Windows 8.1 ausgeführt.

####Wie überprüfe ich die Konfigurationsversion der virtuellen Maschinen auf Hyper-V ausgeführt wird?

Führen Sie an einer Eingabeaufforderung mit erhöhten Rechten den folgenden Befehl aus:

``` PowerShell
Get-VM * | Format-Table Name, Version
```

####Wie aktualisiere ich die Konfigurationsversion eines virtuellen Computers?

Führen Sie ein Windows PowerShell-Eingabeaufforderung einen der folgenden Befehle:

``` PowerShell
Update-VmConfigurationVersion <vmname>
```

Oder

``` PowerShell
Update-VmConfigurationVersion <vmobject>
```


** Wichtig: **
- Nach der Aktualisierung der virtuellen Maschine Konfigurationsversion verschieben keine der virtuellen Maschine auf einem Host, die Windows 8.1 ausgeführt wird.
- Die Version von Virtual Machine-Konfiguration von Version 6 auf Version 5 kann nicht heruntergestuft werden.
- Sie müssen die virtuelle Maschine so aktualisieren Sie die Konfiguration des virtuellen Computers deaktivieren.
- Nach dem Upgrade verwendet die virtuelle Maschine im neuen Dateiformat für die Konfiguration.
    Weitere Informationen finden Sie unter neue virtuelle Maschine Konfigurationsdateiformat.


##Neue virtuelle Maschine Konfigurationsdateiformat

Virtuelle Computer verfügen jetzt über ein neues Format für Konfiguration vorgesehen ist, um die Effizienz des lesen und Schreiben von Konfigurationsdaten für die virtuelle Maschine zu erhöhen.
Dieses Konzept auch potenzielle Datenverluste verringern, wenn Speicherausfalls vorhanden ist.
Die neue Konfiguration Dateien der. VMCX-Erweiterung für die Konfigurationsdaten für die virtuellen Computer und die. VMRS-Erweiterung für die Daten über den Laufzeitzustand.



> **Wichtig:** der. VMCX-Datei ist ein binäres Format.
> Direktes Bearbeiten der. VMCX oder. VMRS Datei wird nicht unterstützt.



##Integrationsservices, die über Windows Update bereitgestellt

Updates für die Integrationsdienste für Windows-basierte Gäste werden jetzt über Windows Update verteilt.

Integrationskomponenten (auch als Integrationsdienste bezeichnet) handelt es sich um den Satz von synthetische Treiber, die einen virtuellen Computer für die Kommunikation mit dem Hostbetriebssystem zu ermöglichen.
Dienste, die von der Synchronisierung bis hin zu Gast Dateikopie steuern.
Wir haben im Gespräch wurde für Kunden Komponenteninstallation Integration und Update im vergangenen Jahr erkennen können, dass sie während der Aktualisierung ein häufiger Problempunkt sind.


In der Vergangenheit Lieferumfang in allen neue Versionen von Hyper-V-Integrationskomponenten neue.
Aktualisieren des Hyper-V-Hosts erforderlich, die Integrationskomponenten auf den virtuellen Computern auch aktualisieren.
Die neue Integrationskomponenten wurden mit dem Hyper-V-Host, und klicken Sie dann sie auf den virtuellen Computern mit vmguest.iso installiert wurden.
Dieser Prozess neu gestartet werden muss der virtuellen Maschine und konnte nicht mit anderen Windows-Updates nicht als Batch verarbeitet werden.
Da der Hyper-V-Administrator hatte, vmguest.iso und die Administratoren mussten sie installieren anzubieten, erforderlich, Aktualisierung der Integration der Hyper-V-Administrator über Administratoranmeldeinformationen verfügen in den virtuellen Computern – was nicht immer der Fall.
　　


Bearbeitet sowie andere wichtige Updates über Windows Update, Windows-10 und zukünftig alle Integration, Komponenten zu virtuell bereitgestellt werden.


Updates stehen für virtuelle Maschinen, heute verfügbar:
*  Windows Server 2012
*  Windows Server 2008 R2
*  Windows 8
*  Windows 7

Der virtuelle Computer muss Windows Update oder einem WSUS-Server verbunden sein.
In Zukunft müssen Komponentenupdates Integration eine Kategorie-ID in dieser Version, die sie als Knowledge Base-Artikel aufgelistet sind.

Weitere Informationen zu wie wir Anwendbarkeit ermitteln, finden Sie in diesem [Blogbeitrag](http://blogs.technet.com/b/virtualization/archive/2014/11/24/integration-components-how-we-determine-windows-update-applicability.aspx).


Finden Sie unter [diesen Blog](http://blogs.msdn.com/b/virtual_pc_guy/archive/2014/11/12/updating-integration-components-over-windows-update.aspx) eine ausführliche exemplarische Vorgehensweise für die Installation von Integrationsservices bereitstellen.


> **Wichtig:** der ISO-Abbild-Datei vmguest.iso wird zum Aktualisieren von Integrationskomponenten nicht mehr benötigt.
> Es ist nicht mit Hyper-V auf Windows 10 enthalten.




##Als Nächstes

[Durchlaufen von Hyper-V auf Windows 10](..\quick_start\walkthrough.md)




