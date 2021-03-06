---
title: Verwenden von Aktionen zum Implementieren des serverseitigen Verhaltens
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: d4be2aa42c667460232f6aa3cd8dc707805750e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Verwenden von Aktionen zum Implementieren des serverseitigen Verhaltens
OData-Aktionen bieten eine Möglichkeit, ein Verhalten für eine aus einem OData-Dienst abgerufene Ressource zu implementieren.  Nehmen wir als Beispiel für eine Ressource einen digitalen Film, den Sie auf viele verschiedene Weisen verwenden können: Auschecken, Bewerten/Kommentieren oder Einchecken. Das alles sind Beispiele für Aktionen, die von einem WCF Data Service implementiert werden können, der digitale Filme verwaltet. Aktionen werden in einer OData-Antwort beschrieben, die eine Ressource enthält, für die die Aktion aufgerufen werden kann. Wenn ein Benutzer eine Ressource anfordert, die einen digitalen Film darstellt, enthält die vom WCF Data Service zurückgegebene Antwort Informationen zu den Aktionen, die für diese Ressource verfügbar sind. Die Verfügbarkeit einer Aktion kann vom Zustand des Datendienstes oder der Ressource abhängen. Nachdem ein digitaler Film beispielsweise ausgecheckt wurde, kann er nicht von einem weiteren Benutzer ausgecheckt werden. Clients können eine Aktion aufrufen, indem sie einfach eine URL angeben. Z. B. http://MyServer/MovieService.svc/Movies(6) würde einen bestimmten digitalen Film identifiziert und http://MyServer/MovieService.svc/Movies(6)/Checkout würde die Aktion für den jeweiligen Film aufgerufen. Mithilfe von Aktionen ist es möglich, das Dienstmodell ohne das Datenmodell verfügbar zu machen. Wir bleiben beim Beispiel mit dem Filmportal: Stellen Sie sich vor, dass Sie einem Benutzer die Bewertung eines Films ermöglichen möchten, ohne die Bewertungsdaten jedoch direkt als Ressource verfügbar zu machen. Sie könnten eine Bewertungsaktion implementieren, um dem Benutzer die Bewertung eines Films zu erlauben, ohne dass auf die Bewertungsdaten direkt als Ressource zugegriffen wird.  
  
## <a name="implementing-an-action"></a>Implementieren einer Aktion  
 Zum Implementieren einer Dienstaktion müssen Sie implementieren die <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx), und [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) Schnittstellen. <xref:System.IServiceProvider> ermöglicht es WCF Data Services zum Abrufen der Implementierung von [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx). [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) ermöglicht WCF Data Services zu erstellen, suchen, beschreiben und Dienstaktionen aufrufen. [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) können Sie den Code aufrufen, das Verhalten der Dienstaktionen implementiert, und rufen Sie die Ergebnisse, falls vorhanden. Bedenken Sie, dass die WCF Data Services pro Aufruf berechnet werden. Bei jedem Aufruf des Dienstes wird eine neue Dienstinstanz erstellt.  Stellen Sie sicher, dass mit dem Dienst keine unnötigen Arbeiten ausgeführt werden.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider> enthält eine Methode mit dem Namen <xref:System.IServiceProvider.GetService%2A>. Diese Methode wird von den WCF Data Services aufgerufen, um eine Reihe von Dienstanbietern abzurufen, einschließlich Anbietern von Metadatendiensten und Anbietern von Datendienstaktionen. Wenn eine Aktion Datendienstanbieter angefordert, Zurückgeben der [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) Implementierung.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) enthält Methoden, mit denen Sie Informationen zu den verfügbaren Aktionen abrufen können. Bei der Implementierung [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) erweitern Sie die Metadaten für den Dienst, der durch die Implementierung des Diensts definiert ist [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) mit Aktionen und behandeln die Verteilung an diese Aktionen nach Bedarf.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.advertiseserviceaction(v=vs.113).aspx) wird aufgerufen, um zu bestimmen, welche Aktionen für die angegebene Ressource verfügbar sind. Diese Methode wird nur für Aktionen aufgerufen, die nicht immer verfügbar sind. Anhand der Methode wird überprüft, ob die Aktion in der OData-Antwort enthalten sein soll. Dies hängt jeweils vom Zustand der angeforderten Ressource bzw. dem Zustand des Dienstes ab. Wie Sie dies überprüfen, liegt völlig in Ihrer Hand. Wenn die Berechnung der Verfügbarkeit zu kostspielig ist und sich die aktuelle Ressource in einem Feed befindet, kann die Überprüfung auch übersprungen und die Aktion angekündigt werden. Der `inFeed`-Parameter ist auf `true` festgelegt, wenn die aktuelle, zurückgegebene Ressource Teil eines Feeds ist.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.createinvokable(v=vs.113).aspx) wird aufgerufen, um das Erstellen einer [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) , enthält ein Delegat, den Code kapselt, die das Verhalten der Aktion implementiert. Dies erstellt die [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) Instanz jedoch nicht die Aktion aufgerufen. Die Aktionen von WCF Data Services weisen Nebeneffekte auf und sind auf den Updateanbieter angewiesen, um diese Änderungen auf dem Datenträger zu speichern. Die [IDataServiceInvokable.Invoke](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable.invoke(v=vs.113).aspx) Methode wird aufgerufen, aus der Updateanbieters aufgerufen wird.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Diese Methode gibt eine Auflistung von [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) Instanzen, die alle Aktionen darstellen, einen WCF-Datendienst verfügbar macht. [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) ist die Metadatendarstellung einer Aktion, die Informationen wie den Aktionsnamen, Parameter und Rückgabetyp umfasst.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Diese Methode gibt eine Auflistung aller [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) Instanzen, die an den angegebenen bindungsparametertyp gebunden werden können. Das heißt, alle [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)s, die auf den angegebenen Ressourcentyp (auch als bindungsparametertyp bezeichnet) zugreifen kann. Dies wird verwendet, wenn der Dienst eine Ressource zurückgibt, um Informationen über Aktionen einzuschließen, die anhand dieser Ressource aufgerufen werden können. Diese Methode sollte nur Aktionen zurückgeben, die an den exakten Bindungsparametertyp (keine abgeleiteten Typen) gebunden werden können. Die Methode wird einmal pro Anforderung jedes gefundenen Typs aufgerufen, und das Ergebnis wird von WCF Data Services zwischengespeichert.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Diese Methode sucht nach einem angegebenen [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) und gibt `true` Wenn die [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) gefunden wird. Wenn gefunden, die [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) wird zurückgegeben, der `serviceAction``out` Parameter.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Diese Schnittstelle bietet eine Möglichkeit zur Ausführung einer WCF Data Service-Aktion. Beim Implementieren von IDataServiceInvokable sind drei Dinge zu beachten:  
  
