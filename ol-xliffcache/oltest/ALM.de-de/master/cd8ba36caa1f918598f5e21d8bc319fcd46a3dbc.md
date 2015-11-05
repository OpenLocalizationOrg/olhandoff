Einführung in die Common Language Runtime (CLR)
===============================================

Von Vance Morrison - 2007

Was ist die Common Language Runtime (CLR)?
Um es kurz gesagt:

> Die Common Language Runtime (CLR) ist eine vollständige auf hohem Niveau virtuelle
Computer, die eine Vielzahl von Programmiersprachen unterstützt.
sowie das Zusammenwirken zwischen ihnen.

Phew, war dies ein Recht großer Brocken.
Es ist auch an und für sich nicht sehr
beleuchtet.
Die obige Anweisung *ist* nützlich, jedoch ist es die
ersten Schritt bei der umfangreiche und komplexe Softwarekomponente bezeichnet
als das [CLR](http://msdn.microsoft.com/library/8bs2ecf4.aspx) und
Gruppieren von verständliche Weise seine Funktionen.
Wir verfügen nun über eine "10.000
Fuß"Überblick über die Common Language Runtime, von der wir die übergeordneten Ziele verstehen
und den Zweck der Laufzeit.
Nach dem Kennenlernen der CLR diese hoch
Ebene ist es leichter, stärker in untergeordneten Komponenten ohne als suchen
viel Wahrscheinlichkeit in den Details verloren geht.

Die CLR: Eine (sehr selten) vollständige Programming Plattform
--------------------------------------------------------------

Jedes Programm ist überraschend viele Abhängigkeiten auf seine Laufzeit
Umgebung.
Das Programm wird am häufigsten natürlich in einem bestimmten geschrieben.
nur der erste von vielen Annahmen Programming Language, aber dies ist ein
Programmierer weaves in das Programm.
Einige benötigen alle interessanten Programme
*-Laufzeitbibliothek* mit dem sie für die Interaktion mit anderen Ressourcen
des Computers (z. B. eine Benutzereingabe, Datenträgerdateien, die Netzwerkkommunikation
usw.).
Die Anwendung muss auch in irgendeiner Form (entweder durch konvertiert werden
Interpretation oder Kompilierung) zu einem Formular, das die systemeigene Hardware kann
direkt ausführen.
Diese Abhängigkeiten eines Programms sind also zahlreiche,
voneinander abhängig und verschiedene, Implementierer von Programmiersprachen
verzögern Sie fast immer andere Standards fest.
Angenommen, die
Programmiersprache C++ gibt das Format der ausführbaren C++ nicht an.
In diesem Fall
Jede C++-Compiler ist auf eine bestimmte Hardware-Architektur (z. B. gebunden
X 86) und ein Betriebssystem (z. B. Windows, Linux, oder
Mac OS) beschreibt das Format der ausführbaren Datei-Format und
Gibt an, wie sie geladen wird.
Folglich machen nicht Programmierer "C++
ausführbare,"aber eher"ausführbare Windows X 86-Datei"oder eine"Power PC Mac OS
ausführbare."

Bei gleichzeitiger Nutzung vorhandener Hardware und Betriebssystem-Standards ist.
in der Regel weist eine gute Sache, es den Nachteil der Bindung der Spezifikation von
um die Ebene der Abstraktion der vorhandenen Standards.
Z. B. Nein
Allgemeine Betriebssystem verfügt heute über das Konzept einer Garbage collection
Heap.
Folglich besteht keine Möglichkeit, mit vorhandenen Standards beschrieben ein
Schnittstelle, die der Garbagecollection (z. B., übergeben nutzt
Zeichenfolgen und her, ohne befürchten zu müssen, wer ist verantwortlich für
Sie löschen).
Auf ähnliche Weise stellt ein normalen Programmdatei-format
einfach genug Informationen, aber nicht genügend Informationen für ein Programm ausführen
ein Compiler andere Binärdateien an die ausführbare Datei gebunden.
Beispielsweise C++
Programme verwenden in der Regel eine Standardbibliothek (unter Windows aufgerufen
Msvcrt.dll) enthält (z. B. die meisten gängigen Funktionen
Printf), aber das Vorhandensein dieser Bibliothek allein reicht nicht aus.
Ohne
die entsprechenden Headerdateien, die zusammen mit dem (z. B. stdio.h)
Programmierer können die Bibliothek nicht verwenden.
Folglich vorhandene ausführbare Datei-format
Standards nicht verwendet sowohl ein Dateiformat zu beschreiben, die ausgeführt werden können
und andere Informationen oder Binärdateien, die erforderlich sind, geben die
das Programm ist abgeschlossen.

Die CLR behebt Probleme wie diese durch die Definition einer [sehr abgeschlossen
Spezifikation](dotnet-standards.md) (standardisiert von ECMA) enthält
die Details benötigen Sie für den gesamten Lebenszyklus eines Programms aus
Konstruktion und Bindung über die Bereitstellung und Ausführung.
Folglich zwischen
andere Dinge gibt die CLR:

-   Ein GC-fähigen virtuellen Computer mit einem eigenen Anweisungssatz (namens das
Common Intermediate Language (CIL)) verwendet wird, um die Primitive angeben
Vorgänge, die von Programmen ausführen.
   Dies bedeutet, dass die CLR nicht ist
Abhängig von einer bestimmten CPU-Typ.
-   Eine umfassende Darstellung für Metadaten (z. B. Programmieren von Deklarationen
Typen, Felder, Methoden usw.), sodass diese Generieren von anderen Compilern
ausführbare Dateien haben die Informationen, die sie benötigen, um Funktionen aufrufen
von "Outside".
-   Ein Dateiformat, das genau vorgibt, wie die Bits in festsetzen gibt ein
Datei, damit Sie ordnungsgemäß für eine CLR-EXE sprechen zu können, die nicht gebunden ist
auf einem bestimmten Betriebssystem oder der Computerhardware.
-   Die Semantik der Lebensdauer eines geladenen Programms Mechanismus, mit dem
eine CLR-EXE-Datei kann zu einem anderen CLR-EXE und die Regeln, wie verweisen
die Laufzeit sucht die referenzierten Dateien zum Zeitpunkt der Ausführung.
-   Eine Klassenbibliothek, die die Funktionen nutzt, die die CLR bereitstellt
(z. B. Garbagecollection, Ausnahmen oder generische Typen) für ein
Zugriff auf grundlegende Funktionen (z. B. ganze Zahlen, Zeichenfolgen, Arrays,
Listen oder Wörterbüchern) als auch Betriebssystemdienste
(z. B. Dateien, Netzwerk oder Interaktion des Benutzers).

Unterstützung mehrerer Sprachen
-------------------------------

Definieren, angeben, und implementieren all diese Angaben ist ein großer
Unternehmen, ist die vollständige Abstraktionen wie die CLR sehr sind
selten.
Tatsächlich führt die große Mehrheit der solche vernünftigerweise abgeschlossen
Abstraktionen, die für die einzelnen Sprachen erstellt wurden.
Beispielsweise ist das Java
der Perl-Interpreter oder frühere Version des Visual Basic-Runtime
Common Language Runtime Angebot entsprechend vollständige Abstraktion Grenzen.
Was
unterscheidet die CLR von diesen früheren Aufwand ist Multi-Language
Natur.
Mit Ausnahme von Visual Basic (da es
nutzt das COM-Objektmodell), der innerhalb der Sprache verwendet wird
oft sehr gut, aber mit anderen geschriebene Programme interoperierende
Sprachen ist bestenfalls sehr schwierig.
Interoperabilität ist schwierig, da
diesen Sprachen können nur mit "foreign" Sprachen mit kommunizieren.
die primitive, die vom Betriebssystem bereitgestellt wird.
Da das Betriebssystem
Abstraktionsebene so niedrig ist (z. B. das Betriebssystem hat kein Konzept
eine Garbage collection-Heap) sind unnötig komplizierte Techniken
erforderlich.
Bereitstellen einer COMMON LANGUAGE RUNTIME, ermöglicht es der CLR
Sprachen, die miteinander kommunizieren, mit Konstrukten auf hoher Ebene
(z. B. Collection Strukturen), Ihnen der interoperation Verwaltungsaufwand
erheblich.

Da die Common Language Runtime gemeinsam *viele* Sprachen, bedeutet das, dass mehr
Ressourcen können ihn auch unterstützt abgelegt werden.
Erstellen von guten Debugger
und Profiler für eine Sprache ist viel Arbeit, und daher befinden sich in einem
voll funktionsfähige Formular nur für die wichtigsten Programmiersprachen.
Dennoch, weil Sprachen, die in der CLR implementiert werden können.
Diese Infrastruktur wiederverwenden, wird die Belastung der einer bestimmten Sprache
verringert.
Vielleicht sogar noch wichtiger, einer beliebigen Sprache erstellt.
in der CLR sofort hat Zugriff auf *alle* baut auf Klassenbibliotheken
Anfang der CLR.
Dieser große (und wachsende) Text (gedebuggt und
Unterstützte) Funktionalität wird einen große Grund, warum die CLR, wurde
erfolgreich.

Kurz gesagt, ist die Common Language Runtime eine vollständige Spezifikation der genauen Bits 1
hat in einer Datei erstellen und Ausführen eines Programms zu platzieren.
Die virtuelle Maschine
dass ausgeführt wird, die diese Dateien auf einer hohen Ebene ist für die Implementierung geeignete einer
Umfassende Klasse Programmiersprachen.
Diese virtuellen Computer zusammen mit
ein wachsenden Text von Klassenbibliotheken, die auf diesem virtuellen ausgeführt
Computer, was wir die common Language Runtime (CLR) aufrufen.

Das Hauptziel der CLR
---------------------

Nun, wir grundlegende Idee haben, was die CLR ist, ist es sinnvoll, Sichern
nur ein bisschen und Verstehen des Problems, die Common Language Runtime vorgesehen war, zu lösen.
Am
eine sehr hohe weist die Laufzeit nur ein Ziel:

> Das Ziel der CLR ist, die Programmierung zu erleichtern.

Diese Anweisung ist aus zwei Gründen nützlich.
Zunächst einmal ist es ein *sehr* nützlich
Hier können Prinzip wie die Common Language Runtime entwickelt.
Angenommen, im Grunde
nur einfache Dinge einfach, also hinzugefügt werden können **für Benutzer sichtbaren** Komplexität
die Common Language Runtime sollten immer mit Argwohn betrachtet werden.
Wichtiger als
das Kosten/Nutzen-Verhältnis einer Funktion ist die *verfügbar gemachte hinzugefügt
über alle Szenarien profitieren Komplexität/gewichteten* Verhältnis.
Im Idealfall dies
Verhältnis negativ ist (d. h. das neue Feature reduziert die Komplexität von
Entfernen von Einschränkungen oder Verallgemeinern von vorhandenen Sonderfälle).
Allerdings ist in der Regel es gering gehalten, durch die Minimierung der verfügbar gemachten
Komplexität und maximieren die Anzahl der Szenarien, in denen die Funktion
Fügt den Wert hinzu.

Die zweite Ursache dieses Ziel ist es so wichtig ist, dass **einfache Benutzung ist die
Der Hauptgrund für die CLR Erfolg**.
Die CLR ist nicht erfolgreich.
Da es schneller oder kleiner als das Schreiben von systemeigenem Code (in der Tat ist.
gut geschriebene systemeigenen Code wins oft).
Die CLR ist nicht erfolgreich, da
von einer bestimmten Funktion es unterstützt (z. B. Garbagecollection Plattform
Unabhängigkeit von der objektorientierten Programmierung oder Unterstützung).
Die
CLR ist erfolgreich, da alle diese Funktionen, wie auch zahlreiche
andere werden kombiniert, um die Programmierung deutlich einfacher, als würde er machen
werden Sie andernfalls.
Einige wichtige, aber häufig übersehene anwenderfreundliche Funktionen
gehören:

1.  Vereinfachte Sprachen (z. B. C\- und Visual Basic sind erheblich
einfacher C++)
2.  Ein Engagement für Einfachheit in der Klassenbibliothek (z. B. nur schon
Ein String-Typ, und es ist unveränderlich. Dies vereinfacht eine
Die API, die Zeichenfolgen verwendet werden)
3.  Starke Konsistenz bei der Benennung in der Klassenbibliothek (z. B.
Anfordern von APIs für das ganze Wörter und konsistente Benennungskonventionen verwenden)
4.  Bietet umfassende Unterstützung in der Kette Tool zum Erstellen einer Anwendung erforderlich
(z. B. Visual Studio wird die Erstellung von CLR-Anwendung sehr einfach,
Suchen Sie nach den richtigen Typen und Methoden erstellen, wodurch Intellisense
die Anwendung sehr einfach).

Ist dieses Engagement für die Verwendung zu erleichtern (der hand in hand mit wechselt
Einfachheit des benutzermodells), der hervorsticht als Grund für die
der Erfolg der CLR.
Etliche eigenartig, einige der wichtigsten erleichterte Bedienung
Funktionen sind auch die meisten "langweilig."
Angenommen, eine Programmierung
Umgebung konnte konsistente Benennungskonventionen noch tatsächlich anwenden
auf diese Weise über eine umfangreiche Klassenbibliothek ist ziemlich viel Arbeit.
Häufig solche
Aufwand in Konflikt mit anderen Ziele (z. B. mit
vorhandene Schnittstellen), oder sie führen in erheblichen logistische Probleme
(z. B. die Kosten der Umbenennung einer Methode über eine *sehr* große Codebasis).
Ist bei solchen, die wir uns zu erinnern, unsere
Nummer 1-Ziel der Laufzeit und stellen Sie sicher, dass haben wir
die gerade unsere Prioritäten, dieses Ziel zu erreichen.

Grundlegende Funktionen der CLR
-------------------------------

Die Common Language Runtime hat viele Features, daher ist es sinnvoll, diese als zu kategorisieren
lautet folgendermaßen:

1.  Grundlegende Funktionen – Funktionen, die Breite auf den Entwurf auswirken
andere Funktionen.
   Dazu gehören:



ein.
Garbage Collection
b.
Arbeitsspeicher-Sicherheit und Sicherheit
c.
Hohes Maß an Programmiersprachen unterstützen.



2.  Sekundäre Merkmale – die wichtigsten Features aktivierte Funktionen
die möglicherweise nicht viele nützliche Programme erforderlich sein:



ein.
Programm-Isolation mit Anwendungsdomänen
b.
Programmieren von Sicherheit und sandboxing



3.  Andere Funktionen – Funktionen, die alle Common Language Runtime-Umgebung müssen jedoch
die wichtigsten Features der CLR werden nicht genutzt werden.
   In diesem Fall
Sie sind das Ergebnis den Wunsch zur Erstellung einer vollständigen
Programmierumgebung.
   Zu diesen zählen:



ein.
Versionskontrolle
b.
Debuggen/Profiling
c.
Interoperation

Der CLR-Garbagecollector (GC)
-----------------------------

Alle Features, die die CLR bereitstellt, der Garbage collector
verdient besondere beachten.
Garbagecollection (GC) ist der allgemeine Begriff für
Automatische Arbeitsspeicher freigeben.
In einem System Garbage collection-Benutzer
Programme müssen nicht mehr Aufrufen einen besonderen Operator, um Speicher zu löschen.
Stattdessen verfolgt Überblick über die Common Language Runtime automatisch alle Verweise auf
Speicher in den Heap der Garbage Collection, und Zeit, wird es
Durchsuchen Sie diese Verweise, um herauszufinden, welcher Speicher immer noch erreichbar ist
das Programm.
Alle anderen Speicher ist *Garbage* und neuer wiederverwendet werden kann.
Zuordnungen.

Garbagecollection ist eine wunderbare User-Funktion, da es vereinfacht
Programmieren.
Die offensichtlichste Vereinfachung ist, die meisten explizit
Löschvorgänge werden nicht mehr benötigt.
Beim Entfernen des Löschvorgangs
Vorgänge ist wichtig, der tatsächliche Wert für den Programmierer ist etwas mehr
Feine:

1.  Garbagecollection Schnittstellenentwurf vereinfacht, da Sie nicht mehr
sorgfältig angeben, welche Seite der Benutzeroberfläche zuständig ist.
zum Löschen von Objekten, die über die Schnittstelle übergeben werden.
   Z. B. CLR
Schnittstellen werden einfach Zeichenfolgen zurück; Nehmen sie Zeichenfolgenpuffer
und Längen.
   Dies bedeutet, dass sie nicht für den Umgang mit der Komplexität
Was geschieht, wenn der Puffer zu klein sind.
   Folglich garbage
-Auflistung können alle Schnittstellen in der Runtime einfacher sein.
Andernfalls werden.
2.  Die Garbagecollection werden eine ganze Klasse von allgemeine Benutzerfehler.
   Es ist schrecklich einfach machen, die über die Lebensdauer einer
bestimmtes Objekt entweder zu schnell zu löschen (führend auf Speicher
eine Beschädigung) oder zu spät (nicht erreichbar Speicherverluste).
   Seit dar
verwendet buchstäblich Millionen von Objekten, die Wahrscheinlichkeit für die Anwendung
Fehler ist sehr hoch.
   Darüber hinaus ist die Lebensdauer Fehler aufspüren
sehr schwierig sein, insbesondere dann, wenn das Objekt von vielen verwiesen wird
Objekten direkt verwendet werden.
   Diese Klasse von Fehlern unmöglich machen wird viel vermieden.
herausgestellt.

Dennoch ist es nicht die Nützlichkeit der Garbagecollection, mit dem
Besonderer Hinweis hier vorgestellt.
Noch wichtiger ist die einfache Anforderung es
die Laufzeit selbst stellen:

> Garbagecollection ist erforderlich, alle Verweise auf den GC-Heap sein
nachverfolgt.

Obwohl dies eine sehr einfache Anforderung ist, ist es tatsächlich weitreichende
die Konsequenzen für die Common Language Runtime.
Wie Sie sich vorstellen können, zu wissen, wo jede
Zeiger auf ein Objekt wird zu jedem Zeitpunkt des Programms kann die Ausführung
recht schwierig.
Wir haben jedoch ein schadensbegrenzenden Faktor.
Technisch gesehen
Diese Anforderung gilt nur für, wenn kein globaler Katalogserver tatsächlich muss ausgeführt werden
(daher theoretisch wir müssen wissen, wo sich alle Verweise von GC alle
die Zeit, aber nur zum Zeitpunkt der GC).
In der Praxis jedoch dadurch
Minderung vollständig aufgrund ein weiteres Feature von gilt nicht die
CLR:

> Die CLR unterstützt mehrere parallele Ausführungsthreads mit einem
einzelner Prozess.

Zu einem beliebigen Zeitpunkt möglicherweise ein anderer Thread der Ausführung eine Zuweisung auszuführen.
erfordert eine Garbagecollection.
Die genaue Reihenfolge der Vorgänge
über gleichzeitig ausgeführten Threads ist nicht deterministisch.
Es ist nicht möglich
Teilen Sie genau welche ein Thread auszuführen, wenn ein anderer Thread angefordert wird.
eine Zuordnung, die eine Garbage Collection auslöst.
Folglich möglich GCs wirklich alle
der Zeit zu messen.
Nun muss die CLR nicht reagieren *sofort* zu einem anderen
Thread des verpflichtet, einen globalen Katalog Sie hierzu die CLR verfügt über eine kleine "bewegen Raum" und
GC-Verweise auf muss nicht *alle* Punkte Ausführung, aber es
*ist* muss an genügend stellen, die es "rechtzeitig" garantieren kann
als Antwort auf die Notwendigkeit eine Garbage Collection zurückzuführen, dass eine Zuweisung auf einem anderen
Thread.

Dies bedeutet, dass die CLR verfolgt werden müssen *alle* Verweise auf die
GC-Heap *fast* ständig.
Da der GC-Verweise auf Computer befinden, auf dem
registriert, in lokalen Variablen, statische Variablen oder anderen Feldern, ist recht
Ein Bit zu verfolgen.
Die problematischsten dieser Speicherorte sind Computer
Register und lokale Variablen, da sie so deutlich mit verknüpft sind
die tatsächliche Ausführung des Benutzercodes.
Was dies bedeutet, ist
die *Computercode* die GC-Verweise bearbeitet hat eine andere
Voraussetzung: verfolgen müssen die GC-Verweise, der verwendet wird.
Dies
bedeutet zusätzliche Arbeit erforderlich, damit der Compiler die Anweisung ausgeben
Verfolgen Sie die Verweise.

Um mehr zu erfahren, besuchen Sie die [Garbage Collector-Entwurf
Dokument](gc-overview.md).

Das Konzept der "Verwalteter Code"
----------------------------------

Code, der zusätzliche Blockheaderstruktur ausführt, damit alle melden kann, seine
aktive Verweise der GC "fast immer" heißt *verwaltetem Code*
(da es "von der CLR verwaltet wird").
Code, der dies nicht der Fall ist, ist
namens *nicht verwaltetem Code*.
Daher wird der gesamte Code, der vor der CLR Bestand
nicht verwalteter Code, und alle Betriebssystem-Code ist in der
nicht verwaltete.

###Der Stapel entladen-problem

Natürlich benötigt, da verwalteter Code die Dienste des Betriebssystems
System gelegentlich, wenn verwalteter Code nicht verwalteten Code aufruft.
Auf ähnliche Weise, da das Betriebssystem ursprünglich verwalteten gestartet
Code, es sind auch Zeiten, wenn nicht verwalteter Code verwalteten Code aufruft.
Also im Allgemeinen gilt: Wenn Sie ein verwaltetes Programm auf einen beliebigen beenden
Speicherort, die Aufrufliste wird eine Mischung von Frames erstellt haben.
verwalteter Code und Frames, die von nicht verwaltetem Code erstellt.

Die Stapelrahmen für nicht verwalteten Code haben *keine* Anforderungen in Bezug auf diese über
und über die Ausführung des Programms.
Es ist insbesondere nicht erforderlich
die sie können *Entladen* zur Laufzeit, um ihre Aufrufer zu suchen.
Dies
Mittel ist, dass Sie ein Programm an einer willkürlich gewählten Stelle und beenden
ist in einer nicht verwalteten Methode, es gibt keine Möglichkeit in allgemein\ [1\]
Suchen, die der Aufrufer wurde.
Hierzu können Sie nur im Debugger aufgrund von
zusätzliche Informationen in die Symbolinformationen (PDB-Datei) gespeichert.
Dies
Informationen nicht unbedingt verfügbar sein (d.h., warum Sie
Rufen Sie manchmal nicht gut stapelüberwachungen in einem Debugger) ab.
Dies ist recht
für verwalteten Code problematisch, da alle Stapel, die entladen nicht möglich
tatsächlich enthalten Frames von verwaltetem Code (die GC-Verweise enthalten.
die müssen gemeldet werden).

Verwalteter Code hat zusätzliche Anforderungen auf: nicht nur müssen die verfolgen
Alle GC verweist darauf verwendet während seiner Ausführung, aber außerdem muss
kann an den Aufrufer zu entladen.
Darüber hinaus ist es ein
Übergang von verwaltetem Code zu nicht verwaltetem Code (oder umgekehrt), verwaltet
Code muss auch zusätzliche Verwaltungsaufgaben für die Tatsache ausführen,
nicht verwalteter Code weiß nicht, wie Sie zu die Stapelrahmen entladen.
Effektiv, verwalteter Code miteinander verknüpft, die Teile des Stapels,
enthalten Sie verwaltete Frames.
Daher zwar weiterhin möglicherweise gar nicht entladen
wird dies jedoch nicht verwaltete Stapelrahmen ohne zusätzliche Informationen
immer möglich, suchen die Blöcke des Stapels, die entsprechen
verwalteter Code und die verwalteten Frames in diesen Segmenten aufzulisten.

\[1\] neueren Plattform definieren ABIs (Application binary-Schnittstelle)
Konventionen für die Codierung dieser Informationen besteht jedoch in der Regel
nicht zwingend notwendig für den gesamten Code zu folgen.

###Der "World" von verwaltetem Code

Dies bedeutet, dass spezielle Blockheaderstruktur an jedem Übergang zu erforderlich ist
und von verwaltetem Code.
Verwalteter Code lebt effektiv in einem eigenen "World"
in denen Ausführung bzw., wenn die CLR kennt.
Die
beiden Welten befinden sich in einem sehr realen Sinne voneinander (jederzeit distinct
Zeitpunkt der Code befindet sich in der *verwalteten Welt* oder *nicht verwaltet
World*).
Darüber hinaus daran, dass die Ausführung von ist Code im angegeben
ein CLR-Format (mit seiner [Common Intermediate
Sprache](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
(CIL)), und der CLR, die für die systemeigene Ausführung konvertiert werden kann
Hardware, die CLR verfügt über *viel* mehr Kontrolle über genau,
die Ausführung ist.
Die CLR könnten z. B. die Bedeutung der Status ändern.
bedeutet, dass ein Feld aus einem Objekt abrufen oder eine Funktion aufrufen.
In der Tat die
CLR tut genau dies Unterstützung zum Erstellen von
MarshalByReference-Objekte.
Diese scheinen herkömmliche lokale Objekte zu sein,
aber in Wirklichkeit auf einem anderen Computer vorhanden.
Kurz gesagt, der verwalteten Welt von
die CLR verfügt über eine große Anzahl von *Ausführung Hooks* die sie verwenden kann, um
leistungsfähige Features der erläutert werden ausführlicher im unterstützt die
Abschnitte zur Verfügung stehen.

Darüber hinaus ist eine andere wichtige Auswirkung von verwaltetem code
Das kann nicht so offensichtlich sein.
Sind in der nicht verwalteten Welt nicht GC-Zeigern
zulässig (da sie nicht zurückverfolgt werden können), und die Buchhaltung Kosten
zugeordnete beim Übergang von verwaltetem zu nicht verwaltetem Code.
Dies
Mittel ist, während Sie *können* beliebige nicht verwaltete Funktionen aus aufrufen
verwalteter Code, es ist oft nicht dazu erfreulich.
Nicht verwaltete Methoden nicht.
Verwenden Sie GC-Objekte in ihren Argumenten und Rückgabetypen Sie, d. h., alle
"Objekte" oder "Objekthandles", die nicht verwalteten Funktionen erstellen und
verwenden, müssen explizit aufgehoben werden.
Dies ist ziemlich unglücklicher.
Da diese APIs der CLR-Funktionen wie z. B. nutzen kann nicht
Ausnahmen oder Vererbung, damit einen Benutzer "nicht übereinstimmenden" tendenziell
Erfahrung im Vergleich zu wie die Schnittstellen entwickelt haben würde
verwalteter Code.

Das Ergebnis davon ist, nicht verwaltete Schnittstellen sind fast immer
*umschlossen* Verwaltung der Entwickler Code verfügbar gemacht werden.
Beispiel:
Beim Zugriff auf Dateien, nicht die CreateFile Win32-Funktionen verwendet werden.
durch das Betriebssystem jedoch eher die verwalteten System.IO.File bereitgestellt
Klasse, die diese Funktion einschließt.
Es handelt tritt nur sehr selten tatsächlich
nicht verwalteten Funktionen wird direkt an Benutzer verfügbar gemacht.

Zwar dieser Wrapper in irgendeiner Form (mehr code, die "schlechten" sein mag
scheint nicht viel), es ist in der Tat gut, da tatsächlich hinzugefügt werden kann.
ziemlich viel Wert.
Denken Sie daran, es war immer *mögliche* verfügbar machen die
nicht verwaltete Schnittstellen direkt; Wir *auswählen* um die Funktionalität zu umschließen.
Warum?
Da das Ziel der Laufzeit ist **machen
einfache Programmierung**, und die nicht verwalteten Funktionen sind in der Regel nicht einfach
ausreichend.
In den meisten Fällen nicht verwaltete Schnittstellen werden *nicht* speziell für die erleichterte Bedienung
verwenden, beachten Sie aber eher auf Vollständigkeit optimiert werden.
Niemand
die Argumente, die CreateFile oder CreateProcess wäre schwierig gedrückt, um
kennzeichnen Sie sie als "einfach".
Die Funktionalität zum Glück Ruft ein
"überarbeiteten", wenn es die verwaltete Welt gibt, und zwar diese Überarbeitung ist.
sehr häufig "Freizeitprojekte" (nichts Komplexeres als umbenennen, erfordern
Vereinfachung und Organisieren von Funktionen), es ist auch richtig
nützlich.
Eine sehr wichtige Dokumente erstellt, für die CLR ist die
[Framework Design
Richtlinien](http://msdn.microsoft.com/en-us/library/ms229042.aspx).
Dies
800 + Seite Dokument Details best Practices bei der neuen ausführenden verwalteten Klasse
Bibliotheken.

Daher haben wir jetzt, verwalteten Code angezeigt (der Repositoryschicht eng beteiligt ist
mit die CLR) unterscheidet sich in zwei wichtigen Aspekten von nicht verwaltetem Code:

1.  Hightech: Der Code befindet sich in einem unterschiedlichen Welt, in der CLR
Steuert die meisten Aspekte der Ausführung des Programms auf einer sehr gut
(möglicherweise auf einzelnen Anweisungen) und die CLR erkennt, wenn
die Ausführung eingibt und verwalteten Code beendet.
   Dies ermöglicht eine Vielzahl
nützliche Features.
2.  Freizeitprojekte: Die Tatsache, dass es einen Übergang beim Wechseln von Kosten
verwaltetem zu nicht verwaltetem Code als auch die Tatsache, die von nicht verwaltetem code
Mit-GC-Objekte kann nicht fördert die Praxis, die meisten umschließen
nicht verwalteter Code in einer verwalteten Fassade.
   Dies bedeutet, dass Schnittstellen können ein
"überarbeiteten" vereinfachen sie und einer einheitlichen Gruppe von entsprechen
Benennen und Designrichtlinien, die einen Grad an Konsistenz erzeugen und
Erkennbarkeit, die in der nicht verwalteten Welt vorhanden waren, konnte aber
geschieht dies nicht.

**Beide** dieser Merkmale sind sehr wichtig für den Erfolg
verwalteter Code.

Speicher und Sicherheit
-----------------------

Einer der weniger offensichtlichen aber ziemlich weit reichende Funktionen, die eine Garbage
Datensammler aktiviert ist, die Arbeitsspeicher-Sicherheit.
Die invariante des Arbeitsspeichers
Sicherheit ist sehr einfach: ein Programm ist sicheren Speicher, wenn es nur zugreift
Arbeitsspeicher, die zugeordnet (und nicht freigegeben) wurde.
Dies bedeutet einfach, dass
Sie verfügen nicht "wild" (Verbleibende) Zeiger, die nach dem Zufallsprinzip zeigen
Standorte (genauer gesagt, Arbeitsspeicher, die vorzeitig freigegeben wurde).
Arbeitsspeicher-Sicherheit ist eine Eigenschaft, die wir alle Programme haben möchten.
Verbleibend Zeiger sind immer Fehler und verfolgen sie oft ziemlich
schwierig.

> GC *ist* garantiert benötigt werden, um für speichersicherheit bereitstellen

Eine kann schnell sehen, wie eine Garbage collection hilft sicherzustellen Speicher
Sicherheit, da es die Möglichkeit entfernt werden, die Benutzer vorzeitig beendet werden
freier Arbeitsspeicher (und somit Zugriff auf Speicher, der nicht ordnungsgemäß zugeordnet wurde).
Was möglicherweise nicht so offensichtlich ist, wenn Sie Speicher gewährleisten möchten
Sicherheit (ist die Ausführung dieser *unmöglich* für Programmierer erstellen
Speicher / unsafe-Programme), praktisch gesehen, Sie können nicht zu vermeiden, dass ein
Garbage Collection.
Der Grund dafür ist, dass nicht trivialen Programme benötigen
*Heaps Stil* Speicherbereiche (dynamisch), in denen die Lebensdauer der
Objekte ist im Wesentlichen beliebige Programm gesteuert (im Gegensatz zu
Stapel reservierten oder statisch zugewiesene Arbeitsspeicher hat eine hoch
Eingeschränkte Allocation-Protokoll).
In einer solchen beschränkten Umgebung
das Problem festgestellt, ob eine bestimmte explizite löschen
Aussage ist richtig unmöglich Programm Analyse vorherzusagen.
Praktisch die einzige Möglichkeit, die müssen Sie bestimmen, ob ein Löschvorgang richtig ist.
Sie werden zur Laufzeit zu überprüfen.
Dies ist genau welche kein globaler Katalogserver (überprüft
Wenn der Arbeitsspeicher noch aktiv ist).
Folglich benötigen für alle Programme, die im Heap-Stil
Speicherbereiche, wenn Sie Arbeitsspeicher-Sicherheit gewährleisten möchten Sie *müssen* ein
GC.

GC ist notwendig, die Arbeitsspeicher-Sicherheit zu gewährleisten, ist es nicht ausreichend.
Die Freispeichersammlung verhindert nicht das Programm über das Ende des Indizierung ein
Array- oder Zugriff auf ein Feld über das Ende eines Objekts (mögliche If Sie
Berechnen Sie die Adresse des Felds mithilfe einer Berechnung Basis- und Offset).
Wenn wir diesen Fällen verhindern, kann jedoch dann wir tatsächlich es definieren
für einen Programmierer zum Erstellen von Speicher / unsafe-Programmen unmöglich.

Während der [common Intermediate
Sprache](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
(CIL) *ist* Operatoren, abrufen und Festlegen von beliebigen Speicher können, haben (und
Folglich Arbeitsspeicher Sicherheit verletzen), verfügt auch über die folgenden arbeitsspeichersicher
Operatoren und die CLR dringend, dass ihre Verwendung in den meisten Programmierung:

1.  Feld-Fetch-Operatoren (LDFLD, STFLD, LDFLDA), die abgerufen werden (gelesen) festgelegt.
und die Adresse eines Felds anhand des Namens.
2.  Array-Fetch-Operatoren (LDELEM STELEM, LDELEMA) abzurufen, festzulegen und
Nehmen Sie die Adresse eines Arrayelements nach Index.
   Alle Arrays enthalten eine
der Tag, deren Länge angibt.
   Dies ermöglicht eine automatische Grenzen
Überprüfen Sie vor jeder Zugriff.

Mithilfe dieser Operatoren anstelle von auf niedrigerer Ebene (oder unsicher)
*Speicher Fetch* Operatoren in Benutzercode als auch andere unsichere vermeiden
[CIL](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
Operatoren (z. B. solche, die auf beliebige, wechseln Sie zu ermöglichen und somit
möglicherweise falsche Speicherorte) konnte eine vorstellen Aufbau eines Systems, das ist
Arbeitsspeicher-Safe jedoch nichts mehr.
Die CLR tut dies, jedoch nicht.
Stattdessen
die CLR erzwingt eine stärkere invariante: Geben Sie die Sicherheit.

Aus Sicherheitsgründen der Typ ist im Prinzip jeder Belegung von Arbeitsspeicher zugeordnet
ein Typ.
Alle Operatoren, die auf Speicheradressen werden auch vom Konzept her
gekennzeichnet mit dem Typ, für den sie gültig sind.
Sicherheit ist erforderlich
mit einem bestimmten Typ gekennzeichnet, dass der Speicher kann nur Operationen unterzogen werden.
für diesen Typ zulässig.
Dies wird nicht nur Arbeitsspeicher-Sicherheit (Nein sichergestellt
Verbleibend von Zeigern), können sie auch zusätzliche Garantien für jede
einzelne Typ.

Die wichtigste dieser Garantien eines spezifischen Typs ist, der
Sichtbarkeitsattribute mit dem Typ (und zwar insbesondere
Felder) werden erzwungen.
Also, wenn ein Feld deklariert ist, privat sein
(zugegriffen werden nur von den Methoden des Typs), dann wird diese Datenschutz
durch alle anderen typsicherer Code tatsächlich eingehalten Sie werden.
Angenommen, ein
bestimmter Typ möglicherweise ein Anzahlfeld zu deklarieren, der die Anzahl darstellt.
Elemente in einer Tabelle.
Die Felder vorausgesetzt, für die Anzahl und der Tabelle sind
privat, und unter der Annahme, dass der einzige Code, der diese updates werden aktualisiert
zusammen, gibt es jetzt eine starke Garantie (über alle typsicherer Code)
die Anzahl und die Anzahl der Elemente in der Tabelle tatsächlich synchronisiert sind.
Wenn Informationen zu Programmen herausstellen, verwenden Programmierer das Konzept des Typs
Sicherheit immer, ob sie es oder nicht kennen.
Die CLR erhöht.
typsicherheit wird einfach ein programming Language/compiler
Konvention, die ausschließlich zur Laufzeit erzwungen werden kann.

###Überprüfbarer Code - Speicher und Typsicherheit erzwingen

Im Prinzip zum Erzwingen von Sicherheit, jeder Vorgang, der das Programm
führt überprüft werden muss, um sicherzustellen, dass sie Speicher ausgeführt wird,
So eingegeben wurde, die mit dem Vorgang kompatibel ist.
Während der
System konnte dies alles zur Laufzeit ausführen, es wäre sehr langsam.
In diesem Fall die
CLR wurde das Konzept der
[CIL](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
Überprüfung, eine statische Analyse erfolgt, in dem auf die
[CIL](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
(vor der Ausführung des Codes) zu bestätigen, dass die meisten Vorgänge in der Tat sind
typsicher.
Nur, wenn dieser statische Analyse kein Auftrag abgeschlossen werden
Common Language Runtime überprüft erforderlich.
In der Praxis, die Anzahl der laufzeitüberprüfungen
erforderlich ist tatsächlich sehr klein.
Dazu zählen die folgenden Vorgänge:

1.  Einen Zeiger auf ein Basistyp als Zeiger auf einen abgeleiteten Typ umwandeln
(die entgegengesetzte Richtung kann statisch überprüft werden)
2.  Überprüfung der Arraygrenzen (so wie wir gesehen, für Arbeitsspeicher-Sicherheit haben)
3.  Zuweisen eines Elements in ein Array von Zeigern auf einen neuen (Zeiger)
zurückgegeben.
   Diese bestimmten Prüfung ist nur erforderlich, da CLR-Arrays
mit der großzügigen Umwandlungsregeln haben (mehr dazu später...)

Beachten Sie, dass die Notwendigkeit, führen Sie diese Tests auf Anforderungen platziert die
Common Language Runtime.
Insbesondere:

1.  Alle Speicher im GC-Heap muss mit dem zugehörigen Typ markiert sein (also die
Umwandlungsoperator kann implementiert werden).
   Diese Typinformationen werden müssen
zur Laufzeit verfügbar und komplex genug, um festzustellen, ob sein
Umwandlungen gültig sind (z. B. die Common Language Runtime muss wissen, die
Vererbungshierarchie).
   Tatsächlich ist das erste Feld in jedem Objekt auf
GC-Heap verweist auf eine Common Language Runtime-Datenstruktur, die darstellt
Der Typ ist.
2.  Alle Arrays müssen ihre Größe (für die Überprüfung von Grenzen).
3.  Arrays müssen vollständige Typinformationen über dem Elementtyp aufweisen.

Zum Glück wurde die teuerste Anforderung (tagging jedes Heap-Element)
etwas, das bereits unterstützt (die Garbagecollection erforderlich ist
GC muss wissen, welche Felder in jedem Objekt enthalten Verweise, die
gescannt werden müssen), daher ist die zusätzliche Kosten für die typsicherheit
Niedrig.

Folglich durch Überprüfen der
[CIL](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
Code und führen Sie einige laufzeitüberprüfungen kann die CLR Typ sicherstellen.
Sicherheit (und speichersicherheit).
Diese zusätzliche Sicherheit dennoch exacts ein
Preis in Programmiersprachen Flexibilität.
Während die CLR allgemeinen Speicher verfügt
FETCH-Operatoren, diese Operatoren können nur verwendet werden, sehr eingeschränkten
Arten der Code überprüfbar sein.
Insbesondere alle Zeiger
arithmetische Operationen fehl Überprüfung noch heute.
Daher viele klassische C oder C++
Konventionen können in überprüfbarem Code verwendet werden. Sie müssen Arrays verwenden.
Stattdessen.
Während dies etwas Programmierung einschränkt, ist es wirklich nicht schlecht
(Arrays sind ausgesprochen leistungsstark), und die Vorteile (weitaus weniger "unangenehm" Fehler)
sind sehr real.

Die CLR empfiehlt dringend die Verwendung der überprüfbar typsicheren Code.
Sogar
sind der Zeiten (vor allem beim Umgang mit nicht Code verwaltetem),
nicht überprüfbarer Programmierung ist erforderlich.
Die CLR ermöglicht dies, aber das beste
Übung hier besteht darin, diese unsicheren Code so weit wie möglich zu beschränken.
Normale Programme weisen nur einen sehr kleinen Teil ihres Codes,
Unsichere sein muss, und den Rest können typsicher sein.

Features für hohe Ebene
-----------------------

Unterstützung von Garbagecollection hatte nachhaltige Auswirkungen auf die Common Language runtime
weil dies erfordert, dass der gesamte Code zusätzliche Verwaltungsaufgaben unterstützen muss.
Die
verpflichtet, für die Sicherheit von Typen verfügte über eine große Wirkung, muss der
Beschreibung des Programms (die
[CIL](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf))
werden Sie auf einer hohen Ebene, Felder und Methoden Typ über detaillierte
Informationen.
Der Wunsch nach Sicherheit erzwingt auch die
[CIL](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
andere allgemeine Programmierkonstrukte unterstützen, die als typsicherer sind.
Diese Konstrukte in einer typsicheren Weise Ausdrücken erfordert auch Common Language runtime
unterstützt.
Die beiden wichtigsten allgemeinen Features werden verwendet, um
zwei wichtige Elemente der objektorientierten Programmierung zu unterstützen:
Vererbung und virtuellen Aufrufs Dispatch.

###Objektorientierte Programmierung

Vererbung ist relativ einfach im mechanischen Sinne.
Die grundlegende Idee
darin, dass die Felder des Typs `abgeleitete` sind eine Obermenge der Felder
Typ `Basis`, und `abgeleitete` angelegt, ihre Felder also die Felder des `Basis`
zuerst und dann Code erwartet einen Zeiger auf eine Instanz von
`Basis` können einen Zeiger angegeben werden, mit einer Instanz von `abgeleitete` und den Code
"funktioniert".
Geben Sie daher `abgeleitete` gilt als erben `Basis`,
Dies bedeutet, dass sie überall verwendet werden kann `Basis` verwendet werden können.
Code wird
*polymorphen* da der gleiche Code auf viele unterschiedliche Arten verwendet werden kann.
Da die Common Language Runtime muss wissen, welche Art Umwandlungen möglich ist, sind die
Common Language Runtime muss die Möglichkeit zu formalisieren Vererbung angegeben ist, also kann es
Überprüfen Sie die Sicherheit.

Virtueller Dispatch generalisiert Vererbung Polymorphie.
Sie können
Basistypen zum Deklarieren von Methoden, die *überschreiben* abgeleitet
Typen.
Code, der Variablen vom Typ `Basis` können davon ausgehen, dass Aufrufe
virtuelle Methoden werden an die richtige überschriebene Methode verteilt werden
basierend auf den tatsächlichen Typ des Objekts zur Laufzeit.
Während z. B. *-Laufzeit
Dispatch-Logik* konnte implementiert wurden mit primitiven
[CIL](http://download.microsoft.com/download/7/3/3/733AD403-90B2-4064-A81E-01035A7FE13C/MS%20Partition%20III.pdf)
Anweisungen ohne direkte Unterstützung in der Common Language Runtime, müsste
aus zwei wichtige Nachteile erlitten

1.  Es wäre nicht typsicher (sind Fehler in der Dispatch-Tabelle
Schwerwiegender Fehler)
2.  Jede objektorientierte Sprache würden wahrscheinlich implementieren eine etwas
andere Weise seine virtuellen Dispatch-Logik zu implementieren.
   Als Ergebnis
Interoperabilität zwischen Sprachen beeinträchtigt würden (eine Sprache konnte
erbt nicht von einem Basistyp in einer anderen Sprache implementiert).

Aus diesem Grund hat die CLR direkte Unterstützung für objektorientierte basic
Funktionen.
In dem Umfang, der möglich ist versucht die CLR, ein Modell der
Vererbung "sprachneutral," in dem Sinne, dass unterschiedliche Sprachen
die gleiche Vererbungshierarchie möglicherweise weiterhin gemeinsam nutzen.
Leider ist
war nicht immer möglich.
Insbesondere kann mehrfache Vererbung sein.
auf viele verschiedene Arten implementiert.
Die CLR wurde nicht unterstützt
Mehrfache Vererbung für Typen mit Feldern, jedoch unterstützt mehrere
Vererbung von speziellen Typen (Schnittstellen bezeichnet), die beschränkt sind
keine Felder haben.

Es ist wichtig zu beachten, die während der Laufzeit diese unterstützt
objektorientierte Konzepte, ist es nicht erforderlich sind.
Sprachen
ohne das Konzept der Vererbung (z. B. funktionale Sprachen) einfach
Verwenden Sie diese Funktionen nicht.

###Werttypen (und Boxing)

Ein weitreichende noch feine Aspekt der objektorientierten Programmierung ist das
Konzept der Objektidentität: das Konzept der Objekte (von zugeordnet
Aufrufe von separaten Zuordnung) unterschieden werden können, selbst wenn alle ihre Feld
Werte sind identisch.
Objektidentität bezieht sich stark auf die Tatsache
dass Objekte durch einen Verweis (Zeiger) und nicht durch einen Wert zugegriffen werden.
Wenn zwei Variablen auf dasselbe Objekt enthalten (deren Zeiger der Adresse
Arbeitsspeicher), dann Updates für eine der Variablen anderen auswirkt
Variable.

Leider ist das Konzept der Identität des Objekts nicht gut semantische
für alle Typen übereinstimmen.
Insbesondere betrachten keine Programmierer in der Regel
ganze Zahlen als Objekte.
Wenn die Anzahl '1' an zwei verschiedenen zugeordnet wurde
Orte Programmierer in der Regel die zwei Elemente gleich berücksichtigen möchten,
und Sie wollen sicher nicht, Updates für eine dieser Instanzen beeinflussen die
andere.
In der Tat bezeichnet eine Breite Programmiersprachen-Klasse
\'functional Sprachen vermeiden, Objekt-Identität und Referenz-Semantik
insgesamt.

Es ist zwar möglich, eine "reine" objektorientiert System haben, in denen
Alles (einschließlich Ganzzahlen) eines Objekts (der Smalltalk-80 Fall), ist ein
bestimmte Speichermenge Implementierung "verrenkungen zum Glück" ist erforderlich, um dies rückgängig machen.
Einheitlichkeit, um eine effiziente Implementierung abzurufen.
Andere Sprachen (Perl,
Java, JavaScript) eine pragmatische erhalten und einige Typen (wie behandeln
ganze Zahlen) nach Wert und andere als Verweis.
Die CLR haben auch einen gemischten
modellieren, aber im Gegensatz zu den anderen zulässig benutzerdefinierte Werttypen.

Die wichtigsten Merkmale von Werttypen sind:

1.  Jede lokale Variable, Feld oder Arrayelement eines Werttyps verfügt über eine
DISTINCT-Kopie der Daten im Wert.
2.  Wenn eine Variable, Feld oder Array-Element zu einem anderen zugewiesen wird,
der Wert wird kopiert.
3.  Gleichheit wird immer nur in Bezug auf die Daten in die Variable definiert.
(nicht seine Position).
4.  Jeder Werttyp verfügt auch über ein entsprechender Verweistyp mit
nur eine implizite, unbenanntes Feld.
   Dies ist den geschachtelten Wert bezeichnet.
   Geschachtelte Werttypen können bei der Vererbung teilnehmen und Objekt
Identity (obwohl die Objektidentität des einen geschachtelten Werttyp verwenden
wird nicht empfohlen).

Werttypen eng Modell der C (C++)-Konzept einer Struktur (oder
C++-Klasse).
Wie C können Sie Zeiger auf Werttypen, haben aber die
Zeiger sind ein Typ, der den Typ der Struktur unterscheiden.

###Ausnahmen

Eine andere allgemeine Programmierung Konstrukt, das direkt die CLR unterstützt
ist Sie Ausnahmen.
Ausnahmen sind eine Sprachfunktion, die Programmierern zu ermöglichen
um *löst* ein beliebiges Objekt dann, wenn ein Fehler auftritt.
When
ein Objekt ausgelöst wird, durchsucht die Common Language Runtime die Aufrufliste für eine Methode
deklariert, dass es kann *catch* der Ausnahme.
Wenn eine solche catch
Deklaration gefunden wird, wird die Ausführung von diesem Punkt fortgesetzt.
Die
Nutzen von Ausnahmen besteht darin, dass sie den häufigen Fehler vermeiden
keine Überprüfung, wenn eine aufgerufene Methode fehlschlägt.
Vermeiden Sie angesichts der Tatsache, dass Ausnahmen-Hilfe
Programmierer Fehler (wodurch Programmierung vereinfachen), ist es nicht
überrascht, dass die CLR unterstützt.

Übrigens während Ausnahmen ein häufig auftretender Fehler (keine Überprüfung für vermeiden.
Fehler), sie verhindern nicht, dass eine andere (Datenstrukturen zum Wiederherstellen einer
Konsistenz bei Auftreten eines Fehlers).
Dies bedeutet, dass nach einer
Ausnahme abgefangen wird, ist es schwierig in der Regel wissen, ob Sie den Vorgang fortsetzen
Ausführung bewirkt weitere Fehler (verursacht durch den ersten Fehler).
Dies ist ein Bereich, in dem die CLR Mehrwert in Zukunft wahrscheinlich ist.
Sogar
wie derzeit implementiert sind jedoch Ausnahmen ein großer Schritt vorwärts
(es muss nur noch weiter gehen).

###Parametrisierte Typen (generische Typen)

Vor Version 2.0 der CLR wurden die einzigen parametrisierten Typen
Arrays.
Alle anderen Container (z. B. Hashtabellen, Listen, Warteschlangen usw.),
alle auf einem generischen Objekttyp betrieben werden.
Die Unfähigkeit, die Liste zu erstellen oder
Wörterbuch war sicherlich einen Effekt negativ auf die Leistung, da Wert
Typen, die auf den Eintrag geschachtelt werden, um eine Auflistung und eine explizite Umwandlung erforderlich
Datenabruf vom Element wurde benötigt werden.
Dennoch ist, die nicht das Überschreiben
Der Grund für die CLR parametrisierte Typen hinzugefügt.
Der Hauptgrund ist
 **parametrisierte Typen erleichtern Programmierung**.

Der Grund dafür ist die feine.
Die einfachste Möglichkeit, die Auswirkung ist
Stellen Sie sich vor, wie eine Klassenbibliothek aussehen würde, wenn alle Typen ersetzt wurden.
mit einem generischen Objekttyp.
Dieser Effekt ist nicht im Gegensatz zu, was geschieht, in
dynamisch typisierte Sprachen wie JavaScript.
In einer perfekten Welt sind
ganz einfach weitere Methoden für einen Programmierer falsch (aber typsicherer) vornehmen.
Programme.
Ist der Parameter für diese Methode sollte eine Liste sein?
a
Zeichenfolge?
eine ganze Zahl?
alle oben genannten?
Es ist nicht mehr aus
betrachten die Signatur der Methode.
Noch schlimmer ist, wenn eine Methode gibt ein
-Objekt, welche anderen Methoden als Parameter akzeptiert werden können?
Typisch
Frameworks haben Hunderte von Methoden. Wenn sie alle Parameter des Typs annehmen
Objekt, wird es sehr schwierig, welche Objektinstanzen zu bestimmen.
gelten für die Vorgänge, die die Methode ausgeführt wird.
Kurz gesagt, starke
Eingabe-Hilfe ein Programmierer seine Absichten klarer express und ermöglicht
Tools (z. B. Compiler) seine Absicht zu erzwingen.
Dies führt zu groß
Produktivität.

Diese Vorteile werden ausgeblendet, nur weil der Typ abgelegt Ruft ein
Liste oder ein Wörterbuch, haben also deutlich parametrisierte Typen-Wert.
Die
nur die eigentliche Frage ist, ob parametrisierte Typen am besten als betrachtet werden
eine bestimmte Sprache-Funktion das ", bis zu dem Zeitpunkt kompiliert wird" wird die CIL
generiert, oder ob diese Funktion erstklassige Unterstützung verfügen soll
die Common Language Runtime.
Implementierung ist sicherlich möglich.
Das CLR-team
Erstklassige Unterstützung ausgewählt haben, da ohne sie parametrisierte Typen würde
verschiedene Sprachen unterschiedlich implementiert werden.
Dies bedeutet
die Interoperabilität ist bestenfalls umständlich sein.
Außerdem:
Ausdrücken Programmierers für parametrisierte Typen ist am nützlichsten
*an der Schnittstelle* einer Klassenbibliothek.
Wenn die CLR nicht offiziell haben
parametrisierte Typen zu unterstützen, und Klassenbibliotheken nicht verwenden können,
und eine wichtige Nutzbarkeit Funktion würde verloren.

###Programme wie Daten (Reflektions-APIs)

Die Grundlagen der CLR werden Garbagecollection, Sicherheit und
Allgemeine Sprachfeatures.
Diese grundlegenden Eigenschaften erzwungen der
die Spezifikation des Programms (CIL) relativ hohen sein.
Einmal
Diese Daten vorhanden waren, zur Laufzeit (etwas nicht richtig für C- oder C++
Programme), wurde offensichtlich, dass es wäre auch wertvolle verfügbar machen
Diese umfangreichen Daten für End-Programmierer.
Diese Idee führte das Erstellen von
die System.Reflection-Schnittstellen (so genannte, da sie ermöglichen die
Programm ansehen (bei angezeigt) selbst).
Diese Schnittstelle ermöglicht es Ihnen
Untersuchen Sie nahezu alle Aspekte eines Programms (besitzt, welche die
vererbungsbeziehung und welche Methoden und Felder vorhanden sind).
In
Tatsächlich ist so wenig Informationen, sehr gut "Dekompilierungsprogramme sind unter" für verloren
verwalteter Code möglich sind (z. B. [NET
Reflector](http://www.red-gate.com/products/reflector/)).
Während die
geistiges Eigentum kümmern Schutz sind auf dieser aghast
Funktion (die behoben werden kann, indem Sie absichtlich Zerstören von Informationen
durch einen Vorgang aufgerufen *verbergen* des Programms), die Tatsache, dass die It
ist möglich, ist ein Beweis für die Vielfalt der verfügbaren Informationen
zur Laufzeit in verwaltetem Code.

Zusätzlich zum Prüfen von Programmen einfach zur Laufzeit, ist es auch
Diese Operationen möglich (z. B. Methoden aufrufen, festlegen
Felder usw.), und vielleicht am häufigsten Beschleunigungshardware zum Generieren von Code aus
Wenn Sie Grund zur Laufzeit (System.Reflection.Emit) auf.
Tatsächlich führt die Common Language runtime
Bibliotheken verwenden diese Funktion zum Erstellen von speziellen Code für den Abgleich
Zeichenfolgen (System.Text.RegularExpressions), und zum Generieren von Code
"Serialisierung" Objekte in einer Datei speichern oder über das Netzwerk senden.
Funktionen, wie dies einfach unmöglich ist, bevor Sie wurden (müssten Sie
Schreiben eines Compilers!)
aber Dank der Laufzeit sind auch in reach
viele weitere Programmierprobleme.

Reflektionsfunktionen tatsächlich ein leistungsfähiges Tool sind, sollte die Möglichkeit sein.
mit Vorsicht verwendet werden.
Reflektion ist in der Regel erheblich langsamer als die
statisch kompilierte Gegenstücke.
Vor allem auf sich selbst verweisende
Systeme sind grundsätzlich schwerer zu verstehen.
Dies bedeutet, dass leistungsstarke
Features wie Reflektion oder Reflection.Emit nur sein sollte verwendet werden, wenn
der Wert ist klar und umfangreiche.

Andere Funktionen
-----------------

Die letzte Gruppierung von Common Language Runtime-Funktionen sind diejenigen, die nicht mit verknüpft sind
die grundlegende Architektur der CLR (GC, Sicherheit, auf hoher Ebene
Spezifikation), aber trotzdem wichtig ausfüllen muss aller abgeschlossen
Common Language Runtime-System.

Interoperation mit nicht verwaltetem Code
-----------------------------------------

Verwalteten Code muss implementierten Funktionen verwenden können
nicht verwalteten Code.
Es gibt zwei wichtigste "Typen" gesehen.
Zunächst ist.
die Möglichkeit, einfach zu nicht verwaltete Funktionen aufgerufen werden (Dies wird Plattform aufgerufen
Rufen Sie PInvoke).
Nicht verwalteter Code verfügt auch über einen objektorientierten Modells von
aufgerufen von COM (Component-Objektmodell) mit mehr Interoperation
die Struktur als ad-hoc-Methodenaufrufe.
Da sowohl COM-als auch die CLR verfügen.
Modelle für Objekte und andere Konventionen (wie Fehler behandelt werden,
Lebensdauer von Objekten usw.), die CLR ist möglich, eine bessere Interoperabilität von Auftrag
com-Code, wenn sie spezielle hat unterstützen.

Der Time-Kompilierung fort
--------------------------

In der CLR-Modell wird verwalteter Code als CIL nicht systemeigenen Code verteilt.
Die Übersetzung in systemeigenen Code wird zur Laufzeit.
Zur Optimierung der
systemeigenen Code, der aus der CIL generiert wird, kann in einer Datei mit gespeichert werden
ein Tool namens Crossgen (ähnlich wie .NET Framework NGEN-Tool).
Dies
große Datenmengen Kompilierung zur Laufzeit vermieden und sehr
wichtig, da die Klassenbibliothek so groß ist.

Threading
---------

Die CLR erwartet vollständig Multithread-Programme in unterstützen müssen.
verwalteter Code.
Ab dem Anfang die CLR-Bibliotheken enthalten die
System.Threading.Thread-Klasse eine 1: 1-Wrapper über die
Betriebssystem-Konzept für einen Thread der Ausführung.
Allerdings ist es
einfach ein Wrapper über die Betriebssystem-Thread Erstellen einer
System.Threading.Thread ist relativ aufwändig (sie dauert Millisekunden
zum Starten).
Dies ist zwar gut für viele Vorgänge, eine Art der
Programmierung erstellt (nur zehn dauert sehr kleine Arbeitsaufgaben
Zeit in Millisekunden).
Dies geschieht häufig im Servercode (z. B. jede Aufgabe ist
für nur eine Webseite) oder im Code, der versucht, nutzen
mit mehreren Prozessoren (z. B. eine Multi-Core-Sort-Algorithmus).
Um dies zu unterstützen,
die CLR verfügt über einen ThreadPool WorkItems, wodurch das Konzept
in der Warteschlange.
Die CLR in diesem Schema ist verantwortlich für das Erstellen der
erforderlichen Threads zu arbeiten.
Während die CLR verfügbar macht die
ThreadPool direkt als die System.Threading.Threadpool-Klasse, die
bevorzugte Methode ist die Verwendung der [Task Parallel
Bibliothek] (https://msdn.microsoft.com/en-us/library/dd460717 (v=vs.110).aspx),
die zusätzliche Unterstützung für häufige Formen der Parallelität wird hinzugefügt
abgerufen werden.

Aus Implementierungssicht ist die wichtige Neuerung in der
ThreadPool besteht darin, dass sie sicherstellen, dass die optimale verantwortlich ist
Anzahl der Threads wird die Arbeit verteilt.
Die CLR überprüft dazu verwenden
eine Feedbacksystem, in dem es sich um den Durchsatz und die Anzahl überwacht
von threads und passt die Anzahl der Threads, um den Durchsatz zu maximieren.
Dies ist sehr praktisch, da jetzt Programmierer, vor allem hinsichtlich der vorstellen können
"Offenlegen von Parallelität" (d. h. das Erstellen von Arbeitsaufgaben), anstatt die
Subtiler Frage bestimmen die richtige Menge an Parallelität
(abhängig von der Arbeitslast und die Hardware, auf der das Programm ist
Führen Sie).

Zusammenfassung und Ressourcen
------------------------------

Phew!
Die Common Language Runtime ist viel!
Er hat viele Seiten einfach zum Beschreiben übernommen.
*einige* Features der Laufzeit, ohne selbst Sprechen starten
zu den internen Details.
Hoffentlich ist jedoch, die in dieser Einführung
Stellt einen angemessenen Rahmen für ein besseres Verständnis davon zur Verfügung
interne Details.
Die grundlegende Gliederung dieses Framework ist:

-   Die Laufzeit ist ein vollständiges Framework für die Unterstützung von Programmiersprachen
-   Die Common Language Runtime-Ziel ist es, die Programmierung zu erleichtern.
-   Die wichtigsten Features der Laufzeit sind:
-   Garbage Collection
-   Speicher und Sicherheit
-   Unterstützung für High-Level-Sprachfunktionen

Hilfreiche Links
----------------

-   [MSDN-Eintrag für die CLR](http://msdn.microsoft.com/library/8bs2ecf4.aspx)
-   [Wikipedia-Eintrag für die CLR](http://en.wikipedia.org/wiki/Common_Language_Runtime)
-   [ECMA-Standard für die Common Language Infrastructure CLI](dotnet-standards.md)
-   [.NET Framework-Entwurfsrichtlinien](http://msdn.microsoft.com/en-us/library/ms229042.aspx)


<div id="livefyre-comments"></div>
<script type="text/javascript" src="//zor.livefyre.com/wjs/v3.0/javascripts/livefyre.js" data-do-not-move="true"></script>
<script type="text/javascript" data-do-not-move="true">
  (() {}-Funktion
    Var ArticleId = fyre.conv.load.makeArticleId(null);
    fyre.conv.Load ({} [{}
      EL: 'Livefyre-Kommentare'
      Netzwerk: "livefyre.com",
      SiteId: "377988"
      ArticleId: ArticleId,
      signiert: false
      CollectionMeta: {}
        ArticleId: ArticleId,
        URL: fyre.conv.load.makeCollectionUrl(),
      }
    }], function() {});
  }());
</script>





