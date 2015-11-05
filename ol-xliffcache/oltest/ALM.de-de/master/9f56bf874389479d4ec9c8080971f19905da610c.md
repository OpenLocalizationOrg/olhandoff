Framework-Bibliotheken
======================

.NET ist eine umfassende Reihe von Klassenbibliotheken, genannt
Die Basisklassenbibliotheken (Kernsatz) oder die Framework-Klassenbibliotheken
(vollständiger Satz).
Diese Bibliotheken stellen Implementierungen für viele allgemeine bereit.
und app-spezifischen Typen, Algorithmen und Dienstprogrammfunktionen.
Beides
kommerzielle und Community-Bibliotheken erstellen, auf die Framework-Klasse
Bereitstellen von benutzerfreundlichen einsatzbereite Bibliotheken für einen umfangreichen Satz-Bibliotheken
der Datenverarbeitung Aufgaben.

Jede Implementierung eine Teilmenge dieser Bibliotheken bereitgestellt.
Base Class Library (BCL)-APIs werden bei jeder Implementierung .NET erwartet,
Da sie Entwickler möchten und da beliebten Bibliotheken
benötigen sie ausgeführt.
App-spezifischen Bibliotheken über den BCL, wie z. B.
ASP.NET ist nicht auf alle bald verfügbar sein.

Basisklassenbibliotheken
------------------------

Die BCL bietet, die meisten grundlegenden Typen und Utility-Funktionen
und bilden die Basis für alle anderen .NET Klassenbibliotheken.
Sie sollen bieten.
sehr allgemein Implementierungen ohne jede Verschiebung alle Arbeitslasten.
Leistung ist immer ein wichtiger Aspekt, da möglicherweise apps
lieber eine bestimmte Richtlinie, z. B. mit geringer Latenz zu hohem Durchsatz oder
wenig Arbeitsspeicher, geringe CPU Nutzung.
Diese Bibliotheken werden sollen
hohe Leistung in der Regel, und führen Sie einen Mittelweg Ansatz entsprechend
Um diese verschiedenen Leistungsbedenken.
Bei den meisten apps hat dieser Ansatz
ziemlich erfolgreich war.

Primitive Typen
---------------

.NET enthält einen Satz von primitiven Typen, die (zu unterschiedlichen Ergebnissen verwendet werden
Grad) in allen Programmen.
Diese Typen enthalten Daten, z. B. Zahlen,
Zeichenfolgen, Bytes und beliebige Objekte.
Die C\-Sprache enthält Schlüsselwörter
für diese Typen.
Ein Beispielsatz dieser Typen ist unten aufgeführten mit der
übereinstimmende C\-Schlüsselwörter.