1.  Erfassen und potenzielles Marshallen der Parameter  
  
2.  Verteilen der Parameter an den Code, durch den die Aktion beim Aufruf von Invoke() tatsächlich implementiert wird  
  
3.  Speichern der Ergebnisse von Invoke(), sodass sie mit GetResult() abgerufen werden können  
  
 Die Parameter können als Token übergeben werden. Das liegt daran, dass ein Datendienstanbieter mit Unterstützung für Token geschrieben werden kann, die Ressourcen darstellen. In diesem Fall müssen die Token u. U. in tatsächliche Ressourcen konvertiert (gemarshallt) werden, bevor sie an die tatsächliche Aktion verteilt werden. Nachdem der Parameter gemarshallt wurde, muss er sich in einem bearbeitbaren Zustand befinden, damit alle Änderungen an der Ressource, die beim Aufrufen der Aktion auftreten, gespeichert und auf den Datenträger geschrieben werden.  
  
 Diese Schnittstelle erfordert zwei Methoden: Invoke und GetResult. Mit Invoke wird der Delegat aufgerufen, der das Verhalten der Aktion implementiert, und GetResult gibt das Ergebnis der Aktion zurück.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Aufrufen einer WCF Data Service-Aktion  
 Aktionen werden mithilfe einer HTTP POST-Anforderung aufgerufen. In der URL wird die Ressource gefolgt vom Aktionsnamen angegeben. Parameter werden im Textkörper der Anforderung übergeben. Stellen Sie sich z. B. einen Dienst mit dem Namen MovieService vor, der die Bewertungsaktion (Rate) verfügbar macht. Sie sollten die folgende URL verwenden, um die Bewertungsaktion (Rate) für einen bestimmten Film aufzurufen:  
  
 http://MovieServer/MovieService.svc/Movies(1)/Rate  
  
 Movies(1) gibt den Film an, den Sie bewerten möchten, und Rate die Bewertungsaktion. Der tatsächliche Wert der Bewertung befindet sich im Textkörper der HTTP-Anforderung, wie im folgenden Beispiel dargestellt:  
  
```  
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
>  Der oben angegebene Beispielcode funktioniert nur mit WCF Data Services 5.2 und höher, da diese Versionen Unterstützung für JSON Light bieten. Wenn Sie eine frühere Version von WCF Data Services verwenden, müssen Sie den Inhaltstyp für "json verbose" wie folgt angeben: `application/json;odata=verbose`.  
  
 Alternativ können Sie eine Aktion mit dem WCF Data Services-Client aufrufen, wie im folgenden Codeausschnitt dargestellt.  
  
```  
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
            //...  
            context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );           
```  
  
 Im oben angegebenen Codeausschnitt wurde die `MoviesModel`-Klasse von Visual Studio generiert, um einem WCF Data Service einen Dienstverweis hinzuzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Entwickeln und Bereitstellen von WCF Data Services](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 [Benutzerdefinierte Datendienstanbieter](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
