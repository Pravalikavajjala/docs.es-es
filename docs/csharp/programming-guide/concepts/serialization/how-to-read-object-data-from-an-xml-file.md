---
title: "Cómo: Leer datos de objetos de un archivo XML (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c5f8c23a86c7a09d6f8d0b8c6f1684a38d0336a3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Cómo: Leer datos de objetos de un archivo XML (C#)
En este ejemplo se leen los datos de objetos que se han escrito anteriormente en un archivo XML con la clase <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Ejemplo  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Reemplace el nombre de archivo "c:\temp\SerializationOverview.xml" por el nombre del archivo que contiene los datos serializados. Para obtener más información sobre la serialización de datos, vea [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) (Cómo: Escribir datos de objetos en un archivo XML (C#)).  
  
 La clase debe tener un constructor público sin parámetros.  
  
 Solo se deserializan las propiedades y los campos públicos.  
  
## <a name="robust-programming"></a>Programación sólida  
 Las condiciones siguientes pueden provocar una excepción:  
  
-   La clase que se está serializando no tiene un constructor público sin parámetros.  
  
-   Los datos del archivo no representan los datos de la clase que se va a deserializar.  
  
-   El archivo no existe (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Seguridad de .NET Framework  
 Compruebe siempre las entradas y nunca deserialice datos de un origen que no sea de confianza. El objeto que se ha vuelto a crear se ejecuta en un equipo local con los permisos del código que lo ha deserializado. Compruebe todas las entradas antes de utilizar los datos en la aplicación.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.IO.StreamWriter>   
 [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  (Cómo: Escribir datos de objetos en un archivo XML (C#))  
 [Serialization (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md)  (Serialización (C#))  
 [Guía de programación de C#](../../../../csharp/programming-guide/index.md)