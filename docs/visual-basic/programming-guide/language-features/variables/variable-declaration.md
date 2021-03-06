---
title: Variablendeklaration in Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: 6890ddfd8b463cd731ab3d8f39565b50a31a1192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="variable-declaration-in-visual-basic"></a>Variablendeklaration in Visual Basic
Sie deklarieren eine Variable, um seinen Namen und die Eigenschaften anzugeben. Ist der deklarationsanweisung für Variablen die [Dim-Anweisung](../../../../visual-basic/language-reference/statements/dim-statement.md). Bestimmen die Variable Merkmale, sein Speicherort und sein Inhalt.  
  
 Regeln für Variablennamen und Überlegungen finden Sie unter [deklarierte Elementnamen](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="declaration-levels"></a>Deklaration von Ebenen  
  
### <a name="local-and-member-variables"></a>Lokale und Membervariablen  
 Ein *lokale Variable* wird innerhalb einer Prozedur deklariert ist. Ein *Membervariable* ist ein Mitglied einer Visual Basic-Typ; er wird auf Modulebene, innerhalb einer Klasse, Struktur oder Modul, aber nicht innerhalb einer Prozedur, die für diese Klasse, Struktur oder Modul intern deklariert.  
  
### <a name="shared-and-instance-variables"></a>Freigegebene und Instanzvariablen  
 Die Kategorie einer Membervariable hängt in einer Klasse oder Struktur davon, ob sie freigegeben werden. Wenn mit der Sie deklariert ist die [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) -Schlüsselwort, es ist ein *freigegebene Variable*, und sie in einer einzigen Kopie für alle Instanzen der Klasse oder Struktur freigegeben ist vorhanden.  
  
 Andernfalls ist es eine *Instanzvariable*, und für jede Instanz der Klasse oder Struktur wird eine separate Kopie erstellt. Eine bestimmte Kopie einer Instanzvariablen steht nur für die Instanz der Klasse oder Struktur, in dem es erstellt wurde. Er ist unabhängig von einer Kopie der Instanzenvariable in einer anderen Instanz der Klasse oder Struktur.  
  
## <a name="declaring-data-type"></a>Deklarieren von-Datentyp  
 Die [als](../../../../visual-basic/language-reference/statements/as-clause.md) -Klausel in der deklarationsanweisung können Sie den Datentyp oder der Objekttyp des deklarierenden Variablen definieren. Sie können eine der folgenden Typen für eine Variable angeben:  
  
-   Geben Sie ein elementarer Datentyp, z. B. `Boolean`, `Long`, oder `Decimal`  
  
-   Eine zusammengesetzte Datentyp, z. B. ein Array oder eine Struktur  
  
-   Ein Objekttyp oder eine Klasse, die in der Anwendung oder in einer anderen Anwendung definiert  
  
-   Ein [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Klasse, z. B. <xref:System.Windows.Forms.Label> oder <xref:System.Windows.Forms.TextBox>  
  
-   Geben Sie eine Schnittstelle, z. B. <xref:System.IComparable> oder <xref:System.IDisposable>  
  
 Sie können mehrere Variablen in einer Anweisung deklarieren, ohne den Datentyp zu wiederholen. In den folgenden Anweisungen, die Variablen `i`, `j`, und `k` als Typ deklariert sind `Integer`, `l` und `m` als `Long`, und `x` und `y` als `Single`:  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 Weitere Informationen zu Datentypen finden Sie unter [Datentypen](../../../../visual-basic/programming-guide/language-features/data-types/index.md). Weitere Informationen zu Objekten finden Sie unter [Objekte und Klassen](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) und [Programmieren mit Komponenten](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).  
  
## <a name="local-type-inference"></a>Lokaler Typrückschluss  
 *Typrückschluss* wird verwendet, um zu bestimmen, die die Datentypen für lokale Variablen deklariert, ohne eine `As` Klausel. Der Compiler leitet den Datentyp der Variablen vom Typ des Initialisierungsausdrucks ab. Dadurch können Sie Variablen deklarieren, ohne einen Typ explizit anzugeben. Im folgenden Beispiel sowohl `num1` und `num2` sind stark typisiert als ganze Zahlen.  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]  
  
 Wenn Sie mithilfe des lokalen Typrückschlusses, möchten `Option Infer` muss festgelegt werden, um `On`. Weitere Informationen finden Sie unter [Local Type Inference (Lokaler Typrückschluss)](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) und [Option Infer Statement (Option Infer-Anweisung)](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="characteristics-of-declared-variables"></a>Merkmale der deklarierten Variablen  
 Die *Lebensdauer* einer Variablen ist der Zeitraum, während die It für die Verwendung verfügbar ist. Im Allgemeinen ist eine Variable vorhanden, solange das Element, das ihn, (z. B. eine Prozedur oder eine Klasse deklariert) ausgeführt wird, vorhanden sein. Wenn die Variable nicht weiter nach Ablauf der Lebensdauer von ihr enthaltendes Element vorhandenen muss, müssen Sie nicht in der Deklaration spezielle nichts zu tun. Wenn die Variable länger als ihr enthaltendes Element gespeichert bleiben muss, können Sie enthalten die `Static` oder `Shared` -Schlüsselwort in seiner `Dim` Anweisung. Weitere Informationen finden Sie unter [Lebensdauer in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
 Die *Bereich* einer Variablen wird die Menge des gesamten Codes, die darauf verweisen kann, ohne dessen Namen zu qualifizieren. Gültigkeitsbereich einer Variablen wird bestimmt, wo sie deklariert ist. Code befindet sich in einer bestimmten Region können die Variablen, die in dieser Region definiert werden, ohne ihren Namen zu qualifizieren. Weitere Informationen finden Sie unter [Gültigkeitsbereich in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
 Einer Variablentyps *Zugriffsebene* wird das Ausmaß der Code mit der Berechtigung, darauf zuzugreifen. Dies wird bestimmt, indem Sie den Zugriffsmodifizierer (wie z. B. [öffentlichen](../../../../visual-basic/language-reference/modifiers/public.md) oder [Private](../../../../visual-basic/language-reference/modifiers/private.md)), mit denen Sie der `Dim` Anweisung. Weitere Informationen finden Sie unter [Zugriffsebenen in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Erstellen einer neuen Variablen](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)  
 [Gewusst wie: Verschieben von Daten in und aus einer Variablen](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Datentypen](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Merkmale deklarierter Elemente](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Lokaler Typrückschluss](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer-Anweisung](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
