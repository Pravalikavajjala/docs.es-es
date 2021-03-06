---
title: "Protocolos de transacción versión 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e616f989416fcee77caa9b9a5d87cfa6812eab32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols-version-10"></a>Protocolos de transacción versión 1.0
La versión 1 de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementa la versión 1.0 de los protocolos WS-Atomic Transaction y WS-Coordination. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]versión 1.1, vea [protocolos de transacción](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).  
  
|Especificación/documento|Link|  
|-----------------------------|----------|  
|WS-Coordination|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|Transacción WS-Atomic|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 La interoperabilidad en estas especificaciones de protocolo se requiere en dos niveles: entre las aplicaciones y entre los administradores de transacciones (véase la siguiente figura). Las especificaciones describen en gran detalle los formatos de mensajes y el intercambio de mensajes para ambos niveles de interoperabilidad. Cierta seguridad, fiabilidad y codificaciones para el intercambio de aplicación a aplicación se aplican tal y como lo hacen para el intercambio normal de aplicaciones. Sin embargo, para una interoperabilidad correcta entre los administradores de transacciones es necesario el acuerdo en el enlace determinado, porque el usuario no lo configura por regla general.  
  
 Este tema describe una composición de la especificación de transacción WS-Atomic (WS-AT) con seguridad y describe el enlace seguro utilizado para la comunicación entre administradores de transacciones. El enfoque descrito en este documento se ha probado correctamente con otras implementaciones de WS-AT y WS-Coordination incluidos IBM, IONA, Sun Microsystems y otros.  
  
 La siguiente figura describe la interoperabilidad entre dos administradores de transacciones, Administrador de transacciones 1 y Administrador de transacciones 2, y dos aplicaciones, Aplicación 1 y Aplicación 2.  
  
 ![Protocolos de transacción](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "administradores")  
  
 Considere un escenario típico WS-Coordination/transacciones WS-Atomic con un Iniciador (I) y un Participante (P). Iniciador y Participante tienen administradores de transacciones (ITM y PTM, respectivamente). La confirmación en dos fases se conoce como 2PC en este tema.  
  
|||  
|-|-|  
|1. CreateCoordinationContext|12. Respuesta de mensajes de aplicaciones|  
|2. CreateCoordinationContextResponse|13. Confirmación (finalización)|  
|3. Registro (finalización)|14. Preparar (2PC)|  
|4. RegisterResponse|15. Preparar (2PC)|  
|5. Mensaje de la aplicación|16. Preparado (2PC)|  
|6. CreateCoordinationContext con contexto|17. Preparado (2PC)|  
|7. Registro (durable)|18. Confirmado (finalización)|  
|8. RegisterResponse|19. Confirmar (2PC)|  
|9. CreateCoordinationContextResponse|20. Confirmar (2PC)|  
|10. Registro (durable)|21. Confirmado (2PC)|  
|11. RegisterResponse|22. Confirmado (2PC)|  
  
 Este documento describe una composición de la especificación de transacción WS-Atomic con seguridad y describe el enlace seguro utilizado para la comunicación entre administradores de transacciones. El enfoque descrito en este documento se ha probado correctamente con otras implementaciones de WS-AT y Coordinación del WS.  
  
 La figura y la tabla muestran cuatro clases de mensajes desde el punto de vista de la seguridad:  
  
-   Mensajes de activación (CreateCoordinationContext y CreateCoordinationContextResponse).  
  
-   Mensajes del registro (Register y RegisterResponse)  
  
-   Mensajes de protocolos (Preparar, Reversión, Confirmar, Anulado, etc.).  
  
-   Mensajes de aplicaciones  
  
 Las primeras tres clases de mensajes están consideradas mensajes de Administrador de transacciones y su configuración de enlaces se describe en el "Intercambio de mensajes de aplicaciones" más adelante en este tema. La cuarta clase del mensaje son mensajes de aplicación a aplicación y se describe en la sección “Ejemplos de mensajes” más adelante en este tema. En esta sección se describen los enlaces de protocolos utilizados por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para cada una de estas clases.  
  
 Los siguientes espacios de nombres XML y prefijos asociados se utilizan a lo largo de este documento.  
  
