---
title: "Cómo: Habilitar el acceso al servicio de datos (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f481a3a918282bf598277dcd4e1bf29d63edddc1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>Cómo: Habilitar el acceso al servicio de datos (WCF Data Services)
En [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], debe permitir explícitamente el acceso a los recursos expuestos por un servicio de datos. Esto significa que después de crear un nuevo servicio de datos, debe proporcionar explícitamente acceso a los recursos individuales como conjuntos de entidades. Este tema muestra cómo habilitar la lectura y acceso de escritura a cinco de la entidad se establece en el servicio de datos de Northwind que se crea cuando completa la [inicio rápido](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Dado que la enumeración <xref:System.Data.Services.EntitySetRights> se define utilizando <xref:System.FlagsAttribute>, puede utilizar un operador OR lógico para especificar varios permisos para un único conjunto de entidades.  
  
> [!NOTE]
>  Cualquier cliente que pueda tener acceso a la aplicación ASP.NET también puede tener acceso a los recursos expuestos por el servicio de datos. En un servicio de datos de producción, para evitar el acceso no autorizado a los recursos, también debería proteger la aplicación. Para obtener más información, consulte [NIB: seguridad de ASP.NET](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).  
  
### <a name="to-enable-access-to-the-data-service"></a>Para habilitar el acceso al servicio de datos  
  
-   En el código del servicio de datos, reemplace el código de marcador de posición de la función `InitializeService` por el siguiente:  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     De esta forma, los clientes pueden tener acceso de lectura y escritura a los conjuntos de entidades de `Orders` y `Order_Details`, y acceso de solo lectura a los conjuntos de entidades de `Customers`.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollo de un servicio de datos WCF que se ejecuta en IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [Configuración del servicio de datos](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
