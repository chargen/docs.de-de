---
title: "CLR ETW Providers | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW, CLR providers"
  - "CLR ETW providers"
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# CLR ETW Providers
Die Common Language Runtime \(CLR\) verfügt über zwei Anbieter: den Laufzeitanbieter und den Rundownanbieter.  
  
 Der Laufzeitanbieter löst Ereignisse in Abhängigkeit von den aktivierten Schlüsselwörtern \(Ereigniskategorien\) aus.  Sie können z. B. Ladeprogrammereignisse sammeln, indem Sie das Schlüsselwort `LoaderKeyword` aktivieren.  
  
 Die ETW \(Event tracking for Windows\)\-Ereignisse werden in einer Datei mit einer ETL\-Erweiterung protokolliert, die bei Bedarf später in CSV \(Comma\-Separated Value\)\-Dateien nachbearbeitet werden kann.  Informationen zum Konvertieren der ETL\-Datei in eine CSV\-Datei finden Sie unter [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).  
  
## Der Laufzeitanbieter  
 Der Laufzeitanbieter ist der zentrale CLR\-ETW\-Anbieter.  
  
 Die GUID des CLR\-Laufzeitanbieters ist e13c0d23\-ccbc\-4e12\-931b\-d9cc2eee27e4.  
  
 Beispiele zum Protokollieren und Anzeigen von CLR\-ETW\-Ereignissen mithilfe gängiger Tools finden Sie unter [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).  
  
 Neben Schlüsselwörtern wie `LoaderKeyword` müssen Sie möglicherweise Schlüsselwörter zum Protokollieren von Ereignissen aktivieren, die möglicherweise zu häufig ausgelöst werden.  Die `StartEnumerationKeyword`\- und `EndEnumerationKeyword`\-Schlüsselwörter aktivieren diese Ereignisse und werden in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) zusammengefasst.  
  
## Der Rundownanbieter  
 Für bestimmte Verwendungszwecke muss der Rundownanbieter aktiviert werden.  Für die Mehrheit der Benutzer sollte nur der Laufzeitanbieter in Frage kommen.  
  
 Die GUID des CLR\-Rundownanbieters ist A669021C\-C450\-4609\-A035\-5AF59AF4DF18.  
  
 Normalerweise wird die ETW\-Protokollierung vor dem Start eines Prozesses aktiviert, und die Protokollierung wird nach dem Beenden des Prozesses deaktiviert.  Wenn jedoch die ETW\-Protokollierung aktiviert wird, während der Prozess ausgeführt wird, werden zusätzliche Informationen zum Prozess benötigt.  Für die Symbolauflösung müssen Sie zum Beispiel Methodenereignisse für Methoden protokollieren, die bereits vor dem Aktivieren der Protokollierung geladen wurden.  
  
 Das `DCStart`\-Ereignis und das `DCEnd`\-Ereignis erfassen den Zustand des Prozesses, als die Datensammlung gestartet und beendet wurde. \(Der Zustand verweist auf allgemeine Informationen, u. a. die bereits just\-in\-time \(JIT\) kompilierten Methoden und die bereits geladenen Assemblys.\) Diese beiden Ereignisse können Informationen dazu liefern, was bereits im Prozess geschehen ist; z. B. welche Methoden JIT\-kompiliert wurden usw.  
  
 Nur die Ereignisse mit `DC`, `DCStart`, `DCEnd` oder `DCInit` in ihren Namen werden unter dem Rundownanbieter ausgelöst.  Darüber hinaus werden diese Ereignisse nur unter dem Rundownanbieter ausgelöst.  
  
 Neben den Ereignisschlüsselwortfiltern unterstützt der Rundownanbieter auch die Schlüsselwörter `StartRundownKeyword` und `EndRundownKeyword`, um eine gezielte Filterung bereitzustellen.  
  
### Startrundown  
 Ein Startrundown wird ausgelöst, wenn Protokollierung unter dem Rundownanbieter mit dem `StartRundownKeyword`\-Schlüsselwort aktiviert wird.  Dadurch wird das `DCStart`\-Ereignis ausgelöst und der Zustand des Systems erfasst.  Vor dem Start der Enumeration wird das `DCStartInit`\-Ereignis ausgelöst.  Am Ende der Enumeration wird das `DCStartComplete`\-Ereignis ausgelöst, um den Controller zu benachrichtigen, dass die Datensammlung ordnungsgemäß beendet wurde.  
  
