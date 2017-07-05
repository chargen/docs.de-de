---
title: "Vorgehensweise: Einen Feed sowohl als Atom als auch als RSS verf&#252;gbar machen | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# Vorgehensweise: Einen Feed sowohl als Atom als auch als RSS verf&#252;gbar machen
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ermöglicht Ihnen die Erstellung eines Diensts, der einen Syndication\-Feed verfügbar macht.  In diesem Thema wird erläutert, wie Sie einen Syndication\-Dienst erstellen, der Syndication\-Feeds sowohl mit Atom 1.0 als auch mit RSS 2.0 verfügbar macht.  Dieser Dienst macht einen Endpunkt verfügbar, der beide Syndication\-Formate zurückgeben kann.  Der Einfachheit halber wird in diesem Beispiel ein selbst gehosteter Dienst verwendet.  In einer Produktionsumgebung würde ein Dienst dieses Typs unter IIS oder WAS gehostet werden.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] zu unterschiedlichen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]\-Hostingoptionen finden Sie unter [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
### So erstellen Sie einen grundlegenden Syndication\-Dienst  
  
1.  Definieren Sie einen Dienstvertrag mit einer Schnittstelle, die mit dem <xref:System.ServiceModel.Web.WebGetAttribute>\-Attribut gekennzeichnet ist.  Jeder Vorgang, der als Syndication\-Feed verfügbar gemacht wird, gibt ein <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>\-Objekt zurück.  Beachten Sie die Parameter für das <xref:System.ServiceModel.Web.WebGetAttribute>.  `UriTemplate` gibt die URL an, mit der dieser Dienstvorgang aufgerufen wird.  Die Zeichenfolge für diesen Parameter enthält Literale und eine Variable in geschweiften Klammern \({*Format*}\).  Diese Variable entspricht dem `format`\-Parameter des Dienstvorgangs.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.UriTemplate>.  `BodyStyle` wirkt sich darauf aus, wie die Nachrichten, die dieser Dienstvorgang sendet und empfängt, geschrieben werden.  <xref:System.ServiceModel.Web.WebMessageBodyStyle> gibt an, dass die an diesen Dienstvorgang gesendeten und von ihm empfangenen Daten nicht von Infrastruktur\-definierten XML\-Elementen eingeschlossen werden.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Web.WebMessageBodyStyle>.  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Verwenden Sie das <xref:System.ServiceModel.ServiceKnownTypeAttribute>, um die Typen anzugeben, die von den Dienstvorgängen in dieser Schnittstelle zurückgegeben werden.  
  
2.  Implementieren Sie den Dienstvertrag.  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3.  Erstellen Sie ein <xref:System.ServiceModel.Syndication.SyndicationFeed>\-Objekt, und fügen Sie einen Autor, eine Kategorie und eine Beschreibung hinzu.  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4.  Erstellen Sie mehrere <xref:System.ServiceModel.Syndication.SyndicationItem>\-Objekte.  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5.  Fügen Sie die <xref:System.ServiceModel.Syndication.SyndicationItem>\-Objekte dem Feed hinzu.  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6.  Verwenden Sie den format\-Parameter, um das angeforderte Format zurückzugeben.  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### So hosten Sie den Dienst  
  
1.  Erstellen eines <xref:System.ServiceModel.Web.WebServiceHost>\-Objekts  Die <xref:System.ServiceModel.Web.WebServiceHost>\-Klasse fügt automatisch einen Endpunkt an der Basisadresse des Diensts hinzu, sofern im Code oder in der Konfiguration kein Endpunkt angegeben ist.  In diesem Beispiel sind keine Endpunkte angegeben, sodass der Standardendpunkt verfügbar gemacht wird.  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2.  Öffnen Sie den Diensthost, laden Sie den Feed vom Dienst, zeigen Sie den Feed an, und warten Sie darauf, dass der Benutzer die Eingabetaste drückt.  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### So rufen Sie GetBlog mit HTTP GET auf  
  
1.  Öffnen Sie den Internet\-Explorer, geben Sie die folgende URL ein, und drücken Sie die EINGABETASTE.  http:\/\/localhost:8000\/BlogService\/GetBlog  
  
     Die URL enthält die Basisadresse des Diensts \(http:\/\/localhost:8000\/BlogService\), die relative Adresse des Endpunkts und den aufzurufenden Dienstvorgang.  
  
### So rufen Sie GetBlog\(\) aus dem Code auf  
  
1.  Erstellen Sie einen <xref:System.Xml.XmlReader> mit der Basisadresse und der Methode, die Sie aufrufen.  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2.  Rufen Sie die statische <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>\-Methode auf, und übergeben Sie dabei den gerade erstellten <xref:System.Xml.XmlReader>.  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     Dies ruft einen Dienstvorgang auf und füllt einen neuen <xref:System.ServiceModel.Syndication.SyndicationFeed> mit dem vom Dienstvorgang zurückgegebenen Formatierungsprogramm auf.  
  
3.  Greifen Sie auf das Feedobjekt zu.  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## Beispiel  
 Unten ist die vollständige Codeauflistung für dieses Beispiel angegeben.  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## Kompilieren des Codes  
 Verweisen Sie beim Kompilieren des obigen Codes auf System.ServiceModel.dll und System.ServiceModel.Web.dll.  
  
## Siehe auch  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Web.WebGetAttribute>