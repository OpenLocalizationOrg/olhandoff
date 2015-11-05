Garbage Collection
==================

Die Garbagecollection ist eines der wichtigsten Features von .NET verwaltet
Code-Plattform.
Der Garbage Collector (GC) verwaltet die Zuordnung und
Freigeben von Arbeitsspeicher für Sie.
Sie müssen nicht zu reservieren und freigeben
Arbeitsspeicher oder Verwalten der Lebensdauer der Objekte, die die Verwendung dieses Speichers.
Ein
Zuordnung erfolgt eine Zeit *neue* wird ein Objekt oder einen Werttyp
geschachtelt.
Zuordnungen sind in der Regel sehr schnell.
Wenn es reicht nicht aus
Speicher für das Zuweisen eines Objekts, das die Freispeichersammlung muss sammeln und Garbage verwerfen
Arbeitsspeicher, Speicher für neue Zuordnungen zur Verfügung stellen.
Dieser Prozess ist
"Garbagecollection" bezeichnet.

Der Garbage Collector fungiert als automatischer Speicher-Manager.
Es bietet
die folgenden Vorteile:

-   Ermöglicht es Ihnen, Ihre Anwendung zu entwickeln, ohne dass
freier Speicher.
-   Ordnet dem verwalteten Heap effizient Objekte zu.
-   Nicht mehr verwendeten Objekte freigegeben, löscht den Speicher,
und hält Speicher für zukünftige Zuordnungen.
   Verwaltet
Objekte erhalten automatisch bereinigen Inhalte, also die
Konstruktoren müssen nicht jedes Datenfeld initialisieren.
-   Bietet speichersicherheit, und stellen Sie sicher, dass ein Objekt verwenden, kann die
der Inhalt eines anderen Objekts.

.NET Garbage Collector ist generationsbasierten und 3 Generationen.
Jeder Generation verfügt.
einen eigenen Heap, den für die Speicherung von zugeordneten Objekten verwendet.
Es ist ein
Grundlegendes Prinzip, dass die meisten Objekte kurzlebig oder langlebig sind.
Generation 0 ist, in denen Objekte zuerst zugeordnet sind.
Objekte nicht oft
nach der ersten Generation Live, da sie nicht mehr verwendet (out of sind
Bereich) zum Zeitpunkt die nächste Garbagecollection erfolgt.
Generation 0 ist.
Schnelle sammeln, da dessen zugeordnete Heap klein ist.
Ist der Generation 1
wirklich zweite Chance Speicherplatz.
Objekte, die kurz sind auskommen konnten jedoch Überleben
die Collection der Generation 0 (häufig basierend auf Zufall Timing) finden Sie unter
Generation 1.
Garbage Collections der Generation 1 sind auch schnell da seine
zugeordnete Heap ist auch klein.
Die ersten zwei heaps kleine bleiben da
Objekte werden entweder erfasst oder werden auf die nächste Generation höher gestuft
Heap.
Generation 2 ist, in denen alle lange kurzlebige Objekte sind.
Die Generation 2
Heap anwachsen kann sehr groß sein, da die darin enthaltenen Objekte können
lange überstehen, und es ist kein Heap Generation 3 weiter zu fördern
Objekte.

Die Freispeichersammlung ist verfügt über eine zusätzliche Heap für große Objekte aufgerufen, die Groß
Objektheap (große Objektheap).
Es ist reserviert für Objekte, die mindestens 85.000 Bytes oder
größer.
(Byte\[\]) mit 85 k Elementen ein Beispiel wäre ein Byte-array
ein großes Objekt.
Große Objekte werden nicht auf die generationsbasierten zugeordnet.
Heaps aber direkt für den großen Objektheap zugeordnet sind.

Generation 2 und LOH-Auflistungen können spürbar Programme dauern
die für einen langen Zeitraum ausgeführt haben oder über große Mengen von Daten ausgeführt werden.
Große Server Programme sind Heaps in die Werte 10 von GB haben.
Der GC
verwendet eine Reihe von Techniken zur Reduzierung der Zeit, dass die it
Programm blockiert die Ausführung.
Der primäre Ansatz besteht darin, so viele garbage
Auflistung der arbeiten möglichst in einem Hintergrundthread auf eine Weise, die
mit der Ausführung des Programms nicht beeinträchtigen.
Die Freispeichersammlung macht auch einige Methoden
Entwickler, die ihr Verhalten beeinflussen, das zu Recht nützlich sein kann
die verbessern Sie Leistung.

Weitere Informationen finden Sie unter [Garbage
Auflistung](http://msdn.microsoft.com/library/0xy59wtx.aspx) auf MSDN.




