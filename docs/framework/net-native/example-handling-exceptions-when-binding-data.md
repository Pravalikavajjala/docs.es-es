---
title: 'Ejemplo: control de excepciones al enlazar datos'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2714d53426bfee22b3d83d76b766816d9bc9d60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="example-handling-exceptions-when-binding-data"></a>Ejemplo: control de excepciones al enlazar datos
> [!NOTE]
>  En este tema se hace referencia a .NET Native Developer Preview, que es una versión preliminar del software. Puede descargar esta versión preliminar desde el [sitio web de Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=394611) (es necesario registrarse).  
  
 En el siguiente ejemplo se explica cómo resolver una excepción [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) que se genera cuando una aplicación compilada con la cadena de herramientas de [!INCLUDE[net_native](../../../includes/net-native-md.md)] intenta enlazar datos. Esta es la información de la excepción:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 Esta es la pila de llamadas asociada:  
  
```  
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a>¿Qué ha hecho la aplicación?  
 En la base de la pila, los marcos del espacio de nombres [Windows.UI.Xaml](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.aspx) indican que el motor de representación XAML se estaba ejecutando.   El uso del método <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> indica una búsqueda basada en la reflexión del valor de una propiedad en el tipo cuyos metadatos se han quitado.  
  
 El primer paso para proporcionar una directiva de metadatos sería agregar metadatos `serialize` para el tipo de forma que sus propiedades sean accesibles:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>¿Se trata de un caso aislado?  
 En este escenario, si el enlace de datos tiene metadatos incompletos para un `ViewModel`, es posible que también los tenga para otros.  Si el código está estructurado de forma que todos los modelos de vista de la aplicación están incluidos en el espacio de nombres `App.ViewModels`, se podría usar una directiva en tiempo de ejecución más general:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>¿Se podría volver a escribir el código para que no use la reflexión?  
 Los enlaces de datos hacen un uso intensivo de la reflexión, de modo que cambiar el código para evitar la reflexión no es factible.  
  
 Sin embargo, hay formas de especificar el `ViewModel` en la página XAML para que la cadena de herramientas pueda asociar enlaces de propiedad con el tipo correcto en tiempo de compilación y mantener los metadatos sin usar una directiva en tiempo de ejecución.  Por ejemplo, puede aplicar el atributo [Windows.UI.Xaml.Data.BindableAttribute](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.data.bindableattribute.aspx) en las propiedades. Esto hace que el compilador XAML genere la información de búsqueda necesaria y permite prescindir de una directiva en tiempo de ejecución en el archivo Default.rd.xml.  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Ejemplo: solucionar problemas de programación dinámica](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
