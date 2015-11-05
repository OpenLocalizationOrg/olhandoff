Allgemeines Typsystem & Common Language Specification
=========================================================

Autor: Zlatko Knezevic

In diesem Fall sind zwei Begriffe, die in der .NET Welt kostenlos verwendet werden tatsächlich wichtig zu verstehen, wie die .NET Plattform mehrsprachige Entwicklung ermöglicht und zu verstehen, wie es funktioniert.

Allgemeines Typsystem
---------------------

Um von vorn zu beginnen, beachten Sie, dass die .NET Plattform *sprachunabhängig*.
Dies bedeutet nicht nur, dass Programmierer schreiben kann ihr Code in einer beliebigen Sprache, die kompiliert werden kann IL.
Dies bedeutet auch, dass er muss für die Interaktion mit dem Programmcode in anderen Sprachen, die auf der .NET-Plattform verwendet werden kann.

Hierzu transparent, es muss eine gängige Methode zum alle unterstützte Typen beschrieben.
Dies ist das Common Type System (CTS) für dadurch verantwortlich.
Es wurde versucht, mehrere Dinge tun:

- Richten Sie ein Framework für die sprachübergreifende ausführen.
- Geben Sie einen objektorientierten Modells zur Unterstützung der Implementierung von verschiedenen Sprachen auf.
- Definieren Sie einen Satz von Regeln, die alle Programmiersprachen eingehalten werden müssen, wenn es darum geht, arbeiten mit Typen.
- Geben Sie eine Bibliothek, die grundlegenden primitiven Typen enthält, die bei der Anwendungsentwicklung verwendet werden (d. h. `boolesche`, `Byte`, `Char` usw..)

CTS definiert zwei Hauptarten von Typen, die unterstützt werden sollen: Verweis- und Werttypen.
Zeigen Sie ihre Namen auf ihre Definitionen.

Verweistypen Objekte werden durch einen Verweis auf den tatsächlichen Wert des Objekts dargestellt. Hier ein Verweis ist ähnlich einem Zeiger in C/C++.
Es bezieht sich lediglich auf einen Speicherbereich, in denen Werte der Objekte sind.
Dies hat einen tiefgreifenden Einfluss auf wie diese Typen verwendet werden.
Wenn Sie einen Verweistyp einer Variablen zuweisen und dann die Variable in eine Methode übergeben, z. B. werden alle Änderungen auf das Objekt auf das Hauptobjekt angezeigt; Es gibt keine kopieren.

Werttypen sind das Gegenteil ist der Fall, in dem die Objekte werden durch ihre Vaulues dargestellt.
Wenn Sie eine Variable ein Werttyps zuweisen, kopieren Sie im Grunde einen Wert des Objekts.

CTS definiert verschiedene Kategorien von Typen, jede mit ihren spezifischen Semantik und Nutzung:

- Klassen
- Strukturen
- Enumerationen
- Schnittstellen
- Delegaten

CTS definiert auch alle anderen Eigenschaften der Typen, wie z. B. Zugriffsmodifizierer, worauf gültige Typmember, wie Vererbung und überladen funktioniert und so weiter.
Leider hier tief in die ist Gegenstand einer einführenden Artikel wie diesem lassen, aber Sie können weitere Resources-Abschnitt am Ende Links für weitere fundierte Inhalte, die in diesen Themen werden behandelt.

Common Language Specification
-----------------------------

Um volle Interoperabilitätsszenarien zu ermöglichen, müssen alle Objekte, die im Code erstellt werden auf einigen Gemeinsamkeit in den Sprachen, die sie verbrauchen verlassen (sind ihre *Aufrufer*).
Da es zahlreiche verschiedene Sprachen gibt, wurde .NET Plattform diese gemeinsamkeiten in so genannte angegeben die **Common Language Specification** (CLS).
CLS definiert eine Reihe von Features, die von vielen gängigen erforderlich sind.
Außerdem bietet es eine Art Rezept für jede Sprache, die auf .NET Plattform auf ihn unterstützen muss implementiert wird.

CLS ist eine Teilmenge des CTS.
Dies bedeutet, dass alle Regeln im CTS auch für die CLS gelten, wenn die CLS-Regeln strikter sind.
Wenn eine Komponente erstellt wird, verwenden nur die Regeln in der CLS, d. h., nur die CLS-Features in der API macht, es gilt als **CLS-kompatible**.
Zum Beispiel die & Lt; Framework-Librares & Gt; CLS-kompatibel sind, genau, da sie über alle Sprachen arbeiten, die auf der unterstützt werden müssen.

Finden Sie die Dokumente im Abschnitt "Weitere Ressourcen" unten, erhalten einen Überblick über alle Funktionen, die in der CLS.

Weitere Ressourcen
------------------

- [Allgemeines Typsystem](https://msdn.microsoft.com/en-us/library/vstudio/zcx1eb1e%28v=vs.100%29.aspx)
- [Common Language Specification](https://msdn.microsoft.com/en-us/library/vstudio/12a7a7h3%28v=vs.100%29.aspx)




