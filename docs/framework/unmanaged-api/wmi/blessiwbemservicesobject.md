---
title: BlessIWbemServicesObject-Funktion (Referenz zur nicht verwalteten API)
description: Die BlessIWbemServicesObject-Funktion gibt an, ob die Anmeldeinformationen des Benutzers Zugriff auf ein Objekt IWbemServices zulassen
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1bc31a4f074891149783dec647a592683564ba0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject-Funktion
Gibt an, ob die Anmeldeinformationen des Benutzers Zugriff auf ein angegebenes zugelassen [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) Objekt.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>Parameter

`pIWbemServices`  
[in] Ein Zeiger auf ein WMI-Dienstobjekt.

`strUser`  
[in] Der Benutzername.

`strPassword`  
[in] Das zugeordnete Kennwort `strUser`.

`strAuthority` [in] Der Domänenname des Benutzers. Finden Sie unter der [ConnectServerWmi](connectserverwmi.md) -Funktion für Weitere Informationen.

`impLevel` [in] Die Ebene des Identitätswechsels.

`authnLevel` [in] Die Autorisierungsebene.

## <a name="return-value"></a>Rückgabewert

Die folgenden Werte, die von dieser Funktion zurückgegebenen werden definiert, der *WinError.h* Header-Datei, oder Sie können diese definieren als Konstanten in Ihrem Code:

|Konstante  |Wert  |Beschreibung  |
|---------|---------|---------|
| `E_INVALIDARG` | 0 x 80070057 | Ein oder mehrere Argumente sind ungültig. |
| `E_POINTER` | 0 x 80004003 | `pIWbemServices` ist `null`. | 
| `E_FAIL` | 0x80000008 | Nicht angegebener Fehler ist aufgetreten. |
| `E_OUTOFMEMORY` | 0x80000002 | Ist nicht genügend Arbeitsspeicher zum Ausführen des Vorgangs verfügbar. | 
| `S_OK` | 0 | Der Funktionsaufruf war erfolgreich. | 

## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** WMINet_Utils.idl  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Siehe auch  
[WMI und Leistungsindikatoren (Referenz zur nicht verwalteten API)](index.md)
