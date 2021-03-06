---
title: 'Vorgehensweise: Verwenden von Anmerkungen zum Transformieren von LINQ to XML-Strukturen in eine XSLT-Formatvorlage (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: c19d290e5b7acdf2702e24383a176ed06c9c7a1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>Vorgehensweise: Verwenden von Anmerkungen zum Transformieren von LINQ to XML-Strukturen in eine XSLT-Formatvorlage (Visual Basic)
Sie können Anmerkungen verwenden, um das Transformieren von XML-Strukturen zu ermöglichen.  
  
 Einige XML-Dokumente sind "dokumentorientiert mit gemischtem Inhalt". Bei solchen Dokumenten kennen Sie nicht unbedingt die Form der untergeordneten Knoten eines Elements. So könnte z. B. ein Knoten, der Text enthält, wie folgt aussehen:  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Pro vorhandenem Textknoten kann eine unbegrenzte Anzahl untergeordneter `<b>`-Elemente und `<i>`-Elemente vorhanden sein. Dieser Ansatz führt zu einer Reihe von anderen Situationen: z. B. Seiten, die eine Vielzahl von untergeordneten Elementen, z. B. normale Absätze, Absätze mit Aufzählungszeichen und Bitmaps enthalten kann. Zellen in einer Tabelle können Text, Dropdownlisten oder Bitmaps enthalten. Eine der wichtigsten Eigenschaften von dokumentorientiertem XML besteht darin, dass Sie nicht wissen, welche untergeordneten Elemente ein bestimmtes Element besitzen wird.  
  
 Wenn Sie Elemente in einer Struktur transformieren möchten und nicht wirklich viel über die untergeordneten Elemente der Elemente wissen, die transformiert werden sollen, bietet sich die Verwendung von Anmerkungen als effektiver Ansatz an.  
  
 Dieser Ansatz sieht, grob zusammengefasst, wie folgt aus:  
  
-   Zuerst werden die Elemente in der Struktur mit einem Ersetzungselement mit einer Anmerkung versehen.  
  
-   Danach wird die gesamte Struktur durchlaufen, wobei eine neue Struktur erstellt wird, in der alle Elemente durch ihre Anmerkung ersetzt werden. Dieses Beispiel implementiert die Iteration und die Erstellung der neuen Struktur mit einer Funktion mit dem Namen `XForm`.  
  
 Genauer gesagt setzt sich der Ansatz aus folgenden Schritten zusammen:  
  
-   Führen Sie mindestens eine LINQ to XML-Abfrage aus, die den Satz von Elementen zurückgibt, die Sie in eine andere Form transformieren möchten. Fügen Sie für jedes Element in der Abfrage ein neues <xref:System.Xml.Linq.XElement>-Objekt als Anmerkung zum Element hinzu. Dieses neue Element ersetzt in der neuen, transformierten Struktur das Element, das Sie mit der Anmerkung versehen haben. Das folgende Beispiel zeigt, dass der dazu zu schreibende Code recht einfach ist:  
  
-   Das neue Element, das als Anmerkung hinzugefügt wird, kann neue untergeordnete Knoten enthalten, und es kann eine Teilstruktur jeder beliebigen Form bilden.  
  
-   Dabei gilt folgende spezielle Regel: Wenn sich ein untergeordneter Knoten des neuen Elements in einem anderen Namespace befindet, einem Namespace, der zu diesem Zweck erfunden wurde (in diesem Beispiel lautet der Namespace `http://www.microsoft.com/LinqToXmlTransform/2007`), wird dieses untergeordnete Element nicht in die neue Struktur kopiert. Stattdessen gilt: Wenn es sich bei dem Namespace um den oben erwähnten speziellen Namespace handelt und der lokale Name des Elements `ApplyTransforms` lautet, dann werden die untergeordneten Knoten des Elements in der ursprünglichen Struktur durchlaufen und in die neue Struktur kopiert (mit der Ausnahme, dass mit Anmerkungen versehene untergeordnete Elemente diesen Regeln entsprechend selbst transformiert werden).  
  
