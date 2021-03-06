---
title: Ausdruck ist vom Typ &#39; &lt;Typename&gt; &#39; die eines eingeschränkten Typs ist, und kann nicht verwendet werden, um die von der geerbten Member zugreifen &#39;Objekt&#39; oder &#39;ValueType&#39;
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 2ba2298da77ac31abc0b1b4ad84328be7bc6dbb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="expression-has-the-type-39lttypenamegt39-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-39object39-or-39valuetype39"></a>Ausdruck ist vom Typ &#39; &lt;Typename&gt; &#39; die eines eingeschränkten Typs ist, und kann nicht verwendet werden, um die von der geerbten Member zugreifen &#39;Objekt&#39; oder &#39;ValueType&#39;
Ein Ausdruck ergibt ein Typ, der von der common Language Runtime (CLR) geschachtelt werden kann, aber greift auf ein Element, das Boxing erfordert.  
  
 *Boxing* bezieht sich auf die Verarbeitung, die zum Konvertieren eines Typs in `Object` oder gelegentlich in <xref:System.ValueType>erforderlich ist. Die common Language Runtime kann nicht bestimmte Typen, z. B. Feld <xref:System.ArgIterator>, <xref:System.RuntimeArgumentHandle>, und <xref:System.TypedReference>.  
  
 Dieser Ausdruck versucht, den eingeschränkten Typ zu verwenden, zum Aufrufen einer Methode geerbt von <xref:System.Object> oder <xref:System.ValueType>, wie z. B. <xref:System.Object.GetHashCode%2A> oder <xref:System.Object.ToString%2A>. Um diese Methode zugreifen zu können, hat Visual Basic eine implizites Boxing-Konvertierung versucht, die diesen Fehler verursacht.  
  
 **Fehler-ID:** BC31393  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Suchen Sie den Ausdruck, der den angegebenen Typ ergibt.  
  
2.  Suchen Sie den Teil der Anweisung, die zum Aufrufen der Methode geerbt von versucht <xref:System.Object> oder <xref:System.ValueType>.  
  
3.  Schreiben Sie die Anweisung aus, um den Aufruf der Methode zu vermeiden.  
  
## <a name="see-also"></a>Siehe auch  
 [Implizite und explizite Konvertierungen](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
