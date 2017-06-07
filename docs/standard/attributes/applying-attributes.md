---
title: "Aplicar atributos | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ensamblados [.NET Framework], atributos"
  - "atributos [.NET Framework], aplicar"
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Aplicar atributos
Para aplicar un atributo a un elemento del código se puede utilizar el proceso siguiente:  
  
1.  Definir un atributo nuevo o utilizar uno existente importando su espacio de nombres de .NET Framework.  
  
2.  Aplique el atributo al elemento de código colocándolo inmediatamente antes del elemento.  
  
     Cada lenguaje tiene su propia sintaxis de atributo.  En C\+\+ y C\#, el atributo está incluido entre corchetes y separado del elemento por un espacio en blanco, que puede incluir un salto de línea.  En Visual Basic, el atributo está incluido entre corchetes angulares y debe estar en la misma línea lógica; se puede utilizar el carácter de continuación de línea si se desea un salto de línea.  En J\#, el atributo está asociado mediante una sintaxis de comentario especial.  
  
3.  Especifique parámetros posicionales y parámetros con nombre para el atributo.  
  
     Los parámetros posicionales son obligatorios y preceden a cualquier parámetro con nombre; corresponden a los parámetros de uno de los constructores del atributo.  Los parámetros con nombre son opcionales y corresponden a las propiedades de lectura y escritura del atributo.  En C\+\+, C\# y J\#, especifique `name`\=`value` para cada parámetro opcional, donde `name` es el nombre de la propiedad.  En Visual Basic, especifique `name`:\=`value`.  
  
 El atributo se emite en metadatos al compilar el código y queda disponible para Common Language Runtime y cualquier aplicación o herramienta personalizada a través de los servicios de reflexión en tiempo de ejecución.  
  
 Por convención, todos los nombres de atributos terminan con la palabra Attribute.  Sin embargo, algunos lenguajes orientados a Common Language Runtime, como Visual Basic y C\#, no requieren que se especifique el nombre completo de los atributos.  Por ejemplo, si desea inicializar <xref:System.ObsoleteAttribute?displayProperty=fullName>, sólo es necesario hacer referencia al mismo como **Obsolete**.  
  
## Aplicar un atributo a un método  
 El siguiente ejemplo de código muestra cómo se declara **System.ObsoleteAttribute**, que marca código como obsoleto.  La cadena `"Will be removed in next version"` se pasa al atributo.  Este atributo da lugar a una advertencia del compilador que muestra la cadena transferida cuando se llama al código que describe el atributo.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## Aplicar atributos a ensamblados  
 Si desea aplicar un atributo a un ensamblado, utilice la palabra clave **assembly** \(`Assembly` en Visual Basic\).  El código siguiente muestra el atributo **AssemblyTitleAttribute** aplicado a un ensamblado.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Cuando se aplica este atributo, la cadena `"My Assembly"` se coloca en el manifiesto del ensamblado, en la parte de metadatos del archivo.  Se puede ver el atributo utilizando el [Desensamblador de MSIL \(Ildasm.exe\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) o creando un programa personalizado que recupere el atributo.  
  
## Vea también  
 [Atributos](../../../docs/standard/attributes/index.md)   
 [Recuperar información almacenada en atributos](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)   
 [Concepts](../Topic/Attributed%20Programming%20Concepts.md)   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)