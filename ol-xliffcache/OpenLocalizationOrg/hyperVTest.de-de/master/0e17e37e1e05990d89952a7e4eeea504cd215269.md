MS. ContentId: A6DD6776-614C-4D28-9B83-CB2EDFD263A3
Titel: Schritt 2: Installieren von Hyper-V auf Windows-10

#Schritt 2: Installieren der Hyper-V auf Windows 10

Bevor Sie virtuelle Maschinen auf Windows 10 verwenden können, müssen Sie die Hyper-V-Rolle.
Dies kann mithilfe der Windows-10 GUI-Schnittstelle, PowerShell oder DISM.
Diese Dokumente werden durch jede dieser geführt.

##Aktivieren Sie Hyper-V über die GUI

1. Klicken Sie mit der rechten Maustaste auf die Windows-Schaltfläche, und wählen Sie "Programme und Funktionen".
    
2. Wählen Sie "Windows-Funktionen ein- oder ausschalten".
    
3. Wählen Sie "Hyper-V", und klicken Sie auf "OK".
    <br />![](media/enable_role_upd.png)
    
4. Nach Abschluss die Installation werden Sie aufgefordert, den Computer neu starten.
    <br />![](media/restart_upd.png)

##Aktivieren Sie Hyper-V mit PowerShell

1. Öffnen Sie eine PowerShell-Konsole als Administrator an.
    
2. Geben Sie den folgenden Befehl aus:

`Enable-WindowsOptionalFeature-Online - FeatureName Microsoft Hyper-V – alle`

Nach Abschluss die Installation müssen Sie den Computer neu starten.

##Hyper-V mit DISM zu aktivieren.

Deployment Image Servicing and Management Tools oder DISM wird zum Warten von Windows-Abbildern und Vorbereiten von Windows vor der Installation Evironments.
DISM kann auch verwendet werden, zum Aktivieren von Windows-Features in Instanzen des Betriebssystems ausgeführt wird.

So aktivieren Sie die Hyper-V-Rolle mithilfe von DISM

1. Öffnen Sie ein PowerShell oder CMD-Sitzung als Administrator.
    
2. Geben Sie den folgenden Befehl ein:

`DISM / Online/Enable-Feature-all /FeatureName:Microsoft-Hyper-V`

Wenn Sie fertig werden Sie aufgefordert, neu zu starten.

![](media/dism_upd.png)


##Als Nächstes

[Schritt 3: Erstellen eines virtuellen switch](walkthrough_virtual_switch.md)




