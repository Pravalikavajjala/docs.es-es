---
title: "Cómo: Obtener acceso a una variable que oculta una clase derivada (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f94e45fcb0a26b0d59789e101c37aceba219250
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Cómo: Obtener acceso a una variable que oculta una clase derivada (Visual Basic)
Cuando el código en una clase derivada tiene acceso a una variable, el compilador resuelve normalmente la referencia a la versión accesible más cercana, es decir, la versión accesible los mínimos pasos de derivación en sentido con versiones anteriores de la clase que tiene acceso. Si la variable se define en la clase derivada, el código tiene acceso normalmente a esa definición.  
  
 Si la variable de clase derivada oculta una variable en la clase base, oculta la versión de la clase base. Sin embargo, puede acceder a la variable de clase base mediante su calificación con la `MyBase` palabra clave.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Para obtener acceso a una variable de clase base oculta mediante una clase derivada  
  
-   En una expresión o instrucción de asignación, incluya delante del nombre de variable con el `MyBase` palabra clave y un período (`.`).  
  
     El compilador resuelve la referencia a la versión de la clase base de la variable.  
  
     En el ejemplo siguiente se ilustra el sombreado por herencia. Realiza dos referencias, una que tiene acceso a la variable de sombreado y otra que omite el sombreado.  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     En el ejemplo anterior se declara la variable `shadowString` en la clase base y la sombra en la clase derivada. El procedimiento `showStrings` en la clase derivada muestra la versión de sombreado de la cadena cuando el nombre `shadowString` no está calificado. A continuación, muestra la versión sombreada cuando `shadowString` se califica con el `MyBase` palabra clave.  
  
## <a name="robust-programming"></a>Programación sólida  
 Para reducir el riesgo de que hace referencia a una versión no deseada de una variable sombreada, puede calificar por completo todas las referencias a una variable sombreada. El sombreado presenta más de una versión de una variable con el mismo nombre. Cuando una instrucción de código hace referencia al nombre de variable, la versión a la que el compilador resuelve la referencia depende de factores como la ubicación de la instrucción de código y la presencia de una cadena de calificación. Esto puede aumentar el riesgo de que hace referencia a una versión incorrecta de la variable.  
  
## <a name="see-also"></a>Vea también  
 [Referencias a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Sombrear en Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Diferencias entre sombrear y reemplazar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Ocultar una variable con el mismo nombre que su variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Ocultar una variable heredada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase y MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Fundamentos de la herencia](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
