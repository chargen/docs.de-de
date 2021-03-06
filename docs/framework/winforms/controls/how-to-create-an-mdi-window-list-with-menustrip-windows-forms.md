---
title: 'Gewusst wie: Erstellen einer MDI-Fensterliste mithilfe von MenuStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
ms.openlocfilehash: c87ffadaef2842f10d40f6fd84eb1c70c6dfe37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Gewusst wie: Erstellen einer MDI-Fensterliste mithilfe von MenuStrip (Windows Forms)
Verwenden Sie die Multiple Document Interface (MDI) zum Erstellen von Anwendungen, die mehrere Dokumente öffnen, auf die gleiche Zeit, und kopieren und Einfügen von Inhalt aus einem Dokument in den anderen können.  
  
 Dieses Verfahren wird gezeigt, wie eine Liste aller aktiven untergeordneten Formulare auf dem übergeordneten Menü "Fenster" zu erstellen.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Zum Erstellen einer MDI-Fensterliste auf einem MenuStrip  
  
1.  Erstellen Sie ein Formular, und legen Sie dessen <xref:System.Windows.Forms.Form.IsMdiContainer%2A>-Eigenschaft auf `true` fest.  
  
2.  Fügen Sie dem Formular eine <xref:System.Windows.Forms.MenuStrip> hinzu.  
  
3.  Fügen Sie zwei Menüelemente auf oberster Ebene auf die <xref:System.Windows.Forms.MenuStrip> und legen Sie ihre <xref:System.Windows.Forms.Control.Text%2A> Eigenschaften `&File` und `&Window`.  
  
4.  Fügen Sie dem `&File`-Menüelement ein Untermenüelement hinzu, und legen Sie dessen <xref:System.Windows.Forms.ToolStripItem.Text%2A>-Eigenschaft auf `&Open` fest.  
  
5.  Festlegen der <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Eigenschaft von der <xref:System.Windows.Forms.MenuStrip> auf die `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Das Projekt ein Formular hinzu, und fügen Sie das gewünschte Steuerelement hinzu, z. B. ein anderer <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Erstellen Sie einen Ereignishandler für das <xref:System.Windows.Forms.Control.Click>-Ereignis von `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  Fügen Sie im Ereignishandler Code etwa wie folgt zu erstellen, und zeigen neue Instanzen eines `Form2` als untergeordnete MDI-Fenster von `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. Fügen Sie Code wie folgt in die `&New` <xref:System.Windows.Forms.ToolStripMenuItem> an den Ereignishandler zu registrieren.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Zwei <xref:System.Windows.Forms.Form>-Steuerelemente namens `Form1` und `Form2`.  
  
-   Ein <xref:System.Windows.Forms.MenuStrip>-Steuerelement auf `Form1`, das den Namen `menuStrip1` hat, und ein <xref:System.Windows.Forms.MenuStrip>-Steuerelement auf `Form2`, das den Namen `menuStrip2` hat.  
  
-   Verweise auf die Assemblys <xref:System?displayProperty=nameWithType> und <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Erstellen von übergeordneten MDI-Formularen](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Gewusst wie: Erstellen von untergeordneten MDI-Formularen](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [MenuStrip-Steuerelement](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
