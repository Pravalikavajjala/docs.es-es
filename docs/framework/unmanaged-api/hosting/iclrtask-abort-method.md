---
title: "ICLRTask::Abort (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Abort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e789afc8f570d647fd44f8f43c23c2cc33ba8f70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="66e27-102">ICLRTask::Abort (Método)</span><span class="sxs-lookup"><span data-stu-id="66e27-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="66e27-103">Solicita que common language runtime (CLR) anule la tarea que actual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instancia representa.</span><span class="sxs-lookup"><span data-stu-id="66e27-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e27-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="66e27-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="66e27-105">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="66e27-105">Return Value</span></span>  
  
|<span data-ttu-id="66e27-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66e27-106">HRESULT</span></span>|<span data-ttu-id="66e27-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="66e27-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66e27-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="66e27-108">S_OK</span></span>|<span data-ttu-id="66e27-109">`Abort`se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="66e27-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="66e27-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66e27-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66e27-111">El CLR no se han cargado en un proceso o el CLR está en un estado en el que no se puede ejecutar código administrado o procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="66e27-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="66e27-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66e27-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66e27-113">La llamada agotó el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="66e27-113">The call timed out.</span></span>|  
|<span data-ttu-id="66e27-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66e27-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66e27-115">El llamador no posee el bloqueo.</span><span class="sxs-lookup"><span data-stu-id="66e27-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66e27-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66e27-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66e27-117">Se canceló un evento mientras un subproceso bloqueado o fibra esperó en él.</span><span class="sxs-lookup"><span data-stu-id="66e27-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66e27-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="66e27-118">E_FAIL</span></span>|<span data-ttu-id="66e27-119">Se ha producido un error catastrófico desconocido.</span><span class="sxs-lookup"><span data-stu-id="66e27-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66e27-120">Cuando un método devuelve E_FAIL, CLR ya no es utilizable dentro del proceso.</span><span class="sxs-lookup"><span data-stu-id="66e27-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66e27-121">Las llamadas posteriores a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="66e27-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66e27-122">Comentarios</span><span class="sxs-lookup"><span data-stu-id="66e27-122">Remarks</span></span>  
 <span data-ttu-id="66e27-123">El CLR genera un <xref:System.Threading.ThreadAbortException> cuando el host llama al método `Abort`.</span><span class="sxs-lookup"><span data-stu-id="66e27-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="66e27-124">Devuelve inmediatamente después de que la información de excepción se inicializa, sin tener que esperar para el código de usuario, como finalizadores o mecanismos de control de excepciones para ejecutar.</span><span class="sxs-lookup"><span data-stu-id="66e27-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="66e27-125">Las llamadas a `Abort` , por tanto, se devolverá rápidamente.</span><span class="sxs-lookup"><span data-stu-id="66e27-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e27-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66e27-126">Requirements</span></span>  
 <span data-ttu-id="66e27-127">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66e27-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e27-128">**Encabezado:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="66e27-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66e27-129">**Biblioteca:** incluye como recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66e27-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66e27-130">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e27-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e27-131">Vea también</span><span class="sxs-lookup"><span data-stu-id="66e27-131">See Also</span></span>  
 [<span data-ttu-id="66e27-132">ICLRTask (interfaz)</span><span class="sxs-lookup"><span data-stu-id="66e27-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="66e27-133">ICLRTaskManager (interfaz)</span><span class="sxs-lookup"><span data-stu-id="66e27-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="66e27-134">IHostTask (interfaz)</span><span class="sxs-lookup"><span data-stu-id="66e27-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="66e27-135">IHostTaskManager (interfaz)</span><span class="sxs-lookup"><span data-stu-id="66e27-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)