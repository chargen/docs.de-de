---
title: Zwischenmaterialisierung (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: b98f9765f5c54a49f26a9d1a3ac351f3eebcf9c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="intermediate-materialization-c"></a>Zwischenmaterialisierung (C#)
Bei fehlender Sorgfalt kann es in bestimmten Situationen dazu kommen, dass die Auflistungen in Ihren Abfragen vorzeitig materialisiert werden, wodurch sich das Speicher- und Leistungsprofil Ihrer Anwendung radikal ändert. Einige Standardabfrageoperatoren verursachen die Materialisierung ihrer Quellauflistung, bevor auch nur ein einziges Element zurückgegeben wird. So durchläuft beispielsweise <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> zuerst die gesamte Quellauflistung, sortiert dann alle Elemente und gibt zum Schluss das erste Element zurück. Das bedeutet, dass es zwar aufwendig ist, das erste Element einer sortierten Auflistung abzurufen, das Abrufen aller folgenden Elemente hingegen ist nicht aufwendig. Dies ist sinnvoll, denn anders würde dieser Abfrageoperator nicht funktionieren.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel ändert das vorherige Beispiel. Die `AppendString`-Methode ruft vor dem Durchlaufen der Quelle <xref:System.Linq.Enumerable.ToList%2A> auf. Dies verursacht eine Materialisierung.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Dieses Beispiel erzeugt die folgende Ausgabe:  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 Diesem Beispiel können Sie entnehmen, dass der Aufruf von <xref:System.Linq.Enumerable.ToList%2A> `AppendString` dazu veranlasst, vor der Rückgabe des ersten Elements seine gesamte Quelle aufzulisten. Wenn die Quelle ein großes Array wäre, würde dies das Arbeitsspeicherprofil der Anwendung deutlich verändern.  
  
 Standardabfrageoperatoren können auch miteinander verkettet werden. Informationen dazu finden Sie im letzten Thema dieses Lernprogramms:  
  
-   [Verketten von Standardabfrageoperatoren (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Tutorial: Verketten von Abfragen (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
