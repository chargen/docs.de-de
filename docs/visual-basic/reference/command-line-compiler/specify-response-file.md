---
title: '@ (Antwortdatei festlegen) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4201dcc094364899984e13c85f2f43a6467ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="-specify-response-file-visual-basic"></a>@ (Antwortdatei festlegen) (Visual Basic)
Gibt eine Datei mit Compileroptionen und Quellcodedateien zu kompilieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>Argumente  
 `response_file`  
 Erforderlich. Eine Datei, die Compileroptionen und Quellcodedateien kompilieren auflistet. Setzen Sie den Dateinamen in Anführungszeichen (""), wenn es sich um ein Leerzeichen enthält.  
  
## <a name="remarks"></a>Hinweise  
 Der Compiler verarbeitet die Compileroptionen und Quellcodedateien in einer Antwortdatei angegeben werden, als ob sie in der Befehlszeile angegeben gewesen.  
  
 Um mehr als eine Antwortdatei in einer Kompilierung anzugeben, geben Sie mehrere Antwortdatei Optionen, wie z. B. die folgenden.  
  
```  
@file1.rsp @file2.rsp  
```  
  
 In einer Antwort können mehrere Compileroptionen und Quellcodedateien in einer Zeile angezeigt. Eine einzelne Compileroption-Spezifikation muss in einer Zeile angezeigt werden (kann nicht mehrere Zeilen umfassen). Antwortdateien können Kommentare, die mit der `#` Symbol.  
  
 Sie können in eine oder mehrere Antwortdateien angegebenen Optionen in der Befehlszeile angegebene Optionen kombinieren. Der Compiler verarbeitet die Befehlsoptionen an, sobald diese auftreten. Aus diesem Grund können die Befehlszeilenargumente zuvor aufgeführte Optionen in Antwortdateien überschreiben. Im Gegensatz dazu überschreiben Optionen in einer Antwortdatei in der Befehlszeile oder in anderen Antwortdateien zuvor aufgeführten Optionen.  
  
 Visual Basic bietet die Datei "vbc.rsp", die sich im selben Verzeichnis wie die Datei Vbc.exe befindet. Die Datei "vbc.rsp" ist standardmäßig enthalten, es sei denn, die `-noconfig` Option verwendet wird. Weitere Informationen finden Sie unter [- Noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).  
  
> [!NOTE]
>  Die `@` Option ist nicht in der Visual Studio-Entwicklungsumgebung verfügbar; er ist nur bei verfügbar über die Befehlszeile kompilieren.  
  
## <a name="example"></a>Beispiel  
 Die folgenden Zeilen werden aus einer Beispiel-Antwortdatei.  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie die `@` Option mit der Antwortdatei, die mit dem Namen `File1.rsp`.  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Basic-Befehlszeilencompiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Beispiele für Kompilierungsbefehlszeilen](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
