---
title: '&lt;permission&gt; (C#-Programmierhandbuch)'
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 815d303c9cfbf01588f5f2877e9f87a7ebbea9a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="ltpermissiongt-c-programming-guide"></a>&lt;permission&gt; (C#-Programmierhandbuch)
## <a name="syntax"></a>Syntax  
  
```xml  
<permission cref="member">description</permission>  
```  
  
#### <a name="parameters"></a>Parameter  
 cref = " `member`"  
 Ein Verweis auf einen Member oder ein Feld, das von der aktuellen Kompilierungsumgebung aufgerufen werden kann. Der Compiler prüft, ob das angegebene Codeelement vorhanden ist, und übersetzt in der Ausgabe-XML `member` in den kanonischen Elementnamen. *member* muss in doppelte Anführungszeichen (" ") gesetzt werden.  
  
 Weitere Informationen zum Erstellen eines cref-Verweises auf einen generischen Typ finden Sie unter [\<see>](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Eine Beschreibung des Zugriffs auf den Member  
  
## <a name="remarks"></a>Hinweise  
 Mit dem \<permission>-Tag können Sie den Zugriff auf einen Member dokumentieren. Mit der <xref:System.Security.PermissionSet>-Klasse können Sie den Zugriff auf ein Member angeben.  
  
 Dokumentationskommentare werden zu einer Datei verarbeitet, indem sie mit [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) kompiliert werden.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
 [Empfohlene Tags für Dokumentationskommentare](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
