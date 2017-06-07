---
title: "&lt;ws2007FederationHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;ws2007FederationHttpBinding&gt;
Un enlace seguro e interoperable que deriva de [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) y admite la seguridad federada.  
  
## Sintaxis  
  
```  
  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                issuedTokenType="string"  
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"   
            maxNameTableCharCount="Integer"           
            maxStringContentLength="Integer" />  
    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`bypassProxyOnLocal`|Un valor que indica si se omitirá el servidor proxy para las direcciones locales.  De manera predeterminada, es `false`.|  
|`closeTimeout`|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de cierre para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|`hostnameComparisonMode`|Especifica el modo de comparación de nombres de host HTTP usado para analizar los URI.  Este atributo es del tipo <xref:System.ServiceModel.HostnameComparisonMode>, que indica si se va a utilizar el nombre del host para llegar al servicio cuando coincida en el URI.  El valor predeterminado es <xref:System.ServiceModel.HostnameComparisonMode.StrongWildcard>, que omite el nombre del host en la coincidencia.|  
|`maxBufferPoolSize`|El tamaño máximo del grupo de búferes para este enlace.  El valor predeterminado es 524.288 bytes \(512x1024\).  Muchas partes de búferes de uso [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  Crear y destruir búferes cada vez que se usan es caro, y la recolección de elementos no utilizados para los búferes también es cara.  Con grupos de búferes, puede tomar un búfer del grupo, usarlo y devolverlo al grupo una vez haya terminado.  Así se evita la sobrecarga al crear y destruir búferes.|  
|`maxReceivedMessageSize`|El tamaño máximo del mensaje, en bytes, incluidos los encabezados, que se puede recibir en un canal configurado con este enlace.  El remitente de un mensaje que supera este límite recibe un error SOAP.  El destinatario quita el mensaje y crea una entrada del evento en el registro de seguimiento.  El valor predeterminado es 65536.|  
|`messageEncoding`|Define el codificador utilizado para codificar el mensaje.  Los valores válidos son los siguientes:<br /><br /> -   Text: utiliza un codificador de mensajes de texto.<br />-   Mtom: usa un codificador de Mecanismo de optimización de transmisión del mensaje 1.0 \(MTOM\).<br /><br /> El valor predeterminado es Text.<br /><br /> Este atributo es del tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Nombre de configuración del enlace.  Este valor debe ser único porque se usa como identificación del enlace.  A partir de [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], no es necesario que los enlaces y los comportamientos tengan nombre.  Para obtener más información sobre la configuración predeterminada, así como sobre enlaces y comportamientos sin nombre, vea [Configuración simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) y [Configuración simplificada de los servicios de WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Valor de la estructura <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de apertura para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|`privactyNoticeAt`|URI en el que se encuentra el aviso de privacidad.|  
|`privactyNoticeVersion`|El número de versión del aviso de privacidad actual.|  
|`proxyAddress`|Un URI que especifica la dirección del proxy HTTP.  Si `useDefaultWebProxy` es `true`, este valor debe ser `null`.  De manera predeterminada, es `null`.|  
|`receiveTimeout`|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de recepción para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:10:00.|  
|`sendTimeout`|Un valor <xref:System.TimeSpan> que especifica el intervalo de tiempo del que dispone una operación de envío para completarse.  Este valor debe ser mayor o igual que <xref:System.TimeSpan.Zero>.  El valor predeterminado es 00:01:00.|  
|`textEncoding`|Establece el codificador del juego de caracteres que se va a usar para emitir los mensajes en el enlace.  Los valores válidos son los siguientes:<br /><br /> -   BigEndianUnicode: codificación Big Endian de Unicode.<br />-   Codificación de 16 bits Unicode.<br />-   UTF8: codificación de 8 bits.<br /><br /> El valor predeterminado es UTF8.  Este atributo es del tipo <xref:System.Text.Encoding>.|  
|`transactionFlow`|Valor que especifica si el enlace admite el flujo de transacciones de WS.  De manera predeterminada, es `false`.|  
|`useDefaultWebProxy`|Un valor que indica si se utiliza el proxy HTTP del sistema configurado automáticamente.  La dirección de proxy debe ser `null` \(es decir, sin establecer\) si este atributo es `true`.  De manera predeterminada, es `true`.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[\<seguridad\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Define la configuración de seguridad del mensaje.  Este elemento es del tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Define las restricciones en la complejidad de los mensajes SOAP que pueden ser procesados por los extremos configurados con este enlace.  Este elemento es del tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/es-es/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica si se establecen sesiones confiables entre los extremos del canal.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[\<enlaces\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Este elemento contiene una colección de enlaces estándar y personalizados.|  
  
## Comentarios  
 La federación es la capacidad de compartir identidades en varias empresas o dominios de confianza para la autenticación y autorización.  Utiliza el protocolo WS\-Trust para asignar la representación de identidad de un dominio de confianza a otro.  El enlace HTTP federado admite la seguridad de SOAP así como la seguridad de modo mixto, pero no permite la seguridad de transporte.  Los servicios configurados con este enlace deben utilizar el transporte de HTTP.  [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
## Ejemplo  
  
```  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## Vea también  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>   
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>   
 [\<wsFederationHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)   
 [Enlaces](../../../../../docs/framework/wcf/bindings.md)   
 [Configuración de enlaces proporcionados por el sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/es-es/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<enlace\>](../../../../../docs/framework/misc/binding.md)