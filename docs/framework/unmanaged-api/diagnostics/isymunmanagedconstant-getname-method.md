---
title: "ISymUnmanagedConstant::GetName (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedConstant.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b6dc3eb79f351041687586327e4e095225acf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="957ff-102">ISymUnmanagedConstant::GetName (Método)</span><span class="sxs-lookup"><span data-stu-id="957ff-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="957ff-103">Obtiene el nombre de la constante.</span><span class="sxs-lookup"><span data-stu-id="957ff-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="957ff-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="957ff-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="957ff-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="957ff-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="957ff-106">[in] La longitud del búfer que el `szName` parámetro señala.</span><span class="sxs-lookup"><span data-stu-id="957ff-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="957ff-107">[out] Un puntero a un `ULONG32` que recibe el tamaño, en caracteres, del búfer necesario para contener el nombre, incluida la terminación null.</span><span class="sxs-lookup"><span data-stu-id="957ff-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="957ff-108">[out] Búfer que almacena el nombre.</span><span class="sxs-lookup"><span data-stu-id="957ff-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="957ff-109">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="957ff-109">Return Value</span></span>  
 <span data-ttu-id="957ff-110">S_OK si el método tiene éxito; en caso contrario, E_FAIL u otro código de error.</span><span class="sxs-lookup"><span data-stu-id="957ff-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="957ff-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="957ff-111">Requirements</span></span>  
 <span data-ttu-id="957ff-112">**Encabezado:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="957ff-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="957ff-113">Vea también</span><span class="sxs-lookup"><span data-stu-id="957ff-113">See Also</span></span>  
 [<span data-ttu-id="957ff-114">ISymUnmanagedConstant (interfaz)</span><span class="sxs-lookup"><span data-stu-id="957ff-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="957ff-115">GetSignature (método)</span><span class="sxs-lookup"><span data-stu-id="957ff-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="957ff-116">GetValue (método)</span><span class="sxs-lookup"><span data-stu-id="957ff-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)