|Prefijo|Espacio de nombres URI|  
|------------|-------------------|  
|s11|http://schemas.xmlsoap.org/soap/envelope|  
|wsa|http://www.w3.org/2004/08/Addressing|  
|wscoor|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|wsat|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|m|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|o|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|xsd|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a>Enlaces del administrador de transacciones  
 R1001: los administradores de transacciones deben utilizar SOAP 1.1 y WS-Addressing 2004/08 para intercambios de mensajes de transacciones WS-Atomic y WS-Coordination.  
  
 Los mensajes de la aplicación no se restringen a estos enlaces y se describen más adelante.  
  
### <a name="transaction-manager-https-binding"></a>Enlace HTTPS de administrador de transacciones  
 El enlace HTTPS del administrador de transacciones confía solamente en la seguridad de transporte para lograr la seguridad y establecer confianza entre cada par de remitente-receptor en el árbol de transacciones.  
  
#### <a name="https-transport-configuration"></a>Configuración de transporte HTTPS  
 Los certificados X.509 se utilizan para establecer la identidad del administrador de transacciones. Se requiere la autenticación cliente/servidor, y la autorización cliente/servidor queda como un detalle de implementación:  
  
-   R1111: los certificados X.509 presentados a través de la conexión deben tener un nombre de sujeto que coincida con el nombre de dominio completo (FQDN) del equipo de origen.  
  
-   B1112: DNS debe ser funcional entre cada par remitente-receptor del sistema para que las comprobaciones de nombre de sujeto X.509 se realicen correctamente.  
  
#### <a name="activation-and-registration-binding-configuration"></a>Activación y configuración de enlace de registro  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiere enlace dúplex de solicitud/respuesta que correlacione sobre HTTPS. (Para obtener más información sobre la correlación y descripciones de los patrones de intercambio de mensajes de solicitud/respuesta, vea Transacción WS-Atomic, sección 8.)  
  
#### <a name="2pc-protocol-binding-configuration"></a>Configuración de enlace de protocolo 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] admite mensajes unidireccionales (datagrama) sobre HTTPS. La correlación entre los mensajes queda como un detalle de implementación.  
  
 B2131: Las implementaciones deben admitir `wsa:ReferenceParameters` tal y como se describe en WS-Addressing para lograr correlación de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]de mensajes 2PC.  
  
### <a name="transaction-manager-mixed-security-binding"></a>Enlace de seguridad mixta del administrador de transacciones  
 Se trata de un enlace que utiliza seguridad de transporte combinada con el modelo de Token emitido de WS-Coordination para el establecimiento de la identidad alternativo (modo mixto).  La activación y el registro son los únicos elementos que difieren entre los dos enlaces.  
  
#### <a name="https-transport-configuration"></a>Configuración de transporte HTTPS  
 Los certificados X.509 se utilizan para establecer la identidad del administrador de transacciones. Se requiere la autenticación cliente/servidor, y la autorización cliente/servidor queda como un detalle de implementación.  
  
