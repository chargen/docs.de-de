---
title: IsNot-Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: babee364d350ca84a8379f675acc4b5c87f98303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="isnot-operator-visual-basic"></a>IsNot-Operator (Visual Basic)
Vergleicht zwei Objektverweisvariablen.  
  
## <a name="syntax"></a>Syntax  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Teile  
 `result`  
 Erforderlich. Ein `Boolean`-Wert.  
  
 `object1`  
 Erforderlich. Alle `Object` Variable oder ein Ausdruck.  
  
 `object2`  
 Erforderlich. Alle `Object` Variable oder ein Ausdruck.  
  
## <a name="remarks"></a>Hinweise  
 Die `IsNot` -Operator ermittelt, ob zwei Objektverweise auf unterschiedliche Objekte verweisen. Er führt jedoch keine Wertvergleiche. Wenn `object1` und `object2` beide verweisen auf genau dieselbe Objektinstanz, `result` ist `False`; Wenn sie keinen `result` ist `True`.  
  
 `IsNot` ist das Gegenteil von der `Is` Operator. Der Vorteil der `IsNot` ist, dass Sie vermeiden können, umständliche Syntax mit `Not` und `Is`, die schwer zu lesen sein können.  
  
 Sie können die `Is` und `IsNot` Operatoren, um früh gebundene und spät gebundene Objekte zu testen.  
  
> [!NOTE]
>  Die `IsNot` Operator kann nicht verwendet werden, um das Vergleichen von Ausdrücken, die zurückgegeben werden, aus der `TypeOf` Operator. Stattdessen müssen Sie verwenden die `Not` und `Is` Operatoren.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel verwendet die `Is` Operator und die `IsNot` Operator, um denselben Vergleich zu erreichen.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Is-Operator](../../../visual-basic/language-reference/operators/is-operator.md)  
 [TypeOf-Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Operator Precedence in Visual Basic (Operatorrangfolge in Visual Basic)](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Gewusst wie: Überprüfen, ob zwei Objekte identisch sind](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
