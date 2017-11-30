---
title: ISymUnmanagedDocument (Interfaz)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument
helpviewer_keywords: ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8654f28cc4d82a5ed1419215807ec3360522fd55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="15851-102">ISymUnmanagedDocument (Interfaz)</span><span class="sxs-lookup"><span data-stu-id="15851-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="15851-103">Representa un documento al que hace referencia un almacén de símbolos.</span><span class="sxs-lookup"><span data-stu-id="15851-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="15851-104">Un documento viene definido por un localizador uniforme de recursos (URL) y un GUID de tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="15851-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="15851-105">Puede encontrar el documento sin tener en cuenta cómo se almacena utilizando la dirección URL y GUID de tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="15851-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="15851-106">Puede almacenar el código fuente del documento en el almacén de símbolos y recuperarlo a través de esta interfaz.</span><span class="sxs-lookup"><span data-stu-id="15851-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15851-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="15851-107">Methods</span></span>  
  
|<span data-ttu-id="15851-108">Método</span><span class="sxs-lookup"><span data-stu-id="15851-108">Method</span></span>|<span data-ttu-id="15851-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="15851-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15851-110">FindClosestLine (método)</span><span class="sxs-lookup"><span data-stu-id="15851-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="15851-111">Devuelve la línea más próxima que sea un punto de secuencia, dada una línea en este documento que puede ser o no un punto de secuencia.</span><span class="sxs-lookup"><span data-stu-id="15851-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="15851-112">GetCheckSum (método)</span><span class="sxs-lookup"><span data-stu-id="15851-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="15851-113">Obtiene la suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="15851-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="15851-114">GetCheckSumAlgorithmId (método)</span><span class="sxs-lookup"><span data-stu-id="15851-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="15851-115">Obtiene el identificador del algoritmo de suma de comprobación o devuelve un GUID de todos los ceros si no hay ninguna suma de comprobación.</span><span class="sxs-lookup"><span data-stu-id="15851-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="15851-116">GetDocumentType (método)</span><span class="sxs-lookup"><span data-stu-id="15851-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="15851-117">Obtiene el tipo de documento de este documento.</span><span class="sxs-lookup"><span data-stu-id="15851-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="15851-118">GetLanguage (método)</span><span class="sxs-lookup"><span data-stu-id="15851-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="15851-119">Obtiene el identificador de idioma de este documento.</span><span class="sxs-lookup"><span data-stu-id="15851-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="15851-120">GetLanguageVendor (método)</span><span class="sxs-lookup"><span data-stu-id="15851-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="15851-121">Obtiene el proveedor de lenguaje de este documento.</span><span class="sxs-lookup"><span data-stu-id="15851-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="15851-122">GetSourceLength (método)</span><span class="sxs-lookup"><span data-stu-id="15851-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="15851-123">Obtiene la longitud, en bytes, del código fuente incrustado.</span><span class="sxs-lookup"><span data-stu-id="15851-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="15851-124">GetSourceRange (método)</span><span class="sxs-lookup"><span data-stu-id="15851-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="15851-125">Devuelve el intervalo especificado de código fuente incrustado en el búfer especificado.</span><span class="sxs-lookup"><span data-stu-id="15851-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="15851-126">GetURL (método)</span><span class="sxs-lookup"><span data-stu-id="15851-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="15851-127">Devuelve la dirección URL de este documento.</span><span class="sxs-lookup"><span data-stu-id="15851-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="15851-128">HasEmbeddedSource (método)</span><span class="sxs-lookup"><span data-stu-id="15851-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="15851-129">Devuelve `true` si el documento tiene código fuente incrustado en los símbolos de depuración; en caso contrario, devuelve `false`.</span><span class="sxs-lookup"><span data-stu-id="15851-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15851-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="15851-130">See Also</span></span>  
 [<span data-ttu-id="15851-131">Interfaces de almacén de símbolos de diagnósticos</span><span class="sxs-lookup"><span data-stu-id="15851-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)