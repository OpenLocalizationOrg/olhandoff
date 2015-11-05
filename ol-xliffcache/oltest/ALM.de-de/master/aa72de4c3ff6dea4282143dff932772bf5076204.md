Delegaten und Lambda-Ausdrücke
==============================

Delegaten definieren ein Typs, die Signatur einer bestimmten Methode angeben.
Eine Methode (statisch oder Instanz) erfüllt diese Signatur, eine Variable dieses Typs zugewiesen und dann aufgerufen direkt (mit den entsprechenden Argumenten) oder als ein Argument an eine andere Methode übergeben und dann aufgerufen.
Im folgende Beispiel wird veranschaulicht, Delegaten verwenden.

``` csharp
public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;
        Console.WriteLine(rev("a string"));
    }
}
```

- In Zeile 4 erstellen wir einen Delegattyp einer bestimmten Signatur in diesem Fall eine Methode, die einen Zeichenfolgenparameter akzeptiert und gibt dann einen Zeichenfolgenparameter zurück.
- In Zeile 6 definieren wir die Implementierung des Delegaten, indem Sie eine Methode, die genaue dieselbe Signatur besitzt.
- Zeile 13 die Methode zugewiesen ist ein Typ, der entspricht dem `umkehren` delegieren.
- Schließlich rufen wir in Zeile 15 der Delegat übergeben einer Zeichenfolge rückgängig gemacht werden.

Um den Entwicklungsprozess zu vereinfachen, enthält .NET eine Reihe von Delegattypen, die Programmierer wieder verwenden und keine neue Typen erstellen können.
Hierbei handelt es sich `Func-<>`, `Aktion <>` und `<>-Prädikat`, und sie können an verschiedenen Stellen in .NET APIs ohne die Notwendigkeit zum Definieren von neuen Delegattypen verwendet werden.
Natürlich bestehen einige Unterschiede zwischen den drei, wie Sie in ihrer Signaturen sehen werden, die hauptsächlich mit der Art und Weise zu tun, die sie gedacht waren:

- `Aktion <>` wird verwendet, wenn muss zum Ausführen einer Aktion, die unter Verwendung der Argumente des Delegaten.
- `Func-<>` wird verwendet, in der Regel eine Transformation, das heißt, Sie müssen die Argumente des Delegaten in ein anderes Ergebnis zu transformieren. Projektionen sind ein gutes Beispiel hierfür.
- `<>-Prädikat` wird verwendet, wenn Sie benötigen, um zu bestimmen, wenn das Argument die Bedingung des Delegaten. Es kann auch als geschrieben werden eine `Func < T, Bool >`.

Wir können nun unser Beispiel oben und Schreiben Sie mithilfe der `Func-<>` anstelle eines benutzerdefinierten Typs zu delegieren.
Das Programm wird weiterhin ausgeführt, genau.

``` csharp
public class Program
{

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Func<string, string> rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

In diesem einfachen Beispiel scheint eine Methode definiert die Main()-Methode etwas überflüssig.
Es ist daher, die .NET Framework 2.0, das Konzept der eingeführt **anonyme Delegaten**.
Mit ihrer Unterstützung können Sie "Inline" Delegaten zu erstellen, ohne dass zusätzliche Typen oder-Methode angegeben.
Sie einfach Inline die Definition des Delegaten, in dem Sie Sie benötigen.

Ein Beispiel werden wir nach oben zu wechseln und anonyme Delegaten verwenden, um eine Liste der nur gerade Zahlen zu filtern und sie dann auf der Konsole ausgegeben.

``` csharp
public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();
        for (int i = 1; i &lt;= 100; i++) { list.Add(i); }
        List<int> result = list.FindAll(
            delegate(int no) { return (no%2 == 0); }
        );

        foreach (var item in result) { Console.WriteLine(item); }
    }
}
```

Beachten Sie die hervorgehobenen Zeilen.
Wie Sie sehen können, ist der Textkörper des Delegaten nur einen Satz von Ausdrücken, wie alle anderen Delegaten.
Aber, dass sie eine separate Definition, haben wir es eingeführt *ad-hoc-* in unseren Aufruf an die `FindAll()` Methode der `List < T >` Typ.

Selbst bei diesem Ansatz ist gibt es jedoch immer noch viel Code, die wir verwerfen können.
Hier kommt **Lambda-Ausdrücke** ins Spiel kommen.

Lambda-Ausdrücke oder kurz, nur "Lambdas" wurden C\ # 3.0 wird als eines der wichtigsten Bausteine von Language Integrated Query (LINQ) eingeführt.
Sie sind einfach ein bequemer Syntax für die Verwendung von Delegaten.
Sie deklarieren eine Signatur und ein Methodentext, aber keinen formale Identität eigenen, wenn sie einen Delegaten zugewiesen werden.
Im Gegensatz zu Delegaten können sie direkt als die linke Seite des ereignisregistrierung oder in verschiedenen Linq-Klauseln und Methoden zugewiesen werden.

Da ein Lambda-Ausdruck nur eine weitere Möglichkeit, ein Delegat ist, sollten wir schreiben Sie im Beispiel oben, um einen Lambda-Ausdruck anstelle eines anonymen Delegaten verwenden können.

``` csharp
public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i &lt;= 100; i++) { list.Add(i); }
        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result) { Console.WriteLine(item); }
    }
}
```

Wenn Sie einen auf die hervorgehobenen Zeilen Blick können Sie sehen, wie ein Lambda-Ausdruck aussieht.
In diesem Fall ist es nur eine **sehr** zweckdienliche Syntax für die Verwendung von Delegaten, was hinter den Kulissen passiert ist ähnlich mit anonymen Delegaten.

Erneut, Lambda-Ausdrücke einfach Delegaten sind, was bedeutet, dass sie ohne Probleme, als Ereignishandler verwendet werden können, wie im folgenden Codeausschnitt veranschaulicht.

``` csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

Weitere Informationen und Ressourcen
------------------------------------

- [Delegaten](https://msdn.microsoft.com/en-us/library/ms173171.aspx)
- [Anonyme Funktionen](https://msdn.microsoft.com/en-us/library/bb882516.aspx)
- [Lambda-Ausdrücke](https://msdn.microsoft.com/en-us/library/bb397687.aspx)




