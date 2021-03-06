---
title: 'Vorgehensweise: Abrufen von Metadaten und Implementieren eines kompatiblen Diensts'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 9ae888f5a9569ef51be52b91ea019fea897597b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Vorgehensweise: Abrufen von Metadaten und Implementieren eines kompatiblen Diensts
Oftmals werden Dienste nicht von derselben Person entworfen und anschließend implementiert. In Umgebungen, in denen zusammenwirkende Anwendungen wichtig sind, können Verträge in Web Services Description Language (WSDL) entworfen oder beschrieben werden, und ein Entwickler muss einen Dienst implementieren, der mit dem bereitgestellten Vertrag kompatibel ist. Sie sollten auch zum Migrieren eines vorhandenen Diensts zu Windows Communication Foundation (WCF), aber das Wire-Format beibehalten. Außerdem werden Aufrufende von Duplexverträgen dazu aufgefordert, auch einen Rückrufvertrag zu implementieren.  
  
 In diesen Fällen verwenden Sie die [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (oder ein entsprechendes Tool) eine dienstvertragschnittstelle in einer verwalteten Sprache zu generieren, die Sie implementieren können, um die Anforderungen erfüllt die Vertrag. In der Regel die [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) wird verwendet, um einen Dienstvertrag zu erwerben, die verwendet wird, mit einer Kanalfactory oder ein WCF-Clienttyp sowie eine Clientkonfigurationsdatei, die die richtige Bindung einrichtet und Adresse. Um die generierte Konfigurationsdatei zu verwenden, müssen Sie diese in eine Dienstkonfigurationsdatei ändern. Sie müssen möglicherweise auch den Dienstvertrag ändern.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>So rufen Sie Daten ab und implementieren einen kompatiblen Dienst:  
  
1.  Verwenden der [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gegen Metadatendateien oder eine Metadatenendpunkt zum Erzeugen einer Codedatei.  
  
2.  Suchen Sie den Bereich der Ausgabecodedatei mit der wichtigen Schnittstelle (falls mehr als eine vorhanden ist), die mit dem <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>-Attribut gekennzeichnet ist. Das folgende Codebeispiel zeigt die beiden Schnittstellen von generierten [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Die erste Schnittstelle (`ISampleService`) ist die Dienstvertragsschnittstelle, die zum Erstellen eines kompatiblen Diensts implementiert wird. Bei der zweiten Schnittstelle (`ISampleServiceChannel`) handelt es sich um eine Hilfsschnittstelle für die Clientverwendung, die sowohl die Dienstvertragsschnittstelle als auch <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> erweitert und für die Verwendung in einer Clientanwendung vorgesehen ist.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  Wird mit WSDL keine Antwortaktion für alle Vorgänge angegeben, ist bei den generierten Vorgangsverträgen die <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A>-Eigenschaft möglicherweise auf das Platzhalterzeichen (*) festgelegt. Entfernen Sie diese Eigenschafteneinstellung. Andernfalls können die Metadaten bei der Implementierung der Dienstvertragsmetadaten nicht für diese Vorgänge exportiert werden.  
  
4.  Implementieren Sie die Schnittstelle in einer Klasse, und hosten Sie den Dienst. Ein Beispiel finden Sie unter [Vorgehensweise: Implementieren eines Dienstvertrags](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), oder finden Sie eine einfache Implementierung unten im Beispielabschnitt.  
  
5.  In der Clientkonfiguration Datei, die mit der [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generiert, ändern Sie die [ \<Client >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) Konfigurationsabschnitt, der eine [ \<Services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) Konfigurationsabschnitt. (Ein Beispiel für eine generierte Clientanwendungs-Konfigurationsdatei finden Sie im folgenden "Beispiel"-Abschnitt.)  
  
6.  Innerhalb der [ \<Services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) Konfiguration im Abschnitt, erstellen Sie eine `name` Attribut in der [ \<Services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) Konfigurationsabschnitt für den Dienst -Implementierung.  
  
7.  Legen Sie das `name`-Dienstattribut auf den Konfigurationsnamen für die Dienstimplementierung fest.  
  
8.  Fügen Sie die Endpunktkonfigurationselemente hinzu, die den implementierten Dienstvertrag für den Dienstkonfigurationsabschnitt verwenden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt den Großteil einer Codedatei an, die durch die Ausführung generiert der [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gegen Metadatendateien.  
  
 Dies wird im folgenden Code veranschaulicht:  
  
-   Die Dienstvertragsschnittstelle (`ISampleService`), die bei der Implementierung den Vertragsanforderungen entspricht.  
  
-   Die Hilfsschnittstelle für die Clientverwendung, die sowohl die Dienstvertragsschnittstelle als auch <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> erweitert und für die Verwendung in einer Clientanwendung (`ISampleServiceChannel`) vorgesehen ist.  
  
-   Die Hilfsklasse, die <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> erweitert und für die Verwendung in einer Clientanwendung (`SampleServiceClient`) vorgesehen ist.  
  
-   Die vom Dienst generierte Konfigurationsdatei.  
  
-   Eine einfache `ISampleService`-Dienstimplementierung.  
  
-   Eine Konvertierung der clientseitigen Konfigurationsdatei in eine dienstseitige Version.  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]    
 [!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    
 [!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Siehe auch  
 [ServiceModel Metadata Utility-Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
