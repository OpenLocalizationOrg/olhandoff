Übersicht über die Implementierung von .NET
===========================================

.NET Plattform ist im Kern sehr einen Satz von Standards, die sein kann
implementiert.
Es gibt verschiedene Implementierungen, einige stammt
Microsoft einige von anderen Unternehmen und Gruppen.
Dieses Dokument
Beschreibt den aktuellen Status des Ökosystems von .NET und die verschiedenen
Implementierungen, sodass Sie eine gute "lay Boden" zugreifen können.

.NET Core
=========

.NET Core ist eine Cloud optimierte und plattformübergreifende Implementierung der
.NET Plattform.
Es unterstützt gegenwärtig drei Haupt-Betriebssysteme:
Linux, Windows und OS X.

Es gibt mehrere Gründe, warum wir .NET Core erstellt.

**Plattformübergreifende Unterstützung** ist eine Voraussetzung für viele Entwickler noch heute.
Es ist wichtig, die Plattform verwenden, die über die erforderlichen Eigenschaften verfügt
von der Anwendung, die wiederum auf die erforderliche Plattform ausgeführt werden kann
Benutzer oder vielleicht ist durch die Unternehmensrichtlinie vorgeschrieben.
Für alle diese wir
benötigen Sie eine plattformübergreifende-Laufzeit.

**Open Source** da es erwiesen hat die beste Möglichkeit,
Aktivieren Sie eine größere Anzahl von Plattformen, die von der Community Beitrag unterstützt.

