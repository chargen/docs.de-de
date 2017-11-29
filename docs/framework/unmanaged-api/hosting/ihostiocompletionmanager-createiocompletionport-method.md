---
title: IHostIoCompletionManager::CreateIoCompletionPort-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CreateIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1942c34b0807b76bbe25aedc60b7b1c6fecc87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="f2d97-102">IHostIoCompletionManager::CreateIoCompletionPort-Methode</span><span class="sxs-lookup"><span data-stu-id="f2d97-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="f2d97-103">Fordert an, dass der Host eine neue e/a-Abschlussport erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2d97-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d97-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2d97-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2d97-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="f2d97-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="f2d97-106">[out] Ein Zeiger auf ein Handle für den neu erstellten e/a-Abschlussport, oder 0 (null), wenn der Port nicht erstellt werden konnte.</span><span class="sxs-lookup"><span data-stu-id="f2d97-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2d97-107">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f2d97-107">Return Value</span></span>  
  
|<span data-ttu-id="f2d97-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2d97-108">HRESULT</span></span>|<span data-ttu-id="f2d97-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f2d97-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2d97-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2d97-110">S_OK</span></span>|<span data-ttu-id="f2d97-111">`CreateIoCompletionPort`wurde erfolgreich zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f2d97-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="f2d97-112">HOST_E_CLRNOTAVAILABLE ZURÜCK</span><span class="sxs-lookup"><span data-stu-id="f2d97-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2d97-113">Die common Language Runtime (CLR) wurde nicht in einen Prozess geladen, oder die CLR wird in einem Zustand, in dem er nicht verwalteten Code ausführen oder den Aufruf erfolgreich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="f2d97-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f2d97-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f2d97-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f2d97-115">Der Aufruf ist ein Timeout aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="f2d97-115">The call timed out.</span></span>|  
|<span data-ttu-id="f2d97-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f2d97-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f2d97-117">Der Aufrufer ist nicht Besitzer der Sperre.</span><span class="sxs-lookup"><span data-stu-id="f2d97-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f2d97-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f2d97-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f2d97-119">Ein Ereignis wurde abgebrochen, während ein blockierten Thread oder eine Fiber darauf gewartet.</span><span class="sxs-lookup"><span data-stu-id="f2d97-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f2d97-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2d97-120">E_FAIL</span></span>|<span data-ttu-id="f2d97-121">Ein Unbekannter Schwerwiegender Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="f2d97-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f2d97-122">Wenn eine Methode E_FAIL zurückgibt, ist die CLR nicht mehr verwendbar innerhalb des Prozesses.</span><span class="sxs-lookup"><span data-stu-id="f2d97-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f2d97-123">Nachfolgende Aufrufe zum Hosten der Methoden HOST_E_CLRNOTAVAILABLE zurück.</span><span class="sxs-lookup"><span data-stu-id="f2d97-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f2d97-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f2d97-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f2d97-125">Es war nicht genügend Arbeitsspeicher verfügbar, um die angeforderte Ressource zuzuweisen.</span><span class="sxs-lookup"><span data-stu-id="f2d97-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2d97-126">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f2d97-126">Remarks</span></span>  
 <span data-ttu-id="f2d97-127">Die CLR ruft die `CreateIoCompletionPort` Methode, um anzufordern, dass der Host eine neue e/a-Abschlussport erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2d97-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="f2d97-128">Bindet e/a-Vorgänge an diesen Port durch einen Aufruf der [IHostIoCompletionManager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) Methode.</span><span class="sxs-lookup"><span data-stu-id="f2d97-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="f2d97-129">Der Host meldet den Status zurück an die CLR durch Aufrufen von [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2d97-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2d97-130">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f2d97-130">Requirements</span></span>  
 <span data-ttu-id="f2d97-131">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2d97-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d97-132">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2d97-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2d97-133">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="f2d97-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2d97-134">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d97-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d97-135">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f2d97-135">See Also</span></span>  
 [<span data-ttu-id="f2d97-136">ICLRIoCompletionManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="f2d97-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="f2d97-137">IHostIoCompletionManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="f2d97-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)