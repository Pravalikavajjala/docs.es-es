---
title: IDebuggerThreadControl (Interfaz)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IDebuggerThreadControl
helpviewer_keywords: IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7e3f8d04a47607958ff5d439b501a6de9bbc5b02
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="8157a-102">IDebuggerThreadControl (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="8157a-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="8157a-103">Proporciona métodos para notificar al host el bloqueo y desbloqueo de subprocesos por los servicios de depuración.</span><span class="sxs-lookup"><span data-stu-id="8157a-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8157a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="8157a-104">Methods</span></span>  
  
|<span data-ttu-id="8157a-105">Método</span><span class="sxs-lookup"><span data-stu-id="8157a-105">Method</span></span>|<span data-ttu-id="8157a-106">Descripción</span><span class="sxs-lookup"><span data-stu-id="8157a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8157a-107">ThreadIsBlockingForDebugger (método)</span><span class="sxs-lookup"><span data-stu-id="8157a-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="8157a-108">Notifica al host que hace referencia el subproceso que está enviando esta devolución de llamada al bloque dentro de los servicios de depuración.</span><span class="sxs-lookup"><span data-stu-id="8157a-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="8157a-109">ReleaseAllRuntimeThreads (método)</span><span class="sxs-lookup"><span data-stu-id="8157a-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="8157a-110">Notifica al host que los servicios de depuración están a punto de liberar todos los subprocesos que están bloqueados.</span><span class="sxs-lookup"><span data-stu-id="8157a-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="8157a-111">StartBlockingForDebugger (método)</span><span class="sxs-lookup"><span data-stu-id="8157a-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="8157a-112">Notifica al host que los servicios de depuración están a punto de iniciarse bloqueando todos los subprocesos.</span><span class="sxs-lookup"><span data-stu-id="8157a-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8157a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8157a-113">Requirements</span></span>  
 <span data-ttu-id="8157a-114">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8157a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8157a-115">**Encabezado:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8157a-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8157a-116">**Biblioteca:** incluye como recurso en MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8157a-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8157a-117">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8157a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8157a-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="8157a-118">See Also</span></span>  
 [<span data-ttu-id="8157a-119">Interfaces de hospedaje</span><span class="sxs-lookup"><span data-stu-id="8157a-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)