---
title: "CorBindToRuntimeHost (Función)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6d69f39aa74665843b0bf91407e764ea67f41d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost (Función)
Permite a los hosts cargar una versión determinada de Common Language Runtime (CLR) en un proceso.  
  
 Esta función está desusada en [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pwszVersion`  
 [in] Cadena que describe la versión de CLR que se desea cargar.  
  
 Un número de versión de .NET Framework consta de cuatro partes separadas por puntos: *principal.secundaria.compilación.revisión*. La cadena que se pasó como `pwszVersion` debe comenzar con el carácter "v" seguido de las primeras tres partes del número de versión (por ejemplo, "v1.0.1529").  
  
 Algunas versiones de CLR se instalan con una instrucción de directiva que especifica la compatibilidad con versiones anteriores de CLR. De forma predeterminada, el proceso intermedio ("shim") de inicio evalúa `pwszVersion` con las instrucciones de directiva y carga la versión más reciente del runtime compatible con la versión solicitada. Un host puede hacer que el proceso intermedio ("shim") omita la evaluación de directivas y cargue exactamente la versión especificada en `pwszVersion`, pasando el valor STARTUP_LOADER_SAFEMODE para el parámetro `startupFlags`.  
  
 Si `pwszVersion` es `null,` el método no carga ninguna versión de CLR. En su lugar, devuelve CLR_E_SHIM_RUNTIMELOAD, que indica que no se cargó el runtime.  
  
 `pwszBuildFlavor`  
 [in] Cadena que especifica si se debe cargar la compilación de CLR para servidor o para estación de trabajo. Los valores válidos son `svr` y `wks`. La compilación para servidor está optimizada para aprovechar las ventajas que aportan varios procesadores al realizar recolecciones de elementos no utilizados, mientras que la compilación para estación de trabajo está optimizada para aplicaciones cliente que se ejecutan en equipos con un solo procesador.  
  
 Si `pwszBuildFlavor` se establece en null, se cargará la compilación para estación de trabajo. Cuando se ejecuta en un equipo con un solo procesador, siempre se carga con la compilación de la estación de trabajo, incluso si `pwszBuildFlavor` está establecido en `svr`. Sin embargo, si `pwszBuildFlavor` está establecido en `svr` y se especifica una colección de elementos no utilizados simultánea (vea la descripción de la `startupFlags` parámetro), se carga la versión del servidor.  
  
> [!NOTE]
>  No se admite la recolección de elementos no utilizados simultánea en aplicaciones en las que se ejecuta el emulador WOW64 x86 en sistemas de 64 bits y que implementan la arquitectura Intel Itanium (denominada anteriormente IA-64). Para obtener más información sobre el uso de WOW64 en sistemas de Windows de 64 bits, consulte [aplicaciones Running 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).  
  
 `pwszHostConfigFile`  
 [in] Nombre de un archivo de configuración de host que especifica la versión de CLR que se debe cargar. Si el nombre de archivo no incluye una ruta de acceso completa, se supone que este se encuentra en el mismo directorio que el ejecutable que realiza la llamada.  
  
 `pReserved`  
 [in] Reservado para extensibilidad futura.  
  
 `startupFlags`  
 [in] Conjunto de marcas que controla la recolección de elementos no utilizados simultánea, el código neutral respecto al dominio y el comportamiento del parámetro `pwszVersion`. Si no se establece ninguna marca, el valor predeterminado es un dominio único. Para obtener una lista de valores admitidos, consulte el [STARTUP_FLAGS (enumeración)](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [in] El `CLSID` de la coclase que implementa la [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfaz. Los valores admitidos son CLSID_CorRuntimeHost o CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] El `IID` de la interfaz solicitada. Los valores admitidos son IID_ICorRuntimeHost o IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Puntero de interfaz a la versión del runtime que se cargó.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** MSCorEE.idl  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [CorBindToCurrentRuntime (función)](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime (función)](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg (función)](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx (función)](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICorRuntimeHost (interfaz)](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Funciones de hospedaje de CLR en desuso](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
