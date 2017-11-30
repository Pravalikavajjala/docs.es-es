---
title: "ICorDebugThread2::GetVolatileOSThreadID (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetVolatileOSThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ef0df7caad2e903e9325eb692fd318bec0c2c78
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="0e3b9-102">ICorDebugThread2::GetVolatileOSThreadID (Método)</span><span class="sxs-lookup"><span data-stu-id="0e3b9-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="0e3b9-103">Obtiene el identificador de subproceso del sistema operativo para esta instancia de ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="0e3b9-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e3b9-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0e3b9-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e3b9-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0e3b9-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="0e3b9-106">[out] El identificador de subproceso de sistema operativo para este subproceso.</span><span class="sxs-lookup"><span data-stu-id="0e3b9-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e3b9-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e3b9-107">Requirements</span></span>  
 <span data-ttu-id="0e3b9-108">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e3b9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e3b9-109">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e3b9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e3b9-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e3b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e3b9-111">**Versiones de .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e3b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>