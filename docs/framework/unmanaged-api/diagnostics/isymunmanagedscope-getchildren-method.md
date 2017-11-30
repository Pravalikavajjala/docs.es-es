---
title: "ISymUnmanagedScope::GetChildren (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetChildren
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a43a0f46532bfb0eeaa4e385946a5aaa1b50eba8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="0aba1-102">ISymUnmanagedScope::GetChildren (Método)</span><span class="sxs-lookup"><span data-stu-id="0aba1-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="0aba1-103">Obtiene a los elementos secundarios de este ámbito.</span><span class="sxs-lookup"><span data-stu-id="0aba1-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aba1-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0aba1-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0aba1-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0aba1-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="0aba1-106">[in] A `ULONG32` que indica el tamaño de la `children` matriz.</span><span class="sxs-lookup"><span data-stu-id="0aba1-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="0aba1-107">[out] Un puntero a un `ULONG32` que recibe el tamaño del búfer necesario para contener los elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="0aba1-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="0aba1-108">[out] La matriz devuelta de elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="0aba1-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0aba1-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="0aba1-109">Return Value</span></span>  
 <span data-ttu-id="0aba1-110">S_OK si el método tiene éxito; en caso contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="0aba1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aba1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0aba1-111">Requirements</span></span>  
 <span data-ttu-id="0aba1-112">**Encabezado:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0aba1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aba1-113">Vea también</span><span class="sxs-lookup"><span data-stu-id="0aba1-113">See Also</span></span>  
 [<span data-ttu-id="0aba1-114">ISymUnmanagedScope (interfaz)</span><span class="sxs-lookup"><span data-stu-id="0aba1-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="0aba1-115">GetParent (método)</span><span class="sxs-lookup"><span data-stu-id="0aba1-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)