-   Dies entspricht in gewissem Maße der Spezifikation von Transformationen in XSL. Die Abfrage, die einen Satz von Knoten auswählt, entspricht dem XPath-Ausdruck für eine Vorlage. Der Code zum Erstellen des neuen <xref:System.Xml.Linq.XElement>, das als Anmerkung gespeichert wird, entspricht dem Sequenzkonstruktor in XSL, und das `ApplyTransforms`-Element entspricht von seiner Funktion her dem `xsl:apply-templates`-Element in XSL.  
  
-   Ein Vorteil dieses Ansatzes besteht darin, dass Sie beim Formulieren von Abfragen stets Abfragen für die nicht geänderte Quellstruktur schreiben. Sie müssen sich damit keine Gedanken machen, wie sich Änderungen an der Struktur auf die Abfragen auswirken, die Sie schreiben.  
  
## <a name="transforming-a-tree"></a>Transformieren einer Struktur  
 Bei diesem ersten Beispiel werden alle `Paragraph`-Knoten in `para` umbenannt.  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
                <Paragraph>More text.</Paragraph>  
            </Root>  
  
        ' Replace Paragraph with p.  
        For Each el In root...<Paragraph>  
            ' same idea as xsl:apply-templates  
            el.AddAnnotation( _  
                <para>  
                    <<%= at %>></>  
                </para>)  
        Next  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newRoot As XElement = XForm(root)  
        Console.WriteLine(newRoot)  
    End Sub  
End Module  
```  
  
 Dieses Beispiel erzeugt die folgende Ausgabe:  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>Kompliziertere Transformation  
 Das folgende Beispiel fragt die Struktur ab, berechnet den Durchschnitt und die Summe der `Data`-Elemente und fügt diese als neue Elemente zur Struktur hinzu.  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim data As XElement = _  
            <Root>  
                <Data>20</Data>  
                <Data>10</Data>  
                <Data>3</Data>  
            </Root>  
  
        ' While adding annotations, you can query the source tree all you want,  
        ' as the tree is not mutated while annotating.  
        data.AddAnnotation( _  
            <Root>  
                <<%= at %>/>  
                <Average>  
                    <%= _  
                        String.Format("{0:F4}", _  
                        data.Elements("Data") _  
                        .Select(Function(z) CDec(z)).Average()) _  
                    %>  
                </Average>  
                <Sum>  
                    <%= _  
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _  
                    %>  
                </Sum>  
            </Root> _  
        )  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(data)  
        Console.WriteLine(vbNewLine)  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newData As XElement = XForm(data)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newData)  
    End Sub  
End Module   
```  
  
 Dieses Beispiel erzeugt die folgende Ausgabe:  
  
```  
Before Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
</Root>  
  
After Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
  <Average>11.0000</Average>  
  <Sum>33</Sum>  
</Root>  
```  
  
## <a name="effecting-the-transform"></a>Ausführen der Transformation  
 Eine kleine Funktion, `XForm`, erstellt aus der ursprünglichen, mit Anmerkungen versehenen Struktur eine neue transformierte Struktur.  
  
-   Der Pseudocode für die Funktion ist recht einfach:  
  
```  
The function takes an XElement as an argument and returns an XElement.   
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 Es folgt die Implementierung dieser Funktion:  
  
```vb  
' Build a transformed XML tree per the annotations.  
Function XForm(ByVal source As XElement) As XElement  
    If source.Annotation(Of XElement)() IsNot Nothing Then  
        Dim anno As XElement = source.Annotation(Of XElement)()  
        Return _  
            <<%= anno.Name.ToString() %>>  
                <%= anno.Attributes() %>  
                <%= anno.Nodes().Select(Function(n As XNode) _  
                    GetSubNodes(n, source)) %>  
            </>  
    Else  
        Return _  
            <<%= source.Name %>>  
                <%= source.Attributes() %>  
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
            </>  
    End If  
