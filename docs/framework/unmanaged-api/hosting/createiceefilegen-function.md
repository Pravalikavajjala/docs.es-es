---
title: "CreateICeeFileGen (Función)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9162da1b48348da745f8616b5cc643bf3dee97fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="2848a-102">CreateICeeFileGen (Función)</span><span class="sxs-lookup"><span data-stu-id="2848a-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="2848a-103">Crea un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="2848a-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="2848a-104">Esta función está desusada en [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2848a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2848a-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2848a-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2848a-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="2848a-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="2848a-107">[out] Un puntero a la dirección de un nuevo `ICeeFileGen` objeto.</span><span class="sxs-lookup"><span data-stu-id="2848a-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2848a-108">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="2848a-108">Return Value</span></span>  
 <span data-ttu-id="2848a-109">Este método devuelve los códigos de error COM estándar.</span><span class="sxs-lookup"><span data-stu-id="2848a-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2848a-110">Comentarios</span><span class="sxs-lookup"><span data-stu-id="2848a-110">Remarks</span></span>  
 <span data-ttu-id="2848a-111">La `ICeeFileGen` objeto se usa para crear common language runtime (CLR) archivos de archivo ejecutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="2848a-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="2848a-112">Llame a la [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) función para destruir el `ICeeFileGen` objeto cuando termine.</span><span class="sxs-lookup"><span data-stu-id="2848a-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2848a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2848a-113">Requirements</span></span>  
 <span data-ttu-id="2848a-114">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2848a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2848a-115">**Encabezado:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="2848a-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="2848a-116">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="2848a-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="2848a-117">**Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2848a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2848a-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="2848a-118">See Also</span></span>  
 [<span data-ttu-id="2848a-119">Funciones de hospedaje de CLR en desuso</span><span class="sxs-lookup"><span data-stu-id="2848a-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)