---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fb3cf8457dc19081e9eb51091453764513da8ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a>&lt;bookmarkResumptionQueries&gt;
Representa una colección de consultas que se usan para realizar el seguimiento de la reanudación de un marcador dentro de una instancia de flujo de trabajo. La consulta es necesaria para que un participante del seguimiento se suscriba a los registros de reanudación del marcador.  
  
 Para obtener más información sobre las consultas de perfil de seguimiento, vea [perfiles de seguimiento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel >  
\<seguimiento >  
\<trackingProfile >  
\<flujo de trabajo >  
\<bookmarkResumptionQueries >  
\<bookmarkResumptionQuery >  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|Una consulta que se usa para realizar el seguimiento de la reanudación de un marcador dentro de una instancia de flujo de trabajo. La consulta es necesaria para que un participante del seguimiento se suscriba a los registros de reanudación del marcador.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[\<flujo de trabajo >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|Un elemento de configuración que contiene todas las consultas para un flujo de trabajo concreto identificado por la **activityDefinitionId** propiedad.|  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [Seguimiento y traza de flujos de trabajo](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Perfiles de seguimiento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
