MS. ContentId: 8D89E9D8-2501-46A7-9304-2F19F37AFC85
Titel: Arbeiten mit Prüfpunkten

#Verwenden von Prüfpunkten, virtuelle Computer in einem früheren Zustand wiederherzustellen.

Hinzufügen von diesem Satz für HO Kont Testverfahren.
Prüfpunkte bieten eine schnelle und einfache Möglichkeit, den virtuellen Computer in einem früheren Zustand wiederherzustellen.
Dies ist besonders hilfreich, wenn Sie zu einer virtuellen Maschine ändern und Sie in der Lage, um den aktuellen Status zurücksetzen, wenn die Ursache von Problemen ändern möchten.


##Aktivieren oder Deaktivieren von Prüfpunkten

1.  In **Hyper-V-Manager**, mit der rechten Maustaste auf den Namen des virtuellen Computers, und klicken Sie auf **Settings**.
2.  In der **Management** Abschnitt **Prüfpunkte**.
3.  Damit können Prüfpunkte, die aus diesem virtuellen Computer ausgeführt werden, stellen Sie sicher, dass Sie Prüfpunkte aktivieren auswählen--ist dies das Standardverhalten.
    Um Prüfpunkte zu deaktivieren, deaktivieren Sie die **Prüfpunkte aktivieren** Kontrollkästchen.
4.  Klicken Sie auf **Übernehmen** um die Änderungen zu übernehmen.
    Wenn Sie fertig sind, klicken Sie auf **OK** um das Dialogfeld zu schließen.


##Wählen Sie die Standard- oder Produktion Prüfpunkte

Es gibt zwei Typen von Prüfpunkten:
*  **Produktion Prüfpunkte** – vor allem auf Servern in produktionsumgebungen als eine Form der Sicherung verwendet.
*  **Standard Prüfpunkte** – in der Entwicklung oder Tests Umgebungen zum Rollback durchführen zu können, wenn eine Änderung fehlschlägt.
    

Beide Typen von Prüfpunkten stellen einen virtuellen Computer in einem früheren Zustand wieder her.

Produktion Prüfpunkte erstellen einen anwendungskonsistente Prüfpunkt eines virtuellen Computers.
Das bedeutet, dass der gespeicherte virtuelle Computer ohne Status der Anwendung fortgesetzt wird.



Standard (früher als Snapshots bezeichnet) Prüfpunkte erfassen den genauen Speicherzustand des virtuellen Computers.
Das bedeutet, dass der virtuelle Computer wird mit restore **genau** den gleichen Zustand, in dem der Prüfpunkt nach unten mit den genauen Anwendungszustand erstellt wurde.
Standard-Prüfpunkte enthalten möglicherweise Informationen über Clientverbindungen, Transaktionen und den Status des externen Netzwerks.
Diese Informationen können nicht gültig sein, wenn der Prüfpunkt angewendet wird.
Darüber hinaus werden ein Prüfpunkt bei einem Absturz der Anwendung erstellt wird, diesen Prüfpunkt wiederherstellen in der Mitte, Abstürze.

Das Vorhandensein eines standard-Prüfpunkts für eine virtuelle Maschine kann die Leistung der Festplatte des virtuellen Computers auswirken.
Wir empfehlen nicht standard Prüfpunkte für virtuelle Computer verwenden, bei der Leistung oder die Verfügbarkeit von Speicherplatz wichtig ist.


Anwenden eines Prüfpunkts Produktion umfasst, starten das Gastbetriebssystem von Offlinestatus.
Dies bedeutet, dass keine Anwendung Zustand und Sicherheitsinformationen im Rahmen der Checkpoint-Prozess erfasst wird.


Die folgende Tabelle zeigt die Verwendung von Prüfpunkten Produktion oder standard-Prüfpunkte, abhängig vom Status des virtuellen Computers.

| **Status der virtuellen Maschine**| **Produktion Prüfpunkt**| **Standard-Prüfpunkt**|
|:-----|:-----|:-----|
| **Ausführen von Integration Services**| Ja| Ja|
| **Ohne Integrationsservices ausgeführt wird**| Nein| Ja|
| **Offline – keine gespeicherten Zustand**| Ja| Ja|
| **Offline – mit gespeicherten Zustand**| Nein| Ja|
| **Angehalten**| Nein| Ja|
Um den Unterschied zwischen Standard- und Produktion Prüfpunkte anzuzeigen, sehen Sie sich die [Prüfpunkte Exemplarische Vorgehensweise](../quick_start/walkthrough_checkpoints.md).

##Legen Sie einen Standardtyp für den Prüfpunkt

1.  In **Hyper-V-Manager**, mit der rechten Maustaste auf den Namen des virtuellen Computers, und klicken Sie auf **Settings**.
2.  In der **Management** Abschnitt **Prüfpunkte**.
3.  Wählen Sie Produktion Prüfpunkte oder standard-Prüfpunkte.
    Wenn Sie Prüfpunkte Produktion auswählen, können Sie auch angeben, ob der Host einen standard-Prüfpunkt ausgeführt werden soll, wenn ein Prüfpunkt für die Produktion geschaltet werden kann.
    Wenn Sie dieses Kontrollkästchen deaktivieren und ein Prüfpunkt für die Produktion nicht ausgeführt werden kann, wird kein Prüfpunkt ausgewählt.
