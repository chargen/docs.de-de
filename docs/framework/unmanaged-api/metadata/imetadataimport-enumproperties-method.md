---
title: IMetaDataImport::EnumProperties-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumProperties
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d46e18707ff6b34e32a73aed81c2b7e57f769ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="9ef82-102">IMetaDataImport::EnumProperties-Methode</span><span class="sxs-lookup"><span data-stu-id="9ef82-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="9ef82-103">Zählt PropertyDef-Token auf, die die Eigenschaften des Typs darstellen, auf den vom angegebenen TypeDef-Token verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="9ef82-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef82-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ef82-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ef82-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="9ef82-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9ef82-106">[in, out] Ein Zeiger auf den Enumerator.</span><span class="sxs-lookup"><span data-stu-id="9ef82-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9ef82-107">Dies muss für den ersten Aufruf dieser Methode NULL sein.</span><span class="sxs-lookup"><span data-stu-id="9ef82-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="9ef82-108">[in] Eine TypeDef-Token, das den Typ mit den Eigenschaften zum Aufzählen darstellt.</span><span class="sxs-lookup"><span data-stu-id="9ef82-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="9ef82-109">[out] Das Array zum Speichern der PropertyDef-Token verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9ef82-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9ef82-110">[in] Die maximale Größe des `rProperties`-Arrays.</span><span class="sxs-lookup"><span data-stu-id="9ef82-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="9ef82-111">[out] Die Anzahl der zurückgegebenen PropertyDef-Token `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="9ef82-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ef82-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="9ef82-112">Return Value</span></span>  
  
|<span data-ttu-id="9ef82-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ef82-113">HRESULT</span></span>|<span data-ttu-id="9ef82-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9ef82-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9ef82-115">`EnumProperties`wurde erfolgreich zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="9ef82-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9ef82-116">Es sind keine Token aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="9ef82-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="9ef82-117">In diesem Fall `pcProperties` 0 (null).</span><span class="sxs-lookup"><span data-stu-id="9ef82-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ef82-118">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9ef82-118">Requirements</span></span>  
 <span data-ttu-id="9ef82-119">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef82-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef82-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9ef82-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ef82-121">**Bibliothek:** als Ressource in MsCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="9ef82-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ef82-122">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef82-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef82-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9ef82-123">See Also</span></span>  
 [<span data-ttu-id="9ef82-124">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="9ef82-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9ef82-125">IMetaDataImport2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="9ef82-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)