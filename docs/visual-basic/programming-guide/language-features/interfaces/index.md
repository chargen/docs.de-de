---
title: Schnittstellen (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: 8380778398495fe9948e6a0eb19b535656a575f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="interfaces-visual-basic"></a>Schnittstellen (Visual Basic)
*Schnittstellen* definieren die Eigenschaften, Methoden und Ereignisse, die von Klassen implementiert werden können. Schnittstellen erlauben es Ihnen, Funktionen als kleine Gruppen mit verwandten Eigenschaften, Methoden und Ereignisse zu definieren. Dadurch werden Kompatibilitätsprobleme reduziert, da Sie für die Schnittstellen erweiterte Implementierungen entwickeln können, ohne vorhandenen Code zu gefährden. Sie können neue Funktionen zu einem beliebigen Zeitpunkt hinzufügen, indem Sie weitere Schnittstellen und Implementierungen entwickeln.  
  
 Es gibt viele weitere Gründe, warum Sie möglicherweise Schnittstellen anstelle der Klassenvererbung verwenden möchten:  
  
-   Schnittstellen sind besser für Situationen geeignet, in denen Anwendungen viele nicht verknüpfte Objekttypen erfordern, um bestimmte Funktionen bereitzustellen.  
  
-   Schnittstellen sind flexibler als Basisklassen, da Sie eine einzelne Implementierung definieren können, die mehrere Schnittstellen implementieren kann.  
  
-   Schnittstellen sind in Situationen vorzuziehen, in denen Sie keine Implementierung von einer Basisklasse erben.  
  
-   Schnittstellen sind nützlich, wenn Sie keine Klassenvererbung verwenden können. Z. B. Strukturen können nicht von Klassen erben, sie können jedoch Schnittstellen implementieren.  
  
## <a name="declaring-interfaces"></a>Deklarieren von Schnittstellen  
 Schnittstellendefinitionen werden innerhalb der `Interface` und `End Interface` Anweisungen eingeschlossen. Nach der `Interface` Anweisung können Sie eine optionale `Inherits` Anweisung hinzufügen, die eine oder mehrere geerbte Schnittstellen auflistet. Die `Inherits` Anweisungen müssen in der Deklaration vor allen anderen Anweisungen, außer Kommentaren, stehen. Die übrigen Anweisungen der Schnittstellendefinition sollten `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, und `Enum` Anweisungen sein. Schnittstellen können keinen Implementierungscode oder Anweisungen, die Implementierungscode zugeordnet sind, enthalten, wie z. B. `End Sub` oder `End Property`.  
  
 In einem Namespace sind Schnittstellenanweisungen standardmäßig `Friend`, aber sie können auch explizit als `Public` oder `Friend` deklariert sein. Schnittstellen, die innerhalb von Klassen, Modulen, Schnittstellen und Strukturen definiert sind, sind standardmäßig `Public`, können aber auch explizit als `Public`, `Friend`, `Protected`, oder `Private` deklariert sein.  
  
> [!NOTE]
>  Das `Shadows` Schlüsselwort kann auf alle Schnittstellenmember angewendet werden. Das `Overloads` Schlüsselwort kann bei `Sub`, `Function`, und `Property` Anweisungen angewendet werden und wird in der Schnittstellendefinition deklariert. Darüber hinaus können `Property` Anweisungen die `Default`, `ReadOnly`, oder `WriteOnly` Modifizierer haben. Alle anderen Modifizierer –`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, oder `Overridable`– sind zulässig. Weitere Informationen finden Sie unter [Deklarationskontexte und Standardzugriffsebenen](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Im folgende Code wird beispielsweise eine Schnittstelle mit einer Funktion, eine Eigenschaft und ein Ereignis definiert.  
  
 [!code-vb[VbVbalrOOP#17](../../../../visual-basic/misc/codesnippet/VisualBasic/index_1.vb)]  
  
## <a name="implementing-interfaces"></a>Implementieren von Schnittsellen  
 Visual Basic reservierten Wort `Implements` wird auf zwei Arten verwendet. Die `Implements` Anweisung gibt an, dass eine Klasse oder Struktur eine Schnittstelle implementiert. Das `Implements` Schlüsselwort gibt an, dass ein Klassenmember oder ein Strukturmember ein bestimmtes Schnittstellenmember implementiert.  
  
### <a name="implements-statement"></a>Implements-Anweisung  
 Wenn eine Klasse oder Struktur eine oder mehrere Schnittstellen implementiert, muss die `Implements` Anweisung unmittelbar nach der `Class` oder `Structure` Anweisung erfolgen. Die `Implements` Anweisung erfordert eine durch Trennzeichen getrennte Liste mit Schnittstellen, die von einer Klasse implementiert werden. Die Klasse oder Struktur muss alle Schnittstellenmember mit dem `Implements` Schlüsselwort implementieren.  
  
### <a name="implements-keyword"></a>Implements-Schlüsselwort  
 Das `Implements` Schlüsselwort erfordert eine durch Trennzeichen getrennte Liste mit Schnittstellenmembern, die implementiert werden. In der Regel wird nur ein einziger Schnittstellenmember angegeben, aber Sie können mehrere Members angeben. Die Spezifikation eines Schnittstellenmembers besteht aus dem Schnittstellennamen, der in einer Implementierungsanweisung innerhalb der Klasse angegeben werden muss, einem Zeitraum und dem Namen der Memberfunktion, der Eigenschaft oder des Ereignisses, das implementiert werden soll. Der Name eines Elements, das einen Schnittstellenmember implementiert, kann jeden beliebigen zulässigen Bezeichner verwenden, und es gibt keine Beschränkung auf die `InterfaceName_MethodName` Konvention, die in früheren Versionen von Visual Basic verwendet.  
  
 Der folgende Code zeigt z. B. das Deklarieren einer Unterroutine namens `Sub1`, die eine Methode einer Schnittstelle implementiert:  
  
 [!code-vb[VbVbalrOOP#69](../../../../visual-basic/misc/codesnippet/VisualBasic/index_2.vb)]  
  
 Die Parametertypen und Rückgabetypen des implementierenden Members müssen mit den Schnittstelleneigenschaften oder der Memberdeklaration in der Schnittstelle übereinstimmen. Die gängigste Methode, um ein Element in einer Schnittstelle zu implementieren, ist mit einem Element, das den gleichen Namen wie die Schnittstelle hat, wie im vorherigen Beispiel gezeigt.  
  
 Zum Deklarieren der Implementierung einer Schnittstellenmethode können Sie alle Attribute verwenden, die für Deklarationen von Instanzenmethoden, einschließlich `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, und `Static` zulässig sind. Das `Shared` Attribut ist nicht zulässig, da es keine Instanzmethode, sondern eine Klasse definiert.  
  
 Mithilfe von `Implements`, können Sie auch eine einzelne Methode schreiben, die mehrere Methoden  implementiert, die in einer Schnittstelle definiert sind, wie z. B.:  
  
 [!code-vb[VbVbalrOOP#70](../../../../visual-basic/misc/codesnippet/VisualBasic/index_3.vb)]  
  
 Sie können einen privaten Member verwenden, um ein Schnittstellenmember zu implementieren. Wenn ein privater Member einen Member einer Schnittstelle implementiert, wird dieses Member durch die Schnittstelle verfügbar, obwohl er nicht direkt in Objektvariablen für die Klasse verfügbar ist.  
  
### <a name="interface-implementation-examples"></a>Beispiele für Schnittstellenimplementierung  
 Klassen, die eine Schnittstelle implementieren, müssen alle Eigenschaften, Methoden und Ereignisse implementieren.  
  
 Im folgenden Beispiel werden zwei Schnittstellen definiert. Die zweite Schnittstelle `Interface2`, erbt `Interface1` und definiert eine zusätzliche Eigenschaft und Methode.  
  
 [!code-vb[VbVbalrOOP#39](../../../../visual-basic/misc/codesnippet/VisualBasic/index_4.vb)]  
  
 Das nächste Beispiel implementiert `Interface1`, die im vorherigen Beispiel definierte Schnittstelle:  
  
 [!code-vb[VbVbalrOOP#40](../../../../visual-basic/misc/codesnippet/VisualBasic/index_5.vb)]  
  
 Das abschließende Beispiel implementiert `Interface2`, einschließlich einer Methode geerbt von `Interface1`:  
  
 [!code-vb[VbVbalrOOP#41](../../../../visual-basic/misc/codesnippet/VisualBasic/index_6.vb)]  
  
 Sie können eine schreibgeschützte Eigenschaft mit einer Readwrite-Eigenschaft implementieren (das heißt, Sie müssen sie nicht als schreibgeschützt in der implementierenden Klasse deklarieren).  Implementieren einer Schnittstelle verspricht mindestens die Member zu implementieren, die die Schnittstelle deklariert, aber Sie können mehr Funktionalität bieten, z. B. Schreibbarkeit Ihrer Eigenschaft.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Exemplarische Vorgehensweise: Erstellen und Implementieren von Schnittstellen](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Bietet eine ausführliche Anleitung, die Sie durch den Prozess des Definierens und Implementierens Ihrer eigenen Schnittstellen führt.|  
|[Varianz in generischen Schnittstellen](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|Erläutert Ko- und Kontravarianz in generischen Schnittstellen und enthält eine Liste der Varianten generischen Schnittstellen in .NET Framework.|
