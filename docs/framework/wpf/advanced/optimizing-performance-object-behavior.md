---
title: 'Optimieren der Leistung: Objektverhalten'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interface virtualization [WPF]
- dependency properties [WPF], performance
- event handlers [WPF]
- object performance considerations [WPF]
- Freezable objects [WPF], performance
ms.assetid: 73aa2f47-1d73-439a-be1f-78dc4ba2b5bd
ms.openlocfilehash: 2e1f56dec87de7a22aa8a0bfefe84222d74ba085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="optimizing-performance-object-behavior"></a>Optimieren der Leistung: Objektverhalten
Wenn Sie das Verhalten von systeminternen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-Objekten verstehen, können Sie Funktionalität und Leistung optimal miteinander vereinen.  
  

  
<a name="Not_Removing_Event_Handlers"></a>   
## <a name="not-removing-event-handlers-on-objects-may-keep-objects-alive"></a>Wenn Ereignishandler nicht aus Objekten entfernt werden, bleiben diese möglicherweise aktiv  
 Der Delegat, den ein Objekt an sein Ereignis übergibt, ist gewissermaßen ein Verweis auf dieses Objekt. Aufgrund von Ereignishandlern können Objekte länger als erwartet aktiv sein. Wenn sie ein Objekt bereinigen, das registriert wurde, um auf ein Ereignis eines Objekts zu lauschen, ist es erforderlich, dass Sie diesen Delegaten entfernen, bevor Sie das Objekt freigeben. Wenn nicht benötigte Objekte weiter aktiv sind, erhöht dies die Speicherauslastung Ihrer Anwendung. Dies ist insbesondere dann der Fall, wenn das Objekt der Stamm einer logischen oder visuellen Struktur ist.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] führt ein schwaches Ereignislistenermuster für Ereignisse ein, das dann nützlich sein kann, wenn die Beziehungen der Objektlebensdauer zwischen Quelle und Listener schwierig zu überwachen sind. Einige vorhandene [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-Ereignisse verwenden dieses Muster. Wenn Sie Objekte mit benutzerdefinierten Ereignissen implementieren, kann dieses Muster für Sie nützlich sein. Weitere Informationen finden Sie unter [Schwache Ereignismuster](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).  
  
 Es gibt mehrere Tools, wie z.B. den CLR-Profiler und den Workingset-Viewer, die Informationen zur Speicherauslastung eines angegebenen Prozesses zur Verfügung stellen können. Der CLR-Profiler umfasst eine Reihe sehr nützlicher Ansichten des Belegungsprofils, darunter z.B. ein Histogramm der zugewiesenen Typen, Zuordnungs- und Aufrufdiagramme, eine Zeitachse mit den automatische Speicherbereinigungen verschiedener Generationen und der daraus entstehende Status des verwalteten Heaps nach diesen Bereinigungen sowie eine Aufrufstruktur, die Zuweisungen und Laden von Assemblys für jede Methode veranschaulicht. Weitere Informationen finden Sie unter [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=117435).  
  
<a name="DPs_and_Objects"></a>   
## <a name="dependency-properties-and-objects"></a>Anhängigkeitseigenschaften und Objekte  
 Im Allgemeinen den Zugriff auf eine Abhängigkeitseigenschaft, der eine <xref:System.Windows.DependencyObject> ist nicht länger als der Zugriff auf eine [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Eigenschaft. Während es einen kleinen Leistungsaufwand für das Festlegen eines Eigenschaftswerts gibt, ist das Abrufen eines Werts genauso schnell wie das Abrufen des Werts über die [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]-Eigenschaft. Der kleine Leistungsaufwand wird durch die Tatsache verursacht, dass Abhängigkeitseigenschaften zuverlässige Funktionen unterstützen, wie z.B. die Datenbindung, die Animation, die Vererbung und das Formatieren. Weitere Informationen finden Sie unter [Übersicht über Abhängigkeitseigenschaften](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
### <a name="dependencyproperty-optimizations"></a>DependencyProperty-Optimierungen  
 Sie sollten Abhängigkeitseigenschaften in Ihrer Anwendung sorgfältig definieren. Wenn Ihre <xref:System.Windows.DependencyProperty> wirkt sich auf nur Rendern Typoptionen-Metadaten, statt weitere Metadatenoptionen wie z. B. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, kennzeichnen Sie es daher durch Überschreiben der zugehörigen Metadaten. Weitere Informationen über das Überschreiben oder Abrufen von Eigenschaftenmetadaten finden Sie unter [Metadaten für Abhängigkeitseigenschaften](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Möglicherweise ist es effizienter, mit einem Handler für Eigenschaftenänderungen die Messungs-, Anordnungs- und Rendering-Durchläufe manuell für ungültig zu erklären, wenn nicht alle Eigenschaftenänderungen „Messung“, „Anordnung“ und „Rendering“ betreffen. Möglicherweise möchten Sie einen Hintergrund nur dann erneut rendern, wenn ein Wert höher als ein festgelegter Grenzwert ist. In diesem Fall würde Ihr Handler für Eigenschaftenänderungen nur „render“ für ungültig erklären, wenn der festgelegte Grenzwert überschritten wird.  
  
### <a name="making-a-dependencyproperty-inheritable-is-not-free"></a>Sie können eine Abhängigkeitseigenschaft nicht frei vererben  
 Registrierte Abhängigkeitseigenschaften sind standardmäßig nicht vererbbar. Allerdings können Sie eine Eigenschaft explizit vererbbar machen. Obwohl dies nützlich ist, beeinträchtigt das Konvertieren einer Eigenschaft in eine vererbbare Eigenschaft die Leistung, da die Zeit für das Aufheben der Validierung erhöht wird.  
  
### <a name="use-registerclasshandler-carefully"></a>Verwenden Sie RegisterClassHandler mit Vorsicht  
 Beim Aufrufen <xref:System.Windows.EventManager.RegisterClassHandler%2A> ermöglicht Ihnen das Speichern der Zustand der Instanz, es ist wichtig, sich bewusst sein, dass der Handler für jede Instanz aufgerufen wird, die Leistungsprobleme verursachen können. Verwenden Sie nur <xref:System.Windows.EventManager.RegisterClassHandler%2A> Fall, Ihre Anwendung benötigt, Ihre instanzzustand zu speichern.  
  
### <a name="set-the-default-value-for-a-dependencyproperty-during-registration"></a>Legen Sie den Standardwert für eine Abhängigkeitseigenschaft während der Registrierung fest  
 Beim Erstellen einer <xref:System.Windows.DependencyProperty> , erfordert einen Standardwert, legen Sie den Wert mithilfe der Standardmetadaten, die als Parameter übergeben der <xref:System.Windows.DependencyProperty.Register%2A> Methode der <xref:System.Windows.DependencyProperty>. Nutzen Sie diese Vorgehensweise, statt den Eigenschaftswert in einem Konstruktor oder in jeder Instanz des Elements festzulegen.  
  
### <a name="set-the-propertymetadata-value-using-register"></a>Festlegen des Werts der Metadaten der Eigenschaft mit der Register-Methode  
 Beim Erstellen einer <xref:System.Windows.DependencyProperty>, haben Sie die Möglichkeit der Einstellung der <xref:System.Windows.PropertyMetadata> entweder die <xref:System.Windows.DependencyProperty.Register%2A> oder <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> Methoden. Obwohl Ihr Objekt einen statischen Konstruktor aufrufen möglicherweise <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>, dies entspricht nicht der optimalen Lösung und wird die Leistung beeinträchtigen. Legen Sie für optimale Leistung der <xref:System.Windows.PropertyMetadata> während des Aufrufs <xref:System.Windows.DependencyProperty.Register%2A>.  
  
<a name="Freezable_Objects"></a>   
## <a name="freezable-objects"></a>Freezable-Objekte  
 Ein <xref:System.Windows.Freezable> ist eine besondere Art von Objekt, das zwei Zustände verfügt: nicht fixiert und fixiert. Wenn Sie Objekte immer dann, wenn es möglich ist, fixieren, wird dadurch die Leistung Ihrer Anwendung verbessert und ihr Workingset reduziert. Weitere Informationen finden Sie unter der [Übersicht über Freezable-Objekte](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Jede <xref:System.Windows.Freezable> verfügt über eine <xref:System.Windows.Freezable.Changed> Ereignis, das ausgelöst wird, wenn er sich ändert. Änderungsbenachrichtigungen nehmen jedoch einiges an Anwendungsleistung in Anspruch.  
  
 Betrachten Sie das folgende Beispiel die einzelnen <xref:System.Windows.Shapes.Rectangle> verwendet die gleiche <xref:System.Windows.Media.Brush> Objekt:  
  
 [!code-csharp[Performance#PerformanceSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet2)]
 [!code-vb[Performance#PerformanceSnippet2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet2)]  
  
 Standardmäßig [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bietet einen Ereignishandler für das <xref:System.Windows.Media.SolidColorBrush> des Objekts <xref:System.Windows.Freezable.Changed> Ereignis, um die für ungültig zu erklären die <xref:System.Windows.Shapes.Rectangle> des Objekts <xref:System.Windows.Shapes.Shape.Fill%2A> Eigenschaft. In diesem Fall jedes Mal, wenn die <xref:System.Windows.Media.SolidColorBrush> ausgelöst hat seine <xref:System.Windows.Freezable.Changed> es erforderlich ist, rufen die Rückruffunktion für jedes Ereignis <xref:System.Windows.Shapes.Rectangle>– die Ansammlung von diesen Rückruf Funktionsaufrufe vorgeben erhebliche Leistungseinbußen. Darüber hinaus ist es sehr ressourcenintensiv, Handler an diesem Punkt hinzuzufügen und zu entfernen, da die Anwendung dazu die gesamte Liste durchlaufen müssten. Wenn in Ihrem Anwendungsszenario nie geändert die <xref:System.Windows.Media.SolidColorBrush>, Sie bezahlen deren Wartungskosten <xref:System.Windows.Freezable.Changed> Ereignishandler unnötig.  
  
 Das Fixieren von einem <xref:System.Windows.Freezable> kann die Leistung verbessern, da es nicht mehr Ressourcen zur Verwaltung von änderungsbenachrichtigungen erweitern muss. Die folgende Tabelle zeigt die Größe eines einfachen <xref:System.Windows.Media.SolidColorBrush> bei seiner <xref:System.Windows.Freezable.IsFrozen%2A> -Eigenschaftensatz auf `true`, im Vergleich zu, wenn er nicht ist. Hierbei wird angenommen, ein Pinsel zum Anwenden der <xref:System.Windows.Shapes.Shape.Fill%2A> Eigenschaft zehn <xref:System.Windows.Shapes.Rectangle> Objekte.  
  
|**Zustand**|**Size**|  
|---------------|--------------|  
|Fixiert <xref:System.Windows.Media.SolidColorBrush>|212 Bytes|  
|Ist nicht fixiert <xref:System.Windows.Media.SolidColorBrush>|972 Bytes|  
  
 Im folgenden Codebeispiel wird dieses Konzept veranschaulicht:  
  
 [!code-csharp[Performance#PerformanceSnippet3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet3)]
 [!code-vb[Performance#PerformanceSnippet3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet3)]  
  
### <a name="changed-handlers-on-unfrozen-freezables-may-keep-objects-alive"></a>Durch geänderte Handler auf nicht fixierten Freezable-Objekte bleiben Objekte möglicherweise aktiv  
 Der Delegat, der an ein Objekt übergibt eine <xref:System.Windows.Freezable> des Objekts <xref:System.Windows.Freezable.Changed> Ereignis ist tatsächlich ein Verweis auf dieses Objekt. Aus diesem Grund <xref:System.Windows.Freezable.Changed> Ereignishandler können erhalten Objekte länger als erwartet. Wenn ein Objekt bereinigen, das zum Abhören registriert hat eine <xref:System.Windows.Freezable> des Objekts <xref:System.Windows.Freezable.Changed> Ereignis, es ist wichtig, diese Delegaten zu entfernen, bevor Sie die Freigabe eines Objekts.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Außerdem bindet <xref:System.Windows.Freezable.Changed> Ereignisse intern. Z. B. alle Abhängigkeitseigenschaften die akzeptieren <xref:System.Windows.Freezable> als ein Wert überwachen, <xref:System.Windows.Freezable.Changed> Ereignisse automatisch. Die <xref:System.Windows.Shapes.Shape.Fill%2A> -Eigenschaft, die nimmt eine <xref:System.Windows.Media.Brush>, veranschaulicht dieses Konzept.  
  
 [!code-csharp[Performance#PerformanceSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet4)]
 [!code-vb[Performance#PerformanceSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet4)]  
  
 Bei der Zuordnung von `myBrush` auf `myRectangle.Fill`, einen Delegaten zurück auf die <xref:System.Windows.Shapes.Rectangle> Objekt werden hinzugefügt werden, um die <xref:System.Windows.Media.SolidColorBrush> des Objekts <xref:System.Windows.Freezable.Changed> Ereignis. Dies bedeutet, dass folgender Code `myRect` nicht zur automatischen Speicherbereinigung berechtigt:  
  
 [!code-csharp[Performance#PerformanceSnippet5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet5)]
 [!code-vb[Performance#PerformanceSnippet5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet5)]  
  
 In diesem Fall `myBrush` behalten ist `myRectangle` aktiv und wird aufgerufen, wenn es ausgelöst wird seine <xref:System.Windows.Freezable.Changed> Ereignis. Beachten Sie, Zuweisen von `myBrush` auf die <xref:System.Windows.Shapes.Shape.Fill%2A> Eigenschaft eines neuen <xref:System.Windows.Shapes.Rectangle> wird einfach an einen anderen Ereignishandler hinzufügen `myBrush`.  
  
 Wird empfohlen, um diese Arten von Objekten zu bereinigen, entfernen Sie die <xref:System.Windows.Media.Brush> aus der <xref:System.Windows.Shapes.Shape.Fill%2A> -Eigenschaft, die wiederum zu entfernen, wird die <xref:System.Windows.Freezable.Changed> -Ereignishandler.  
  
 [!code-csharp[Performance#PerformanceSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet6)]
 [!code-vb[Performance#PerformanceSnippet6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet6)]  
  
<a name="User_Interface_Virtualization"></a>   
## <a name="user-interface-virtualization"></a>Virtualisierung der Benutzeroberfläche  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bietet auch eine Variante der <xref:System.Windows.Controls.StackPanel> -Element, das von datengebundenen untergeordneten Inhalt automatisch "virtualisiert". In diesem Zusammenhang bezieht sich das Wort „virtualisieren“ auf eine Technik, mit der eine Teilmenge von Objekten aus einer größeren Menge von Datenelementen generiert wird, je nachdem, welche Elemente auf dem Bildschirm sichtbar sind. Es ist sowohl für den Arbeitsspeicher als auch für den Prozessor sehr aufwändig, eine große Menge an UI-Elementen zu generieren, wenn sich möglicherweise nur sehr wenige Elemente zu einer angegebenen Zeit auf einem Bildschirm befinden. <xref:System.Windows.Controls.VirtualizingStackPanel> (über eine Funktionalität von bereitgestellten <xref:System.Windows.Controls.VirtualizingPanel>) sichtbaren Elemente berechnet und kann mit der <xref:System.Windows.Controls.ItemContainerGenerator> aus einer <xref:System.Windows.Controls.ItemsControl> (z. B. <xref:System.Windows.Controls.ListBox> oder <xref:System.Windows.Controls.ListView>) nur Elemente für die sichtbaren Elemente erstellen.  
  
 Zur Leistungsoptimierung werden visuelle Objekte für diese Elemente nur generiert oder aktiv gehalten, wenn sie auf dem Bildschirm sichtbar sind. Wenn sie sich nicht mehr im sichtbaren Bereich des Steuerelements befinden, können die visuellen Objekte entfernt werden. Dies ist nicht zu verwechseln mit Datenvirtualisierung, bei der Datenobjekte nicht alle in der lokalen Auflistung vorhanden sind, sondern bei Bedarf einfließen.  
  
 Die folgende Tabelle zeigt die verstrichene Zeit hinzufügen und das rendering von 5000 <xref:System.Windows.Controls.TextBlock> Elemente, die eine <xref:System.Windows.Controls.StackPanel> und ein <xref:System.Windows.Controls.VirtualizingStackPanel>. In diesem Szenario stellt die Maße die Zeit zwischen anfügen zu eine Textzeichenfolge dar, mit die <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Eigenschaft ein <xref:System.Windows.Controls.ItemsControl> Objekt, das die Zeit, wenn der Bereich die Textzeichenfolge Anzeigeelemente.  
  
|**Hostpanel**|**Renderingzeit (in ms)**|  
|--------------------|----------------------------|  
|<xref:System.Windows.Controls.StackPanel>|3210|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|46|  
  
## <a name="see-also"></a>Siehe auch  
 [Optimieren der WPF-Anwendungsleistung](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Planen der Anwendungsleistung](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Vorteile der Hardware nutzen](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Layout und Entwurf](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D-Grafiken und Bildverarbeitung](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Anwendungsressourcen](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datenbindung](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Weitere Leistungsempfehlungen](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
