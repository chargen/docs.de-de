---
title: "Standardabfrageoperatoren in LINQ to Entities-Abfragen | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Standardabfrageoperatoren in LINQ to Entities-Abfragen
In einer Abfrage geben Sie die Informationen an, die aus der Datenquelle abgerufen werden sollen.  In der Abfrage kann auch angegeben werden, wie die Abfrageergebnisse sortiert, gruppiert und formatiert werden sollen, bevor sie zurückgegeben werden.  LINQ stellt eine Reihe von Standardabfragemethoden für die Verwendung in einer Abfrage bereit.  Die meisten dieser Methoden bearbeiten Sequenzen. In diesem Zusammenhang ist eine Sequenz ein Objekt, dessen Typ die <xref:System.Collections.Generic.IEnumerable%601>\-Schnittstelle oder die <xref:System.Linq.IQueryable%601>\-Schnittstelle implementiert.  Die Standardabfrageoperatoren stellen Abfragefunktionen wie Filterung, Projektion, Aggregation, Sortierung, Gruppierung, Paging und mehr bereit.  Einige der häufiger verwendeten Standardabfrageoperatoren verfügen über eine dedizierte Schlüsselwortsyntax, sodass sie mithilfe von Abfrageausdruckssyntax aufgerufen werden können.  Mit einem Abfrageausdruck kann eine Abfrage besser lesbar ausgedrückt werden als mit dessen methodenbasierter Entsprechung.  Die Abfrageausdrucksklauseln werden bei der Kompilierung in Aufrufe der Abfragemethoden übersetzt.  Eine Liste von Standardabfrageoperatoren, die über äquivalente Abfrageausdrucksklauseln verfügen, finden Sie unter [Standard Query Operators Overview](../../../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Nicht alle Standardabfrageoperatoren werden in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]\-Abfragen unterstützt.  Weitere Informationen finden Sie unter [Unterstützte und nicht unterstützte LINQ\-Methoden \(LINQ to Entities\)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Dieses Thema enthält Informationen über die für [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] spezifischen Standardabfrageoperatoren.  Weitere Informationen über häufige Probleme in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]\-Abfragen finden Sie unter [Bekannte Probleme von und Überlegungen zu LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## Projektions\- und Filtermethoden  
 Mit *Projektion* wird das Umwandeln der Elemente eines Resultsets in eine gewünschte Form bezeichnet.  Beispielsweise kann eine Teilmenge der benötigten Eigenschaften der einzelnen Objekte im Resultset projiziert werden, es kann eine Eigenschaft projiziert werden, um eine mathematische Berechnung damit auszuführen, oder es kann das ganze Objekt aus dem Resultset projiziert werden.  Zur Projektion werden die `Select`\-Methode und die `SelectMany`\-Methode verwendet.  
  
 Mit *Filtern* wird die Einschränkung des Resultsets auf Elemente bezeichnet, die eine bestimmte Bedingung erfüllen.  Zum Filtern wird die `Where`\-Methode verwendet.  
  
 Die meisten Überladungen von Methoden zur Projektion und Filterung werden in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] unterstützt. Davon ausgenommen sind die Methoden, denen positionelle Argumente übergeben werden.  
  
## Methoden zur Verknüpfung  
 Das Verknüpfen ist eine wichtige Operation bei Abfragen von Daten aus Datenquellen, die nicht über navigierbare Beziehungen verfügen.  Eine Verknüpfung zweier Datenquellen ist die Zuordnung von Objekten der einen Datenquelle zu Objekten in der anderen Datenquelle, die über ein gemeinsames Attribut oder eine gemeinsame Eigenschaft verfügen.  Zur Verknüpfung werden die `Join`\-Methode und die `GroupJoin`\-Methode verwendet.  
  
 Die meisten Überladungen der Methoden zur Verknüpfung werden unterstützt. Davon ausgenommen sind Methoden, die einen <xref:System.Collections.Generic.IEqualityComparer%601> verwenden.  Der Grund dafür ist, dass der Vergleich nicht für die Datenquelle übersetzt werden kann.  
  
