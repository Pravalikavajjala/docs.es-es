---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f3db50a32fabc117c79eef5ac086a7798f86ed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="activitytransfer"></a>ActivityTransfer
Evento de transferencia de actividad  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Métodos  
 La clase ActivityTransfer no define ningún método.  
  
## <a name="properties"></a>Propiedades  
 La clase ActivityTransfer posee las propiedades siguientes:  
  
### <a name="activityid"></a>ActivityID  
  
-   Tipo de datos: objeto  
    Tipo de acceso: solo lectura  
  
-   Id. de actividad  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   Tipo de datos: objeto  
    Tipo de acceso: solo lectura  
  
-   Id. de actividad relacionada  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Se declara en Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espacio de nombres|Se define en root\ServiceModel.|
