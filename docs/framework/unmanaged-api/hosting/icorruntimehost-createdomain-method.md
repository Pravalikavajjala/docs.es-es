---
title: "ICorRuntimeHost::CreateDomain (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0da99f05b09d44338a5f4d695fb2a4114f0e1f30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="6d6cf-102">ICorRuntimeHost::CreateDomain (Método)</span><span class="sxs-lookup"><span data-stu-id="6d6cf-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="6d6cf-103">Crea un dominio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-103">Creates an application domain.</span></span> <span data-ttu-id="6d6cf-104">El llamador recibe un puntero de interfaz de tipo <xref:System._AppDomain> a una instancia de tipo <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6cf-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="6d6cf-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d6cf-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6d6cf-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="6d6cf-107">[in] Un parámetro opcional que se utiliza para asignar un nombre descriptivo para el dominio.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="6d6cf-108">Este nombre descriptivo puede mostrarse en las interfaces de usuario como depuradores para identificar el dominio.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="6d6cf-109">[in] Una matriz opcional de punteros a `IIdentity` instancias que representan la evidencia asignada mediante la directiva de seguridad para establecer un conjunto de permisos.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="6d6cf-110">Un `IIdentity` objeto se puede obtener mediante una llamada a la [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="6d6cf-111">[out] Un puntero de interfaz de tipo <xref:System._AppDomain> a una instancia de <xref:System.AppDomain?displayProperty=nameWithType> que se puede utilizar para controlar aún más el dominio.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d6cf-112">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="6d6cf-112">Return Value</span></span>  
  
|<span data-ttu-id="6d6cf-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d6cf-113">HRESULT</span></span>|<span data-ttu-id="6d6cf-114">Descripción</span><span class="sxs-lookup"><span data-stu-id="6d6cf-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6d6cf-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6d6cf-115">S_OK</span></span>|<span data-ttu-id="6d6cf-116">La operación fue correcta.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-116">The operation was successful.</span></span>|  
|<span data-ttu-id="6d6cf-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6d6cf-117">S_FALSE</span></span>|<span data-ttu-id="6d6cf-118">No se pudo completar la operación.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6d6cf-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6d6cf-119">E_FAIL</span></span>|<span data-ttu-id="6d6cf-120">Se ha producido un error catastrófico desconocido.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6d6cf-121">Si el método devuelve E_FAIL, common language runtime (CLR) ya no es utilizable en el proceso.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6d6cf-122">Las llamadas subsiguientes a cualquier API de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6d6cf-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6d6cf-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6d6cf-124">El CLR no se han cargado en un proceso o el CLR está en un estado en el que no se puede ejecutar código administrado o procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="6d6cf-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d6cf-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6d6cf-125">Requirements</span></span>  
 <span data-ttu-id="6d6cf-126">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d6cf-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d6cf-127">**Encabezado:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d6cf-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d6cf-128">**Biblioteca:** incluye como recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d6cf-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d6cf-129">**Versiones de .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6d6cf-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6cf-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="6d6cf-130">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="6d6cf-131">ICorRuntimeHost (interfaz)</span><span class="sxs-lookup"><span data-stu-id="6d6cf-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)