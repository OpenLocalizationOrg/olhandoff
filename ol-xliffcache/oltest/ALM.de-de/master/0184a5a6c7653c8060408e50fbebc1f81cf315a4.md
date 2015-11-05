Installieren von .NET Core unter Windows
========================================

Von Zlatko Knezevic

Dieses Dokument führt Sie durch den Erwerb von .NET Core DNX SDK über
die [.NET Version Manager (DNVM)](https://github.com/aspnet/dnvm) und
eine "Hello World" Demo unter Windows ausgeführt werden.

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
Sie können ihn über eine PowerShell installieren.
der Befehl in ein Eingabeaufforderungsfenster.
Sie können alternative DNVM finden.
Installieren Sie die Anweisungen in der [ASP.NET-Startseite
repo](https://github.com/aspnet/home).

``` powershell
@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&{$Branch='dev';iex ((new-object net.webclient).DownloadString('https://raw.githubusercontent.com/aspnet/Home/dev/dnvminstall.ps1'))}"
```

Das Skript werden mehrere globale Umgebungsvariablen Verwendung mit festgelegt.
In Zukunft einfacher DNVM.
Für diese starten müssen Sie
Starten der Befehlsshell-Sitzungs.

Installieren eine .NET Core DNX
-------------------------------

Es ist einfach, installieren Sie die neuesten .NET Core-basierte DNX mithilfe der
`Dnvm Installation` Befehl.

``` console
dnvm install -r coreclr latest -u
```

Hiermit wird die 32-Bit-Version von .NET Core installiert.
Wenn Sie möchten die
64-Bit-Version können Sie die Prozessorarchitektur angeben.

``` console
dnvm install -r coreclr -arch x64 latest -u
```

Sehen Sie die aktuell installierten Version von DNX mit `Dnvm Liste`.

``` console
dnvm list

 Active Version           Runtime Architecture Location                            Alias
 ------ -------           ------- ------------ --------                            -----
   *    1.0.0-beta5-11649 coreclr x64          C:\Users\[user]\.dnx\runtimes
        1.0.0-beta5-11649 coreclr x86          C:\Users\[user]\.dnx\runtimes       default
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
dnvm use -r coreclr -arch x86 1.0.0-beta5-11649
Adding C:\Users\[user]\.dnx\runtimes\dnx-coreclr-win-x86.1.0.0-beta5-11649\bin
to process PATH

dnvm list

Active Version           Runtime Architecture Location                            Alias
------ -------           ------- ------------ --------                            -----
       1.0.0-beta5-11649 coreclr x64          C:\Users\[user]\.dnx\runtimes
  *    1.0.0-beta5-11649 coreclr x86          C:\Users\[user]\.dnx\runtimes       default
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
        Console.WriteLine("Hello, Windows");
        Console.WriteLine("Love from CoreCLR.");
    }
}
```

Ein Beispiel für ehrgeizigere steht auf der [Corefxlab Repository](https://www.github.com/dotnet/corefxlab/) wird, die ein ziemlich Bild basierend auf das Argument, das Sie zur Laufzeit bereitstellen ausgegeben.
Wenn Sie dieses Beispiel verwenden möchten, speichern Sie einfach die [C\ #file](https://raw.githubusercontent.com/dotnet/corefxlab/master/demos/CoreClrConsoleApplications/HelloWorld/HelloWorld.cs) in ein Verzeichnis auf Ihrem Computer.

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

``` console
dnu restore
```

Sie können Ihre Anwendung mit dem Befehl DNX ausführen.

``` console
dnx . run
```

Damit weisen Sie der derzeit aktiven DNX, um die Anwendung auszuführen.
Hinweis
Sie müssen nicht den Code zu erstellen. DNX übernimmt dies
für Sie.

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
Erstellen von .NET Core Windows Sie in finden der [.NET Core Windows erstellen
Anleitung](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
auf GitHub.




