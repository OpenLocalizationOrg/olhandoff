Willkommen bei .NET Core-Dokumentation
======================================

Dies ist das Repository des .NET Kerndokumentation unterstützt von MSDN öffnen veröffentlichen.

Schnellstart
------------

-Benutzerprofil .NET Core-Dokumentation, die mit den folgenden Schritten:

1. Klonen des Repositorys:
   ```
   git clone https://github.com/openpublish/coredocs.git
   ```

2. Bearbeiten Sie die Markdown-Dateien, die mit Ihrem bevorzugten Abzug-Editor.
3. Commit, und drücken Sie die Änderungen:
   ```
   git add -u
   git commit -m "update doc"
   git push
   ```

4. Warten Sie einen Moment, und Ihre Änderungen automatisch in veröffentlicht:
https://msdnnext.Redmond.corp.Microsoft.com/en-US/openpublishing/corefx/Intro-CLR

> Wenn Sie nicht die Berechtigung, auf dieses Repository übertragen haben, verzweigen sie zu Ihrem Konto und verwenden Sie Pull-Anforderung, um die Änderungen zu übermitteln.

Überprüfung und Vorschau
------------------------

Vor dem Laden der Änderungen auf Remote, erstellen und eine Vorschau Ihrer Doc in lokalen Probleme früh zu ermitteln:

1. Um die Änderungen zu überprüfen, führen Sie einfach `Msbuild` unter dem Stamm der das Repository.
2. Um die Änderungen in der Vorschau anzeigen:
   1. Führen Sie `Msbuild /t:serve` unter dem Stamm der das Repository.
   2. Open `http://localhost: 8000` in Ihrem Browser.





