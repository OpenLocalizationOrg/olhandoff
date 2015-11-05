Was ist "verwalteter Code"?
===========================

Bei der Arbeit mit .NET Framework treten häufig den Begriff
"verwalteter Code".
Dieses Dokument wird erläutert, was bedeutet, dass dieser Begriff und
zusätzliche Informationen ein.

Sehr einfach ausgedrückt, handelt es sich um verwalteter Code: code, dessen Ausführung
wird von einer Laufzeit verwaltet werden.
In diesem Fall wird die betreffende Laufzeit aufgerufen.
die **Common Language Runtime** oder CLR, unabhängig von der Implementierung
([Mono](http://www.mono-project.com/) oder .NET Framework oder .NET Core).
CLR ist verantwortlich für des verwalteten Codes, kompilieren es in den Computer
Code und ausführen.
Oben in diesem, stellt Common Language Runtime mehrere
wichtige Dienste wie z. B. automatische Verwaltung, Sicherheit
Grenzen, Sicherheit usw. geben.

Vergleichen Sie dies im Hinblick auf, wenn Sie eine C/C++-Programms, sogenannte ausführen würden
"nicht verwalteter Code".
In der nicht verwalteten Welt ist der Programmierer charge von
nahezu alles.
Das eigentliche Programm ist im Wesentlichen eine Binärdatei
das Betriebssystem (OS) in den Speicher geladen und gestartet wird.
Alles
Andernfalls sind Speicherverwaltungsfunktionen Security Considerations eine Belastung der
der Programmierer.

Verwalteter Code wird in einer hoch entwickelter Sprachen geschrieben, die werden können
Führen Sie auf der .NET Plattform, wie z. B. C\ # Visual Basic F\- und
andere.
Beim Kompilieren von Code in diesen Sprachen mit ihren
entsprechende Compiler nicht Computercode erhalten Sie.
Sie erhalten **Intermmidiate
Sprache** Code, der die Common Language Runtime wird dann kompiliert und ausgeführt wird.
C++ ist die
eine Ausnahme von dieser Regel, wie sie können auch systemeigenen, nicht verwalteten erzeugen
Binärdateien, die unter Windows ausgeführt werden.

Intermediate Language & Ausführung
--------------------------------------

Was ist "Intermediate Language" (oder kurz IL-Code)?
Es ist ein Produkt von
die Kompilierung von Code in .NET Sprachen geschrieben wurden.
Sobald Sie
Kompilieren des Codes in einer dieser Sprachen geschrieben wird Ihnen ein
binäre, die außerhalb des IL erfolgt.
Es ist wichtig zu beachten, dass die IL ist
unabhängig von anderen bestimmten Sprachen, die auf die Common Language Runtime ausgeführt wird;
Es gibt sogar eine separate Spezifikation dafür, die Sie lesen können, wenn
Sie sind also tendieren.

Sobald Sie IL aus Ihrem Code auf hoher Ebene erzeugen, werden Sie wahrscheinlich
um es auszuführen.
Hier wird die CLR übernimmt und startet den Prozess der
**Just-in-Time** kompilieren oder **JIT-Ing** Code IL Computer
Code, der tatsächlich sein kann, die auf einer CPU ausgeführt werden.
Auf diese Weise weiß die CLR
genau welche Code ausgeführten Aktionen und Effectivelly können *verwalten* es.

Umanaged Code-Interoperabilität
-------------------------------

Natürlich die CLR ermöglicht die Übergabe der Grenzen zwischen verwaltetem und
nicht verwaltete Welt, und es gibt viel Code, die das, sogar in der
Base Class Libraries & Lt; Framework-Bibliotheken & Gt;.
Dies wird aufgerufen
**Interoperabilität** oder **Interop** kurz.
Diese Vorschriften
würden Sie z. B. eine nicht verwaltete Bibliothek und Aufruf umschließen können
hinein.
Es ist jedoch wichtig zu beachten, dass, wenn Sie dies tun, wenn
der Code übergibt die Grenzen der Runtime, die tatsächliche Verwaltung
die Ausführung ist wieder in den Händen von nicht verwaltetem Code und somit liegt.
unter der gleichen Einschränkungen.

Ähnlich wie dies C\ # ist eine Sprache, die Ihnen ermöglicht, verwenden Sie nicht verwaltete
erstellt z. B. Zeiger direkt im Code durch Nutzung bekannt ist
als **unsicheren Kontext** die kennzeichnet ein Stück des Codes für die die
die Ausführung wird nicht von der CLR verwaltet.

Weitere Ressourcen
------------------

-   [.NET Framework – konzeptionelle Übersicht](https://msdn.microsoft.com/en-us/library/zw4w595w%28v=vs.85%29.aspx)
-   [Unsicheren Code und Zeiger](https://msdn.microsoft.com/en-us/library/t2yzs44b.aspx)
-   [Interoperabilität (C\-Programmierhandbuch)](https://msdn.microsoft.com/en-us/library/ms173184.aspx)

##Kommentare

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




