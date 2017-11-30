---
title: "ISymUnmanagedMethod::GetScopeFromOffset (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetScopeFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b863031cae487a2c081f23aeada1971893aa339f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="b7bb0-102">ISymUnmanagedMethod::GetScopeFromOffset (Método)</span><span class="sxs-lookup"><span data-stu-id="b7bb0-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="b7bb0-103">Obtiene el ámbito léxico más envolvente dentro de este método que contiene el desplazamiento especificado.</span><span class="sxs-lookup"><span data-stu-id="b7bb0-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="b7bb0-104">Esto se puede utilizar para iniciar búsquedas de variables locales.</span><span class="sxs-lookup"><span data-stu-id="b7bb0-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bb0-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b7bb0-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7bb0-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b7bb0-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="b7bb0-107">[in] Un `ULONG` que contiene el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="b7bb0-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b7bb0-108">[out] Un puntero que se establece en el valor devuelto [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfaz.</span><span class="sxs-lookup"><span data-stu-id="b7bb0-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7bb0-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="b7bb0-109">Return Value</span></span>  
 <span data-ttu-id="b7bb0-110">S_OK si el método tiene éxito; en caso contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="b7bb0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7bb0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7bb0-111">Requirements</span></span>  
 <span data-ttu-id="b7bb0-112">**Encabezado:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b7bb0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7bb0-113">Vea también</span><span class="sxs-lookup"><span data-stu-id="b7bb0-113">See Also</span></span>  
 [<span data-ttu-id="b7bb0-114">ISymUnmanagedMethod (interfaz)</span><span class="sxs-lookup"><span data-stu-id="b7bb0-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)