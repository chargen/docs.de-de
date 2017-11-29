---
title: ICorProfilerInfo4::GetFunctionFromIP2-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetFunctionFromIP2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2173326c5c67d1f4d3a8e28f84508fd6affb8299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="63519-102">ICorProfilerInfo4::GetFunctionFromIP2-Methode</span><span class="sxs-lookup"><span data-stu-id="63519-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>
<span data-ttu-id="63519-103">Ordnet einen verwalteten Code Anweisungszeiger der JIT-kompilierten Version einer Funktion.</span><span class="sxs-lookup"><span data-stu-id="63519-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63519-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="63519-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63519-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="63519-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="63519-106">[in] Der Anweisungszeiger in verwaltetem Code.</span><span class="sxs-lookup"><span data-stu-id="63519-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="63519-107">[out] Die Funktions-ID</span><span class="sxs-lookup"><span data-stu-id="63519-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="63519-108">[out] Die Identität der erneut JIT-kompilierten Version der Funktion.</span><span class="sxs-lookup"><span data-stu-id="63519-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63519-109">Hinweise</span><span class="sxs-lookup"><span data-stu-id="63519-109">Remarks</span></span>  
 <span data-ttu-id="63519-110">`GetFunctionFromIP2`ähnelt dem `GetFunctionFromIP`, außer dass es sich um die JIT-kompilierten ID anstelle der Funktions-ID der Funktion abruft, die die angegebene IP-Adresse enthält.</span><span class="sxs-lookup"><span data-stu-id="63519-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63519-111">`GetFunctionFromIP2`kann eine Garbagecollection auslösen, wohingegen `GetFunctionFromIP` geschieht dies nicht.</span><span class="sxs-lookup"><span data-stu-id="63519-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="63519-112">Weitere Informationen finden Sie unter [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="63519-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63519-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="63519-113">Requirements</span></span>  
 <span data-ttu-id="63519-114">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63519-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63519-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63519-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63519-116">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63519-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63519-117">**.NET Framework-Versionen:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63519-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63519-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="63519-118">See Also</span></span>  
 [<span data-ttu-id="63519-119">ICorProfilerInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="63519-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)