**Bessere Verpackung Story** der gesamten Laufzeit ist auch etwas,
beeinflusst den Entwurf der Laufzeit.
Wir wollten sicherstellen, dass die
gesamte Laufzeit kann als eine Reihe von Teilen der verteilt werden, die Entwickler können
Wählen Sie aus aus, anstatt eine einzelne monolithische Plattform.
.NET
Kern ist die erste Implementierung der .NET Plattform, die
über verteilte [NuGet](http://www.nuget.org/) -Paket-Manager.

**Bessere Isolierung und Versionskontrolle** gehörte zu den Einflussfaktoren erstellen
.NET Core.
Aktuelle Trends in Entwicklungsverfahren dazu führen, dass ein sehr
Entwickeln von Software als Was wurde auch ein paar neue Weise
vor Jahren.
Cloud-Dienste dann folgt radikal ändern der Darstellung
Entwickler erstellen, testen und ihre Projektmappen ausführen.
Anwendungscontainer
wie neue Möglichkeiten und Chancen Docker einführen, wenn sie
Konsolidierung von Server (und Services) stammt.
In diesem Sinn die
.NET Core bildet die Szenarien, in denen die Anwendung im Wesentlichen
"akzeptiert" die Laufzeit mit.
Dies ermöglicht die app-versioning
Szenario; der Entwickler muss nur die Common Language Runtime (eine Gruppe von Gedanken
Pakete, wie im vorherigen Absatz), hat die Anwendung abhängig ist.
auf.

Alle oben genannten .NET Core stellt eine sehr allgemeine dar.
Plattformübergreifende und moderne Runtime, die mehrere unterstützen kann
Arbeitslasten mit Cloud-Diensten auf desktopanwendungen CLI-Tools.

.NET Framework
==============

.NET Framework ist die wichtigste Implemetentation der
für WindowsServer und Client-Entwickler verfügbar.
Es ist ein sehr
leistungsstarke, höchst ausgereifter Framework mit einer großen Klassenbibliothek (bekannt als die
**Framework-Klasse Librariries**) unterstützt eine Vielzahl von
Clientanwendungen und Lösungen unter Windows.

Es gibt zusätzliche Stapel nach oben .NET Framework erstellt, mit denen
Entwickler von konsolenanwendungen bis hin zu erstellen,
Anwendungsübergreifende rich-Client (WPF), skalierbare von ASP.NET-Webanwendungen.

[Windows
Formulare] (https://msdn.microsoft.com/en-us/library/dd30h2yb (v=vs.110).aspx)
und [Windows Presentation Foundation
(WPF)] (https://msdn.microsoft.com/en-us/library/ms754130 (v=vs.110).aspx)
werden zwei Stapel der Benutzeroberfläche (UI), die Sie zum Erstellen von Desktop zulassen
Anträge auf Windows-Betriebssystem.
Windows Forms Sicherheit ist in
die umfassende Unterstützung für häufig verwendete Databinding sowie Zugriff auf Windows
systemeigene Steuerelemente der Benutzeroberfläche.
WPF ermöglicht andererseits,
Üben Sie wesentlich mehr Kontrolle über das Aussehen und Verhalten Ihrer Anwendung.
Beide Eigenschaften können zum Erstellen von umfangreichen desktop-Anwendung, die ausgeführt werden
unter Windows und wählen Sie diejenige, die geeignet ist für Ihre Verwendung
Fall.

[Windows Communication Foundation
(WCF)] (https://msdn.microsoft.com/en-us/library/ms731082 (v=vs.110).aspx)
ist ein Satz von Bibliotheken, die den Middleware-Services-Stapel auf umfassen
.NET Framework.
Sie können zum Erstellen von Diensten, die kommunizieren können
über die verschiedenen unterstützten Protokolle mit verschiedenen Datenformaten und
kann es sich um Hoster in jeden beliebigen Prozess sein, die Sie auswählen.
Dies führt zu einem wichtigen
Features von WCF: Ihre Dienste sind nicht an bestimmten hosting gebunden
Strategie oder einen anderen Ansatz.

**ASP.NET** Web .NET Framework ist.
Ein sehr umfangreiches Framework, wird es
bestehen aus mehreren unterschiedliche Teilen, die verwendet werden, um moderne zu erzeugen und
hohe Leistung von ASP.NET-Webanwendungen.
[ASP.NET Web
Forms](http://www.asp.net/web-forms) ist ein Satz von Tools, die in erster Linie ausgerichtet
für die Entwicklerproduktivität, ermöglicht die schnelle Abwicklung Web
Clientanwendungen mit Drag & Drop-Oberfläche Websteuerelemente für die Wiederverwendung
Alles von Dienstbetrieb vermittelt in an Daten binden.
[ASP.NET
MVC](http://www.asp.net/mvc) für einen anderen Ansatz ermöglicht eine,
ermöglicht Ihnen größere Kontrolle über die gesamte Pipeline von HTTP-Ebene
die Benutzeroberfläche.
[ASP.NET WebAPI](http://www.asp.net/web-api) ist ein
auf Konventionen basierendes Framework zum Erstellen von REST-Diensten.
Sie können
Berge extrem schnell einen REST-Endpunkt.
Zum Schluss
[SignalR](http://www.asp.net/signalr) können Sie angeben, Push-basierten
Kommunikation mit einer Anwendung
[WebSocket](https://en.wikipedia.org/wiki/WebSocket) Protokoll.

.NET systemeigen
================

Systemeigene .NET ist nicht so sehr ein "Edition" der .NET Plattform ist eine
der Satz von Tools, mit die Entwickler verschiedene Buildausgaben haben können.
Die
normale dauert .NET Quelle Kompilierung in den Quellcode
eine der .NET Sprachen (z. B. C\-, Visual Basic-, F\ # usw.)
und
erzeugt einen so genannten "Intermediate Language".
IL-Code wird dann übernommen
durch die Common Language Runtime und Just-In-Time-bei der Ausführung in Maschinencode kompiliert.

Systemeigene .NET ist ein zusätzlicher Schritt in diese Pipeline nimmt den IL-Code
und kompiliert es **Ahead-of-Time** (AOT) in Maschinencode, sodass beim
der Code wird ausgeführt, nur "systemeigener" Code ausgeführt.
Dies bedeutet, dass
die sich ergebende Binärdatei was das Betriebssystem ausführt ist. Es gibt keine JIT-Wert,
keine Common Language Runtime-Kompilierung.
Dies führt zu einer besseren Leistung als auch
Einige Vorteile für die Sicherheit.

Systemeigene .NET ist ein Satz von Tools zum Erstellen von .NET **Universal Windows
Plattform (UWP)** Applications.

Unterstützte Betriebssysteme
============================

.NET Framework wird nur auf Windows-Betriebssystem unterstützt.
.NET
Systemeigene ist zu diesem Zeitpunkt nur unter Windows unterstützt.

.NET Core wird unter Windows, Linux und OS X unterstützt.




