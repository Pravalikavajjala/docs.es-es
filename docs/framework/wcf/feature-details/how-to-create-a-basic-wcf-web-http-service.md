---
title: "Cómo: Crear un servicio básico web HTTP de WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dc60bbb51bc573840d0d45356f0cd84fd32db2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a>Cómo: Crear un servicio básico web HTTP de WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] le permite crear un servicio que expone un extremo web. Los puntos de conexión web envían los datos por XML o JSON, no hay ninguna envoltura SOAP. En este tema se muestra cómo exponer este tipo de extremos.  
  
> [!NOTE]
>  La única manera de proteger un extremo web es exponerlo a través de HTTPS, utilizando la seguridad de transporte. Al usar la seguridad basada en mensaje, la información de seguridad se coloca normalmente en encabezados SOAP, y dado que los mensajes enviados a los extremos que no son SOAP no contienen envoltura SOAP, no hay ningún lugar donde colocar la información de seguridad y debe confiar en la seguridad de transporte.  
  
### <a name="to-create-a-web-endpoint"></a>Para crear un punto de conexión web  
  
1.  Defina un contrato de servicios mediante una interfaz marcada con los atributos <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> y <xref:System.ServiceModel.Web.WebGetAttribute>.  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  De forma predeterminada, <xref:System.ServiceModel.Web.WebInvokeAttribute> asigna las llamadas POST a la operación. Puede, sin embargo, especificar el método HTTP (por ejemplo, HEAD, PUT o DELETE) para asignar a la operación especificando un parámetro “method=”. <xref:System.ServiceModel.Web.WebGetAttribute> no tiene un parámetro “method=” y solo asigna llamadas GET a la operación de servicio.  
  
2.  Implemente el contrato de servicios.  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a>Para hospedar el servicio  
  
1.  Crear un objeto <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  Agregue un <xref:System.ServiceModel.Description.ServiceEndpoint> al <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  Si no agrega un extremo, <xref:System.ServiceModel.Web.WebServiceHost> crea automáticamente un extremo predeterminado. <xref:System.ServiceModel.Web.WebServiceHost> también agrega <xref:System.ServiceModel.Description.WebHttpBehavior> y deshabilita la página de ayuda de HTTP y la funcionalidad GET del lenguaje de descripción de servicios Web (WSDL) para que el extremo de metadatos no interfiera con el extremo HTTP predeterminado.  
    >   
    >  Agregar un extremo que no es SOAP a una dirección URL de"" causa un comportamiento inesperado cuando se intenta llamar a una operación en el extremo. La razón para esto es que el URI de escucha del extremo es igual al URI de la página de ayuda (la página que se muestra al ir a la dirección base de un servicio de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]).  
  
     Para evitar que esto suceda, puede realizar una de las siguientes acciones:  
  
    -   Siempre especifique un URI que no esté en blanco para un extremo que no sea SOAP.  
  
    -   Desactive la página de ayuda. Esto se puede hacer mediante el siguiente código.  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  Abra el host de servicio y espere hasta que el usuario presione Entrar.  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     Este ejemplo muestra cómo hospedar un servicio de tipo web con una aplicación de consola. También puede hospedar este tipo de servicios dentro de IIS. Para ello, especifique la clase <xref:System.ServiceModel.Activation.WebServiceHostFactory> en un archivo .svc como muestra el siguiente código.  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Para llamar a las operaciones de servicio asignadas a GET en Internet Explorer  
  
1.  Abra Internet Explorer y escriba "`http://localhost:8000/EchoWithGet?s=Hello, world!`" y presione ENTRAR. La dirección URL contiene la dirección base del servicio ("http://localhost:8000/"), la dirección relativa del punto de conexión (""), la operación del servicio que se ha de llamar ("EchoWithGet") y un signo de interrogación seguido de una lista de parámetros con nombre separados por una Y comercial (&).  
  
### <a name="to-call-service-operations-in-code"></a>Realización de llamadas a operaciones de servicio mediante código  
  
1.  Cree una instancia de <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` dentro de un `using` bloque.  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  Agregue <xref:System.ServiceModel.Description.WebHttpBehavior> al extremo que <xref:System.ServiceModel.ChannelFactory> llamará.  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  Cree el canal y llame al servicio.  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  Cierre el <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a>Ejemplo  
 A continuación, se muestra una lista de código completa para este ejemplo.  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Al compilar Service.cs, haga una referencia a System.ServiceModel.dll y a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Modelo de programación de web HTTP de WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
