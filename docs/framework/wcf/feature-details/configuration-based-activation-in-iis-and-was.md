---
title: Konfigurationsbasierte Aktivierung unter IIS und WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: aa4a3c682ab1d5d7ca0869fee588934b9ed2bf75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Konfigurationsbasierte Aktivierung unter IIS und WAS
Wenn Sie einen Windows Communication Foundation (WCF)-Dienst unter Internetinformationsdienste (Internet Information Services, IIS) oder Windows Process Activation Service (WAS) hosten, müssen Sie normalerweise eine SVC-Datei angeben. Die SVC-Datei enthält den Namen des Diensts und eine optionale benutzerdefinierte Diensthostfactory. Diese Zusatzdatei verursacht einen höheren Verwaltungsmehraufwand. Die konfigurationsbasierte Aktivierungsfunktion entfernt die Anforderung einer SVC-Datei, sodass auch der damit verbundene Mehraufwand entfällt.  
  
## <a name="configuration-based-activation"></a>Konfigurationsbasierte Aktivierung  
 Die konfigurationsbasierte Aktivierung fügt die Metadaten, die zuvor in die SVC-Datei eingefügt wurden, in die Datei "Web.config" ein. In der <`serviceHostingEnvironment`> Element besteht eine <`serviceActivations`> Element. In der <`serviceActivations`>-Element sind eine oder mehrere <`add`> Elemente, jeweils eines für jeden gehosteten Dienst. Die <`add`>-Element enthält Attribute, mit denen Sie die relative Adresse für den Dienst und den Typ oder einer Diensthostfactory festlegen können. Der folgende Konfigurationsbeispielcode zeigt, wie dieser Abschnitt verwendet wird.  
  
> [!NOTE]
>  Jedes <`add`>-Element muss einen Dienst oder ein factoryattribut angeben. Es kann auch einen Dienst und Factoryattribute angeben.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Wenn dieser Code in der Datei Web.config enthalten ist, können Sie den Dienstquellcode in das Verzeichnis App_Code der Anwendung oder eine kompilierte Assembly im Verzeichnis Bin der Anwendung einfügen.  
  
> [!NOTE]
>  -   Bei Verwendung der konfigurationsbasierten Aktivierung wird Inlinecode in SVC-Dateien nicht unterstützt.  
> -   Die `relativeAddress` Attribut muss festgelegt werden, um eine relative Adresse wie z. B. "\<Unterverzeichnis > / service.svc" oder "~ /\<Unterverzeichnis/service.svc".  
> -   Es wird eine Konfigurationsausnahme ausgelöst, wenn Sie eine relative Adresse registrieren, für die keine bekannte Erweiterung mit WCF-Zuordnung vorhanden ist.  
> -   Die angegebene relative Adresse ist relativ zum Stamm der virtuellen Anwendung.  
> -   Aufgrund des hierarchischen Konfigurationsmodells werden die registrierten relativen Adressen auf Computer- und Siteebene von den virtuellen Anwendungen geerbt.  
> -   Registrierungen in einer Konfigurationsdatei haben Vorrang vor Einstellungen in einer SVC-, XAMLX-, XOML- oder anderen Datei.  
> -   Alle umgekehrten Schrägstriche ('\') in einem URI, der an IIS/WAS gesendet wird, werden automatisch in einen normalen Schrägstrich ('/') konvertiert. Wenn eine relative Adresse hinzugefügt wird, die '\' enthält, und Sie einen URI an IIS senden, für den die relative Adresse verwendet wird, wird der umgekehrte Schrägstrich in einen Schrägstrich konvertiert, und IIS kann keine Übereinstimmung mit der relativen Adresse herstellen. IIS sendet Ablaufverfolgungsinformationen, die angeben, dass keine Übereinstimmungen gefunden wurden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Hosting-Dienste](../../../../docs/framework/wcf/hosting-services.md)  
 [Übersicht über das Hosten von Workflowdiensten](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<ServiceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Windows Server AppFabric-Hostingfunktionen](http://go.microsoft.com/fwlink/?LinkId=201276)
