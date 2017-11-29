---
title: ICorRuntimeHost::EnumDomains-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.EnumDomains
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c63e4345815a073fe6aa422018b6fadf45bd5370
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="ba2c0-102">ICorRuntimeHost::EnumDomains-Methode</span><span class="sxs-lookup"><span data-stu-id="ba2c0-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="ba2c0-103">Ruft einen Enumerator für die Domänen im aktuellen Prozess ab.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba2c0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba2c0-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba2c0-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="ba2c0-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ba2c0-106">[out] Ein Enumerator für die Domänen.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba2c0-107">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ba2c0-107">Return Value</span></span>  
  
|<span data-ttu-id="ba2c0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba2c0-108">HRESULT</span></span>|<span data-ttu-id="ba2c0-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ba2c0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba2c0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba2c0-110">S_OK</span></span>|<span data-ttu-id="ba2c0-111">Der Vorgang war erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-111">The operation was successful.</span></span>|  
|<span data-ttu-id="ba2c0-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ba2c0-112">S_FALSE</span></span>|<span data-ttu-id="ba2c0-113">Der Vorgang konnte nicht abgeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ba2c0-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ba2c0-114">E_FAIL</span></span>|<span data-ttu-id="ba2c0-115">Ein Unbekannter, schwerwiegender Fehler ist aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ba2c0-116">Wenn eine Methode E_FAIL zurückgibt, ist die common Language Runtime (CLR) nicht mehr im Prozess verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ba2c0-117">Nachfolgende Aufrufe hosting-APIs HOST_E_CLRNOTAVAILABLE zurück.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ba2c0-118">HOST_E_CLRNOTAVAILABLE ZURÜCK</span><span class="sxs-lookup"><span data-stu-id="ba2c0-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ba2c0-119">Die CLR wurde nicht in einen Prozess geladen, oder die CLR wird in einem Zustand, in dem er nicht verwalteten Code ausführen oder den Aufruf erfolgreich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="ba2c0-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba2c0-120">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ba2c0-120">Requirements</span></span>  
 <span data-ttu-id="ba2c0-121">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba2c0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba2c0-122">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ba2c0-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba2c0-123">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="ba2c0-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba2c0-124">**.NET Framework-Version:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ba2c0-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2c0-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ba2c0-125">See Also</span></span>  
 [<span data-ttu-id="ba2c0-126">ICorRuntimeHost-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ba2c0-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)