---
title: ICorDebugController::IsRunning-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.IsRunning
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0cfb2c0fe3c2ebf9473afc4f1a93f50e8fe437f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerisrunning-method"></a><span data-ttu-id="b41fb-102">ICorDebugController::IsRunning-Methode</span><span class="sxs-lookup"><span data-stu-id="b41fb-102">ICorDebugController::IsRunning Method</span></span>
<span data-ttu-id="b41fb-103">Ruft einen Wert, der angibt, ob die Threads im Prozess zurzeit frei ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b41fb-103">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b41fb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b41fb-104">Syntax</span></span>  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b41fb-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="b41fb-105">Parameters</span></span>  
 `pbRunning`  
 <span data-ttu-id="b41fb-106">[out] Ein Zeiger auf einen Wert, der `true` , wenn die Threads im Prozess, frei ist, andernfalls ausgeführt werden `false`.</span><span class="sxs-lookup"><span data-stu-id="b41fb-106">[out] A pointer to a value that is `true` if the threads in the process are running freely; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b41fb-107">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b41fb-107">Requirements</span></span>  
 <span data-ttu-id="b41fb-108">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b41fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b41fb-109">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b41fb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b41fb-110">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b41fb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b41fb-111">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b41fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41fb-112">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b41fb-112">See Also</span></span>  
 