End Function  
  
Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
    Dim annoEl As XElement = TryCast(n, XElement)  
    If annoEl IsNot Nothing Then  
        If annoEl.Name = at Then  
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
        End If  
    End If  
    Return n  
End Function  
  
Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
    Dim e2 As XElement = TryCast(n2, XElement)  
    If e2 Is Nothing Then  
        Return n2  
    Else  
        Return XForm(e2)  
    End If  
End Function  
```  
  
## <a name="complete-example"></a>Vollständiges Beispiel  
 Der folgende Code ist ein vollständiges Beispiel, das die `XForm`-Funktion enthält. Er beinhaltet einige typische Verwendungen dieser Transformationsart:  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Linq  
Imports System.Text  
Imports System.Xml  
Imports System.Xml.Linq  
  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    ' Build a transformed XML tree per the annotations.  
    Function XForm(ByVal source As XElement) As XElement  
        If source.Annotation(Of XElement)() IsNot Nothing Then  
            Dim anno As XElement = source.Annotation(Of XElement)()  
            Return _  
                <<%= anno.Name.ToString() %>>  
                    <%= anno.Attributes() %>  
                    <%= anno.Nodes().Select(Function(n As XNode) _  
                        GetSubNodes(n, source)) %>  
                </>  
        Else  
            Return _  
                <<%= source.Name %>>  
                    <%= source.Attributes() %>  
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
                </>  
        End If  
    End Function  
  
    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
        Dim annoEl As XElement = TryCast(n, XElement)  
        If annoEl IsNot Nothing Then  
            If annoEl.Name = at Then  
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
            End If  
        End If  
        Return n  
    End Function  
  
    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
        Dim e2 As XElement = TryCast(n2, XElement)  
        If e2 Is Nothing Then  
            Return n2  
        Else  
            Return XForm(e2)  
        End If  
    End Function  
  
    Sub Main()  
        Dim root As XElement = _  
<Root Att1='123'>  
    <!--A comment-->  
    <Child>1</Child>  
    <Child>2</Child>  
    <Other>  
        <GC>3</GC>  
        <GC>4</GC>  
    </Other>  
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
    <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
        ' Each of the following serves the same semantic purpose as  
        ' XSLT templates and sequence constructors.  
  
        ' Replace Child with NewChild.  
        For Each el In root.<Child>  
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)  
        Next  
  
        ' Replace first GC with GrandChild, add an attribute.  
        For Each el In root...<GC>.Take(1)  
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)  
        Next  
  
        ' Replace Other with NewOther, add new child elements around original content.  
        For Each el In root.<Other>  
            el.AddAnnotation( _  
                <NewOther>  
                    <MyNewChild>1</MyNewChild>  
                    <<%= at %>></>  
                    <ChildThatComesAfter/>  
                </NewOther>)  
        Next  
  
        ' Change name of element that has mixed content.  
        root...<SomeMixedContent>(0).AddAnnotation( _  
                <MixedContent><<%= at %>></></MixedContent>)  
  
        ' Replace <b> with <Bold>.  
        For Each el In root...<b>  
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)  
        Next  
  
        ' Replace <i> with <Italic>.  
        For Each el In root...<i>  
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)  
        Next  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(root)  
        Console.WriteLine(vbNewLine)  
        Dim newRoot As XElement = XForm(root)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newRoot)  
    End Sub  
End Module   
```  
  
 Dieses Beispiel erzeugt die folgende Ausgabe:  
  
```  
Before Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <Child>1</Child>  
  <Child>2</Child>  
  <Other>  
    <GC>3</GC>  
    <GC>4</GC>  
  </Other>  
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
After Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <NewChild>1</NewChild>  
  <NewChild>2</NewChild>  
  <NewOther>  
    <MyNewChild>1</MyNewChild>  
    <GrandChild ANewAttribute="999">3</GrandChild>  
    <GC>4</GC>  
    <ChildThatComesAfter />  
  </NewOther>  
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterte LINQ to XML-Programmierung (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
