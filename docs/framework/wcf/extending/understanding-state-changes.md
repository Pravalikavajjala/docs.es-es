---
title: "Introducci&#243;n a los cambios de estado | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a79ed2aa-e49a-47a8-845a-c9f436ec9987
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Introducci&#243;n a los cambios de estado
En este tema se discuten los estados y transiciones que los canales tienen, los tipos utilizados para estructurar los estados del canal, y cómo implementarlos.  
  
## Equipos de estado y canales  
 Los objetos que están relacionados con la comunicación, por ejemplo los sockets, normalmente presentan un equipo de estado cuyas transiciones de estado están relacionadas con asignar los recursos de la red, realizar o aceptar conexiones, cerrar conexiones y finalizar la comunicación.La máquina de estados del canal proporciona un modelo uniforme de los estados de un objeto de comunicación que abstrae la implementación subyacente de ese objeto.La interfaz <xref:System.ServiceModel.ICommunicationObject> proporciona un conjunto de estados, métodos de transición de estado y eventos de transición de estado.Todos los canales, generadores de canales y escuchas de canal implementan la máquina de estados del canal.  
  
 Los eventos Cerrado, Cerrando, Error, Abierto y Abriendo señalan un observador externo después de que se produzca una transición de estado.  
  
 La métodos Anular, Cerrar, y Abrir \(y sus equivalentes asincrónicos\) producen las transiciones de estado.  
  
 La propiedad de estado devuelve el estado actual como definido por <xref:System.ServiceModel.CommunicationState>:  
  
## ICommunicationObject, CommunicationObject y estados y transición de estado  
 <xref:System.ServiceModel.ICommunicationObject> empieza en el estado Creado donde se pueden configurar sus diferentes propiedades.Una vez en el estado Abierto, el objeto se puede utilizar para enviar y recibir mensajes pero sus propiedades se consideran inmutables.Una vez en el estado Cerrando, el objeto ya no puede procesar nuevas solicitudes de envío o recepción, pero las solicitudes existentes tiene una oportunidad para completarse hasta que se alcance el tiempo de espera de Cerrar.Si se produce un error irrecuperable, el objeto pasa al estado Error donde se puede inspeccionar para obtener información sobre el error y finalmente cerrarlo.Cuando en el estado Cerrado el objeto ha llegado esencialmente al fin de la máquina de estados.Cuando objeto pasa de un estado al siguiente, no regresa a un estado anterior.  
  
 El diagrama siguiente muestra los estados <xref:System.ServiceModel.ICommunicationObject> y transiciones de estado.Las transiciones de estado se pueden producir llamando a uno de los tres métodos: Anular, Abrir o Cerrar.También se pueden producir llamando a otros métodos específicos de la implementación.La transición al estado Error se podría producir como resultado de los errores mientras se abre o después de haber abierto el objeto de comunicación.  
  
 Cada <xref:System.ServiceModel.ICommunicationObject> empieza en el estado Creado.En este estado, una aplicación puede configurar el objeto estableciendo sus propiedades.Cuando un objeto está en un estado diferente a Creado, se considera inmutable.  
  
 ![Transición del estado del canal](../../../../docs/framework/wcf/extending/media/channelstatetranitionshighleveldiagram.gif "ChannelStateTranitionsHighLevelDiagram")  
Figura 1.La máquina de estados de ICommunicationObject.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] proporciona una clase base abstracta denominada <xref:System.ServiceModel.Channels.CommunicationObject> que implementa <xref:System.ServiceModel.ICommunicationObject> y la máquina de estados del canal.El gráfico siguiente es un diagrama de estados modificado que es específico de <xref:System.ServiceModel.Channels.CommunicationObject>.Además de la máquina de estados <xref:System.ServiceModel.ICommunicationObject>, muestra el control de tiempo cuando se invocan métodos <xref:System.ServiceModel.Channels.CommunicationObject> adicionales.  
  
 ![Cambios de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure5statetransitionsdetailsc.gif "wcfc\_WCFChannelsigure5StateTransitionsDetailsc")  
Figura 2.La implementación de CommunicationObject del equipo de estados ICommunicationObject incluidas las llamadas a eventos y métodos protegidos.  
  
