---
title: "Basic LINQ Query Operations (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "orderby clause [LINQ in C#]"
  - "ordering data [LINQ in C#]"
  - "selecting data [LINQ in C#]"
  - "queries [LINQ in C#], basic operations"
  - "grouping data [LINQ in C#]"
  - "data sources [LINQ in C#]"
  - "sorting data [LINQ in C#]"
  - "projections [LINQ in C#]"
  - "filtering data [LINQ in C#]"
  - "joining data [LINQ in C#]"
  - "select clause [LINQ in C#]"
  - "LINQ [C#], basic query operations"
  - "join clause [LINQ in C#]"
  - "group clause [LINQ in C#]"
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 37
---
# Basic LINQ Query Operations (C#)
En este tema se ofrece una breve introducción a las expresiones de consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] y algunas de las clases de operaciones típicas que se realizan en una consulta.  En los temas siguientes se ofrece información más detallada:  
  
 [Expresiones de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Si ya está familiarizado con un lenguaje de consultas como SQL o XQuery, puede omitir la mayoría de este tema.  Lea la parte dedicada a la cláusula `from` en la sección siguiente para obtener información sobre el orden de las cláusulas en las expresiones de consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  
  
## Obtener un origen de datos  
 En una consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], el primer paso es especificar el origen de datos.  En C\#, como en la mayoría de los lenguajes de programación, se debe declarar una variable antes de poder utilizarla.  En una consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], la cláusula `from` aparece en primer lugar para introducir el origen de datos \(`customers`\) y la *variable de rango* \(`cust`\).  
  
 [!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 La variable de rango es como la variable de iteración en un bucle `foreach`, con la diferencia de que en una expresión de consulta realmente no se produce ninguna iteración.  Cuando se ejecuta la consulta, la variable de rango actúa como referencia para cada elemento sucesivo de `customers`.  Dado que el compilador puede deducir el tipo de `cust`, no tiene que especificarlo explícitamente.  Una cláusula `let` puede introducir variables de rango adicionales.  Para obtener más información, consulte [let \(cláusula\)](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  Para los orígenes de datos no genéricos, como <xref:System.Collections.ArrayList>, el tipo de la variable de rango debe establecerse explícitamente.  Para obtener más información, consulte [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md) y [from \(cláusula\)](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## Filtrar  
 Probablemente la operación de consulta más común es aplicar un filtro en forma de expresión booleana.  El filtro hace que la consulta devuelva sólo los elementos para los que la expresión es verdadera.  El resultado se genera mediante la cláusula `where`.  El filtro aplicado especifica qué elementos se deben excluir de la secuencia de origen.  En el ejemplo siguiente, sólo se devuelven los `customers` cuya dirección se encuentra en Londres \(London\).  
  
 [!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 Puede utilizar los operadores lógicos `AND` y `OR` de C\#, con los que ya estará familiarizado, para aplicar las expresiones de filtro que sean necesarias en la cláusula `where`.  Por ejemplo, para devolver sólo los clientes con dirección en "London" `AND` cuyo nombre sea "Devon", escribiría el código siguiente:  
  
 [!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 Para devolver los clientes con dirección en Londres o París, escribiría el código siguiente:  
  
 [!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 Para obtener más información, consulte [where \(cláusula\)](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## Ordering  
 A menudo es necesario ordenar los datos devueltos.  La cláusula `orderby` hará que los elementos de la secuencia devuelta se ordenen según el comparador predeterminado del tipo que se va a ordenar.  Por ejemplo, la consulta siguiente se puede extender para ordenar los resultados según la propiedad `Name`.  Dado que `Name` es una cadena, el comparador predeterminado realiza una ordenación alfabética de la A a la Z.  
  
 [!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 Para ordenar los resultados en orden inverso, de la Z a la A, utilice la cláusula `orderby…descending`.  
  
 Para obtener más información, consulte [orderby \(cláusula\)](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## Grupo  
 La cláusula `group` permite agrupar los resultados según la clave que se especifique.  Por ejemplo, podría especificar que los resultados se agrupen por `City` para que todos los clientes de London o París estén en grupos individuales.  En este caso, la clave es `cust.City`.  
  
 [!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 Al finalizar una consulta con una cláusula `group`, los resultados adoptan la forma de una lista de listas.  Cada elemento de la lista es un objeto que tiene un miembro `Key` y una lista de elementos agrupados bajo esa clave.  Al procesar una iteración en una consulta que genera una secuencia de grupos, debe utilizar un bucle `foreach` anidado.  El bucle exterior recorre en iteración cada grupo y el bucle interior recorre en iteración los miembros de cada grupo.  
  
 Si debe hacer referencia a los resultados de una operación de grupo, puede utilizar la palabra clave `into` para crear un identificador con el que se puedan realizar más consultas.  La consulta siguiente devuelve sólo los grupos que contienen más de dos clientes:  
  
 [!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 Para obtener más información, consulte [group \(cláusula\)](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## Combinación  
 Las operaciones de combinación crean asociaciones entre las secuencias que no se modelan explícitamente en los orígenes de datos.  Por ejemplo, puede realizar una combinación para buscar todos los clientes y distribuidores que tengan la misma ubicación.  En [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], la cláusula `join` funciona siempre con colecciones de objetos, en lugar de con tablas de base de datos directamente.  
  
 [!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 En [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] no es necesario utilizar `join` tan a menudo como en SQL, porque las claves externas en [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] se representan en el modelo de objetos como propiedades que contienen una colección de elementos.  Por ejemplo, un objeto `Customer` contiene una colección de objetos `Order`.  En lugar de realizar una combinación, se tiene acceso a los pedidos utilizando la notación de punto:  
  
```  
from order in Customer.Orders...  
```  
  
 Para obtener más información, consulte [join \(cláusula\)](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## Selección \(proyecciones\)  
 La cláusula `select` genera resultados de consulta y especifica la "forma" o el tipo de cada elemento devuelto.  Por ejemplo, puede especificar si sus resultados estarán compuestos de objetos `Customer` completos, un solo miembro, un subconjunto de miembros o algún tipo de resultado completamente diferente basado en un cálculo o en un objeto nuevo.  Cuando la cláusula `select` genera algo distinto de una copia del elemento de origen, la operación se denomina *proyección*.  El uso de proyecciones para transformar los datos es una eficaz funcionalidad de las expresiones de consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  Para obtener más información, consulte [Transformaciones de datos con LINQ \(C\#\)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) y [select \(cláusula\)](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## Vea también  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Expresiones de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Palabras clave para consultas \(LINQ\)](../../../../csharp/language-reference/keywords/query-keywords.md)   
 [Tipos anónimos](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Operaciones básicas de consulta \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)