## Methoden für Mengen  
 Mengenoperationen in LINQ sind Abfrageoperationen, deren Resultsets auf der Gegenwart oder Abwesenheit äquivalenter Elemente in derselben oder in einer anderen Auflistung \(oder Menge\) basieren.  Für Mengen werden die Methoden `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect` und `Union` verwendet.  
  
 Die meisten Überladungen von Methoden für Mengen werden in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] unterstützt. Im Vergleich mit LINQ to Objects gibt es jedoch einige Unterschiede im Verhalten.  Methoden für Mengen, die einen <xref:System.Collections.Generic.IEqualityComparer%601> verwenden, werden allerdings nicht unterstützt, da der Vergleich nicht für die Datenquelle übersetzt werden kann.  
  
## Sortiermethoden  
 Mit Sortierung wird das auf einem oder mehreren Attributen basierende Sortieren von Elementen eines Resultsets bezeichnet.  Durch die Angabe eines oder mehrerer Sortierkriterien können Verbindungen innerhalb einer Gruppe aufgelöst werden.  
  
 Die meisten Überladungen der Sortiermethoden werden unterstützt. Davon ausgenommen sind Methoden, die einen <xref:System.Collections.Generic.IComparer%601> verwenden.  Der Grund dafür ist, dass der Vergleich nicht für die Datenquelle übersetzt werden kann.  Zum Sortieren werden die Methoden `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending` und `Reverse` verwendet.  
  
 Da die Abfrage für die Datenquelle ausgeführt wird, kann sich das Sortierverhalten von den Abfragen unterscheiden, die in der CLR ausgeführt werden.  Der Grund dafür ist, dass in der Datenquelle Sortieroptionen wie Fallsortierung, Kanjisortierung und Nullsortierung festgelegt werden können.  Je nach Datenquelle können diese Sortieroptionen zu anderen Ergebnissen als in der CLR führen.  
  
 Wenn dieselbe Schlüsselauswahlfunktion in mehr als einem Sortiervorgang angegeben wird, wird eine doppelte Sortierung ausgeführt.  Da dies nicht gültig ist, wird eine Ausnahme ausgelöst.  
  
## Gruppierungsmethoden  
 Mit Gruppierung wird das Anordnen von Daten in Gruppen bezeichnet, sodass die Elemente in jeder Gruppe über ein gemeinsames Attribut verfügen.  Zum Gruppieren wird die `GroupBy`\-Methode verwendet.  
  
 Die meisten Überladungen der Gruppierungsmethoden werden unterstützt. Davon ausgenommen sind Methoden, die einen <xref:System.Collections.Generic.IEqualityComparer%601> verwenden.  Der Grund dafür ist, dass der Vergleich nicht für die Datenquelle übersetzt werden kann.  
  
 Die Gruppierungsmethoden werden der Datenquelle mithilfe einer eigenen Unterabfrage für die Schlüsselauswahlfunktion zugeordnet.  Die Unterabfrage für den Vergleich mit der Schlüsselauswahlfunktion wird unter Verwendung der Semantik der Datenquelle ausgeführt. Dies ist beispielsweise beim Vergleich von `null`\-Werten bedeutsam.  
  
## Aggregatmethoden  
 Während eines Aggregationsvorgangs wird aus einer Auflistung von Werten ein einzelner Wert berechnet.  Ein Beispiel für einen Aggregationsvorgang ist die Berechnung der durchschnittlichen Tagestemperatur aus den Tagestemperaturen eines Monats.  Für die Aggregation werden die Methoden `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min` und `Sum` verwendet.  
  
 Die meisten Überladungen der Aggregatmethoden werden unterstützt.  Das Verhalten der Aggregatmethoden bzgl. NULL\-Werten wird durch die Semantik der Datenquelle gesteuert.  Das Verhalten der Aggregatmethoden im Zusammenhang mit NULL\-Werten ist je nach verwendeter Backenddatenquelle unterschiedlich.  Das Verhalten der Aggregatmethoden, das die Semantik der Datenquelle verwendet, kann sich auch von dem von CLR\-Methoden erwarteten Verhalten unterscheiden.  Beim Standardverhalten der `Sum`\-Methode in SQL Server werden beispielsweise NULL\-Werte ignoriert und keine Ausnahmen ausgelöst.  
  
 Sämtliche bei einer Aggregation ausgelösten Ausnahmen, wie ein Überlauf der `Sum`\-Funktion, werden als Datenquellenausnahmen oder Entity Framework\-Ausnahmen während der Materialisierung der Abfrageergebnisse ausgelöst.  
  
 Für Methoden, die eine Berechnung aus einer Sequenz beinhalten, wie `Sum` oder `Average`, wird die eigentliche Berechnung auf dem Server ausgeführt.  Daher können Typkonvertierungen und Präzisionsverlust auf dem Server auftreten, und die Ergebnisse können sich von denen, die bei der Verwendung der CLR\-Semantik zu erwarten sind, unterscheiden.  
  
 Das Standardverhalten der Aggregatmethoden für NULL\-Werte und Werte, die von NULL verschieden sind, wird in der folgenden Tabelle dargestellt:  
  
