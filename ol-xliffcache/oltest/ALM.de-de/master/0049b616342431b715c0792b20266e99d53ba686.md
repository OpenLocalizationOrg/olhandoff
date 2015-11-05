Einführung in die .NET
======================

Durch umfangreiche Lander, Zlatko Knezevic

.NET ist eine Entwicklungsplattform für allgemeine Zwecke.
Hiermit können Sie für alle
Art der app-Typ oder die Arbeitsauslastungsgruppe, in denen Lösungen für allgemeine Zwecke verwendet werden.
Er hat mehrere wichtige Features, die für viele Entwickler verlockend,
Automatische Speicherverwaltung und moderner Programmiersprachen einschließlich
die erleichtern qualitativ hochwertige apps effizient zu erstellen.
.NET ermöglicht
eine allgemeine Programmierumgebung mit vielen Features der Einfachheit halber
Beim Bereitstellen von Low-Level-Zugriff auf systemeigene Arbeitsspeicher und APIs.

Mehrere Implementierungen von .NET sind verfügbar, basierend auf Open [.NET
Standards](https://github.com/dotnet/coreclr/blob/master/Documentation/dotnet-standards.md)
angeben, dass die Grundlagen der Plattform.
Sie sind getrennt
optimiert für andere app-Typen (z. B. Desktop, mobil, Spiele, Cloud)
und viele Chips unterstützen (z. B.: X 86/X 64, ARM) und Betriebssystemen (z. B.
Windows, Linux, iOS, Android, OS X).
Open-Source ist auch eine wichtige
Teil der Ökosystem .NET mit mehreren Implementierungen von .NET und viele
Bibliotheken unter OSI genehmigten Lizenzen verfügbar sind.

Sie können sehen Sie sich das... /Getting-Started/Overview Dokument
alle von den verschiedenen Versionen von .NET Framework, die herausfinden
verfügbar von Microsoft und andere.

Wichtige .NET-Konzepte
----------------------

Es gibt eine bestimmte Anzahl von Konzepten, die äußerst wichtig sind
Verstehen Sie, wenn Sie die neu sind.
Diese Begriffe sind die
Eckpfeiler der gesamten Plattform und verstehen sie am Anfang
für allgemeine Kenntnisse der Funktionsweise von .NET beachtet werden.

-   [Verwalteter Code](managed-code.md)
-   [Allgemeines Typsystem](common-type-system.md)
-   [Die Common Language runtime](common-language-runtime.md)
-   [Basisklassenbibliothek](framework-libraries.md)

Einen Spaziergang über .NET
---------------------------

Wie alle Reifen und erweiterte Anwendungsentwicklungs-Framework hat
viele leistungsstarke Features, die die Arbeit von Entwicklern erleichtern und zielt darauf ab
Stellen Sie leistungsfähigere und das Schreiben von Code.
In diesem Abschnitt werden
Gliedern Sie die Grundlagen der herausragendsten Features und gelangen Sie zu
Ausführlichere Diskussionen bei Bedarf.
Nach Abschluss dieser Spaziergang Sie
sollte keine ausreichenden Informationen werden sollen, lesen Sie die Beispiele auf unsere
GitHub-Repositorys sowie anderen code und verstehen, was passiert.

-   Automatische Speicherverwaltung
-   Sicherheit
-   Der verwalteten compiler
-   Delegaten und Lambda-Ausdrücke
-   Generische Typen (generische Typen)
-   LINQ
-   Asynchrone Unterstützung
-   Dynamische Sprachfeatures
-   Codeverträge
-   Systemeigene Interoperabilität

###Automatische Speicherverwaltung

Garbagecollection ist das bekannteste ASP.NET-Funktionen.
Entwickler
müssen Sie keine Speicher aktiv zu verwalten zwar, sodass eine Rationellere sind
Weitere Informationen zu der Garbage Collector (GC) bereitgestellt.
C\-enthält die
`neue` Schlüsselwort in Bezug auf einen bestimmten Typ, Speicher und die
`mit` Schlüsselwort, um den Bereich für die Verwendung des Objekts bereitzustellen.
Der GC
eine verzögerte Ansatz für die Speicherverwaltungsfunktionen, vorzugsweise jedoch die Anwendung ausgeführt wird
der Durchsatz der unmittelbaren Auflistung des Speichers.

Die folgenden beiden Zeilen sowohl Speicher:

``` csharp
var title = ".NET Primer";
var list = new List<string>;
```

Es ist kein Schlüsselwort entspricht, Zuweisen von Arbeitsspeicher, als die Aufhebung der Zuordnung aufheben
erfolgt automatisch, wenn der Garbage Collector den Speicher freigibt
Mithilfe der geplanten Ausführung.

Variablen Methode normalerweise den Gültigkeitsbereich nach Abschluss eine Methode an
welchem Punkt sie gesammelt werden können.
Allerdings können Sie in den globalen Katalog angeben
dass ein bestimmtes Objekt außerhalb des Gültigkeitsbereichs, schneller als die Verwendung von Methode beenden liegt
die `mit` Anweisung.

``` csharp
using(FileStream stream = GetFileStream(context))
{
    //operations on the stream
}
```

Einmal die `mit` Block abgeschlossen hat, kann die Freispeichersammlung erkennen, dass die `Stream`
Objekt im obigen Beispiel ist kostenlos gesammelt werden und der Arbeitsspeicher
freigegeben.

Einer der weniger offensichtlichen aber ziemlich weit reichende Funktionen, die eine Garbage
Sammlung ermöglicht wird für speichersicherheit.
Ist die invariante Arbeitsspeicher-Sicherheit
sehr einfach: ein Programm Speicher sicher ist, wenn es nur Speicherzugriffe,
reserviert (und nicht freigegeben) wurde.
Verbleibendes Zeiger sind immer Fehler,
und verfolgen sie Sie nach unten ist oft schwierig.

.NET Runtime bietet zusätzliche Dienste, um das Versprechen abzuschließen.
der für speichersicherheit, natürlich nicht von einem globalen Katalog angeboten werden.
Es wird sichergestellt, dass
Programme indizieren nicht über das Ende eines Arrays oder zugreifen auf phantom
Feld über das Ende eines Objekts.

Im folgende Beispiel wird durch das speichersicherheit ausgelöst.

``` csharp
int[] numbers = new int[42];
int number = numbers[42]; // will throw (indexes are 0-based)
```

###Sicherheit

Objekte, die im Hinblick auf Typen zugeordnet werden.
Die einzigen Operationen zulässig für.
ein angegebenes Objekt und den Speicher, den er nutzt, den werden von deren Typ.
A
`Hund` Typ möglicherweise `springen` und `WagTail` Methoden, aber wahrscheinlich kein
`SumTotal` Methode.
Ein Programm kann nur die deklarierten Methoden Aufrufen einer
angegebenen Typ.
Alle anderen Aufrufe führt entweder zu einem Fehler während der Kompilierung
oder eine Laufzeitausnahme (bei einem dynamischen Funktionen oder `Objekt`).

.NET Sprachen kann objektorientierten, mit der Basis-Hierarchien und
abgeleitete Klassen.
.NET Runtime wird nur Objekt Umwandlungen und Aufrufe zulassen.
die Hierarchie der Objekte, die ausgerichtet.
Beachten Sie, dass jeder Typ definiert.
in jeder Sprache abgeleitet wird, von zentralen `Objekt` Typ.

``` csharp
Dog dog = Dog.AdoptDog(); // Returns a Dog type
Pet pet = (Pet)dog; // Dog derives from Pet
pet.ActCute();
Car car = (Car)dog; // will throw - no relationship between Car and Dog
object temp = (object)dog; // legal - a Dog is an object
car = (Car)temp; // will throw - the runtime isn't fooled
car.Accelerate() // the dog won't like this, nor will the program get this far
```

Sicherheit wird auch verwendet, um die Kapselung und garantiert erzwingen
die Genauigkeit der Accessor Schlüsselwörter.
Accessor-Schlüsselwörter sind Artefakte
Zugriff auf Member eines bestimmten Typs von anderem Code steuern.
Dies sind
für verschiedene Arten von Daten innerhalb eines Typs, die verwendet werden, um verwendet in der Regel.
Verwalten Sie ihr Verhalten.

``` csharp
Dog dog = Dog._nextDogToBeAdopted; // will throw - this is a private field
```

Einige Sprachen .NET unterstützen **den Typrückschluss**.
Geben Sie Typrückschluss bedeutet
dass der Compiler den Typ des Ausdrucks auf abzuleiten wird die
linke Seite aus dem Ausdruck auf der rechten Seite.
Dies ist
bedeutet, dass die Sicherheit von vermieden oder beschädigt ist.
Der resultierende Typ
**hat** einen starken Typ mit allem impliziert.
Schreiben Sie uns die
zunächst zwei Zeilen des vorherigen Beispiels Typrückschluss einführen.
Benutzer
Beachten, dass der Rest des Beispiels vollständig identisch ist.

``` csharp
var dog = Dog.AdoptDog();
var pet = (Pet)dog;
pet.ActCute();
Car car = (Car)dog; // will throw - no relationship between Car and Dog
object temp = (object)dog; // legal - a Dog is an object
car = (Car)temp; // will throw - the runtime isn't fooled
car.Accelerate() // the dog won't like this, nor will the program get this far
```

###Delegaten und Lambda-Ausdrücke

Delegaten ähneln C++-Funktionszeigern, die mit einem großen Unterschied, die
Sie sind typsicher.
Sie sind eine Art von getrennten Methode innerhalb der
CLR-Typsystem.
Reguläre Methoden sind mit einer Klasse verknüpft ist und nur
durch statische oder die aufrufende Instanz direkt aufgerufen Konventionen.

Delegaten sind in verschiedenen APIs und stellen in der .NET Welt verwendet,
vor allem über Lambda-Ausdrücke, die ein Kernstück von Linq sind.

Lesen Sie mehr dazu im Delegaten Lambdas Dokument.

###Generische Typen (generische Typen)

Generische Typen sind bzw. "Generika" eine Funktion, die in .NET hinzugefügt wurde
Framework 2.0.
Kurz gesagt, generischen Typen können Programmierer einführen einer
"Parameter vom Typ" Wenn ihre Klassen zu entwerfen, bei denen die
Client (d. h. die Benutzer des Typs) Geben Sie den exakten Typ zu code
Verwenden Sie anstelle der Type-Parameter.

Generika wurden hinzugefügt, damit Programmierer generische Daten implementieren können
Strukturen.
Vor ihrer Ankunft, in der Reihenfolge für ein, z. B. Listentyp werden
generisch, müssten sie mit Elementen arbeiten, die vom Typ Object waren.
Dies würde nicht zu verschiedenen Leistung als auch als semantische Probleme haben
Erwähnen Sie mögliche feine Laufzeitfehler.
Die zweite bekannteste
Wenn eine Datenstruktur, z. B. sowohl ganze Zahlen enthält, und
Zeichenfolgen und eine InvalidCastException-Ausnahme wird ausgelöst, zum Arbeiten mit der
in der Liste enthaltenen Elemente.

Die im folgenden Beispiel wird ein basic-Programm ausgeführt wird, die mit einer Instanz von
Liste & Lt; T & Gt; Typen.

``` csharp
using System;
using System.Collections.Generic;

namespace GenericsSampleShort {
    public static void Main(string[] args){
        // List<string> is the client way of specifying the actual type for the type parameter T
        List<string> listOfStrings = new List<string> { "First", "Second", "Third" };

        // listOfStrings can accept only strings, both on read and write.
        listOfStrings.Add("Fourth");

        // Below will throw a compile-time error, since the type parameter
        // specifies this list as containing only strings.
        listOfStrings.Add(1);

    }
}
```

Lesen Sie mehr darüber in der Generika-Dokument.

###Asynchrone Programmierung

Async ist ein erstklassiges Konzept in .NET mit Async-Unterstützung in der
Common Language Runtime, die Framework-Bibliotheken und verschiedene Sprachen für .NET.
Async ist.
Deaktivieren der Basis der `Aufgabe` Konzept, das eine Reihe von Vorgängen kapselt
abgeschlossen werden.
Aufgaben unterscheiden sich von Threads und möglicherweise nicht
Threads oder erfordern CPU Zeit viel, insbesondere für e/A-gebundenen
Aufgaben.

TODO: Konzept weiter auszuführen.

C\-beinhaltet eine besondere Behandlung für asynchrone, einschließlich das spezielle Schlüsselwort
`"await"` für die Verwaltung von Aufgaben.
Das folgende Beispiel veranschaulicht den Aufruf einer
Webdienst-Endpunkt als ein asynchroner Vorgang.

``` csharp
    string url = "http://someUrl";
    HttpClient client = new HttpClient();
    string json = await client.GetStringAsync(url);
```

Der Aufruf von `Client. GetStringAsync(url)` nicht blockiert, sondern stattdessen
sofort nach der Rückgabe ergibt ein `Aufgabe`.
Berechnung fortgesetzt und die
Aufruf zurückgegeben die angeforderte Zeichenfolge hat die Netzwerkaktivität
abgeschlossen.

###Language Integrated Query (LINQ)

.NET Programme, die in der Regel eine Form der Daten ausgeführt werden.
Die Daten werden können
Datenbank-Residenter oder in Form von Objekten (bezeichnet POCOs für
"Plain Old CLR Objects").
LINQ stellt ein einheitliches sprachintegrierte bereit.
Query-Modell über Daten, unabhängig von der Quelle.
LINQ-Anbieter-Brücke
die Lücke zwischen dem einheitlichen Abfragemodell und die Form der Daten, solche
als SQL Server-Tabellen XML dokumentiert, standard Sammlungen wie List und
Weitere.

Die folgenden Beispielen veranschaulichen verschiedene Verwendungen von LINQ zu verschiedenen Abfrage
Formen von Daten.

TODO: Abschnitt abzuschließen, Verknüpfen mit einer ausführlicheren Dokument.

###Dynamische Sprachfeatures

TODO: "Fertig stellen" im Abschnitt

###Codeverträge

TODO: "Fertig stellen" im Abschnitt

###Systemeigene Interoperabilität

.NET bietet einfachen Zugriff auf systemeigene APIs über die Plattform aufrufen oder
P/Invoke-Funktion.
Dies ermöglicht eine Zuordnung von .NET-Typen zu systemeigenen Typen,
die .NET Runtime Funktionsaufruf vor dem Aufruf der systemeigenen API.

TODO: Beispiele.

Mit P/Invoke werden auf höherer Ebene systemeigenen Interop hergestellt.
Die COM
und WinRT-interop-Systeme in der CLR werden sowohl über P/Invoke erstellt.
Die Java und Objective-C Interop-Systeme, die Xamarin auf der Basis von
Mono sind im Wesentlichen identisch.

####Unsicherer Code

Die CLR ermöglicht die Möglichkeit des Zugriffs systemeigenen Speicher, und führen Sie Zeiger
arithmetische Operationen.
Diese Vorgänge sind für einige Algortithms und erforderlich.
Aufrufen von einige systemeigene APIs.
Die Verwendung dieser Funktionen ist nicht empfehlenswert,
Da Sie nicht mehr die Vorteile Überprüfbarkeitsstufe, noch wird Ihr code
zugelassen Sie in allen Umgebungen ausführen werden.
Die bewährte besteht Methode darin, zu beschränken
unsicheren Code so weit wie möglich und die große Mehrheit der Code ist.
typsicher.

TODO: Beispiele.

Notizen
-------

Der Begriff ".NET Runtime" wird im gesamten Dokument verwendet, um die Anpassung an
für mehrere Implementierungen von .NET CLR, Mono, IL2CPP und
andere.
Die über spezifischeren Namen werden nur bei Bedarf verwendet.

Dieses Dokument richtet sich keine Verlaufsdaten Natur sein, aber beschreiben
wie sie objektorientiert ist jetzt.
Es ist nicht wichtig, ob .NET
Feature ist seit jeher verfügbar oder erst vor kurzem eingeführt wurde, nur
Es ist wichtig genug ist, markieren und besprechen.
####Wir testen

####Kommentare

<div id="disqus_thread"></div>
<script type="text/javascript">
  KONFIGURATIONSVARIABLEN: VOR DEM EINFÜGEN IN IHRE WEBSEITE ZU BEARBEITEN
  Var Disqus_Shortname = 'Devdivcn'; / / erforderlich: Ihr Forum Shortname Beispiel ersetzen
  UNTERHALB DIESER ZEILE BEARBEITEN
  (function() {}
    Var Dsq = document.createElement('script'); dsq.Type = "Text/Javascript"; dsq.Async = True;
    dsq.Src = ' / /' + Disqus_Shortname + '.disqus.com/embed.js';
    (document.getElementsByTagName('head') [0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
  })();
  </script>
<noscript>
            Aktivieren Sie JavaScript zum Anzeigen der 
            <a href="http://disqus.com/?ref_noscript">Kommentare, unterstützt von Disqus.</a>
          </noscript>





