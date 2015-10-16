MS. ContentId: 95FE9554-3968-4EED-B65D-E03F06A7598D
Titel: Schritt 3: Erstellen eines virtuellen Switch

#Schritt 3: Erstellen eines virtuellen switch

Vor dem Erstellen eines virtuellen Computers in Hyper-V müssen Sie eine Möglichkeit für den virtuellen Computer für die Verbindung mit einem physischen Netzwerk bereitzustellen.
Hyper-V beinhaltet softwarebasierte networking-Technologie, die eine Netzwerkkarte virtuelle Computer für die Verbindung mit einem virtuellen Switch, ermöglicht die Bereitstellung von Netzwerkkonnektivität.
Jeder virtueller Switch in Hyper-V erstellt wurden, kann mit einem der drei Verbindungstypen konfiguriert werden:

- Externes Netzwerk – dem virtuellen Switch ist mit einem physischen Netzwerk angepasst verbunden, die Konnektivität zwischen dem physischen Netzwerk, Hyper-V-Hosts und der virtuelle Computer bereitstellt.
    In dieser Konfiguration können Sie auch die aktivieren oder Deaktivieren von Hosts können über die physische Verbindung zwischen Netzwerkkarte zu kommunizieren.
    Dies kann nur virtuelle Computer Datenverkehr an eine bestimmte physische Netzwerkkarte isolieren nützlich sein.
- Interne Netzwerk – dem virtuellen Switch ist nicht mit einem physischen Netzwerkadapter verbunden, jedoch die Netzwerkkonnektivität zwischen virtuellen Computern und Hyper-V-Host vorhanden ist.
- Privates Netzwerk – dem virtuellen Switch nicht mit einem physischen Netzwerkadapter verbunden ist und die Konnektivität zwischen virtuellen Computern und Hyper-V-Host nicht vorhanden.

In dieser exemplarischen Vorgehensweise wird das Arbeiten mit einem externen Netzwerk ausführlich.

##Manuelles Erstellen eines virtuellen Switch

In dieser Übung durchlaufen Sie erstellen einen virtuellen Switch mit Vollzugriff auf das Netzwerk-Konnektivität über die Hyper-V-Verwaltungstools.
Nach Abschluss der Hyper-V-Host enthält einen virtuellen Switch, die mit dem virtuelle Computer mit einem physischen Netzwerk verbunden werden kann.


1. Öffnen Sie den Hyper-V-Manager.
    
2. Der rechten Maustaste auf den Namen des Hyper-V-Hosts, und wählen Sie "Virtueller Switch-Manager".
    
3. Wählen Sie unter 'Virtuelle Switches' "Neues virtuelles Netzwerk-Switch" ein.
    
4. Wählen Sie unter "Erstellen virtueller Switch" externes"ein.
5. Wählen Sie die Schaltfläche "Virtuellen Switch erstellen".
    
6. Benennen Sie unter virtuelle Switch Eigenschaften dem neuen Schalter wie z. B. 'Externe VM Schalter'.
    
7. Unter "Verbindungstyp" Stellen Sie sicher, dass "Externes Netzwerk" ausgewählt wurde.
    
8. Wählen Sie die physische Netzwerkkarte, die mit dem neuen virtuellen Switch kombiniert werden kann, dies ist der Netzwerkkarte, die physisch mit dem Netzwerk verbunden ist.
    <br />![](media/newSwitch_upd.png)
    
9. Wählen Sie 'Anwenden', um den virtuellen Switch zu erstellen.
    An diesem Punkt sehen Sie wahrscheinlich die folgende Meldung, und klicken Sie auf 'Ja', um den Vorgang fortzusetzen.
    <br />![](media/pen_changes_upd.png)
    
10. Wählen Sie 'OK', um die virtuellen Switch-Manager-Fenster zu schließen.

##Erstellen eines virtuellen Switch mit PowerShell

Die folgenden Schritte können verwendet werden, um einen virtuellen Switch über eine externe Verbindung mithilfe von PowerShell zu erstellen.


1. Verwendung `Get-NetAdapter` zurückgeben eine Liste der Netzwerkadapter, der mit dem Windows-10-System verbunden.
    


    ```
    PS C:\> Get-NetAdapter

    Name                      InterfaceDescription                    ifIndex Status       MacAddress             LinkSpeed
    ----                      --------------------                    ------- ------       ----------             ---------
    Ethernet 2                Broadcom NetXtreme 57xx Gigabit Cont...       5 Up           BC-30-5B-A8-C1-7F         1 Gbps
    Ethernet                  Intel(R) PRO/100 M Desktop Adapter            3 Up           00-0E-0C-A8-DC-31        10 Mbps  
    ```

2. Wählen Sie den Netzwerkadapter mit dem Hyper-V-Schalter verwenden und eine Instanz in einer Variablen namens `$NetAdapter`.

    ```
    $net = Get-NetAdapter -Name 'Ethernet'
    ```

3.  Führen Sie den folgenden Befehl ein, um den neuen virtuellen Hyper-V-Switch zu erstellen.

    ```
    New-VMSwitch -Name "External VM Switch" -AllowManagementOS $True -NetAdapterName $net.Name
    ```

##Hinweise zum virtuellen Switches und Laptops:

Wenn Windows 10 Hyper-V auf einem Laptop sollten Sie berücksichtigen, erstellen einen virtuellen Switch für Ethernet und wireless-Karte ausgeführt wird.
Klicken Sie bei dieser Konfiguration, die Sie ändern können Ihre virtuellen Computer zwischen Thesen Switches auf dem Laptop abhängigen Netzwerk verbunden ist.
Virtuelle Computer wechselt nicht automatisch zwischen verkabelt und drahtlos.

##Nächster Schritt:

[Schritt 4: Erstellen einer virtuellen Windows-Maschine aus einer ISO-Datei](walkthrough_create_vm.md)




