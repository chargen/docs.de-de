---
title: ICorRuntimeHost::CurrentDomain-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CurrentDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 592b604f5e873f479f2e0489144240c3f021c270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="a6881-102">ICorRuntimeHost::CurrentDomain-Methode</span><span class="sxs-lookup"><span data-stu-id="a6881-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="a6881-103">Ruft einen Schnittstellenzeiger vom Typ <xref:System.AppDomain?displayProperty=nameWithType> , die die Domäne geladen wird, für den aktuellen Thread darstellt.</span><span class="sxs-lookup"><span data-stu-id="a6881-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6881-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6881-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6881-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="a6881-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a6881-106">[out] Ein Zeiger des Typs <xref:System.AppDomain?displayProperty=nameWithType> , die aktuelle Anwendungsdomäne des Threads darstellt.</span><span class="sxs-lookup"><span data-stu-id="a6881-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="a6881-107">This-Zeiger typisiert ist `IUnknown`, sodass Aufrufer in der Regel aufrufen sollte `QueryInterface` um einen Zeiger vom Typ <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a6881-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6881-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="a6881-108">Return Value</span></span>  
  
|<span data-ttu-id="a6881-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6881-109">HRESULT</span></span>|<span data-ttu-id="a6881-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a6881-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6881-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6881-111">S_OK</span></span>|<span data-ttu-id="a6881-112">Der Vorgang war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="a6881-112">The operation was successful.</span></span>|  
|<span data-ttu-id="a6881-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a6881-113">S_FALSE</span></span>|<span data-ttu-id="a6881-114">Der Vorgang konnte nicht abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="a6881-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a6881-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6881-115">E_FAIL</span></span>|<span data-ttu-id="a6881-116">Ein Unbekannter, schwerwiegender Fehler ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="a6881-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a6881-117">Wenn eine Methode E_FAIL zurückgibt, ist die common Language Runtime (CLR) nicht mehr im Prozess verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a6881-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a6881-118">Nachfolgende Aufrufe hosting-APIs HOST_E_CLRNOTAVAILABLE zurück.</span><span class="sxs-lookup"><span data-stu-id="a6881-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a6881-119">HOST_E_CLRNOTAVAILABLE ZURÜCK</span><span class="sxs-lookup"><span data-stu-id="a6881-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6881-120">Die CLR wurde nicht in einen Prozess geladen, oder die CLR wird in einem Zustand, in dem er nicht verwalteten Code ausführen oder den Aufruf erfolgreich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="a6881-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6881-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a6881-121">Requirements</span></span>  
 <span data-ttu-id="a6881-122">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6881-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6881-123">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a6881-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6881-124">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="a6881-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6881-125">**.NET Framework-Versionen:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a6881-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6881-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a6881-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="a6881-127">ICorRuntimeHost-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="a6881-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)