### Eventos ICommunicationObject  
 <xref:System.ServiceModel.Channels.CommunicationObject> expone los cinco eventos definidos por <xref:System.ServiceModel.ICommunicationObject>.Estos eventos están diseñados para el código que utiliza el objeto de comunicación al que notificar las transiciones de estado.Como se muestra en la figura 2 anterior, se desencadena cada evento después de las transiciones de estado del objeto al estado denominado por el evento.Los cinco eventos son del tipo `EventHandler` que se define como:  
  
 `public delegate void EventHandler(object sender, EventArgs e);`  
  
 En la implementación <xref:System.ServiceModel.Channels.CommunicationObject>, el remitente es el propio <xref:System.ServiceModel.Channels.CommunicationObject> o lo que se pasó como remitente al constructor <xref:System.ServiceModel.Channels.CommunicationObject> \(si se utilizó esa sobrecarga de constructor\).El parámetro EventArgs, `e`, siempre es `EventArgs.Empty`.  
  
### Devoluciones de llamada de objetos derivados  
 Además de los cinco eventos, <xref:System.ServiceModel.Channels.CommunicationObject> declara ocho métodos virtuales protegidos diseñados para permitir a un objeto derivado volver a llamar antes y después de que se produzcan las transiciones de estado.  
  
 Los métodos <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=fullName> y <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=fullName> tienen tres devoluciones de llamada de este tipo asociadas a cada uno de ellos.Por ejemplo, correspondiendo a <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=fullName> hay <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=fullName>, <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=fullName>y <xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=fullName>.Se asocian a <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=fullName> los métodos <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=fullName>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=fullName>, y <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=fullName>.  
  
 De igual forma, el método <xref:System.ServiceModel.Channels.CommunicationObject.Abort%2A?displayProperty=fullName> tiene un <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=fullName>correspondiente.  
  
 Aunque <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A?displayProperty=fullName>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClose%2A?displayProperty=fullName>y <xref:System.ServiceModel.Channels.CommunicationObject.OnAbort%2A?displayProperty=fullName> no tienen ninguna implementación predeterminada, las otras devoluciones de llamada tienen una implementación predeterminada que es necesaria para la exactitud de la máquina de estados.Si invalida esos métodos asegúrese de llamar a la implementación base o reemplazarla correctamente.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=fullName>, <xref:System.ServiceModel.Channels.CommunicationObject.OnClosing%2A?displayProperty=fullName> y <xref:System.ServiceModel.Channels.CommunicationObject.OnFaulted%2A?displayProperty=fullName> desencadenan los eventos <xref:System.ServiceModel.Channels.CommunicationObject.Opening?displayProperty=fullName>, <xref:System.ServiceModel.Channels.CommunicationObject.Closing?displayProperty=fullName> y <xref:System.ServiceModel.Channels.CommunicationObject.Faulted?displayProperty=fullName> correspondientes.<xref:System.ServiceModel.Channels.CommunicationObject.OnOpened%2A?displayProperty=fullName> y <xref:System.ServiceModel.Channels.CommunicationObject.OnClosed%2A?displayProperty=fullName> establecen el estado de objeto en Opened y Closed respectivamente y, después, desencadenan los eventos <xref:System.ServiceModel.Channels.CommunicationObject.Opened?displayProperty=fullName> y <xref:System.ServiceModel.Channels.CommunicationObject.Closed?displayProperty=fullName> correspondientes.  
  
### Métodos de transición de estado  
 <xref:System.ServiceModel.Channels.CommunicationObject> proporciona implementaciones de Anular, Cerrar y Abrir.También proporciona un método Error que provoca una transición de estado al estado Error.La figura 2 muestra la máquina de estados <xref:System.ServiceModel.ICommunicationObject> con cada transición etiquetada por el método que la produce \(las transiciones no etiquetadas tienen lugar dentro de la implementación del método que produjo la última transición etiquetada\).  
  
