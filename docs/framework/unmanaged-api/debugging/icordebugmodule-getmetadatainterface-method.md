---
title: "ICorDebugModule::GetMetaDataInterface (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4b1944c68db0cbdd8eb49e10433defc953e4494
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="3055c-102">ICorDebugModule::GetMetaDataInterface (Método)</span><span class="sxs-lookup"><span data-stu-id="3055c-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="3055c-103">Obtiene un objeto de interfaz de metadatos que puede usarse para examinar los metadatos para el módulo.</span><span class="sxs-lookup"><span data-stu-id="3055c-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3055c-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3055c-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3055c-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="3055c-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="3055c-106">[in] El identificador de referencia que especifica la interfaz de metadatos.</span><span class="sxs-lookup"><span data-stu-id="3055c-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="3055c-107">[out] Un puntero a la dirección de un `T:IUnknown` objeto que es uno de los [interfaces de metadatos](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="3055c-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3055c-108">Comentarios</span><span class="sxs-lookup"><span data-stu-id="3055c-108">Remarks</span></span>  
 <span data-ttu-id="3055c-109">El depurador puede utilizar el `GetMetaDataInterface` método para realizar una copia de los metadatos originales para un módulo, lo que es necesario para editar ese módulo.</span><span class="sxs-lookup"><span data-stu-id="3055c-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="3055c-110">El depurador llama `GetMetaDataInterface` para obtener un [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) objeto de interfaz para el módulo, a continuación, llama a [SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) para guardar una copia de los metadatos del módulo en memoria.</span><span class="sxs-lookup"><span data-stu-id="3055c-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3055c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3055c-111">Requirements</span></span>  
 <span data-ttu-id="3055c-112">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3055c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3055c-113">**Encabezado:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3055c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3055c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3055c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3055c-115">**Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3055c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3055c-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="3055c-116">See Also</span></span>  
 [<span data-ttu-id="3055c-117">Metadatos</span><span class="sxs-lookup"><span data-stu-id="3055c-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)