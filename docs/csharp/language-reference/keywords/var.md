---
title: var (C#-Referenz)
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: c311993ebcc5b5072959b2e79242bcdabd6de913
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2018
---
# <a name="var-c-reference"></a>var (C#-Referenz)
Ab Visual Studio C# 3.0 können Variablen, die im Methodenbereich deklariert wurden, den impliziten „Typ“ `var` haben. Eine implizit typisierte lokale Variable ist stark typisiert, als hätten Sie den Typ selbst deklariert. Tatsächlich legt der Compiler den Typ fest. Die folgenden beiden `i`-Aktivitäten sind funktional äquivalent:  
  
```csharp  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 Weitere Informationen finden Sie unter [Implizit typisierte lokale Variablen](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) und [Type relationships in LINQ query operations (Typbeziehungen in LINQ-Abfragevorgängen)](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden zwei Abfrageausdrücke gezeigt. Im ersten Ausdruck in das Verwenden von `var` erlaubt aber nicht erforderlich, da der Typ des Abfrageergebnisses explizit als `IEnumerable<string>` angegeben werden kann. Im zweiten Ausdruck ermöglicht `var`, dass das Ergebnis eine Auflistung von anonymen Typen ist und dass auf die Namen dieser Typen nicht zugegriffen werden kann. Nur der Compiler kann darauf zugreifen. Durch die Verwendung von `var` wird die Voraussetzung beseitigt, eine neue Klasse für das Ergebnis erstellen zu müssen. Beachten Sie, dass die `foreach`-Iterationsvariable `item` im zweiten Beispiel auch implizit typisiert sein muss.  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Referenz](../../../csharp/language-reference/index.md)  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Implizit typisierte lokale Variablen](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
