---
title: "Cómo: Realizar escuchas de varias solicitudes de cancelación"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 397de114a3d8c3cbcfbc8ab55e4dbaf45ca9b652
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Cómo: Realizar escuchas de varias solicitudes de cancelación
En este ejemplo se muestra cómo escuchar dos tokens de cancelación simultáneamente, para poder cancelar una operación si el token lo solicita.  
  
> [!NOTE]
>  Cuando está habilitada la opción "Solo mi código", en algunos casos, Visual Studio se interrumpe en la línea que produce la excepción y muestra el mensaje de error "Excepción no controlada por el código de usuario". Este error es benigno. Puede presionar F5 para continuar y ver el comportamiento de control de excepciones que se muestra en estos ejemplos. Para evitar que Visual Studio se interrumpa con el primer error, desactive la casilla "Solo mi código" en **Herramientas, Opciones, Depurar, General**.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, el método <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> se utiliza para combinar dos tokens en uno. Esto permite que el token se pase a métodos que adoptan un token de cancelación como un argumento. En el ejemplo se muestra un escenario común en el que un método debe observar un token pasado desde fuera de la clase y un token generado dentro de la clase.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Cuando el token vinculado produce una clase <xref:System.OperationCanceledException>, el token que se pasa a la excepción es el token vinculado, no uno de los tokens predecesores. Para determinar cuál de los tokens se canceló, compruebe el estado de los tokens predecesores directamente.  
  
 En este ejemplo, <xref:System.AggregateException> nunca debería iniciarse, pero se detecta aquí porque en escenarios del mundo real cualquier otra excepción aparte de <xref:System.OperationCanceledException> producida a partir del delegado de tarea se encapsula en <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Vea también  
 [Cancelación en subprocesos administrados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
