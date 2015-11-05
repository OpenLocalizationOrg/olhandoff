.NET Assembly-Dateiformat
=========================

Objektorientiert definiert ein binäres Dateiformat - "Assembly" -, mit dem vollständig beschreiben und .NET Programme enthalten.
Assemblys werden für die Programme selbst als auch für alle abhängigen Bibliotheken verwendet.
Ein Programm .NET kann als eine weitere Assemblys mit keinen anderen erforderlichen Artefakte, über die entsprechenden .NET Runtime ausgeführt werden.
Systemeigene Abhängigkeiten von Betriebssystem-APIs, einschließlich sind separate relevant und werden nicht in das .NET Assembly-Format enthalten, jedoch manchmal mit diesem Format (z. B. WinRT) beschrieben werden.

> Jede CLI-Komponente führt die Metadaten für Deklarationen und Implementierungen bestimmte Verweise auf diese Komponente.
> Daher wird die komponentenspezifischen Metadaten als Komponentenmetadaten bezeichnet, und die resultierende Komponente gilt als--von ECMA 335 I.9.1, Komponenten und Assemblys selbstbeschreibende werden.

Das Format ist vollständig angegeben und als standardisiert [ECMA-335](dotnet-standards.md).
Verwenden Sie dieses Format, alle .NET Compiler und Laufzeiten.
Die Presense von einem binären Format dokumentiert und unregelmäßig aktualisierte wurde ein großer Vorteil (wohl erforderlich) für die Interoperabilität der Netze.
Das Format wurde zuletzt materiellen Weise im Jahr 2005 (.NET 2.0) für Generika und Prozessorarchitektur aktualisiert.

Das Format ist unabhängig von CPU und Betriebssystem.
Es wurde als Teil des .NET Laufzeiten verwendet, die viele Chips und CPUs abzielen.
Auch das Format selbst Windows Erbe hat, ist es unter jedem Betriebssystem implementiert.
Der wohl wichtigste Wahl für OS-Interopertability ist, dass die meisten Werte im little-Endian-Format gespeichert werden.
Er verfügt nicht über eine bestimmte Affinität für die Größe des Zeigers Computer (z. B. 32-Bit, 64-Bit).

Das .NET Assembly-Format ist auch über die Struktur einer bestimmten Anwendung oder Bibliothek sehr aussagekräftig.
Es beschreibt die internen Komponenten einer Assembly speziell: Assemblyverweise und definierten Typen und deren interne Struktur.
Tools oder-APIs kann lesen und verarbeiten diese Informationen für die Anzeige oder programmgesteuerte Entscheidungen treffen.

Format
------

Das Binärformat .NET basiert auf der Windows [PE-Datei](http://en.wikipedia.org/wiki/Portable_Executable) Format.
In der Tat Klassenbibliotheken für .NET konforme Windows PE-Dateien sind und auf den ersten Blick auf Windows dynamic Link Libraries (DLLs) oder ausführbaren Dateien der Anwendung (EXE-Dateien) werden angezeigt.
Dies ist ein sehr nützlich Merkmal unter Windows, wo sie agieren als systemeigene ausführbare Binärdateien und einige der hier genauso vor (z. B. Betriebssystem laden, PE-Tools) erhalten können.

Assembly-Header Assemblys Header von ECMA 335 II.25.1, Struktur des Formats der Laufzeitdatei.

Verarbeiten von Assemblys
-------------------------

Es ist möglich, Tools oder APIs in Prozess-Assemblys zu schreiben.
Assemblyinformationen ermöglicht programmgesteuerten Entscheidungen zur Laufzeit, Assemblys erneut zu schreiben, API-Intellisense in einem Editor bereitstellen und Generieren von Dokumentation.
[System.Reflection](https://msdn.microsoft.com/library/system.reflection.aspx) und [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) sind gute Beispiele für Tools, die häufig für diesen Zweck verwendet werden.




