---
title: "ICLRTaskManager::GetCurrentTask (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.GetCurrentTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1adf2959beb8687dc3d08ceb7a118bb19a5fa68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="1e48c-102">ICLRTaskManager::GetCurrentTask (Método)</span><span class="sxs-lookup"><span data-stu-id="1e48c-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="1e48c-103">Obtiene el [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instancia que se está ejecutando en el subproceso del sistema operativo desde el que se originó la llamada al método.</span><span class="sxs-lookup"><span data-stu-id="1e48c-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e48c-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1e48c-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e48c-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1e48c-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="1e48c-106">[out] Un puntero a la dirección de un `ICLRTask` instancia que se está ejecutando actualmente en el subproceso de sistema operativo desde el que se originó la llamada, o null si no hay ninguna tarea se está ejecutando en este subproceso.</span><span class="sxs-lookup"><span data-stu-id="1e48c-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e48c-107">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="1e48c-107">Return Value</span></span>  
  
|<span data-ttu-id="1e48c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e48c-108">HRESULT</span></span>|<span data-ttu-id="1e48c-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="1e48c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e48c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e48c-110">S_OK</span></span>|<span data-ttu-id="1e48c-111">El método se devolvió correctamente.</span><span class="sxs-lookup"><span data-stu-id="1e48c-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="1e48c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e48c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e48c-113">Common language runtime (CLR) no se han cargado en un proceso o el CLR está en un estado en el que no se puede ejecutar código administrado o procesar la llamada correctamente.</span><span class="sxs-lookup"><span data-stu-id="1e48c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e48c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e48c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e48c-115">La llamada agotó el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="1e48c-115">The call timed out.</span></span>|  
|<span data-ttu-id="1e48c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e48c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e48c-117">El llamador no posee el bloqueo.</span><span class="sxs-lookup"><span data-stu-id="1e48c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e48c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e48c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e48c-119">Se canceló un evento mientras un subproceso bloqueado o fibra esperó en él.</span><span class="sxs-lookup"><span data-stu-id="1e48c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e48c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e48c-120">E_FAIL</span></span>|<span data-ttu-id="1e48c-121">Se ha producido un error catastrófico desconocido.</span><span class="sxs-lookup"><span data-stu-id="1e48c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e48c-122">Cuando un método devuelve E_FAIL, CLR ya no es utilizable dentro del proceso.</span><span class="sxs-lookup"><span data-stu-id="1e48c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e48c-123">Las llamadas posteriores a métodos de hospedaje devuelven HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1e48c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e48c-124">Comentarios</span><span class="sxs-lookup"><span data-stu-id="1e48c-124">Remarks</span></span>  
 <span data-ttu-id="1e48c-125">El `ICLRTask` instancia que la `ppTask` parámetro señala a representa la tarea que se ejecuta actualmente para el CLR.</span><span class="sxs-lookup"><span data-stu-id="1e48c-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="1e48c-126">El `ICLRTask` instancia está asociada con su correspondiente [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instancia que representa la tarea para el host.</span><span class="sxs-lookup"><span data-stu-id="1e48c-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e48c-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e48c-127">Requirements</span></span>  
 <span data-ttu-id="1e48c-128">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e48c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e48c-129">**Encabezado:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e48c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e48c-130">**Biblioteca:** incluye como recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e48c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e48c-131">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e48c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e48c-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="1e48c-132">See Also</span></span>  
 [<span data-ttu-id="1e48c-133">ICLRTask (interfaz)</span><span class="sxs-lookup"><span data-stu-id="1e48c-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1e48c-134">ICLRTaskManager (interfaz)</span><span class="sxs-lookup"><span data-stu-id="1e48c-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1e48c-135">IHostTask (interfaz)</span><span class="sxs-lookup"><span data-stu-id="1e48c-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1e48c-136">IHostTaskManager (interfaz)</span><span class="sxs-lookup"><span data-stu-id="1e48c-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)