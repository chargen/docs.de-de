---
title: Benutzerdefinierte Nachrichtenformatierung
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: 301c508a0c639985e226dc55f62431ad8bb9c12b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="custom-message-formatters"></a>Benutzerdefinierte Nachrichtenformatierung
Der Inhalt einer Nachricht weist häufig das XML-Format auf, also kein gängiges Format für eine Anwendung. Anwendungen bearbeiten Objekte, indem sie ihre Eigenschaften abrufen und festlegen. Windows Communication Foundation (WCF) verwendet die *Datenvertrag* Konvertieren einer <xref:System.ServiceModel.Channels.Message> Objekt in ein Objekt, das von einer Anwendung problemlos bewältigt. Diese Prozesse werden als Serialisierung und Deserialisierung bezeichnet. Beachten Sie, dass diese Begriffe auch verwendet werden, um die Serialisierung und Deserialisierung einer Transportebene in das bzw. aus dem Nachrichtensendeformat zu beschreiben. Dabei handelt es sich um einen nicht verwandten Prozess.  
  
 Sie können eine benutzerdefinierte Nachrichtenformatierung verwenden, wenn Sie eine spezielle Konvertierung zwischen Nachrichten und Objekten implementieren müssen, die Sie mithilfe eines Datenvertrags nicht durchführen können. Ändern bzw. erweitern Sie dazu das Ausführungsverhalten eines bestimmten Vertragsvorgangs auf einem Client oder für einen Dienst.  
  
## <a name="custom-message-formatters-on-the-client"></a>Benutzerdefinierte Nachrichtenformatierungen auf dem Client  
 Die <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>-Schnittstelle definiert Methoden, die verwendet werden, um für Clientanwendungen die Konvertierung von Nachrichten in Objekte und von Objekten in Nachrichten zu steuern.  
  
 Sie müssen diese Schnittstelle implementieren. Überschreiben Sie zuerst die <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A>-Methode, um eine Nachricht zu deserialisieren. Diese Methode wird aufgerufen, nachdem eine eingehende Nachricht empfangen wurde, aber bevor sie an den Clientvorgang gesendet wurde.  
  
 Überschreiben Sie im nächsten Schritt die <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A>-Methode, um ein Objekt zu serialisieren. Diese Methode wird vor dem Senden einer ausgehenden Nachricht aufgerufen.  
  
 Um die benutzerdefinierte Formatierung in die Dienstanwendung einzufügen, müssen Sie das <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>-Objekt der <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A>-Eigenschaft zuweisen, indem Sie ein Vorgangsverhalten verwenden. Informationen zum Verhalten finden Sie unter [konfigurieren und Erweitern der Laufzeit mit Verhalten](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Benutzerdefinierte Nachrichtenformatierungen für den Dienst  
 Die <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>-Schnittstelle definiert Methoden, die ein <xref:System.ServiceModel.Channels.Message>-Objekt in Parameter für einen Vorgang bzw. aus Parametern in ein <xref:System.ServiceModel.Channels.Message>-Objekt in einer Dienstanwendung konvertieren.  
  
 Sie müssen diese Schnittstelle implementieren. Überschreiben Sie zuerst die <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A>-Methode, um eine Nachricht zu deserialisieren. Diese Methode wird aufgerufen, nachdem eine eingehende Nachricht empfangen wurde, aber bevor sie an den Clientvorgang gesendet wurde.  
  
 Überschreiben Sie im nächsten Schritt die <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A>-Methode, um ein Objekt zu serialisieren. Diese Methode wird vor dem Senden einer ausgehenden Nachricht aufgerufen.  
  
 Um die benutzerdefinierte Formatierung in die Dienstanwendung einzufügen, müssen Sie das <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>-Objekt der <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A>-Eigenschaft zuweisen, indem Sie ein Vorgangsverhalten verwenden. Informationen zum Verhalten finden Sie unter [konfigurieren und Erweitern der Laufzeit mit Verhalten](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
 [Konfigurieren und Erweitern der Laufzeit mit Verhalten](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
