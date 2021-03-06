---
title: 'Tutorial „Branches und Schleifen“: Lokale C#-Schnellstarts'
description: In diesem Schnellstart zu Branches und Schleifen schreiben Sie C#-Code, um die Sprachsyntax zu erkunden, die bedingte Branches und Schleifen zur wiederholten Ausführung von Anweisungen unterstützt.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 711cc9b40284076d28b5003935bbbbb77dc36664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="branches-and-loops"></a>Verzweigungen und Schleifen

In diesem Schnellstart erfahren Sie, wie Sie Code schreiben, der Variablen untersucht und basierend auf diesen Variablen den Ausführungspfad ändert. Sie schreiben einen C#-Code und sehen dort die Ergebnisse der Kompilierung und Ausführung Ihres Codes. Der Schnellstart enthält eine Reihe von Lektionen, in denen Branch- und Schleifenkonstrukte in C# untersucht werden. In diesen Lektionen lernen Sie die Grundlagen der Programmiersprache C# kennen.

Für diesen Schnellstart wird vorausgesetzt, dass Sie über einen Computer verfügen, den Sie für die Entwicklung nutzen können. Das .NET-Thema [Erste Schritte in 10 Minuten](https://www.microsoft.com/net/core) umfasst Anweisungen zum Einrichten Ihrer lokalen Entwicklungsumgebung auf einem Mac-, Windows- oder Linux-PC. Einen schnellen Überblick über die Befehle, die Sie verwenden werden, finden Sie in der [Einführung zu lokalen Schnellstarts](local-environment.md), die Links mit weiteren Einzelheiten enthalten.

## <a name="make-decisions-using-the-if-statement"></a>Treffen von Entscheidungen mithilfe der `if`-Anweisung

Erstellen Sie ein Verzeichnis mit dem Namen **branches-quickstart**. Machen Sie dieses Verzeichnis zum aktuellen Verzeichnis, und führen Sie `dotnet new console -n BranchesAndLoops -o .` aus. Dieser Befehl erstellt im aktuellen Verzeichnis eine neue .NET Core-Konsolenanwendung.

Öffnen Sie **Program.cs** in Ihrem bevorzugten Editor, und ersetzen Sie die Zeile `Console.Writeline("Hello World!");` durch den folgenden Code:

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

Testen Sie diesen Code, indem Sie `dotnet run` in Ihr Konsolenfenster eingeben. Es sollte folgende Meldung in Ihrer Konsole angezeigt werden: „Die Antwort ist größer als 10.“

Ändern Sie die Deklaration von `b` so, dass die Summe kleiner als 10 ist: 

```csharp
int b = 3;
```

Geben Sie erneut `dotnet run` ein. Da die Antwort kleiner als 10 ist, wird nichts ausgegeben. Die von Ihnen getestete **Bedingung** ist falsch. Es ist kein Code auszuführen, da Sie lediglich eine der möglichen Verzweigungen für eine `if`-Anweisung geschrieben haben: die true-Verzweigung.

> [!TIP]
> Bei Ihren ersten Schritten mit C# (oder einer anderen Programmiersprache) kann es zu Fehlern kommen, wenn Sie Codes schreiben. Der Compiler findet und meldet die Fehler. Sehen Sie sich die Fehlerausgabe und den Code, der den Fehler erzeugt hat, genau an. Der Compilerfehler kann Ihnen in der Regel helfen, das Problem zu finden.

Das erste Beispiel veranschaulicht die Vorteile von `if`-Anweisungen und Boolean-Typen. Ein *boolean*-Typ ist eine Variable, die einen der folgenden zwei Werte enthalten kann: `true` oder `false`. In C# ist ein besonderer Typ für boolesche Variablen, `bool`, definiert. Die `if`-Anweisung überprüft den Wert eines `bool`-Typs. Wenn der Wert `true` lautet, wird die nach `if` folgende Anweisung ausgeführt. Andernfalls wird diese übersprungen.

Dieser Vorgang zum Überprüfen von Bedingungen und Ausführen von Anweisungen basierend auf diesen Bedingungen ist sehr nützlich.

## <a name="make-if-and-else-work-together"></a>Kombinieren von if- und else-Anweisungen

Um einen anderen Code in den true- und false-Verzweigungen auszuführen, erstellen Sie eine `else`-Verzweigung, die ausgeführt wird, wenn die Bedingung falsch ist. Testen Sie diese. Fügen Sie die letzten beiden Zeilen im nachfolgenden Code zu Ihrer `Main`-Methode hinzu (die ersten vier sollten Sie bereits haben):

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

Die Anweisung, die nach dem Schlüsselwort `else` folgt, wird nur ausgeführt, wenn die zu testende Bedingung `false` lautet. Wenn Sie `if` und `else` mit booleschen Bedingungen kombinieren, müssen Sie sowohl eine `true`- als auch eine `false`-Bedingung verarbeiten.

> [!IMPORTANT]
> Der Einzug unter den `if`- und `else`-Anweisungen dient zur besseren Lesbarkeit.
> In der Programmiersprache C# werden Einzüge oder Leerräume nicht berücksichtigt. Die Anweisung nach dem Schlüsselwort `if` bzw. `else` wird basierend auf der Bedingung ausgeführt. Alle Beispiele in diesem Schnellstart folgen der gängigen Vorgehensweise, Zeilen basierend auf der Ablaufsteuerung von Anweisungen mit einem Einzug zu versehen.

Da Einzüge nicht relevant sind, müssen Sie mit `{` und `}` angeben, dass Sie mehr als eine Anweisung im Rahmen des bedingt ausgeführten Blocks verwenden möchten. C#-Programmierer verwenden solche geschweifte Klammern in der Regel bei allen `if`- und `else`-Anweisungen. Das folgende Beispiel ist identisch mit dem Inhalt, den Sie soeben erstellt haben. Ändern Sie den obigen Code dahingehend, dass er mit dem folgenden Code übereinstimmt:

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> Im restlichen Schnellstart enthalten alle Codebeispiele geschweifte Klammern gemäß den allgemeingültigen Vorgehensweisen.

Sie können kompliziertere Bedingungen testen. Fügen Sie den folgenden Code in Ihrer `Main`-Methode unter dem Code, den Sie bisher geschrieben haben, hinzu:

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

Das Zeichen `&&` steht für „and“. Es bedeutet, dass beide Bedingungen „true“ lauten müssen, damit die Anweisung in der true-Verzweigung ausgeführt wird.  Diese Beispiele zeigen außerdem, dass Sie in jeder bedingten Verzweigung mehrere Anweisungen verwenden können, sofern Sie sie mit `{` und `}` umschließen.

Sie können auch `||` für „or“ verwenden. Fügen Sie den folgenden Code unter dem Code hinzu, den Sie bereits geschrieben haben:

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

Sie haben den ersten Schritt abgeschlossen. Bevor Sie mit dem nächsten Abschnitt beginnen, verschieben wir den aktuellen Code in eine separate Methode. Dies erleichtert das Arbeiten mit einem neuen Beispiel. Benennen Sie Ihre `Main` -Methode in `ExploreIf` um, und schreiben Sie eine neue `Main`-Methode, die `ExploreIf` aufruft. Anschließend sollte der Code wie folgt aussehen:

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

Kommentieren Sie den Aufruf von `ExploreIf()` aus. Dadurch wird die Ausgabe weniger überladen, wenn Sie in diesem Abschnitt arbeiten:

```csharp
//ExploreIf();
```

Mit `//` wird ein **Kommentar** in C# begonnen. Kommentare sind Texte, die Sie in Ihrem Quellcode beibehalten, jedoch nicht als Code ausführen möchten. Der Compiler generiert keinen ausführbaren Code über die Kommentare.

## <a name="use-loops-to-repeat-operations"></a>Wiederholen von Vorgängen durch Schleifen

In diesem Abschnitt verwenden Sie **Schleifen**, um Anweisungen zu wiederholen. Testen Sie diesen Code in Ihrer `Main`-Methode:

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

Die `while`-Anweisung prüft eine Bedingung und führt die Anweisung oder der Anweisungsblock nach `while` aus. Es wiederholt die Überprüfung der Bedingung und die Ausführung dieser Anweisungen, bis die Bedingung „false“ lautet.

In diesem Beispiel kommt ein weiterer neuer Operator vor. Das `++`-Zeichen nach der `counter`-Variable ist der **increment**-Operator. Er erhöht den Wert von `counter` um 1 und speichert diesen Wert in der Variable `counter`.

> [!IMPORTANT]
> Stellen Sie sicher, dass die Schleifenbedingung `while` zu „false“ wechselt, nachdem Sie den Code ausgeführt haben. Erstellen Sie anderenfalls eine **Endlosschleife**, durch die das Programm niemals beendet wird. Das wird in diesem Beispiel nicht gezeigt, weil Sie die programmseitige Verwendung von **STRG+C** oder anderen Mitteln unterbinden müssen.

Die `while`-Schleife testet die Bedingung, bevor der Code nach `while` ausgeführt wird. Die `do` ... `while`-Schleife führt den Code zuerst aus und überprüft anschließend die Bedingung. Die do while-Schleife wird im folgenden Code gezeigt:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

Diese `do`-Schleife und die vorherige `while`-Schleife erzeugen die gleiche Ausgabe.

## <a name="work-with-the-for-loop"></a>Arbeiten mit der for-Schleife

Die **for**-Schleife wird üblicherweise in C# verwendet. Testen Sie diesen Code in Ihrer Main()-Methode:

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

Dieser funktioniert auf dieselbe Weise wie die `while`-Schleife und die `do`-Schleife, die Sie bereits verwendet haben. Die `for`-Anweisung besteht aus drei Teilen, die steuern, wie sie ausgeführt wird.

Der erste Teil ist der **for-Initialisierer**: `for index = 0;` deklariert, dass `index` die Schleifenvariable ist, und legt den Anfangswert auf `0` fest.

Der mittlere Teil ist die **for-Bedingung**: `index < 10` deklariert, dass diese `for`-Schleife ausgeführt wird, solange der Wert des Zählers kleiner als 10 ist.

Der letzte Teil ist der **for-Iterator**: `index++` gibt an, wie die Schleifenvariable geändert wird, nachdem der Block nach der `for`-Anweisung ausgeführt wurde. Hier gibt dieser an, dass `index` bei jeder Blockausführung um 1 erhöht werden soll.

Experimentieren Sie selbst damit. Testen Sie Folgendes:

- Ändern Sie den Initialisierer, um mit einem anderen Wert zu beginnen.
- Ändern Sie die Bedingung, um an einem anderen Wert anzuhalten.

Wenn Sie fertig sind, fahren Sie damit fort, mithilfe der erworbenen Kenntnisse selbst Codes zu schreiben.

## <a name="combine-branches-and-loops"></a>Kombinieren von Branches und Schleifen

Nachdem Sie nun die `if`-Anweisung und die Schleifenkonstrukte in der Programmiersprache C# kennengelernt haben, versuchen Sie, einen C#-Code zu schreiben, der die Summe aller ganzen Zahlen von 1 bis 20 ermittelt, die durch 3 teilbar sind.  Im Folgenden einige Tipps:

- Der `%`-Operator ermittelt den Restwert einer Divisionsoperation.
- Die `if`-Anweisung ermittelt die Bedingung, um festzustellen, ob eine Zahl in der Summe berücksichtigt werden soll.
- Die `for`-Schleife ermöglicht es, eine Reihe von Schritten für alle Zahlen von 1 bis 20 zu wiederholen.

Probieren Sie es selbst aus. Prüfen Sie dann, wie Sie abgeschnitten haben. Sie sollten 63 als Antwort erhalten. Sie können eine mögliche Antwort sehen, indem Sie sich [den fertig gestellten Code auf GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54) ansehen.

Sie haben den Schnellstart „Branches und Schleifen“ abgeschlossen.

Sie können mit dem Schnellstart [Zeichenfolgeninterpolation](interpolated-strings-local.md) in Ihrer eigenen Entwicklungsumgebung fortfahren.

Weitere Informationen zu diesen Begriffen finden Sie unter folgenden Themen:

[if- und else-Anweisung](../language-reference/keywords/if-else.md)  
[while-Anweisung](../language-reference/keywords/while.md)  
[do-Anweisung](../language-reference/keywords/do.md)  
[for-Anweisung](../language-reference/keywords/for.md)  
