---
title: Cert2spc.exe (Software Publisher Certificate Test-Tool)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c1d1944ae06ea26ce9bf7b4726e79155768d444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Software Publisher Certificate Test-Tool)
Das Software Publisher Certificate Test-Tool erstellt ein SPC (Software Publisher's Certificate, Softwareherausgeberzertifikat) aus einem oder mehreren X.509-Zertifikaten. "Cert2spc.exe" wird ausschließlich zu Textzwecken verwendet. Sie erhalten ein gültiges SPC von einer Zertifizierungsstelle, beispielsweise VeriSign oder Thawte. Weitere Informationen zum Erstellen von X.509-Zertifikaten finden Sie unter [Makecert.exe (Certificate Creation-Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 Dieses Tool wird automatisch mit Visual Studio installiert. Zum Ausführen des Tools verwenden Sie die Developer-Eingabeaufforderung (oder die Visual Studio-Eingabeaufforderung in Windows 7). Weitere Informationen finden Sie unter [Eingabeaufforderungen](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
## <a name="syntax"></a>Syntax  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Argument|description|  
|--------------|-----------------|  
|`certN.cer`|Der Name eines X.509-Zertifikats, das in die SPC-Datei eingebunden werden soll. Sie können mehrere Namen angeben, die durch Leerzeichen voneinander getrennt werden müssen.|  
|`crlN.crl`|Der Name einer Zertifikatssperrliste, die in die SPC-Datei aufgenommen werden soll. Sie können mehrere Namen angeben, die durch Leerzeichen voneinander getrennt werden müssen.|  
|`outputSPCfile.spc`|Der Name des PKCS #7-Objekts, das die X.509-Zertifikate enthält.|  
  
|Option|description|  
|------------|-----------------|  
|**/?**|Zeigt Befehlssyntax und Optionen für das Tool an.|  
  
## <a name="examples"></a>Beispiele  
 Der folgende Befehl erstellt ein SPC aus `myCertificate.cer` und platziert es in `mySPCFile.spc`.  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Der folgende Befehl erstellt ein SPC aus `oneCertificate.cer` und `twoCertificate.cer` und platziert es in `mySPCFile.spc`.  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Extras](../../../docs/framework/tools/index.md)  
 [Makecert.exe (Tool für die Zertifikaterstellung)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Eingabeaufforderungen](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
