---
title: "ICorDebugFunction2::GetJMCStatus (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.GetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dc5e5e6a0ff0784825a69ba1873224a537ad46c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="cb9bb-102">ICorDebugFunction2::GetJMCStatus (Método)</span><span class="sxs-lookup"><span data-stu-id="cb9bb-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="cb9bb-103">Obtiene un valor que indica si la función representada por este objeto ICorDebugFunction2 está marcada como código de usuario.</span><span class="sxs-lookup"><span data-stu-id="cb9bb-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb9bb-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cb9bb-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb9bb-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="cb9bb-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="cb9bb-106">[out] Un puntero a un valor booleano que es `true`, si esta función está marcada como código de usuario; en caso contrario, el valor es `false`.</span><span class="sxs-lookup"><span data-stu-id="cb9bb-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb9bb-107">Comentarios</span><span class="sxs-lookup"><span data-stu-id="cb9bb-107">Remarks</span></span>  
 <span data-ttu-id="cb9bb-108">Si la función representada por este `ICorDebugFunction2` no se pueden depurar, `pbIsJustMyCode` siempre será `false`.</span><span class="sxs-lookup"><span data-stu-id="cb9bb-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb9bb-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb9bb-109">Requirements</span></span>  
 <span data-ttu-id="cb9bb-110">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb9bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb9bb-111">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb9bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb9bb-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb9bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb9bb-113">**Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb9bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>