### Endrundown  
 Ein Endrundown wird ausgelöst, wenn Protokollierung unter dem Rundownanbieter mit dem Schlüsselwort `EndRundownKeyword` aktiviert wird.  Der Endrundown beendet die Profilerstellung für einen Prozess, der weiterhin ausgeführt wird.  Die `DCEnd`\-Ereignisse erfassen den Zustand des Systems, wenn die Profilerstellung beendet wird.  
  
 Vor dem Start der Enumeration wird das `DCEndInit`\-Ereignis ausgelöst.  Am Ende der Enumeration wird das `DCEndComplete`\-Ereignis ausgelöst, um den Consumer zu benachrichtigen, dass die Datensammlung ordnungsgemäß beendet wurde.  Start\- und Endrundown werden hauptsächlich für verwaltete Symbolauflösung verwendet.  Der Startrundown kann Adressbereichsinformationen für Methoden enthalten, die bereits JIT\-kompiliert wurden, bevor die Profilerstellungssitzung gestartet wurde.  Der Endrundown kann Adressbereichsinformationen für alle Methoden liefern, deren JIT\-Kompilierung zum Zeitpunkt der Deaktivierung der Profilerstellung erfolgt ist.  
  
 Der Endrundown wird nicht automatisch ausgeführt, wenn eine Profilerstellungssitzung beendet wird.  Stattdessen muss ein Tool, von dem verwaltete Symbolauflösung ausgeführt werden soll, explizit eine CLR\-Rundownanbietersitzung aufrufen, bei der das Schlüsselwort `EndRundownKeyword` aktiviert ist \(unmittelbar vor dem Beenden der Profilerstellung\).  
  
 Obwohl entweder vom Start\- oder vom Endrundown Methodenadressbereichsinformationen für verwaltete Symbolauflösung bereitgestellt werden können, wird empfohlen, das Schlüsselwort `EndRundownKeyword` \(das `DCEnd`\-Ereignisse angibt\) anstelle des Schlüsselworts `StartRundownKeyword` zu verwenden \(das `DCStart`\-Ereignisse angibt\).  Mit `StartRundownKeyword` wird der Rundown während der Profilerstellungssitzung ausgeführt, wodurch u. U. das Szenario, für das ein Profil erstellt wurde, beeinträchtigt wird.  
  
## ETW\-Datensammlung mit Laufzeit\- und Rundownanbietern  
 Im folgenden Beispiel wird veranschaulicht, wie der CLR\-Rundownanbieter so verwendet wird, dass die Symbolauflösung verwalteter Prozesse mit minimalen Auswirkungen ermöglicht wird, unabhängig davon, ob die Prozesse innerhalb oder außerhalb des Fensters, für das ein Profil erstellt wurde, beginnen oder enden.  
  
1.  Aktivieren Sie die ETW\-Protokollierung mit dem CLR\-Laufzeitanbieter:  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Das Protokoll wird in der Datei clr1.etl gespeichert.  
  
2.  Um die Profilerstellung zu beenden, während der Prozess weiterhin ausgeführt wird, starten Sie den Rundownanbieter, um die `DCEnd`\-Ereignisse zu erfassen:  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Dadurch kann mit dem Sammeln von `DCEnd`\-Ereignissen eine Rundownsitzung begonnen werden.  Das Sammeln aller Ereignisse dauert möglicherweise 30 bis 60 Sekunden.  Das Protokoll wird in der Datei clr1.et2 gespeichert.  
  
3.  Deaktivieren Sie die gesamte ETW\-Profilerstellung:  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  Führen Sie die Profile zusammen, um eine Protokolldatei zu erstellen:  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     Die Datei "merged.etl" enthält die Ereignisse von den Laufzeit\- und Rundownanbietersitzungen.  
  
 Ein Tool kann die Schritte 2 und 3 ausführen \(dabei wird eine Rundownsitzung gestartet und anschließend die Profilerstellung beendet\), anstatt sofort die Profilerstellung zu deaktivieren, wenn ein Benutzer das Beenden der Profilerstellung anfordert.  Schritt 4 kann auch mit einem Tool ausgeführt werden.  
  
## Siehe auch  
 [ETW Events in the Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)