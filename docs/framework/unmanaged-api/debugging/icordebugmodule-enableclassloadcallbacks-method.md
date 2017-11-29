---
title: ICorDebugModule::EnableClassLoadCallbacks-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9045cceda54e6fe89c8c1baa8d4b9fa63105607
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="9924f-102">ICorDebugModule::EnableClassLoadCallbacks-Methode</span><span class="sxs-lookup"><span data-stu-id="9924f-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="9924f-103">Steuert, ob die [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) und [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) Rückrufe für dieses Modul aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="9924f-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9924f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9924f-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9924f-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="9924f-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="9924f-106">[in] Legen Sie diesen Wert auf `true` So aktivieren Sie die common Language Runtime (CLR) aufrufen, die `ICorDebugManagedCallback::LoadClass` und `ICorDebugManagedCallback::UnloadClass` Methoden, wenn die zugeordneten Ereignisse auftreten.</span><span class="sxs-lookup"><span data-stu-id="9924f-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="9924f-107">Der Standardwert ist `false` für nicht-dynamische Module.</span><span class="sxs-lookup"><span data-stu-id="9924f-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="9924f-108">Der Wert ist immer `true` bei dynamischen Modulen kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="9924f-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9924f-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9924f-109">Remarks</span></span>  
 <span data-ttu-id="9924f-110">Die `ICorDebugManagedCallback::LoadClass` und `ICorDebugManagedCallback::UnloadClass` Rückrufe werden für dynamische Module immer aktiviert und kann nicht deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="9924f-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9924f-111">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9924f-111">Requirements</span></span>  
 <span data-ttu-id="9924f-112">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9924f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9924f-113">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9924f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9924f-114">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9924f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9924f-115">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9924f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9924f-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9924f-116">See Also</span></span>  
    
 