|Methode|Keine Daten|Alle NULL\-Werte|Einige NULL\-Werte|Keine NULL\-Werte|  
|-------------|-----------------|----------------------|------------------------|-----------------------|  
|`Average`|Gibt NULL zurück.|Gibt NULL zurück.|Gibt den Durchschnitt der von NULL verschiedenen Werte in einer Sequenz zurück.|Berechnet den Durchschnitt einer Sequenz von numerischen Werten.|  
|`Count`|Gibt 0 \(null\) zurück|Gibt die Anzahl der NULL\-Werte in der Sequenz zurück.|Gibt die Anzahl der NULL\-Werte und der von NULL verschiedenen Werte in einer Sequenz zurück.|Gibt die Anzahl der Elemente in der Sequenz zurück.|  
|`Max`|Gibt NULL zurück.|Gibt NULL zurück.|Gibt den maximalen von NULL verschiedenen Wert in einer Sequenz zurück.|Gibt den Maximalwert in einer Sequenz zurück.|  
|`Min`|Gibt NULL zurück.|Gibt NULL zurück.|Gibt den minimalen von NULL verschiedenen Wert in einer Sequenz zurück.|Gibt den Minimalwert in einer Sequenz zurück.|  
|`Sum`|Gibt NULL zurück.|Gibt NULL zurück.|Gibt die Summe der von NULL verschiedenen Werte in einer Sequenz zurück.|Berechnet die Summe einer Sequenz von numerischen Werten.|  
  
## Typmethoden  
 Die beiden LINQ\-Methoden, die für Typkonvertierung und \-test verwendet werden, werden im Kontext des [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] unterstützt.  Dies bedeutet, dass nur Typen unterstützt werden, die einem entsprechenden [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]\-Typ zugeordnet werden können.  Eine Liste dieser Typen finden Sie unter [Conceptual Model Types \(CSDL\)](http://msdn.microsoft.com/de-de/987b995f-e429-4569-9559-b4146744def4).  Als Typmethoden werden `Convert` und `OfType` verwendet.  
  
 `OfType` wird für Entitätstypen unterstützt.  `Convert` wird für primitive Typen in einem konzeptionellen Modell unterstützt.  Die C\#\-Methoden `is` und `as` werden ebenfalls unterstützt.  
  
## Pagingmethoden  
 Bei Pagingvorgängen werden einzelne, spezifische Elemente aus einer Sequenz zurückgegeben.  Als Elementmethoden werden `ElementAt`, `First`, `FirstOrDefault`, `Last`, `LastOrDefault`, `Single`, `Skip`, `Take` und `TakeWhile` verwendet.  
  
 Einige Pagingmethoden werden nicht unterstützt, da entweder Funktionen nicht der Datenquelle zugeordnet werden können oder keine implizite Sortierung der Mengen in der Datenquelle vorgenommen wird.  Methoden, die einen Standardwert zurückgeben, sind auf primitive Typen in einem konzeptionellen Modell und Referenztypen mit dem Standardwert NULL beschränkt.  Pagingmethoden, die für eine leere Sequenz ausgeführt werden, geben NULL zurück.  
  
## Siehe auch  
 [Unterstützte und nicht unterstützte LINQ\-Methoden \(LINQ to Entities\)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)   
 [Standard Query Operators Overview](../../../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)