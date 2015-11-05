Installieren von .NET Core auf OS X
===================================

Von Zlatko Knezevic

Diese Anleitung führt Sie durch den Erwerb .NET Core DNX SDK
über die [.NET Version Manager (DNVM)](https://github.com/aspnet/dnvm)
und eine "Hello World" Demo auf OS X ausgeführt.

.NET Core NuGet-Pakete und die .NET Core DNX SDKs finden Sie auf der
[Feed von ASP.NET "Vnext" Myget](https://www.myget.org/F/aspnetvnext), mit dem
Sie können einfacher auf anzeigen.
[Katalog](https://www.myget.org/gallery/aspnetvnext) für den Feed.

Installieren von DNVM
---------------------

Sie benötigen DNVM als Ausgangspunkt.
DNVM ermöglicht es Ihnen, eine abzurufen oder
mehrere .NET Ausführung Umgebungen (DNX).
DNVM ist einfach ein Skript,
die .NET abhängig ist.
Auf OS X eignet sich zum Abrufen von DNVM verwenden
[Homebrew](http://www.brew.sh).
Wenn Sie keine Homebrew installiert haben
Führen Sie dann die [Homebrew Installation
Anweisungen](http://www.brew.sh).
Wenn Ihre Homebrew einsatzbereit
Sie können die folgenden Befehle:

``` console
brew tap aspnet/dnx
brew update
brew install dnvm
```

Sie müssen wahrscheinlich den Dnvm-Befehl zu registrieren:

``` console
source dnvm.sh
```

Installieren der .NET Core DNX
------------------------------

Da .NET Core noch In Bearbeitung ist, müssen Sie verwenden
der [Mono](http://www.mono-project.com) bestimmte Teile der DNX ausführen
Tools.
Bei nicht-Windows-Betriebssystemen ist Mono DNX, standardmäßig also
können Sie eine einfache `Dnvm Upgrade` Befehl aus, um es zu installieren.

``` console
dnvm upgrade -u
```

Als Nächstes .NET Core DNX SDK zu erhalten.

``` console
dnvm install latest -r coreclr -u
```

Sehen Sie die aktuell installierten Version von DNX mit `Dnvm Liste`.

``` console
dnvm list
```

``` console
Active Version              Runtime Arch Location             Alias
------ -------              ------- ---- --------             -----
  *    1.0.0-beta5-11649    coreclr x64  ~/.dnx/runtimes
       1.0.0-beta5-11649    mono         ~/.dnx/runtimes      default
```

> **Hinweis:**
> 
> Die oben aufgeführten Versionsnummern ändern können und werden beim Ausführen der
Befehle, die normalerweise der Fall ist.
> Vergessen Sie nicht, verwenden Sie die entsprechenden Zahlen, wenn
Weitere Interaktion mit DNVM in den folgenden Beispielen.

Verwenden einer bestimmten Laufzeit
-----------------------------------

Sie können die von der installierten DNXs auswählen, die, denen Sie mit verwenden möchten.
`Dnvm mit`, Angeben von Argumenten, die ähnliche verwendet werden, wenn
Installieren eine Laufzeit.

``` console
dnvm use -r coreclr -arch x64 1.0.0-beta5-11649
Adding ~/.dnx/runtimes/dnx-coreclr-win-x86.1.0.0-beta5-11649/bin
to process PATH

dnvm list

Active Version              Runtime Arch Location             Alias
------ -------              ------- ---- --------             -----
  *    1.0.0-beta5-11649    coreclr x64  ~/.dnx/runtimes
       1.0.0-beta5-11649    mono         ~/.dnx/runtimes      default
```

Sehen Sie das Sternchen in der obigen Liste?
Es dient, Ihnen mitzuteilen, die
Common Language Runtime ist jetzt aktiv.
"Aktiv" bedeutet hier, dass alle der Aktivität
mit Projekten und .NET Core Verwenden dieser Laufzeit.

Das ist alles!
Sie haben jetzt die auf Ihrem Rechner installierte .NET Core-Laufzeit
und es wird Zeit, die für ein Drehfeld dauert.

Schreiben Sie Ihre App
----------------------

Dieser wird eine Einführung in Dokument scheint es geeignete starten
mit einer Anwendung "Hello World".
Hier ist eine sehr einfache können kopiert und
Fügen Sie in einer CS-Datei in einem Verzeichnis.

``` csharp
using System;

public class Program
{
    public static void Main (string[] args)
    {
        Console.WriteLine("Hello, OS X");
        Console.WriteLine("Love from CoreCLR.");
    }
}
```

Ein Beispiel für ehrgeizigere steht auf der [Corefxlab
Repository](https://www.github.com/dotnet/corefxlab/) das Drucken einer
ziemlich Bild basierend auf das Argument, das Sie zur Laufzeit bereitstellen.
Wenn Sie möchten
Um dieses Beispiel zu verwenden, speichern Sie einfach die [C\-
Datei](https://raw.githubusercontent.com/dotnet/corefxlab/master/demos/CoreClrConsoleApplications/HelloWorld/HelloWorld.cs)
in einem Verzeichnis auf Ihrem Computer.

Als Nächstes Sie müssen eine `project.json` Datei, die beschreiben, werden
die Abhängigkeiten einer App, und Sie können **tatsächlich** ausführen.
Verwenden Sie
Inhalt unten, funktioniert es für beide Beispiele.
Speichern Sie diese Datei in
ein Verzeichnis neben der CS-Datei, die den Code enthält.

``` json
{
    "version": "1.0.0-*",
    "dependencies": {
    },
    "frameworks" : {
        "dnx451" : { },
        "dnxcore50" : {
            "dependencies": {
                "System.Console": "4.0.0-beta-*"
            }
        }
    }
}
```

Führen Sie die App
------------------

Sie müssen für Ihre app, basierend auf Ihrer project.json-Pakete wiederherstellen,
mit `Dnu Wiederherstellung`.
Sie müssen diesen Befehl unter den Mono ausführen
DNX.
Mit dem erste Befehl wechselt aktive Laufzeit, in dem eine Mono.

``` console
dnvm use 1.0.0-beta5-11649 -r mono
dnu restore
```

Sie können nun die Anwendung unter .NET Core auszuführen.
Wie Sie sich denken können,
jedoch, bevor Sie dies tun müssen Sie zuerst in den Kern des .NET wechseln
Common Language Runtime.
Der erste Befehl unten tut genau dies.

``` console
dnvm use 1.0.0-beta5-11649 -r coreclr
dnx . run

Hello, OSX
Love from CoreCLR.
```

Erstellen von .NET Core von Quelle
----------------------------------

.NET Core ist ein open-Source-Projekt, das auf GitHub gehostet wird.
Dies bedeutet, dass
können, an einem bestimmten Zeitpunkt, Klonen Sie das Repository und .NET erstellen
Der Kern von Quelle.
Dies ist ein erweitertes Szenario, das in der Regel verwendet wird
Wenn Sie .NET Runtime oder der BCL-Funktionen hinzufügen möchten, oder wenn Sie
sind Sie an diesen Projekten.
Die ausführliche Anweisung zum
Erstellen von .NET Core Windows Sie in finden der [.NET Core OS X-Build
Anleitung](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
auf GitHub.