> [!NOTE]
>  Todas las implementaciones <xref:System.ServiceModel.Channels.CommunicationObject> de estado de comunicación obtener\/establecer están sincronizadas por subproceso.  
  
 Constructor  
  
 <xref:System.ServiceModel.Channels.CommunicationObject> proporciona tres constructores; todos ellos dejan el objeto en el estado Creado.Los constructores se definen como:  
  
 El primer constructor es un constructor predeterminado que delega a la sobrecarga del constructor que toma un objeto:  
  
 `protected CommunicationObject() : this(new object()) { … }`  
  
 El constructor que toma un objeto utiliza ese parámetro como el objeto a bloquear al sincronizar el acceso con el estado de objeto de comunicación:  
  
 `protected CommunicationObject(object mutex) { … }`  
  
 Finalmente, un tercer constructor toma un parámetro adicional que se utiliza como argumento de remitente cuando se desencadenan los eventos <xref:System.ServiceModel.ICommunicationObject>.  
  
 `protected CommunicationObject(object mutex, object eventSender) { … }`  
  
 Los dos constructores anteriores establecen el remitente en esto.  
  
 Método Abrir  
  
 Condición previa: el estado está Creado.  
  
 Condición posterior: el estado está Abierto o tiene un Error.Podría iniciar una excepción.  
  
 El método Open \(\) intentará abrir el objeto de comunicación y establecer el estado en Abierto.Si encuentra un error, establecerá el estado en Error.  
  
 El método comprueba primero que el estado actual sea Creado.Si el estado actual es Abriendo o Abierto inicia <xref:System.InvalidOperationException>.Si el estado actual es Cerrando o Cerrado, inicia <xref:System.ServiceModel.CommunicationObjectAbortedException> si se ha finalizado el objeto y <xref:System.ObjectDisposedException>.Si el estado actual es Error, inicia <xref:System.ServiceModel.CommunicationObjectFaultedException>.  
  
 A continuación establece el estado en Abriendo y llama a OnOpening \(\) \(que desencadena el evento Abriendo\), OnOpen \(\) y OnOpened \(\) en ese orden.OnOpened \(\) establece el estado en Abierto y desencadena el evento Abierto.Si cualquiera de estas operaciones provoca una excepción, Open\(\) llama a Fault\(\) y permite que se produzca la excepción.El diagrama siguiente muestra con más detalle el proceso Abrir.  
  
 ![Cambios de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigurecoopenflowchartf.gif "wcfc\_WCFChannelsigureCOOpenFlowChartf")  
Invalide el método OnOpen para implementar lógica abierta personalizada como abrir un objeto de comunicación interno.  
  
 Método Cerrar  
  
 Condición previa: ninguna.  
  
 Condición posterior: el estado es Cerrado.Podría iniciar una excepción.  
  
 Se puede llamar al método Close\(\) en cualquier estado.Intenta cerrar normalmente el objeto.Si se encuentra un error, finaliza el objeto.El método no hace nada si el estado actual es Cerrando o Cerrado.De lo contrario establece el estado en Cerrando.Si el estado original era Creado, Abriendo o Error, llama a Abort\(\) \(vea el diagrama siguiente\).Si el estado original era Abierto, llama a OnClosing\(\) \(que desencadena el evento Cerrando\), OnClose\(\) y OnClosed\(\) en ese orden.Si cualquiera de estas operaciones provoca una excepción, Close\(\) llama a Abort\(\) y permite que se produzca la excepción.OnClosed\(\) establece el estado en Cerrado y desencadena el evento Cerrado.El diagrama siguiente muestra con más detalle el proceso Cerrar.  
  
 ![Cambios de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsguire7ico-closeflowchartc.gif "wcfc\_WCFChannelsguire7ICO\-CloseFlowChartc")  
Invalide el método OnClose para implementar la lógica del cierre personalizada, como cerrar un objeto de comunicación interno.Toda lógica de cierre elegante que se pueda bloquear durante mucho tiempo \(por ejemplo, esperando a que el otro lado responda\) se debería implementar en OnClose\(\) porque toma un parámetro de tiempo de espera y porque no se llama como parte de Abort\(\).  
  
 Anular  
  
 Condición previa: ninguna.  
Condición posterior: el estado es Cerrado.Podría iniciar una excepción.  
  
 El método Abort\(\) no hace nada si el estado actual es Cerrado o si el objeto se ha finalizado antes \(por ejemplo, posiblemente teniendo Abort\(\) ejecutándose en otro subproceso\).De lo contrario establece el estado a Cerrando y llama a OnClosing\(\) \(que desencadena el evento Cerrando\), OnAbort\(\) y OnClosed\(\) en ese orden \(no llama a OnClose porque se está finalizando el objeto, no cerrado\).OnClosed\(\) establece el estado en Cerrado y desencadena el evento Cerrado.Si cualquiera de estas operaciones provoca una excepción, se reinicia el llamador de Anular.Las implementaciones de OnClosing\(\), OnClosed\(\) y OnAbort\(\) no se deberían bloquear \(por ejemplo, en entrada\/salida\).El diagrama siguiente muestra con más detalle el proceso Anular.  
  
 ![Cambios de estado](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure8ico-abortflowchartc.gif "wcfc\_WCFChannelsigure8ICO\-AbortFlowChartc")  
