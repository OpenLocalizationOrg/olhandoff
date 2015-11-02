MS. ContentId: 7561B149-A147-4F71-9840-6AE149B9DED5
Titel: unterstützte Windows-Gastbetriebssysteme


#Unterstützte Windows-Gäste

Dieser Artikel enthält die Windows-Betriebssysteme als Gäste in Hyper-V unter Windows unterstützt, sowie Informationen über Integrationsservices.


> Windows-10 wird als Gast-Betriebssystem auf Windows 8.1 und Windows Server 2012 R2 Hyper-V-Hosts.

##Was bedeutet unterstützt?

Unterstützung bedeutet, dass dieser Host/Gast-Kombinationen von Microsoft getestet wurde.
Probleme mit diesen Kombinationen möglicherweise Aufmerksamkeit von Product Support Services.

Microsoft bietet Unterstützung für Gastbetriebssysteme auf folgende Weise:
* Der Microsoft-Support hilft beim Lösen von Problemen in Microsoft-Betriebssystemen und -Integrationsdiensten.
* Für Probleme in anderen Betriebssystemen, die vom Anbieter des Betriebssystems für die Ausführung unter Hyper-V zertifiziert wurden, wird der Support vom Anbieter geleistet.
* Informationen zu Problemen, die in anderen Betriebssystemen gefunden werden, sendet Microsoft das Problem mit der Community Unterstützung verschiedener Hersteller [TSANet](http://www.tsanet.org/).

##Was sind die Integrationsdienste, und warum sind sie wichtig?

Hyper-V umfasst die Integrationsdienste für unterstützte Gastbetriebssysteme.
Integrationsservices verbessern die Interaktion zwischen dem Hostsystem und dem virtuellen Computer.



Einige Betriebssysteme (einschließlich der verschiedene Versionen von Windows) haben den Integrationsservices integriert, während andere Integrationsservices über Windows Update zur Verfügung stellen.

##Unterstützte Gastbetriebssysteme für Windows Server

Windows-10-Hyper-V-Hosts:


| Gastbetriebssystem| Maximale Anzahl virtueller Prozessoren| Integration Services| Hinweise| |
| -----                                | -----                                     | -----                     | -----     | ----- |
| Windows Server Technical Preview| 64| Integrierte| | | |
| Windows Server 2012 R2| 64| Integrierte| | | |
| Windows Server 2012| 64| Integrierte| | | |
| Windows Server 2008 R2 mit Service Pack 1 (SP 1)| 64| Installieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| Datacenter, Enterprise, Standard und Web Edition.| |
| Windows Server 2008 mit Service Pack 2 (SP 2)| 4| Installieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| Datacenter, Enterprise, Standard und Web Edition (32-Bit und 64-Bit).| |
| Windows Home Server 2011| 4| Installieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| |
| Windows Small Business Server 2011| Essentials Edition - 2, Standard Edition - 4| Installieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| Essentials und Standard Edition.| |

##Unterstützte Windows-Gastbetriebssysteme

Windows-10-Hyper-V-Hosts:

| Gastbetriebssystem| Maximale Anzahl virtueller Prozessoren| Integrationsservice| Hinweise| |
| ----- | ----- | ----- | ----- | ----- |
| Windows-10| 32| Integrierte| | |
| Windows 8.1| 32| Integrierte| | |
| Windows 8| 32| Aktualisieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| | |
| Windows 7 mit Service Pack 1 (SP 1)| 4| Aktualisieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| Ultimate, Enterprise und Professional Edition (32-Bit und 64-Bit).| |
| Windows 7| 4| Aktualisieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| Ultimate, Enterprise und Professional Edition (32-Bit und 64-Bit).| |
| Windows Vista mit Service Pack 2 (SP2)| 2| Installieren Sie die Integrationsdienste, nachdem Sie das Betriebssystem auf dem virtuellen Computer eingerichtet haben.| Business, Enterprise und Ultimate einschließlich N- und KN-Editionen.| |
 Windows-10 ist ein Gastbetriebssystem auf Windows 8.1 und Windows Server 2012 R2 Hyper-V-Hosts.

##Linux und kostenlose BSD

Windows-10-Hyper-V-Hosts:

| Gastbetriebssystem| |
| -----|------|
| [CentOS und Red Hat Enterprise Linux ](https://technet.microsoft.com/library/dn531026.aspx)| |
| [Debian virtuelle Computer in Hyper-V](https://technet.microsoft.com/library/dn614985.aspx)| |
| [SUSE](https://technet.microsoft.com/en-us/library/dn531027.aspx)| |
| [Oracle Linux](https://technet.microsoft.com/en-us/library/dn609828.aspx)| |
| [Ubuntu](https://technet.microsoft.com/en-us/library/dn531029.aspx)| |
| [FreeBSD](https://technet.microsoft.com/library/dn848318.aspx)| |
Vorsichtsmaßnahmen, um bestimmte Kernel-Versionen sind.
Weitere Informationen, einschließlich Supportinformationen zu früheren Versionen von Hyper-V, finden Sie unter [Linux und FreeBSD virtuellen Maschinen auf Hyper-V-](https://technet.microsoft.com/library/dn531030.aspx).




