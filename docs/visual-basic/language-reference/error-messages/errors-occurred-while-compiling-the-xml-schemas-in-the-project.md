---
title: Fehler beim Kompilieren der XML-Schemas im Projekt
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Fehler beim Kompilieren der XML-Schemas im Projekt
Fehler beim Kompilieren der XML-Schemas im Projekt. Aus diesem Grund ist die XML-IntelliSense nicht verfügbar.  
  
 Es ist ein Fehler in einem XML-Schemadefinition (XSD)-Schema, das im Projekt enthalten. Dieser Fehler tritt auf, wenn Sie eine XSD-Schemadatei (.xsd) hinzufügen, die Konflikte mit vorhandenen XSD-Schema für das Projekt festgelegt.  
  
 **Fehler-ID:** BC36810  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Doppelklicken Sie auf die Warnung in der **Fehlerliste** Fenster. Visual Basic wird die Position in der XSD-Datei aufzurufen, die die Quelle der Warnung ist. Korrigieren Sie den Fehler in der XSD-Schema.  
  
-   Stellen Sie sicher, dass alle erforderlichen XSD-Schemadateien (.xsd) im Projekt enthalten sind. Möglicherweise müssen Sie auf klicken **alle Dateien anzeigen** auf die **Projekt** Menü, um die XSD-Dateien im **Projektmappen-Explorer**. Mit der rechten Maustaste einer XSD-Datei, und klicken Sie dann auf **zu Projekt hinzufügen** auf die Datei im Projekt enthalten.  
  
-   Wenn Sie die XML zu Schema-Assistenten verwenden, wird dieser Fehler kann auftreten, wenn Sie Schemas mehr als ein Mal aus der gleichen Quelle ableiten. In diesem Fall fügen Sie Sie die vorhandenen XSD-Schema-Dateien aus dem Projekt entfernen können eine neue XML Schema-Elementvorlage, und geben Sie dann die XML zu Schema-Assistenten mit den entsprechenden XML-Datenquellen für das Projekt.  
  
-   Wenn keine Fehler in der XSD-Schema identifiziert wird, möglicherweise die XML-Compiler nicht genügend Informationen, um eine detaillierte Fehlermeldung. Möglicherweise können ausführlichere Fehlerinformationen abgerufen werden, wenn Sie sicherstellen, dass die XML-Namespaces für die XSD-Dateien in Ihrem Projekt Übereinstimmung, die XML-Namespaces für das XML-Schemaset in Visual Studio identifiziert enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Fenster „Fehlerliste“](/visualstudio/ide/reference/error-list-window)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
