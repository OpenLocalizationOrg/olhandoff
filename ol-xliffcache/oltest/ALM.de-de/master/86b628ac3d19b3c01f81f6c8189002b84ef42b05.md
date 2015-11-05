Installieren .NET Core unter Linux
==================================

Von Zlatko Knezevic

Diese Anleitung führt Sie durch den Erwerb .NET Core DNX SDK
über die [.NET Version Manager (DNVM)](https://github.com/aspnet/dnvm)
und eine "Hello World" Demo auf Linux ausgeführt wird.

.NET Core NuGet-Pakete und die .NET Core DNX SDKs finden Sie auf der
[Feed von ASP.NET "Vnext" Myget](https://www.myget.org/F/aspnetvnext), mit dem
Sie können einfacher auf anzeigen.
[Katalog](https://www.myget.org/gallery/aspnetvnext) für den Feed.

Einrichten der Umgebung
-----------------------

Diese Anleitung wurden geschrieben und auf Ubuntu 14.04 LTS getestet,
Da das wichtigste Linux-Distribution ist verwendet das .NET Core-Team.
Diese
Anweisungen möglicherweise auf andere Distributionen ebenfalls erfolgreich ausgeführt.
Wir sind immer
akzeptieren neue Pull-Anforderungen auf [unserer GitHub
Repository](https://www.github.com/dotnet/coreclr/) dieser Adresse auf
andere Linux-Distributionen.
Die einzige Voraussetzung ist, dass sie nicht
Unterbrechen Sie die Möglichkeit, Ubuntu 14.04 LTS verwenden.

###Installieren die erforderlichen Pakete

Installieren Sie die `libunwind8`, `Libssl-Dev` und `Entzippen` Pakete:

``` console
sudo apt-get install libunwind8 libssl-dev unzip
```

Sie benötigen auch eine aktuelle Version von Mono, die für DNX erforderlich ist
Tools.
Dies ist eine temporäre Anforderung und nicht erforderlich
die Zukunft.

``` console
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb http://download.mono-project.com/repo/debian wheezy main" | sudo tee /etc/apt/sources.list.d/mono-xamarin.list
sudo apt-get update
sudo apt-get install mono-complete
```

###Zertifikate

Vertrauenswürdige Stammzertifikate zum Wiederherstellen von NuGet importiert werden müssen
Pakete.
Sie erreichen dies, mit der `Mozroots` Tool.

``` console
mozroots --import --sync
```

Installieren von DNVM
---------------------

Sie benötigen DNVM als Ausgangspunkt.
DNVM ermöglicht es Ihnen, eine abzurufen oder
mehrere .NET Ausführung Umgebungen (DNX).
DNVM ist ein Shell-Skript und
.NET ist nicht erforderlich.
Sie können den folgenden Befehl aus, um es zu installieren.

``` console
curl -sSL https://raw.githubusercontent.com/aspnet/Home/dev/dnvminstall.sh | DNX_BRANCH=dev sh && source ~/.dnx/dnvm/dnvm.sh
```

Installieren der .NET Core DNX
------------------------------

Sie müssen zuerst die Mono DNX abzurufen.
Er enthält keine Mono, sondern
Verwenden der DNX auf Mono erforderlich.
Vor allem die DNU
Befehl wird auf Mono für Verwendung erfordern .NET Core noch nicht unterstützt
diesem Zweck (bis DNU auf .NET Core ausgeführt wird).
Mono ist die Standardeinstellung DNX, also
Sie können es über abrufen `Dnvnm Upgrade`.

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

Verwenden einer bestimmten Laufzeit
-----------------------------------

Sie können die von der installierten DNXs auswählen, die, denen Sie mit verwenden möchten.
`Dnvm mit`, Angeben von Argumenten, die ähnliche verwendet werden, wenn
Installieren eine Laufzeit.

``` console
dnvm use -r coreclr -arch x86 1.0.0-beta5-11649
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

seine wird eine Einführung in Ebene Dokument scheint es geeignete zu
eine app "Hello World".
Hier ist ein sehr einfaches Kopieren und einfügen
in einer CS-Datei in einem Verzeichnis.

``` csharp
using System;

public class Program
{
    public static void Main (string[] args)
    {
        Console.WriteLine("Hello, Linux");
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

Hello, Linux
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
Erstellen von .NET Core Windows Sie in finden der [Erstellen CoreCLR unter
Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
auf GitHub.




