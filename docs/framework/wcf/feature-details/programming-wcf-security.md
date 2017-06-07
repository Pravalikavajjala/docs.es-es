---
title: "Programaci&#243;n de la seguridad de WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "seguridad de mensaje [WCF], iInformación general sobre programación"
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
caps.latest.revision: 25
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 25
---
# Programaci&#243;n de la seguridad de WCF
Este tema describe las tareas de programación fundamentales utilizadas para crear una aplicación de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] segura.Este tema solo cubre la autenticación, confidencialidad e integridad, conocido colectivamente como *seguridad de transferencia*.En este tema no se cubre la autorización \(el control de acceso a recursos o servicios\); para obtener información sobre la autorización, vea [Autorización](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Dispone de una valiosa introducción a los conceptos de seguridad, sobre todo con respecto a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], en el conjunto de tutoriales sobre modelos y procedimientos de MSDN, en la [Guía sobre escenarios, modelos e implementación de Web Services Enhancements \(WSE\) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).  
  
 La programación de la seguridad de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se basa en tres pasos que establecen lo siguiente: el modo de seguridad, un tipo de credencial de cliente y los valores de credenciales.Puede realizar estos pasos mediante código o configuración.  
  
## Establecimiento del modo de seguridad  
 Lo siguiente explica los pasos generales para programar con el modo de seguridad en [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
1.  Seleccione uno de los enlaces predefinidos adecuado a sus requisitos de aplicación.Para obtener una lista de opciones de enlaces, vea [Enlaces proporcionados por el sistema](../../../../docs/framework/wcf/system-provided-bindings.md).De forma predeterminada, prácticamente todos los enlaces tienen la seguridad habilitada.La única excepción es la clase <xref:System.ServiceModel.BasicHttpBinding> \(utilizando configuración, el [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)\).  
  
     El enlace que seleccione determina el transporte.Por ejemplo, <xref:System.ServiceModel.WSHttpBinding> utiliza HTTP como el transporte; <xref:System.ServiceModel.NetTcpBinding> utiliza TCP.  
  
2.  Seleccione uno de los modos de seguridad para el enlace.Tenga en cuenta que el enlace que seleccione determinará las opciones de modo disponibles.Por ejemplo, <xref:System.ServiceModel.WSDualHttpBinding> no permite la seguridad de transporte \(no es una opción\).De igual forma, ni <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ni <xref:System.ServiceModel.NetNamedPipeBinding> permiten el modo de seguridad.  
  
     Dispone de tres opciones:  
  
    1.  `Transport`  
  
         La seguridad de transporte depende del mecanismo que use el enlace que haya seleccionado.Por ejemplo, si utiliza `WSHttpBinding`, el mecanismo de seguridad es Secure Sockets Layer \(SSL\) \(también es el mecanismo para el protocolo HTTPS\).Generalmente hablando, la principal ventaja de la seguridad de transporte es que proporciona un buen rendimiento independientemente del transporte que esté utilizando.No obstante, tiene dos limitaciones: la primera es que el mecanismo de transporte dicta el tipo de credencial utilizado para autenticar a un usuario.Ésta es una desventaja solo si un servicio necesita interoperar con otros servicios que exigen tipos diferentes de credenciales.La segunda es que, puesto que la seguridad no se aplica en el nivel de mensaje, la seguridad se implementa salto por salto en lugar de de extremo a extremo.Esta última limitación es un problema solo si la ruta de mensajes entre el cliente y el servicio incluye intermediarios.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] qué transporte usar, vea [Elección del transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] cómo usar la seguridad de transporte, vea [Información general de la seguridad del transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2.  `Message`  
  
         El modo de seguridad significa que cada mensaje incluye los encabezados y datos necesarios para mantener el mensaje protegido.Dado que la composición de los encabezados varía, puede incluir cualquier número de credenciales.Este es un factor a tener en cuenta si está interoperando con otros servicios que exigen un tipo de credencial concreto que un mecanismo de transporte no puede proporcionar o si el mensaje se debe utilizar con más de un servicio, donde cada servicio exige un tipo de credencial diferente.  
  
         [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Seguridad de los mensajes](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3.  `TransportWithMessageCredential`  
  
         Esta opción utiliza el nivel de transporte para proteger la transferencia del mensaje, mientras que cada mensaje incluye las credenciales enriquecidas que necesitan otros servicios.Esto combina la ventaja de rendimiento de la seguridad de transporte con la ventaja de las credenciales enriquecidas de la seguridad de mensaje.Esto está disponible con los siguientes enlaces: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding> y <xref:System.ServiceModel.WSHttpBinding>.  
  
3.  Si decide utilizar la seguridad de transporte para HTTP \(en otras palabras, HTTPS\), debe configurar también el host con un certificado SSL y habilitar SSL en un puerto.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Seguridad de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4.  Si está utilizando el <xref:System.ServiceModel.WSHttpBinding> y no necesita establecer una sesión segura, establezca la propiedad <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> en `false`.  
  
     Una sesión segura se produce cuando un cliente y servicio crean un canal mediante una clave simétrica \(tanto el cliente como el servidor usan la misma clave durante la duración de una conversación, hasta que se cierre el diálogo\).  
  
## Establecimiento del tipo de credencial de cliente  
 Seleccione según corresponda un tipo de credencial de cliente.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Selección de tipos de credenciales](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).Los siguientes tipos de credencial de cliente están disponibles:  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 Dependiendo de cómo establezca el modo, deberá establecer el tipo de credencial.Por ejemplo, si ha seleccionado el `wsHttpBinding`, y ha establecido el modo en "Mensaje", también puede establecer el atributo `clientCredentialType` del elemento Message en uno de los valores siguientes: `None`, `Windows`, `UserName`, `Certificate` y `IssuedToken`, como se muestra en el ejemplo de configuración siguiente.  
  
```  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 O bien, en el código:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## Establecimiento de valores de credenciales de servicio  
 Cuando selecciona un tipo de credencial de cliente, debe establecer las credenciales reales que el servicio y el cliente han de utilizar.En el servicio, las credenciales se establecen utilizando la clase <xref:System.ServiceModel.Description.ServiceCredentials> y se devuelven mediante la propiedad <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> de la clase <xref:System.ServiceModel.ServiceHostBase>.El enlace en uso implica el tipo de credencial de servicio, el modo de seguridad elegido y el tipo de la credencial de cliente.El código siguiente establece un certificado para una credencial de servicio.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## Establecimiento de los valores de credencial de cliente  
 En el cliente, establezca valores de credencial de cliente mediante la clase <xref:System.ServiceModel.Description.ClientCredentials> y devueltos por la propiedad <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la clase <xref:System.ServiceModel.ClientBase%601>.El código siguiente establece un certificado como una credencial en un cliente utilizando el protocolo TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## Vea también  
 [Programación básica de WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)   
 [Escenarios de seguridad comunes](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)