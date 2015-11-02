MS. ContentId: 8DE9250B-556B-47BC-AD9A-8992B3D3D0F9
Titel: PowerShell-Ausschnitte

#PowerShell-Ausschnitte

Hinzufügen von diesem Satz für HO Kont Testverfahren.
PowerShell ist ein großartiger Skripting, Automatisierung und Verwaltungstool für Hyper-V.  Hier ist eine Toolbox zum Erkunden einiger neuen Dinge, die sie ausführen kann.

Alle Hyper-V-Verwaltung ausgeführt werden müssen als Administrator angenommen alle Skripts und Ausschnitte als Administrator über ein Administratorkonto mit Hyper-V ausgeführt werden müssen.

Wenn Sie nicht sicher, ob Sie die richtigen Berechtigungen verfügen, geben Sie `Get-VM` und wenn es ohne Fehler ausgeführt wird, sind Sie bereit.


##PowerShell-Direct-tools

Alle Skripts und Codeausschnitte in diesem Abschnitt wird auf den folgenden Grundlagen zu verlassen.

**Anforderungen** :


*  PowerShell Direct.
    Windows-10-Gast und Host-Betriebssystem.

**Allgemeine Variablen** :  
`$VMName` – Dies ist eine Zeichenfolge mit der VMName.
Eine Liste der verfügbaren virtuellen Maschinen mit `Get-VM`  
`$cred` -Anmeldeinformationen für das Gastbetriebssystem.
Ausgefüllt werden, die mit `$cred = Get-Credential`



###Überprüfen Sie, ob der Gast gestartet wurde

Hyper-V-Manager nicht Einblick in das Gastbetriebssystem, erhalten Sie dadurch häufig wird es schwierig herauszufinden, ob das Gastbetriebssystem gestartet wurde.

Verwenden Sie diesen Befehl zum Überprüfen, ob der Gast gestartet wurde.

``` PowerShell
if((Invoke-Command -VMName $VMName -Credential $cred {"Test"}) -ne "Test"){Write-Host "Not Booted"} else {Write-Host "Booted"}
```

**Ergebnis**  
Druckt eine Meldung, die den Status des Gastbetriebssystems deklarieren.


###Skript sperren, bis der Gast gestartet wurde

Die folgende Funktion verwendet das gleiche Prinzip erst, wenn PowerShell auf dem Gast steht (d. h. das Betriebssystem gestartet hat, und die meisten Dienste ausgeführt werden) wartet dann zurück.

``` PowerShell
function waitForPSDirect([string]$VMName, $cred){
   Write-Output "[$($VMName)]:: Waiting for PowerShell Direct (using $($cred.username))"
   while ((Invoke-Command -VMName $VMName -Credential $cred {"Test"} -ea SilentlyContinue) -ne "Test") {Sleep -Seconds 1}}
```

**Ergebnis**  
Druckt eine Meldung und sperren, bis die Verbindung mit dem virtuellen Computer erfolgreich ist.
Automatisch erfolgreich.

###Skript sperren, bis der Gast ein Netzwerk verfügt.

Mit PowerShell Direct ist es möglich, eine Verbindung mit einer PowerShell-Sitzung auf einem virtuellen Computer, bevor Sie den virtuellen Computer hat eine IP-Adresse empfangen.

``` PowerShell
# Wait for DHCP
while ((Get-NetIPAddress | ? AddressFamily -eq IPv4 | ? IPAddress -ne 127.0.0.1).SuffixOrigin -ne "Dhcp") {sleep -Milliseconds 10}
```

** Ergebnisses **
Sperren, bis eine DHCP-Lease empfangen wird.
Da dieses Skript nicht für ein bestimmtes Subnetz oder die IP-Adresse, sucht es funktioniert ganz gleich, welche Netzwerkkonfiguration verwenden Sie.
Automatisch erfolgreich.

##Verwalten von Anmeldeinformationen mit PowerShell

Hyper-V-Skripts erfordern häufig Anmeldeinformationen für eine oder mehrere virtuelle Maschinen, Hyper-V-Host oder beides.

Es gibt mehrere Methoden, die Sie dies erreichen können, bei der Arbeit mit PowerShell Direct oder standard-PowerShell-Remoting:

1. Die erste (und einfachste) Möglichkeit ist die gleichen Anmeldeinformationen, die in den Host und Gast oder lokale und remote-Host gültig sein.
    Dies ist recht einfach, wenn Sie sich mit Ihrem Microsoft-Konto - Protokollierung sind oder wenn Sie in einer domänenumgebung.
    In diesem Szenario können Sie einfach ausführen `Invoke-Command - VMName "Test" {Get-Process}`.
    
2. Lassen Sie PowerShell, die Sie zur Eingabe von Anmeldeinformationen  
    Wenn Sie Ihre Anmeldeinformationen nicht entsprechen, erhalten Sie automatisch eine administratoranmeldeaufforderung, sodass Sie die entsprechenden Anmeldeinformationen für den virtuellen Computer bereitstellen.
    
3. Speichern von Anmeldeinformationen in einer Variablen für die Wiederverwendung.
    Ausführen eines einfachen Befehls wie folgt:
    

  ``` PowerShell
  $localCred = Get-Credential
   ```
  And then running something like this:
  ``` PowerShell
  Invoke-Command -VMName "test" -Credential $localCred  {get-process} 
  ```
  Bedeutet, dass Sie nur einmal im Skript/PowerShell-Sitzung zum Eingeben Ihrer Anmeldeinformationen aufgefordert.

4. Codieren Sie Ihre Anmeldeinformationen in Ihre Skripts.
    **Keine tatsächlichen Arbeitslast oder system**
    > Warnung: _diesem nicht in einem Produktionssystem.
    > Tun Sie dies nicht mit der tatsächlichen Kennwörter. _
    
    Sie können übergeben ein PSCredential-Objekt mit einem Code wie folgt erstellen:
    

  ``` PowerShell
  $localCred = New-Object -typename System.Management.Automation.PSCredential -argumentlist "Administrator", (ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force) 
  ```
Bemessen unsichere- jedoch hilfreich beim Testen.
Jetzt können Sie keine Abfragen in dieser Sitzung.






