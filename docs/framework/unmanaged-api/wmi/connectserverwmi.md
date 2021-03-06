---
title: ConnectServerWmi-Funktion (Referenz zur nicht verwalteten API)
description: Die Funktion ConnectServerWmi verwendet DCOM für die um eine Verbindung mit einem WMI-Namespace zu erstellen.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de8447b9b090fc7f53df23346d61932bcb4dd6ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="connectserverwmi-function"></a>ConnectServerWmi-Funktion
Erstellt eine Verbindung über DCOM mit einem WMI-Namespace auf einem angegebenen Computer an.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel, 
   [in] DWORD              authLevel
);
```  
## <a name="parameters"></a>Parameter

`strNetworkResource` [in] Zeiger auf eine gültige `BSTR` , den richtigen Namespace des WMI-Objektpfad enthält. Finden Sie unter der ["Hinweise"](#remarks) Abschnitt, um weitere Informationen.

`strUser` [in] Ein Zeiger auf eine gültige `BSTR` , die den Benutzernamen enthält. Ein `null` Wert gibt an, den aktuellen Sicherheitskontext. Wenn der Benutzer aus einer anderen Domäne als der aktuelle `strUser` kann auch die Domänen- und Benutzernamen Namen getrennt durch einen umgekehrten Schrägstrich enthalten. `strUser` kann auch werden Benutzer Benutzerprinzipalnamen (UPN) formatieren im Suhc als *userName@domainName*. Finden Sie unter der ["Hinweise"](#remarks) Abschnitt, um weitere Informationen.

`strPassword` [in] Ein Zeiger auf eine gültige `BSTR` , der Kennwort enthält. Ein `null` gibt den aktuellen Sicherheitskontext an. Eine leere Zeichenfolge ("") gibt ein gültiges Kennwort für die Länge 0 (null) an.

`strLocale` [in] Ein Zeiger auf eine gültige `BSTR` , der das richtige Gebietsschema für den Abruf von Informationen angibt. Für Microsoft-Gebietsschemabezeichner, ist das Format der Zeichenfolge "MS\_*Xxx*", wobei *Xxx* ist eine Zeichenfolge in hexadezimaler Form, der den Gebietsschemabezeichner (LCID) angibt. Wenn ein ungültiges Gebietsschema angegeben wird, gibt die Methode `WBEM_E_INVALID_PARAMETER` außer auf Windows 7, in dem das Standardgebietsschema des Servers verwendet. Wenn "null1, das aktuelle Gebietsschema verwendet wird. 
 
`lSecurityFlags` [in] Flags für die Übergabe an die `ConnectServerWmi` Methode. Der Wert 0 (null) für diesen Parameter im Aufruf führt `ConnectServerWmi` zurückgeben, nachdem eine Verbindung mit dem Server hergestellt wird. Dies kann führen in einer Anwendung nicht unbegrenzt reagiert, wenn der Server unterbrochen wird. Gültige Werte sind:

| Konstante  | Wert  | Beschreibung  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | 0 x 40 | Für die interne Verwendung vorgesehen. Nicht verwenden. |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | 0x80 | `ConnectServerWmi` Gibt innerhalb von zwei Minuten oder weniger. |

`strAuthority` [in] Der Domänenname des Benutzers. Sie können die folgenden Werte aufweisen:

| Wert | Beschreibung |
|---------|---------|
| leer | NTLM-Authentifizierung verwendet wird, und die NTLM-Domäne des aktuellen Benutzers verwendet. Wenn `strUser` gibt die Domäne (als empfohlenen Speicherort) darf nicht hier angegeben werden. Die Funktion gibt `WBEM_E_INVALID_PARAMETER` Wenn Sie die Domäne in beide Parameter angeben. |
| Kerberos:*Prinzipalname* | Kerberos-Authentifizierung wird verwendet, und dieser Parameter enthält einen Kerberos-Prinzipalname. |
| NTLMDOMAIN:*Domänennamen* | NT LAN Manager-Authentifizierung wird verwendet, und dieser Parameter enthält einen NTLM-Domänennamen. |

`pCtx`   
[in] In der Regel ist dieser Parameter ist `null`. Andernfalls ist ein Zeiger auf ein ["IWbemContext"](https://msdn.microsoft.com/library/aa391465%28v=vs.85%29.aspx) Objekt, das durch einen oder mehrere dynamische Klasse Anbieter erforderlich. 

`ppNamespace`  
[out] Wenn die Funktion zurückgibt, erhält einen Zeiger auf eine [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) Objekt an den angegebenen Namespace gebunden. Es wird festgelegt, auf `null` , wenn ein Fehler vorliegt.

`impLevel`  
[in] Die Ebene des Identitätswechsels.

`authLevel`  
[in] Die Autorisierungsebene.

## <a name="return-value"></a>Rückgabewert

Die folgenden Werte, die von dieser Funktion zurückgegebenen werden definiert, der *WbemCli.h* Header-Datei, oder Sie können diese definieren als Konstanten in Ihrem Code:

|Konstante  |Wert  |Beschreibung  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0 x 80041001 | Ein allgemeiner Fehler ist aufgetreten. |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Ein Parameter ist ungültig. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Es ist nicht genügend Arbeitsspeicher verfügbar, um den Vorgang abzuschließen. |
| `WBEM_S_NO_ERROR` | 0 | Der Funktionsaufruf war erfolgreich.  |
  
## <a name="remarks"></a>Hinweise

Diese Funktion dient als Wrapper für einen Aufruf der [IWbemLocator::ConnectServer](https://msdn.microsoft.com/libraryaa391769%28v=vs.85%29.aspx) Methode.

 Für den lokalen Zugriff auf den Standardnamespace `strNetworkResource` ein einfaches Objekt-Pfad: "Root\default" oder "\\.\root\default". Für den Zugriff auf die Standard-Namespace auf einem Remotecomputer von COM- oder Microsoft-kompatiblen-Netzwerken, den Computernamen enthalten: "\\Myserver\root\default". Der Computername kann auch einen DNS-Namen oder die IP-Adresse sein. Die `ConnectServerWmi` Funktion kann auch mit IPv6-Computern eine Verbindung mit einer IPv6-Adresse.

`strUser` eine leere Zeichenfolge darf nicht sein. Wenn in die Domäne angegeben ist `strAuthority`, er darf nicht auch einbezogen werden `strUser`, oder die Funktion gibt `WBEM_E_INVALID_PARAMETER`.


## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** WMINet_Utils.idl  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Siehe auch  
[WMI und Leistungsindikatoren (Referenz zur nicht verwalteten API)](index.md)
