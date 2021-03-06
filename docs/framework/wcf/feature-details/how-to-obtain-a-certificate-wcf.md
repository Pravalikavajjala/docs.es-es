---
title: "Cómo obtener un certificado (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5dcefa658aec37b9af3c4f9285ec76a0d549b868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Cómo obtener un certificado (WCF)
Para usar cualquiera de las características de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] que usan certificados X.509, ha de obtener primero los certificados.  
  
### <a name="to-obtain-an-x509-certificate"></a>Para obtener un certificado X.509.  
  
1.  Elija una de las siguientes opciones:  
  
    -   Adquiera un certificado de una entidad emisora de certificados, como VeriSign, Inc.  
  
    -   Configure su propio servicio de certificados y haga que una entidad de certificación los firme. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter y Windows 2000 Datacenter Server incluyen servicios de servidor de certificados que admiten la infraestructura de clave pública (PKI). En Windows Server 2008, use la [servicios de certificados de Active Directory](http://go.microsoft.com/fwlink/?LinkID=153483) para administrar una entidad de certificación.  
  
    -   Configure su propio servicio de certificados y asegúrese de que los certificados no estén firmados.  
  
    > [!NOTE]
    >  Elija el método que elija, el destinatario de la solicitud SOAP que contiene el certificado X.509 debe confiar en el certificado X.509. Esto significa que el certificado X.509 o un emisor en la cadena de certificados está en el almacén de certificados de gente de confianza y que el certificado X.509 no está en el almacén de certificados que no son de confianza.  
  
## <a name="see-also"></a>Vea también  
 [Trabajo con certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Creación de certificados temporales que puedan utilizarse durante las operaciones de desarrollo](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