-   ["System.Object"](https://msdn.microsoft.com/library/system.object.aspx)
([object](https://msdn.microsoft.com/library/9kkx3h3c.aspx)) - The
Ultimate Basisklasse im CLR-Typsystem.
   Es ist der Stamm der
Geben Sie die Hierarchie.
-   [Int16](https://msdn.microsoft.com/library/system.int16.aspx)
([short](https://msdn.microsoft.com/library/ybs77ex4.aspx)) - A
Typ der 16-Bit-Ganzzahl mit Vorzeichen.
   Die ohne Vorzeichen
[UInt16](https://msdn.microsoft.com/en-us/library/system.uint16.aspx)
auch vorhanden ist.
-   [System. Int32](https://msdn.microsoft.com/library/system.int32.aspx)
([int](https://msdn.microsoft.com/library/5kzh1b5w.aspx)) - A 32-bit
Integer-Datentyp mit Vorzeichen darstellt.
   Die ohne Vorzeichen
[UInt32](https://msdn.microsoft.com/library/x0sksh43.aspx)
auch vorhanden ist.
-   [System.Single](https://msdn.microsoft.com/library/system.single.aspx)
([float](https://msdn.microsoft.com/library/b1e65aza.aspx)) - A
32-Bit-Gleitkommatyp.
-   [System.Decimal](https://msdn.microsoft.com/library/system.decimal.aspx)
([decimal](https://msdn.microsoft.com/library/364x0z75.aspx)) - A
128-Bit-Dezimaltyps.
-   [System.Byte](https://msdn.microsoft.com/en-us/library/system.byte.aspx)
([byte](https://msdn.microsoft.com/library/5bdb6693.aspx)) - An
nicht signierte 8-Bit-Integeger, die ein Byte Speicher darstellt.
-   [System.Boolean](https://msdn.microsoft.com/library/system.boolean.aspx)
([bool](https://msdn.microsoft.comlibrary/c8f5xwh7.aspx)) - A
Boolean-Typ, der darstellt, 'true' oder 'false'.
-   [System.Char](https://msdn.microsoft.com/library/system.char.aspx)
([char](https://msdn.microsoft.com/library/x9h8tsay.aspx)) - A
numerische 16-Bit-Typ, der eine Unicode-Zeichen darstellt.
-   [System.String](https://msdn.microsoft.com/library/system.string.aspx)
([string](https://msdn.microsoft.com/library/362314fe.aspx))
-Eine Reihe von Zeichen darstellt.
   Anders als eine `char []`, aber
in jeder einzelnen Indizierung ermöglicht `Char` in den `Zeichenfolge`.

Datenstrukturen
---------------

.NET umfasst eine Reihe von Datenstrukturen, die Workhorses von fast sind
.NET apps.
Diese sind meistens Auflistungen, jedoch auch andere
Typen.

-   [Array](https://msdn.microsoft.com/library/system.array.aspx)
-Stellt ein Array von stark Typen von Objekten, auf die zugegriffen werden kann
über den Index.
   Einen feste Größe hat, pro seine Konstruktion bindet.
-   [Liste](https://msdn.microsoft.com/library/6sh2ey19.aspx) -darstellt
eine stark typisierte Liste von Objekten, die über den Index zugegriffen werden kann.
   Is
automatisch angepasst, je nach Bedarf.
-   [Wörterbuch](https://msdn.microsoft.com/library/xfhwa508.aspx)
– Stellt eine Auflistung von Werten, die durch einen Schlüssel indiziert werden.
   Werte
kann über den Schlüssel zugegriffen werden.
   Wird automatisch nach Bedarf angepasst.
-   [URI](https://msdn.microsoft.com/library/system.uri.aspx) -bietet
eine objektdarstellung einen uniform Resource Identifier (URI) und
einfacher Zugriff auf die Teile des URIS.
-   [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx)
   - Eine sofortige Zeitpunkt darstellt, in der Regel als Datum ausgedrückt und
Tageszeit.

Hilfsprogramm-APIs
------------------

.NET enthält einen Satz von Dienstprogramm-APIs, die für viele Funktionen bereitstellen
wichtige Aufgaben.

-   [HttpClient](https://msdn.microsoft.com/library/system.net.http.httpclient.aspx)
   - Eine API für HTTP-Anforderungen senden und Empfangen von HTTP-Antworten aus
eine Ressource, die von einem URI identifiziert wird.
-   [XDocument](https://msdn.microsoft.com/library/system.xml.linq.xdocument.aspx)
   - Eine API für das Laden und XML-Dokumenten mit LINQ Abfragen.
-   [StreamReader](https://msdn.microsoft.com/library/system.io.streamreader.aspx)
   - Eine API zum Lesen von Dateien
([StreamWriter](https://msdn.microsoft.com/library/system.io.stringwriter.aspx))
Kann verwendet werden, um Dateien zu schreiben.

App-Modell-APIs
---------------

Es gibt viele app-Modelle, die mit .NET von bereitgestellten verwendet werden können
mehrere Unternehmen.

-   [ASP.NET](http://asp.net) -bietet ein Web-Framework zum Erstellen von
Websites und Dienste.
   Unter Windows, Linux und OS X unterstützt
(je nach Version von ASP.NET).





