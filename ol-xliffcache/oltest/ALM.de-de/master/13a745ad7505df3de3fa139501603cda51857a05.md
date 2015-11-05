---
title: Override .NET Class Libraries
another: Another attribute
---

Klassenbibliotheken für .NET
============================

Klassenbibliotheken sind die [gemeinsam genutzte Bibliothek](http://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) Konzept für .NET.
Sie können damit nützliche Funktionen in Module in Komponenten zerlegen, die von mehreren Clientanwendungen verwendet werden können.
Sie können auch verwendet werden, als ein Mittel zum Laden von Funktionen, die nicht benötigt oder beim Start der Anwendung nicht bekannt ist.
Klassenbibliotheken werden beschrieben, mit der [.NET Framework-Assembly-Dateiformat](assembly-format.md).

Es gibt drei Arten von Klassenbibliotheken, die Sie verwenden können:

- **Plattformspezifische** Klassenbibliotheken haben Zugriff auf alle APIs in einer bestimmten Plattform (z. B. .NET Framework Xamarin iOS), aber nur von apps und Bibliotheken, die diese Plattform als Ziel verwendet werden kann.
- **Tragbaren** Klassenbibliotheken haben Zugriff auf eine Teilmenge der APIs und kann von apps und Bibliotheken, die mehrere Plattformen als Ziel verwendet werden.
- **.NET Core** Klassenbibliotheken sind ein Zusammenschluss von das plattformspezifische und portable Library-Konzept in ein einziges Modell, das das beste aus beiden bereitstellt.

Plattformspezifische Klassenbibliotheken
----------------------------------------

Plattformspezifischen Bibliotheken können gebunden sind, auf einer einzigen .NET Plattform (z. B. .NET Framework unter Windows) und daher wichtige Abhängigkeiten bekannte-Umgebung.
Einer solchen Umgebung wird verfügbar machen einen bekannten Satz von APIs (.NET und OS-APIs) wird verwalten und Bereitstellen der erwarteten Status (z. B. Windows-Registrierung).

Entwickler von Plaform bestimmten Bibliotheken können die zugrunde liegende Plattform vollständig ausnutzen.
Die Bibliotheken werden immer nur auf, die Plattform überprüft oder andere Formen der bedingten Code unnötige (modulo einzelne sourcing Code für mehrere Plattformen) machen-Plattform ausgeführt werden.

Plattformspezifischen Bibliotheken wurden die primäre Klasse Bibliothekstyp für .NET Framework.
Auch bei anderen Plattformen .NET entwickelt, blieb plattformspezifischen Bibliotheken der vorherrschende Bibliothekstyp.

Portable Klassenbibliotheken
----------------------------

Portable Bibliotheken werden auf mehreren Plattformen für .NET unterstützt.
Sie können dennoch Abhängigkeiten bekannte-Umgebung, die Umgebung ist jedoch eine synthetische, die durch die Schnittmenge einer Reihe von konkreten .NET Plattformen generiert wird.
Somit verfügbar gemachten APIs und Plattform Annahmen sind eine Teilmenge von was eine plattformspezifische Bibliothek zur Verfügung wäre.

Beim Erstellen einer portablen Bibliothek, wählen eine Plattformkonfiguration.
Hierbei handelt es sich um den Satz von Plattformen, die Sie unterstützen müssen (z. B. .NET Framework 4.5 +, Windows Phone 8.0 +).
Die weitere Plattformen, die Sie unterstützen, die weniger APIs und weniger Plattform Annahmen, die Sie vornehmen können, die den kleinsten gemeinsamen Nenner entscheiden.
Dieses Merkmal kann auf den ersten seit oft Denken Sie nur an Personen verwirrend sein "mehr ist besser", jedoch feststellen, dass mehrere Plattformen Ergebnisse in weniger verfügbaren APIs unterstützt.

Viele Bibliotheksentwickler haben mehrere plattformspezifischen Bibliotheken aus einer Quelle (mit bedingten Kompilierungsdirektiven) nicht mehr auf portablen Bibliotheken gewechselt.
Es gibt [mehrere Ansätze](http://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) für den Zugriff auf plattformspezifische Funktionen innerhalb von portablen Bibliotheken
mit [Köder Switch](http://log.paulbetts.org/the-bait-and-switch-pcl-trick/) werden die gängigsten Verfahren zu diesem Zeitpunkt akzeptiert.

###.NET Core-Klassenbibliotheken

.NET Core-Bibliotheken sind eine Ersetzung der plattformspezifischen und portable Bibliotheken Konzepte.
Sie sind plattformspezifisch in dem Sinne, dass alle Funktionen der zugrunde liegenden Plattform (keine synthetischen Plattformen oder Plattform Schnittpunkten) verfügbar gemacht.
Sie sind in dem Sinne, die sie auf alle unterstützenden Plattformen übertragbar.

.NET Core stellt eine Reihe von Bibliothek *Verträge*.
.NET Plattformen müssen jeden Vertrag vollständig oder überhaupt nicht unterstützen.
Jede Plattform unterstützt daher einen Satz von .NET Core-Verträge.
Die geschäftskritisch ist, dass jede .NET Core-Klassenbibliothek auf den Plattformen unterstützt wird, die sie unterstützen den Vertrag Abhängigkeiten.

.NET Core Verträge machen Sie nicht die gesamte Funktionalität von .NET Framework (noch ist, die das Ziel), sie machen jedoch viele weitere APIs als Portable Klassenbibliotheken.
Mit der Zeit werden weitere APIs hinzugefügt.

Die folgenden Plattformen unterstützt .NET Core-Klassenbibliotheken:

- .NET Core 5
- ASP.NET 5
- .NET Framework 4.5 +
- Windows Store-Apps
- Windows Phone 8 +

###Mono-Klassenbibliotheken

Klassenbibliotheken werden auf Mono, einschließlich der drei Typen von Bibliotheken, die oben beschriebenen unterstützt.
Mono kann häufig als plattformübergreifende Implementierung von Microsoft .NET Framework (richtig) angezeigt.
Teilweise war dies, da .NET Framework-Klassenbibliotheken plattformspezifische auf die Mono-Laufzeit ohne Änderung oder erneute Kompilierung ausgeführt werden.
Dieses Merkmal wurde vor der Erstellung von portablen Klassenbibliotheken, war offensichtlich angebracht binäre Portabilität zwischen .NET Framework und Mono aktivieren (obwohl es nur in eine Richtung funktioniert).




