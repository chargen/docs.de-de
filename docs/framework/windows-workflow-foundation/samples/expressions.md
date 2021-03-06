---
title: Expressions2
ms.date: 03/30/2017
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
ms.openlocfilehash: 2f08e114729d9fd00a51fe0c4182862257e8c330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="expressions"></a>Ausdrücke
In diesem Beispiel wird veranschaulicht, wie Basisausdrücke in einem Workflow verwendet werden. Es besteht aus einem Workflow, der die grundlegende Gehaltsstatistik für zwei Mitarbeiter eines fiktiven Unternehmens berechnet. In "Employee.cs" und "SalaryStats.cs" sind zwei Klassen (`Employee` und `SalaryStats`) definiert. Diese Klassen werden in einem Workflow verwendet, der zeigt, wie einfache arithmetische Operationen und Zeichenfolgenoperationen für Variableneigenschaften komplexer Typen ausgeführt werden.  
  
 Der Workflow zur Berechnung der Gehaltsstatistik ist zur Veranschaulichung beider Erstellungsformate sowohl in XAML als auch in C# definiert. Die XAML-Version ist in "SalaryCalculation.xaml" enthalten und kann im Workflow-Designer angezeigt und bearbeitet werden. Die C#-Version befindet sich in "Program.cs". Die in XAML verwendeten Ausdrücke entsprechen Visual Basic-Syntax und verwenden die Ausdrucksaktivitäten <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> und <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> zur Ausführung. Weitere Informationen zu Visual Basic-Ausdrücken finden Sie unter [Visual Basic-Ausdrücke](http://go.microsoft.com/fwlink/?LinkId=165912). Ausdrücke in C# werden als Lambda-Ausdrücke geschrieben und verwenden die Ausdrucksaktivitäten <xref:System.Activities.Expressions.LambdaValue%601> und <xref:System.Activities.Expressions.LambdaReference%601>. Durch das Schreiben von Ausdrücken als Lambdaausdrücke kann der C#-Compiler Syntaxhervorhebung und statische Überprüfung bereitstellen. Weitere Informationen zu Lambda-Ausdrücken in c# finden Sie unter [Lambda-Ausdrücke (C#-Programmierhandbuch)](http://go.microsoft.com/fwlink/?LinkId=182082). Wenn ein Workflow im Code mithilfe von Visual Basic erstellt wird, werden Visual Basic-Lambdaausdrücke verwendet. Weitere Informationen zu Lambda-Ausdrücken in Visual Basic finden Sie unter [Lambda-Ausdrücke (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437). Weitere Informationen zum Erstellen von Workflows mithilfe von Code finden Sie unter [Entwickeln von Workflows, Aktivitäten und Ausdrücken mithilfe von imperativem Code](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### <a name="to-run-the-sample"></a>So führen Sie das Beispiel aus  
  
1.  Öffnen Sie die Projektmappe "Expressions.sln" in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Drücken Sie STRG + UMSCHALT + B, um die Projektmappe zu erstellen, oder wählen Sie **Projektmappe** aus der **erstellen** Menü.  
  
    > [!NOTE]
    >  Zum Öffnen von "SalaryCalculation.xaml" im Visual Studio-Designer müssen Sie das Projekt zunächst kompilieren, um sicherzustellen, dass die `Employee`-Klasse und die `SalaryStats`-Klasse im Designer zur Verfügung stehen.  
  
3.  Sobald die Erstellung erfolgreich war, drücken Sie F5, oder wählen Sie **Debuggen** aus der **Debuggen** Menü. Alternativ können Sie STRG + F5 oder wählen Sie **Starten ohne Debugging** aus der **Debuggen** -Menü, um ohne Debuggen auszuführen.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, fahren Sie mit [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) aller Windows Communication Foundation (WCF) herunterladen und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`