#### <a name="activation-message-binding-configuration"></a>Configuración del enlace de mensajes de activación  
 Los mensajes de activación normalmente no participan en la interoperabilidad porque, por lo general, se producen entre una aplicación y su administrador de transacción local.  
  
 B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa el enlace HTTPS dúplex (se describe en [protocolos de mensajería](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) para los mensajes de activación. Los mensajes de solicitud y respuesta se ponen en correlación mediante WS-Addressing 2004/08.  
  
 La especificación de transacción WS-Atomic, sección 8, describe detalles adicionales sobre la correlación y los patrones de intercambio de mensajes.  
  
-   R1222: tras recibir `CreateCoordinationContext`, el coordinador debe emitir un `SecurityContextToken` con `STx`secreto asociado. Este token se devuelve dentro de un encabezado `t:IssuedTokens` que sigue la especificación de WS-Trust.  
  
-   R1223: si la activación se produce dentro de un contexto de coordinación existente, el encabezado `t:IssuedTokens` con el `SecurityContextToken` asociado al contexto existente debe fluir en el mensaje `CreateCoordinationContext`.  
  
 Un nuevo `t:IssuedTokens` encabezado se debe generar para adjuntar a la salida `wscoor:CreateCoordinationContextResponse` mensaje.  
  
#### <a name="registration-message-binding-configuration"></a>Configuración del enlace de mensajes de registro  
 B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa el enlace HTTPS dúplex (se describe en [protocolos de mensajería](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)). Los mensajes de solicitud y respuesta se ponen en correlación mediante WS-Addressing 2004/08.  
  
 La transacción WS-Atomic, sección 8, describe detalles adicionales sobre la correlación y las descripciones del patrón de intercambio de mensajes.  
  
 R1232: Salida `wscoor:Register` mensajes deben utilizar el `IssuedTokenOverTransport` se describe el modo de autenticación en [protocolos de seguridad](../../../../docs/framework/wcf/feature-details/security-protocols.md).  
  
 El `wsse:Timestamp` elemento debe firmarse mediante el `SecurityContextToken``STx` emitido. Esta firma es una prueba de posesión del token asociado a la transacción determinada y se utiliza para autenticar a un participante enumerado en la transacción. El mensaje RegistrationResponse se devuelve sobre HTTPS.  
  
#### <a name="2pc-protocol-binding-configuration"></a>Configuración de enlace de protocolo 2PC  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] admite mensajes unidireccionales (datagrama) sobre HTTPS. La correlación entre los mensajes queda como un detalle de implementación.  
  
 B2131: Las implementaciones deben admitir `wsa:ReferenceParameters` tal y como se describe en WS-Addressing para lograr correlación de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]de mensajes 2PC.  
  
## <a name="application-message-exchange"></a>Intercambio de mensajes de aplicaciones  
 Las aplicaciones pueden utilizar cualquier enlace determinado para los mensajes de aplicación a aplicación, con tal de que el enlace cumpla los siguientes requisitos de seguridad:  
  
-   R2001: los mensajes de aplicación a aplicación deben fluir el encabezado `t:IssuedTokens` junto con `CoordinationContext` en el encabezado del mensaje.  
  
-   R2002: se debe proporcionar la integridad y confidencialidad de `t:IssuedToken`.  
  
 El encabezado `CoordinationContext` contiene `wscoor:Identifier`. Aunque la definición de `xsd:AnyURI` permite el uso de URI absolutos y relativos, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] solo admite `wscoor:Identifiers`, que sean URI absolutos.  
  
 B2003: si el `wscoor:Identifier` de `wscoor:CoordinationContext` es un URI relativo, los errores se devolverán desde los servicios transaccionales de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="message-examples"></a>Ejemplos de mensajes  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a>Mensajes de solicitud/respuesta CreateCoordinationContext  
 Los siguientes mensajes siguen un patrón de solicitud/respuesta.  
  
#### <a name="createcoordinationcontext"></a>CreateCoordinationContext  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a>CreateCoordinationContextResponse  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a>Mensajes del registro  
 Los siguientes mensajes son mensajes del registro.  
  
#### <a name="register"></a>Registro  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a>Respuesta de registro  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a>Mensajes de protocolo de confirmación de dos fase  
 El siguiente mensaje se relaciona con el protocolo de confirmación en dos fases (2PC).  
  
#### <a name="commit"></a>Confirmar  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a>Mensajes de aplicaciones  
 Los siguientes mensajes son mensajes de aplicaciones.  
  
#### <a name="application-message-request"></a>Solicitud de mensaje de aplicación  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
