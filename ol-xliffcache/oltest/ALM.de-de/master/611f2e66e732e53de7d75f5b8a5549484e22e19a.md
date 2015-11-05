Generische Typen (generische Typen) (Übersicht)
===============================================

Von Kasey Uhlenhuth

Wir verwenden Generika ständig in C\ #, ob implizit von explizit.
Bei Verwendung von LINQ in C\-haben Sie schon einmal bemerkt, mit dem Sie arbeiten
IEnumerable & Lt; T & Gt;?
Oder, wenn Sie alle Säge eines onlinebeispiels eines generischen"
Repository"für die Kommunikation mit Datenbanken, die mit Entity Framework haben Sie gesehen.
dass die meisten Methoden IQueryable & Lt zurück. T & Gt;?
Sie können was gefragt haben
die **T** in diesen Beispielen und warum es vorhanden ist?

In .NET Framework 2.0, beteiligten Änderungen Generika eingeführt.
die C\-Sprache und der Common Language Runtime (CLR).
**Generika** sind im Wesentlichen ein "Code Template", mit dem Entwickler
Definieren
[als typsicherer](https://msdn.microsoft.com/en-us/library/hbzz1a9a%28v=vs.110%29.aspx)
Datenstrukturen ohne einen tatsächlichen Datentyp. Beispiel:
`List < T >` [generisch ist
Collection] (https://msdn.microsoft.com/en-us/library/System.Collections.Generic (v=vs.110).aspx)
deklariert und mit einem beliebigen Typ verwendet werden kann: `List < Int >`,
`Liste < Zeichenfolge >`, `Liste < Person >`, usw..

Was ist der Punkt? Sind Generika hilfreich? Um zu verstehen
Hierzu müssen wir Betrachten einer bestimmten Klasse vor und nach dem Hinzufügen
Generika. Sehen wir uns die `ArrayList`. C\-1.0 die `ArrayList`
Elemente vom Typ wurden `Objekt`. Dies bedeutete, dass jedes Element, das war
hinzugefügt wurde automatisch konvertiert und in ein `Objekt`; gleichen auf das gleiche
Lesen Sie die Elemente aus der Liste (dieser Prozess wird als bezeichnet
[Boxing](https://msdn.microsoft.com/en-us/library/yz2be5wk.aspx) und
Unboxing bzw.). Boxing und unboxing Einfluss von
die Leistung. Mehrere, jedoch besteht keine Möglichkeit zur Kompilierzeit mitteilen
Zeit, was der tatsächliche Typ der Daten in der Liste ist. Dies ist für
Einige unsicherem Code. Generika löst dieses Problem durch die Bereitstellung zusätzlicher
Informationen vom Typ der Daten wird jede Instanz der Liste enthalten. Put
einfach ausgedrückt, können Sie nur hinzufügen zu Ganzzahlen `List < Int >` und nur die Personen hinzufügen
`Liste < Person >`, usw..

Generika sind ebenfalls verfügbar zur Laufzeit oder **reified**.
Dies bedeutet, dass die
Common Language Runtime weiß, welche Art von Datenstruktur verwenden und speichern
im Arbeitsspeicher effizienter.

Hier ist ein kleines Programm, das veranschaulicht, die Effizienz zu wissen, die
Struktur-Datentyp zur Laufzeit:

``` csharp
using System; using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;

namespace GenericsExample
{
    class Program
    {
        static void Main(string\[\] args)
        {
            //generic list
            List ListGeneric = new List { 5, 9, 1, 4 };
            //non-generic list
            ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
            // timer for generic list sort
            Stopwatch s = Stopwatch.StartNew();
            ListGeneric.Sort();
            s.Stop();
            Console.WriteLine(\$"Generic Sort: {ListGeneric} n Time taken: {s.Elapsed.TotalMilliseconds}ms");

            //timer for non-generic list sort
            Stopwatch s2 = Stopwatch.StartNew();
            ListNonGeneric.Sort();
            s2.Stop();
            Console.WriteLine(\$"Non-Generic Sort: {ListNonGeneric} n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
            Console.ReadLine();
        }
    }
}
```

Dieses Programm führt die folgende Ausgabe:

``` console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

Zunächst, den Sie bemerken, dass hier ist dieser generische Liste sortieren
bedeutend schneller als die nicht generische Liste. Sie können auch
Beachten Sie, dass der Typ für die generische Liste distinct (\[System.Int32\])
während Sie der Typ für die nicht generische Liste verallgemeinert werden. Da die
Common Language Runtime kennt den generischen `List < Int >` ist vom Typ Int, speichern sie die
Liste der Elemente im zugrunde liegenden Array von Ganzzahlen im Arbeitsspeicher, während die
nicht generische `ArrayList` jedes Element in der Liste als Objekt als umgewandelt wurde
in einem Objektarray im Arbeitsspeicher gespeichert. Dieses Beispiel zeigt, wie die
Typumwandlungen zusätzliche Zeit beanspruchen und verlangsamt die Liste sortieren.

Als letztes hilfreich zur Laufzeit den Typ der generischen
ist eine bessere Umgebung debuggen.
Wenn Sie eine generische in Debuggen
C\ #, wissen Sie, welchen Typ jedes Element in der Datenstruktur handelt.
Ohne
Generika, keine Ahnung Art müssten Sie jedes Element wurde.

Weitere Informationen und Ressourcen
------------------------------------

-   [Einführung in C\-Generika](https://msdn.microsoft.com/en-us/library/ms379564%28v=vs.80%29.aspx)
-   [C\ Programming Guide - Generika](https://msdn.microsoft.com/en-us/library/512aeb7t.aspx)





