---
title: ICLRMetaHost::EnumerateLoadedRuntimes-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.EnumerateLoadedRuntimes
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0724bf44eaf82b39262876ea4a44509b6c7d576
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="5dee4-102">ICLRMetaHost::EnumerateLoadedRuntimes-Methode</span><span class="sxs-lookup"><span data-stu-id="5dee4-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>
<span data-ttu-id="5dee4-103">Gibt eine Enumeration, die eine gültige enthält [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) Schnittstellenzeiger für jede Version der common Language Runtime (CLR), die in einem bestimmten Prozess geladen wird.</span><span class="sxs-lookup"><span data-stu-id="5dee4-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="5dee4-104">Diese Methode hat Vorrang vor den [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) Funktion.</span><span class="sxs-lookup"><span data-stu-id="5dee4-104">This method supersedes the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dee4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5dee4-105">Syntax</span></span>  
  
```  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dee4-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dee4-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="5dee4-107">[in] Das Handle des Prozesses, für die geladene Laufzeitmodule zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5dee4-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="5dee4-108">[out] Ein <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` Enumeration von [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) Schnittstellen, die für jede CLR, die vom Prozess geladen wird.</span><span class="sxs-lookup"><span data-stu-id="5dee4-108">[out] An <!--zz <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown>--> `Microsoft.VisualStudio.OLE.Interop.IEnumUnknown` enumeration of [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5dee4-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5dee4-109">Return Value</span></span>  
 <span data-ttu-id="5dee4-110">Diese Methode gibt die folgenden spezifischen HRESULTs sowie HRESULT-Fehler zurück, die Methodenfehler anzeigen.</span><span class="sxs-lookup"><span data-stu-id="5dee4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5dee4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5dee4-111">HRESULT</span></span>|<span data-ttu-id="5dee4-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5dee4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5dee4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5dee4-113">S_OK</span></span>|<span data-ttu-id="5dee4-114">Die Methode wurde erfolgreich abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="5dee4-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5dee4-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5dee4-115">E_POINTER</span></span>|<span data-ttu-id="5dee4-116">`ppEnumerator` ist NULL.</span><span class="sxs-lookup"><span data-stu-id="5dee4-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dee4-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5dee4-117">Remarks</span></span>  
 <span data-ttu-id="5dee4-118">Diese Methode ist führt alle geladenen Laufzeiten, auch wenn sie z. B. mit veralteten Funktionen geladen wurden [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="5dee4-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dee4-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5dee4-119">Requirements</span></span>  
 <span data-ttu-id="5dee4-120">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dee4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dee4-121">**Header:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5dee4-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5dee4-122">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="5dee4-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5dee4-123">**.NET Framework-Versionen:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dee4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dee4-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5dee4-124">See Also</span></span>  
 [<span data-ttu-id="5dee4-125">ICLRMetaHost-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="5dee4-125">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="5dee4-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="5dee4-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)