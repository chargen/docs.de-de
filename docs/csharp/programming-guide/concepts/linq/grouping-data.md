---
title: Gruppieren von Daten (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 1d2aca79fd6ae5df84b34a903ecb5e18ae7ab5a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="grouping-data-c"></a>Gruppieren von Daten (C#)
Als „Gruppieren“ wird das Anordnen von Daten in Gruppen bezeichnet, sodass die Elemente in jeder Gruppe über ein gemeinsames Attribut verfügen.  
  
 Die folgende Abbildung zeigt die Ergebnisse der Gruppierung einer Zeichenfolge. Der Schlüssel für jede Gruppe ist das Zeichen.  
  
 ![LINQ-Gruppierungsvorgänge](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 Die Methoden des Standardabfrageoperators, die Datenelemente gruppieren, sind im folgenden Abschnitt aufgeführt.  
  
## <a name="methods"></a>Methoden  
  
|Methodenname|description|C#-Abfrageausdruckssyntax|Weitere Informationen|  
|-----------------|-----------------|---------------------------------|----------------------|  
|GroupBy|Gruppenelemente, die über ein gemeinsames Attribut verfügen. Jede Gruppe wird durch ein <xref:System.Linq.IGrouping%602>-Objekt dargestellt.|`group … by`<br /><br /> - oder - <br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|ToLookup|Fügt Elemente basierend auf einer Schlüsselauswahlfunktion in eine <xref:System.Linq.Lookup%602>-Klasse (one-to-many-Wörterbuch) ein.|Nicht zutreffend.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Beispiel für die Abfrageausdruckssyntax  
 Im folgenden Codebeispiel wird die `group by`-Klausel angewandt, um die Gruppe ganzer Zahlen in Listen mit geraden und ungeraden Zahlen zu aufzuteilen.  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Linq>  
 [Standard Query Operators Overview (C#) (Übersicht der Standardabfrageoperatoren (C#))](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [group-Klausel](../../../../csharp/language-reference/keywords/group-clause.md)  
 [Gewusst wie: Erstellen einer geschachtelten Gruppe](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)  
 [Vorgehensweise: Gruppieren von Dateien nach Erweiterung (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [Gewusst wie: Gruppieren von Abfrageergebnissen](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)  
 [Gewusst wie: Ausführen einer Unterabfrage für eine Gruppierungsoperation](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)  
 [Vorgehensweise: Teilen einer Datei in mehrere Dateien durch das Verwenden von Gruppen (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
