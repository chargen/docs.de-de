---
title: DataGrid-Stile und -Vorlagen
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: 71c9b08407c6e570b42c4fbb7dc264829b5dc17c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
---
# <a name="datagrid-styles-and-templates"></a>DataGrid-Stile und -Vorlagen
In diesem Thema wird beschrieben, die Stile und Vorlagen für die <xref:System.Windows.Controls.DataGrid> Steuerelement. Sie können den Standardwert ändern <xref:System.Windows.Controls.ControlTemplate> auf dem Steuerelement ein einzigartiges aussehen zu verleihen. Weitere Informationen finden Sie unter [Anpassen der Darstellung eines vorhandenen Steuerelements durch Erstellen einer ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>DataGrid-Teile  
 Die folgende Tabelle enthält die benannten Teile für die <xref:System.Windows.Controls.DataGrid> Steuerelement.  
  
|Segment|Typ|Beschreibung|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Die Zeile, die Spaltenüberschriften enthält.|  
  
 Beim Erstellen einer <xref:System.Windows.Controls.ControlTemplate> für eine <xref:System.Windows.Controls.DataGrid>, Ihrer Vorlage enthalten möglicherweise eine <xref:System.Windows.Controls.ItemsPresenter> innerhalb einer <xref:System.Windows.Controls.ScrollViewer>. (Die <xref:System.Windows.Controls.ItemsPresenter> wird jedes Element in der <xref:System.Windows.Controls.DataGrid>; das <xref:System.Windows.Controls.ScrollViewer> Bildlauf im Steuerelement aktiviert).  Wenn die <xref:System.Windows.Controls.ItemsPresenter> ist kein direkte untergeordnetes Element von der <xref:System.Windows.Controls.ScrollViewer>, geben Sie die <xref:System.Windows.Controls.ItemsPresenter> den Namen `ItemsPresenter`.  
  
 Die Standardvorlage für den <xref:System.Windows.Controls.DataGrid> enthält eine <xref:System.Windows.Controls.ScrollViewer> Steuerelement. Weitere Informationen zu den Webparts, die definiert, indem Sie die <xref:System.Windows.Controls.ScrollViewer>, finden Sie unter [ScrollViewer-Stile und Vorlagen](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>DataGrid-Zustände  
 Die folgende Tabelle enthält die visueller Zustände für die <xref:System.Windows.Controls.DataGrid> Steuerelement.  
  
|VisualState-Name|VisualStateGroup-Name|Beschreibung|  
|-|-|-|  
|Normal|CommonStates|Der Standardzustand|  
|Deaktiviert|CommonStates|Das Steuerelement ist deaktiviert.|  
|InvalidFocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt den Fokus.|  
|InvalidUnfocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt keinen Fokus.|  
|Gültig|ValidationStates|Das Steuerelement ist gültig.|  
  
## <a name="datagridcell-parts"></a>DataGridCell-Teile  
 Die <xref:System.Windows.Controls.DataGridCell> -Element verfügt nicht über benannte Teile.  
  
## <a name="datagridcell-states"></a>DataGridCell-Zustände  
 Die folgende Tabelle enthält die visueller Zustände für die <xref:System.Windows.Controls.DataGridCell> Element.  
  
|VisualState-Name|VisualStateGroup-Name|Beschreibung|  
|-|-|-|  
|Normal|CommonStates|Der Standardzustand|  
|MouseOver|CommonStates|Der Mauszeiger über der Zelle.|  
|Focused|FocusStates|Die Zelle hat den Fokus.|  
|Ohne Fokus|FocusStates|Die Zelle den Fokus verfügt nicht über werden.|  
|Aktuell|CurrentStates|Die Zelle ist die aktive Zelle.|  
|Regulär|CurrentStates|Die Zelle ist nicht die aktive Zelle.|  
|Anzeige|InteractionStates|Die Zelle befindet sich im Anzeigemodus.|  
|Bearbeiten|InteractionStates|Die Zelle befindet sich im Bearbeitungsmodus befindet.|  
|Ausgewählt|SelectionStates|Die Zelle ausgewählt ist.|  
|Nicht markiert|SelectionStates|Die Zelle ist nicht ausgewählt.|  
|InvalidFocused|ValidationStates|Die Zelle ist ungültig und den Fokus hat.|  
|InvalidUnfocused|ValidationStates|Die Zelle ist ungültig und nicht den Fokus besitzt.|  
|Gültig|ValidationStates|Die Zelle ist ungültig.|  
  
## <a name="datagridrow-parts"></a>DataGridRow-Teile  
 Die <xref:System.Windows.Controls.DataGridRow> -Element verfügt nicht über benannte Teile.  
  
## <a name="datagridrow-states"></a>DataGridRow-Zustände  
 Die folgende Tabelle enthält die visueller Zustände für die <xref:System.Windows.Controls.DataGridRow> Element.  
  
|VisualState-Name|VisualStateGroup-Name|Beschreibung|  
|-|-|-|  
|Normal|CommonStates|Der Standardzustand|  
|MouseOver|CommonStates|Der Mauszeiger über der Zeile.|  
|MouseOver_Editing|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, und der Zeile befindet sich im Bearbeitungsmodus befindet.|  
|MouseOver_Selected|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, und die Zeile ausgewählt ist.|  
|MouseOver_Unfocused_Editing|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, der Zeile befindet sich im Bearbeitungsmodus befindet, und verfügt nicht über den Fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Befindet sich des Mauszeigers über der Zeile, die Zeile ausgewählt ist, und verfügt nicht über den Fokus.|  
|Normal_AlternatingRow|CommonStates|Die Zeile steht ein abwechselnde Zeilen.|  
|Normal_Editing|CommonStates|Die Zeile befindet sich im Bearbeitungsmodus.|  
|Normal_Selected|CommonStates|Die Zeile ausgewählt ist.|  
|Unfocused_Editing|CommonStates|Die Zeile im Bearbeitungsmodus befindet und verfügt nicht über den Fokus.|  
|Unfocused_Selected|CommonStates|Die Zeile ausgewählt ist, und verfügt nicht über den Fokus.|  
|InvalidFocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt den Fokus.|  
|InvalidUnfocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt keinen Fokus.|  
|Gültig|ValidationStates|Das Steuerelement ist gültig.|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader-Teile  
 Die folgende Tabelle enthält die benannten Teile für die <xref:System.Windows.Controls.Primitives.DataGridRowHeader> Element.  
  
|Segment|Typ|Beschreibung|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Das Element, das verwendet wird, um die Größe der Zeile mit einer Überschrift von oben.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Das Element, das verwendet wird, um die Größe der Zeile mit einer Überschrift von unten.|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader-Zustände  
 Die folgende Tabelle enthält die visueller Zustände für die <xref:System.Windows.Controls.Primitives.DataGridRowHeader> Element.  
  
|VisualState-Name|VisualStateGroup-Name|Beschreibung|  
|-|-|-|  
|Normal|CommonStates|Der Standardzustand|  
|MouseOver|CommonStates|Der Mauszeiger über der Zeile.|  
|MouseOver_CurrentRow|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, und die Zeile wird die aktuelle Zeile.|  
|MouseOver_CurrentRow_Selected|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, und die Zeile ist, aktuellen und dem ausgewählten.|  
|MouseOver_EditingRow|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, und der Zeile befindet sich im Bearbeitungsmodus befindet.|  
|MouseOver_Selected|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, und die Zeile ausgewählt ist.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Befindet sich der Mauszeiger über der Zeile, die Zeile wird der aktuellen und dem ausgewählten und verfügt nicht über den Fokus.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Der Mauszeiger auf die Zeile positioniert ist, der Zeile befindet sich im Bearbeitungsmodus befindet, und verfügt nicht über den Fokus.|  
|MouseOver_Unfocused_Selected|CommonStates|Befindet sich des Mauszeigers über der Zeile, die Zeile ausgewählt ist, und verfügt nicht über den Fokus.|  
|Normal_CurrentRow|CommonStates|Die Zeile ist die aktuelle Zeile.|  
|Normal_CurrentRow_Selected|CommonStates|Die Zeile der aktuellen Zeile und ausgewählt ist.|  
|Normal_EditingRow|CommonStates|Die Zeile befindet sich im Bearbeitungsmodus.|  
|Normal_Selected|CommonStates|Die Zeile ausgewählt ist.|  
|Unfocused_CurrentRow_Selected|CommonStates|Die Zeile der aktuellen Zeile ist, ausgewählt ist und verfügt nicht über den Fokus.|  
|Unfocused_EditingRow|CommonStates|Die Zeile im Bearbeitungsmodus befindet und verfügt nicht über den Fokus.|  
|Unfocused_Selected|CommonStates|Die Zeile ausgewählt ist, und verfügt nicht über den Fokus.|  
|InvalidFocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt den Fokus.|  
|InvalidUnfocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt keinen Fokus.|  
|Gültig|ValidationStates|Das Steuerelement ist gültig.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter-Teile  
 Die folgende Tabelle enthält die benannten Teile für die <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> Element.  
  
|Segment|Typ|Beschreibung|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Der Platzhalter für die Spaltenkopfzeilen.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter-Zustände  
 Die folgende Tabelle enthält die visueller Zustände für die <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> Element.  
  
|VisualState-Name|VisualStateGroup-Name|Beschreibung|  
|-|-|-|  
|InvalidFocused|ValidationStates|Die Zelle ist ungültig und den Fokus hat.|  
|InvalidUnfocused|ValidationStates|Die Zelle ist ungültig und nicht den Fokus besitzt.|  
|Gültig|ValidationStates|Die Zelle ist ungültig.|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader-Teile  
 Die folgende Tabelle enthält die benannten Teile für die <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> Element.  
  
|Segment|Typ|Beschreibung|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Das Element, das verwendet wird, um die Größe der Kopfzeile der Spalte von links.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Das Element, das verwendet wird, um die Größe der Kopfzeile der Spalte von rechts.|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader-Zustände  
 Die folgende Tabelle enthält die visueller Zustände für die <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> Element.  
  
|VisualState-Name|VisualStateGroup-Name|Beschreibung|  
|-|-|-|  
|Normal|CommonStates|Der Standardzustand|  
|MouseOver|CommonStates|Der Mauszeiger ist über dem Steuerelement positioniert.|  
|Gedrückt|CommonStates|Das Steuerelement wird gedrückt.|  
|SortAscending|SortStates|Die Spalte wird in aufsteigender Reihenfolge sortiert.|  
|SortDescending|SortStates|Die Spalte wird in absteigender Reihenfolge sortiert.|  
|Unsortierte|SortStates|Die Spalte ist nicht sortiert.|  
|InvalidFocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt den Fokus.|  
|InvalidUnfocused|ValidationStates|Das Steuerelement ist nicht gültig und besitzt keinen Fokus.|  
|Gültig|ValidationStates|Das Steuerelement ist gültig.|  
  
## <a name="datagrid-controltemplate-example"></a>Beispiel für DataGrid-ControlTemplate  
 Das folgende Beispiel zeigt, wie Sie definieren eine <xref:System.Windows.Controls.ControlTemplate> für die <xref:System.Windows.Controls.DataGrid> -Steuerelement und seine zugehörigen Typen.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 Im vorhergehenden Beispiel wird mindestens eine der folgenden Ressourcen verwendet.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Das vollständige Beispiel finden Sie unter [Beispiel zum Formatieren mit ControlTemplates](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Steuerelementformate und -vorlagen](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Anpassung von Steuerelementen](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Erstellen von Formaten und Vorlagen](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Anpassen der Darstellung eines vorhandenen Steuerelements durch Erstellen einer ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