Invalide el método OnAbort para implementar lógica de finalización personalizada como finalizar un objeto de comunicación interno.  
  
 Error  
  
 El método Error es específico de <xref:System.ServiceModel.Channels.CommunicationObject> y no forma parte de la interfaz <xref:System.ServiceModel.ICommunicationObject>.Se incluye aquí para proporcionar información completa.  
  
 Condición previa: ninguna.  
  
 Condición posterior: el estado es Error.Podría iniciar una excepción.  
  
 El método Fault\(\) no hace nada si el estado actual es Error o Cerrado.De lo contrario establece el estado a Error y llama a OnFaulted\(\), que desencadena el evento Error.Si OnFaulted producir una excepción se reinicia.  
  
### Métodos ThrowIfXxx  
 CommunicationObject tiene tres métodos protegidos que se pueden utilizar para producir excepciones si el objeto está en un estado concreto.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposed%2A> produce una excepción si el estado es Cerrando, Cerrado o Error.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrImmutable%2A> produce una excepción si el estado no es Creado.  
  
 <xref:System.ServiceModel.Channels.CommunicationObject.ThrowIfDisposedOrNotOpen%2A> produce una excepción si el estado no es Abierto.  
  
 Las excepciones iniciadas dependen del estado.La tabla siguiente muestra los diferentes estados y el tipo de excepción correspondiente iniciados llamando a ThrowIfXxx que se inicia en ese estado.  
  
|Estado|¿Se ha llamado a Anular?|Excepción|  
|------------|------------------------------|---------------|  
|Creado|N\/D|<xref:System.InvalidOperationException?displayProperty=fullName>|  
|Abriendo|N\/D|<xref:System.InvalidOperationException?displayProperty=fullName>|  
|Abierto|N\/D|<xref:System.InvalidOperationException?displayProperty=fullName>|  
|Closing|Sí|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=fullName>|  
|Cerrando|No|<xref:System.ObjectDisposedException?displayProperty=fullName>|  
|Cerrado|Sí|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=fullName> en el caso de que una llamada anterior y explícita de Anular cerrara un objeto.Si llama a Cerrar en el objeto, se produce <xref:System.ObjectDisposedException?displayProperty=fullName>.|  
|Closed|No|<xref:System.ObjectDisposedException?displayProperty=fullName>|  
|Error|N\/D|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=fullName>|  
  
### Tiempos de espera  
 Algunos de los métodos que hemos abordado utilizan parámetros de tiempo de espera.Son Cerrar, Abrir \(ciertas sobrecargas y versiones asincrónicas\), OnClose y OnOpen.Estos métodos están diseñados para permitir las operaciones largas \(por ejemplo, bloquear en entrada\/salida mientras se cierra una conexión\) de modo que el parámetro de tiempo de espera indica cuánto tiempo pueden tardar tales operaciones antes de ser interrumpidas.Las implementaciones de cualquiera de estos métodos deberían utilizar el valor de tiempo de espera proporcionado para garantizar que vuelvan al llamador dentro de ese tiempo de espera.Las implementaciones de otros métodos que no tienen un tiempo de espera no están diseñadas para las operaciones largas y no se bloquean en entrada\/salida.  
  
 Las excepciones son las sobrecargas de Open\(\) y Close\(\) que no tienen un tiempo de espera.Estos usan un valor de tiempo de espera predeterminado proporcionado por la clase derivada.<xref:System.ServiceModel.Channels.CommunicationObject> expone dos propiedades abstractas protegidas denominadas <xref:System.ServiceModel.Channels.CommunicationObject.DefaultCloseTimeout%2A> y <xref:System.ServiceModel.Channels.CommunicationObject.DefaultOpenTimeout%2A> definidas como:  
  
 `protected abstract TimeSpan DefaultCloseTimeout { get; }`  
  
 `protected abstract TimeSpan DefaultOpenTimeout { get; }`  
  
 Una clase derivada implementa estas propiedades para proporcionar el tiempo de espera predeterminado para las sobrecargas Open\(\) y Close\(\) que no tienen un valor de tiempo de espera.A continuación, las implementaciones de Open\(\) y Close\(\) delegan a la sobrecarga que tiene un tiempo de espera que les pase el valor de tiempo de espera predeterminado, por ejemplo:  
  
 `public void Open()`  
  
 `{`  
  
 `this.Open(this.DefaultOpenTimeout);`  
  
 `}`  
  
#### IDefaultCommunicationTimeouts  
 Esta interfaz tiene cuatro propiedades de solo lectura para proporcionar los valores de tiempo de espera predeterminados para abrir, enviar, recibir y cerrar.Cada implementación es responsable de obtener los valores predeterminados de la manera apropiada.Como una comodidad, <xref:System.ServiceModel.Channels.ChannelFactoryBase> y <xref:System.ServiceModel.Channels.ChannelListenerBase> tienen como valor predeterminado de estos valores 1 minuto cada uno.