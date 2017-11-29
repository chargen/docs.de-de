---
title: IsFrameworkAssembly-Funktion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 216a7221550cb6345b29b5ed9e45b13ce40eadf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="isframeworkassembly-function"></a><span data-ttu-id="55652-102">IsFrameworkAssembly-Funktion</span><span class="sxs-lookup"><span data-stu-id="55652-102">IsFrameworkAssembly Function</span></span>
<span data-ttu-id="55652-103">Ruft einen Wert, der angibt, ob die angegebene Assembly verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="55652-103">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55652-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="55652-104">Syntax</span></span>  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55652-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="55652-105">Parameters</span></span>  
 `pwzAssemblyReference`  
 <span data-ttu-id="55652-106">[in] Der Name der Assembly zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="55652-106">[in] The name of the assembly to check.</span></span>  
  
 `pbIsFrameworkAssembly`  
 <span data-ttu-id="55652-107">[out] Ein boolescher Wert, der angibt, ob die Assembly verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="55652-107">[out] A Boolean value that indicates whether the assembly is managed.</span></span>  
  
 `pwzFrameworkAssemblyIdentity`  
 <span data-ttu-id="55652-108">[in] Eine uncanonicalized Zeichenfolge, die eindeutige Identität der Assembly enthält.</span><span class="sxs-lookup"><span data-stu-id="55652-108">[in] An uncanonicalized string that contains the unique identity of the assembly.</span></span>  
  
 `pccSize`  
 <span data-ttu-id="55652-109">[in] Die Größe des `pwzFrameworkAssemblyIdentity`.</span><span class="sxs-lookup"><span data-stu-id="55652-109">[in] The size of `pwzFrameworkAssemblyIdentity`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55652-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="55652-110">Remarks</span></span>  
 <span data-ttu-id="55652-111">Die `pwzAssemblyReference` Parameter ist ein Zeiger auf eine Zeichenfolge, die den Namen einer Assembly enthält.</span><span class="sxs-lookup"><span data-stu-id="55652-111">The `pwzAssemblyReference` parameter is a pointer to a character string that contains the name of an assembly.</span></span>  
  
 <span data-ttu-id="55652-112">Wenn diese Assembly Bestandteil von .NET Framework ist die `pbIsFrameworkAssembly` Parameter enthält einen booleschen Wert des `true`.</span><span class="sxs-lookup"><span data-stu-id="55652-112">If this assembly is part of the .NET Framework, the `pbIsFrameworkAssembly` parameter will contain a Boolean value of `true`.</span></span>  
  
 <span data-ttu-id="55652-113">Wenn der benannte Assembly kein Bestandteil von .NET Framework ist oder wenn die `pwzAssemblyReference` Parameter wird nicht den Namen einer Assembly `pbIsFrameworkAssembly` enthält einen booleschen Wert des `false`.</span><span class="sxs-lookup"><span data-stu-id="55652-113">If the named assembly is not part of the .NET Framework, or if the `pwzAssemblyReference` parameter does not name an assembly, `pbIsFrameworkAssembly` will contain a Boolean value of `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55652-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="55652-114">Requirements</span></span>  
 <span data-ttu-id="55652-115">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55652-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55652-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="55652-116">See Also</span></span>  
 [<span data-ttu-id="55652-117">Globale statische Fusionsfunktionen</span><span class="sxs-lookup"><span data-stu-id="55652-117">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)