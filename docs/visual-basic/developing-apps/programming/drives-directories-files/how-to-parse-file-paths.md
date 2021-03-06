---
title: 'Gewusst wie: Analysieren von Dateipfaden in Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 7479f368558a8a8a07c1e6ed588bdfef21a0b1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>Gewusst wie: Analysieren von Dateipfaden in Visual Basic
Das <xref:Microsoft.VisualBasic.FileIO.FileSystem> -Objekt bietet eine Reihe nützlicher Methoden für die Analyse von Dateipfaden.  
  
-   Die <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> -Methode übernimmt zwei Pfade und gibt einen korrekt formatierten kombinierten Pfad zurück.  
  
-   Die <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> -Methode gibt den absoluten übergeordneten Pfad des bereitgestellten Pfads zurück.  
  
-   Die <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> -Methode gibt ein <xref:System.IO.FileInfo> -Objekt zurück, das abgefragt werden kann, um die Eigenschaften der Datei zu ermitteln, beispielsweise deren Name und Pfad.  
  
 Beurteilen Sie den Inhalt der Datei nicht anhand der Dateinamenerweiterung. Bei der Datei "Form1.vb" handelt es sich zum Beispiel nicht unbedingt um eine Visual Basic-Quelldatei.  
  
### <a name="to-determine-a-files-name-and-path"></a>So ermitteln Sie den Namen und den Pfad einer Datei  
  
-   Verwenden Sie die <xref:System.IO.FileInfo.DirectoryName%2A> - und die <xref:System.IO.FileInfo.Name%2A> -Eigenschaft des <xref:System.IO.FileInfo> -Objekts, um den Namen und den Pfad einer Datei zu ermitteln. In diesem Beispiel werden der Name und der Pfad ermittelt und angezeigt.  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>So kombinieren Sie den Namen und das Verzeichnis einer Datei, um den vollständigen Pfad zu erstellen  
  
-   Verwenden Sie die `CombinePath` -Methode, und geben Sie das Verzeichnis und den Namen an. In diesem Beispiel werden die im vorherigen Beispiel erstellten Zeichenfolgen `folderPath` und `fileName` kombiniert, und das Ergebnis wird angezeigt.  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [Gewusst wie: Abrufen einer Sammlung von Dateien in einem Verzeichnis](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
