---
title: ICorDebugDataTarget-Schnittstelle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 030ad5e61d215bd840da5b16a56e4b8f8b7791ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="729b7-102">ICorDebugDataTarget-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="729b7-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="729b7-103">Stellt eine Rückrufschnittstelle bereit, die Zugriff auf einen bestimmten Zielprozess bietet.</span><span class="sxs-lookup"><span data-stu-id="729b7-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="729b7-104">Methoden</span><span class="sxs-lookup"><span data-stu-id="729b7-104">Methods</span></span>  
  
|<span data-ttu-id="729b7-105">Methode</span><span class="sxs-lookup"><span data-stu-id="729b7-105">Method</span></span>|<span data-ttu-id="729b7-106">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="729b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="729b7-107">GetPlatform-Methode</span><span class="sxs-lookup"><span data-stu-id="729b7-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="729b7-108">Enthält Informationen über die Plattform, einschließlich der Prozessorarchitektur und Betriebssystem, auf denen der Zielprozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="729b7-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="729b7-109">ReadVirtual-Methode</span><span class="sxs-lookup"><span data-stu-id="729b7-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="729b7-110">Ruft einen Block zusammenhängender Arbeitsspeicher ab der angegebenen Adresse, und wird in der bereitgestellte Puffer zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="729b7-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="729b7-111">GetThreadContext-Methode</span><span class="sxs-lookup"><span data-stu-id="729b7-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="729b7-112">Fordert den aktuellen Kontext des Threads für den angegebenen Thread.</span><span class="sxs-lookup"><span data-stu-id="729b7-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="729b7-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="729b7-113">Remarks</span></span>  
 <span data-ttu-id="729b7-114">`ICorDebugDataTarget`und seine Methoden besitzen die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="729b7-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="729b7-115">Die Debugdienste rufen Methoden für diese Schnittstelle den Zugriff auf Speicher und andere Daten im Zielprozess.</span><span class="sxs-lookup"><span data-stu-id="729b7-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="729b7-116">Der Debuggerclient muss diese Schnittstelle für das bestimmte Ziel (z. B. ein Liveprozess oder ein Speicherabbild) geeigneten Form implementieren.</span><span class="sxs-lookup"><span data-stu-id="729b7-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="729b7-117">Die `ICorDebugDataTarget` Methoden können nur aus aufgerufen werden, innerhalb von Methoden, die in anderen implementiert `ICorDebug*` Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="729b7-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="729b7-118">Dadurch wird sichergestellt, dass der Debuggerclient steuern kann, über welchen Thread auf und wann Aufrufversuch stattfindet.</span><span class="sxs-lookup"><span data-stu-id="729b7-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="729b7-119">Die `ICorDebugDataTarget` Implementierung muss stets aktuelle Informationen zu dem Ziel.</span><span class="sxs-lookup"><span data-stu-id="729b7-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="729b7-120">Der Zielprozess beendet und in keiner Weise beim nicht geändert werden `ICorDebug*` Schnittstellen (und daher `ICorDebugDataTarget` Methoden) aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="729b7-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="729b7-121">Wenn das Ziel ein Liveprozess und dessen Zustand ändert, ist die [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) -Methode erneut aufgerufen, um ein Ersatz-ICorDebugProcess-Instanz bereitstellen muss.</span><span class="sxs-lookup"><span data-stu-id="729b7-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="729b7-122">Diese Schnittstelle kann weder computerübergreifend noch prozessübergreifend remote aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="729b7-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="729b7-123">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="729b7-123">Requirements</span></span>  
 <span data-ttu-id="729b7-124">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="729b7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="729b7-125">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="729b7-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="729b7-126">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="729b7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="729b7-127">**.NET Framework-Versionen:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="729b7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729b7-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="729b7-128">See Also</span></span>  
 [<span data-ttu-id="729b7-129">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="729b7-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="729b7-130">Debuggen</span><span class="sxs-lookup"><span data-stu-id="729b7-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)