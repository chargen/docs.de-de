---
title: WCF und ASP.NET-Web-API
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: c8bc8d3483d2f6c85ff14073f34caaf75d639bdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-and-aspnet-web-api"></a>WCF und ASP.NET-Web-API
WCF ist das einheitliche Programmiermodell von Microsoft, mit dem dienstorientierte Anwendungen erstellt werden können. Es ermöglicht Entwicklern das Erstellen sicherer, zuverlässiger und transaktiver Lösungen für die plattformübergreifende Integration und bietet unfassende Interoperabilität mit vorhandenen Investitionen. [ASP.NET Web API](http://www.asp.net/web-api) ist ein Framework, die erleichtert das Erstellen von HTTP-Diensten, die eine Breite Palette von Clients, einschließlich Browsern und mobilen Geräten erreichen. Die ASP.NET-Web-API ist eine ideale Plattform zum Erstellen von RESTful-Anwendungen in .NET Framework. Die Informationen in diesem Thema sollen Sie dabei unterstützen, die für Ihre Anforderungen optimal geeignete Technologie zu finden.  
  
## <a name="choosing-which-technology-to-use"></a>Wahl der richtigen Technologie  
 In der folgenden Tabelle sind die wichtigsten Funktionen der jeweiligen Technologie beschrieben.  
  
|WCF|ASP.NET-Web-API|  
|---------|---------------------|  
|Ermöglicht das Erstellen von Diensten, die mehrere Transportprotokolle (HTTP, TCP, UDP und benutzerdefinierte Transporte) und das Wechseln zwischen den Protokollen unterstützen.|nur HTTP Erstrangige Programmiermodell für HTTP. Für den Zugriff von verschiedenen Browsern, mobile Geräte aktivieren usw. breit erreichen besser geeignet.|  
|Ermöglicht das Erstellen von Diensten, die mehrere Codierungen (textbasiert, MTOM und binär) desselben Nachrichtentyps sowie den Wechsel zwischen den Codierungen unterstützen.|Ermöglicht das Erstellen von Web-APIs, die eine Vielzahl von Medientypen einschließlich XML, JSON usw. unterstützen.|  
|Unterstützt das Erstellen von Diensten mit WS-*-Standards, z. B. zuverlässigem Messaging, Transaktionen und Nachrichtensicherheit.|Verwendet Standardprotokolle und-Formate wie HTTP, WebSockets, SSL, JSON und XML. Höher entwickelte Protokolle wie zuverlässiges Messaging oder Transaktionen werden nicht unterstützt.|  
|Unterstützt die Nachrichtenaustauschmuster "Anforderung-Antwort", "Unidirektional" und "Duplex".|Anforderung/Antwort "HTTP" ist jedoch zusätzliche Mustern können unterstützt werden, über [SignalR](https://github.com/SignalR/SignalR) und WebSockets-Integration.|  
|WCF-SOAP-Dienste können in WSDL beschrieben werden und bieten automatisierten Tools die Möglichkeit, selbst für Dienste mit komplexen Schemas Clientproxys zu generieren.|Es gibt zahlreiche Methoden zur Beschreibung einer Web-API, von automatisch generierten HTML-Hilfeseiten mit Informationen zu Codeausschnitten bis hin zu strukturierten Metadaten für integrierte OData-APIs.|  
|Im Lieferumfang von .NET Framework enthalten.|Im Lieferumfang von .NET Framework enthalten, steht jedoch auch als unabhängiges Out-of-Band-Download bereit, da es sich um eine Open Source-API handelt.|  
  
 Verwenden Sie WCF zum Erstellen zuverlässiger, sicherer Webdienste, auf die über eine Vielzahl von Transporten zugegriffen werden kann. Verwenden Sie die ASP.NET-Web-API zum Erstellen HTTP-basierter Dienste, auf die von vielen verschiedenen Clients zugegriffen werden kann. Verwenden Sie die ASP.NET-Web-API, wenn Sie neue REST-Dienste entwerfen und erstellen. Obwohl WCF das Schreiben von REST-Diensten bis zu einem gewissen Grad unterstützt, bietet die ASP.NET-Web-API umfassendere REST-Unterstützung. Darüber hinaus werden zukünftige Optimierungen an REST-Funktionen in der ASP.NET-Web-API vorgenommen. Wenn Sie bei einem vorhandenen WCF-Dienst zusätzliche REST-Endpunkte verfügbar machen möchten, verwenden Sie WCF und <xref:System.ServiceModel.WebHttpBinding>.  
  
## <a name="see-also"></a>Siehe auch  
 [Was ist die Windows Communication Foundation?](../../../docs/framework/wcf/whats-wcf.md)  
 [Wesentliche Windows Communication Foundation-Begriffe](../../../docs/framework/wcf/fundamental-concepts.md)  