4.  Wenn Sie den Speicherort ändern, in dem die Konfigurationsdateien für den Prüfpunkt gespeichert werden, soll, ändern Sie den Pfad in der **Prüfpunkt Dateispeicherort** Abschnitt.
5.  Klicken Sie auf **Übernehmen** um die Änderungen zu übernehmen.
    Wenn Sie fertig sind, klicken Sie auf **OK** um das Dialogfeld zu schließen.

Das Standardverhalten in Windows 10 für neue virtuelle Computer ist die Erstellung von Produktion Prüfpunkte zu standard-Prüfpunkte


##Erstellen eines Prüfpunkts

So erstellen Sie einen Prüfpunkt
1.  In **Hyper-V-Manager**, unter **virtuellen Maschinen**, wählen Sie den virtuellen Computer.
2.  Mit der rechten Maustaste in des Namens des virtuellen Computers, und klicken Sie dann auf **Prüfpunkt**.
3.  Wenn der Prozess abgeschlossen ist, wird der Prüfpunkt unter angezeigt **Prüfpunkte** in den **Hyper-V-Manager**.
    


##Anwenden eines Prüfpunkts

Wenn Sie den virtuellen Computer zu einem vorherigen Point-in-Time wiederherstellen möchten, können Sie einen vorhandenen Prüfpunkt anwenden.

1.  In **Hyper-V-Manager**, unter **virtuellen Maschinen**, wählen Sie den virtuellen Computer.
2.  Der Abschnitt Prüfpunkte mit der rechten Maustaste des Prüfpunkts aus, die Sie verwenden möchten und klicken Sie auf **Übernehmen**.
3.  Ein Dialogfeld mit den folgenden Optionen:
    

``` 
**Create Checkpoint and Apply**: Creates a new checkpoint of the virtual machine before it applies the earlier checkpoint. 

**Apply**: Applies only the checkpoint that you have chosen. You cannot undo this action.

**Cancel**: Closes the dialog box without doing anything.
```

##Löschen eines Prüfpunkts

So löschen Sie einen Prüfpunkt ordnungsgemäß:


1.  In **Hyper-V-Manager**, wählen Sie den virtuellen Computer.
2.  In der **Prüfpunkte** im Abschnitt mit der rechten Maustaste in des Prüfpunkts aus, die Sie löschen möchten, und klicken Sie auf Löschen.
    Sie können auch einen Prüfpunkt und alle nachfolgenden Prüfpunkte löschen.
    Zu diesem Zweck Maustaste den frühesten Prüfpunkt, die Sie verwenden möchten, löschen, und klicken Sie dann auf **** Löschen Prüfpunkt** Unterstruktur **.
3.  Sie u. u. Vergewissern Sie sich, dass den Prüfpunkt gelöscht werden soll.
    Vergewissern Sie sich, dass sie die richtige Prüfpunkt ist, und klicken Sie dann auf **Löschen**.
    
4.  Die .avhdx und vhdx-Dateien werden zusammengeführt, und nach Abschluss des Vorgangs wird die .avhdx-Datei aus dem Dateisystem gelöscht werden.
    

> **Tipp:** können Sie Windows Powershell verwenden, um einen Prüfpunkt gelöscht, indem die **Remove-VMSnapshot** Cmdlet.
> 

Prüfpunkte werden als .avhdx-Dateien in demselben Speicherort wie die vhdx-Dateien für den virtuellen Computer gespeichert.
Sie sollten die .avhdx-Dateien nicht direkt löschen.


##Ändern des Prüfpunkts Einstellungen und Speichern des Zustands, die Dateien gespeichert sind

Wenn der virtuelle Computer keine Prüfpunkte verfügt, können Sie ändern, wo die Prüfpunkt-Konfiguration und die Dateien mit dem gespeicherten Zustand gespeichert werden.

1.  In **Hyper-V-Manager**, mit der rechten Maustaste auf den Namen des virtuellen Computers, und klicken Sie auf **Settings**.
    
2.  In der **Management** Abschnitt **Prüfpunkte** oder **Prüfpunkt Dateispeicherort**.
    
4.  In **Prüfpunkt Dateispeicherort**, geben Sie den Pfad zu dem Ordner, in dem Sie die Dateien speichern möchten.
    
5.  Klicken Sie auf **Übernehmen** um die Änderungen zu übernehmen.
    Wenn Sie fertig sind, klicken Sie auf **OK** um das Dialogfeld zu schließen.

Der Standardspeicherort für das Speichern von Konfigurationsdateien Prüfpunkt ist: % systemroot%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots.




##Umbenennen eines Prüfpunkts

1.  In **Hyper-V-Manager**, wählen Sie den virtuellen Computer.
2.  Mit der rechten Maustaste in des Prüfpunkts aus, und wählen Sie **Umbenennen**.
3.  Geben Sie den neuen Namen für den Prüfpunkt.
    Es muss weniger als 100 Zeichen sein, und das Feld darf nicht leer sein.
4.  Klicken Sie auf **EINGABETASTE** Wenn Sie fertig sind.

Standardmäßig ist der Name eines Prüfpunkts der Name des virtuellen Computers in Kombination mit dem Datum und die Uhrzeit der Prüfpunkt erstellt wurde.
Dies ist das Standardformat:


```
virtual_machine_name (MM/DD/YYY –hh:mm:ss AM\PM)
```

Namen sind maximal 100 Zeichen lang sein, und der Name darf nicht leer sein.







