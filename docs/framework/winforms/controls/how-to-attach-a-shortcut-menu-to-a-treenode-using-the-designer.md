---
title: "Cómo: Adjuntar un menú contextual a un objeto TreeNode mediante el Diseñador"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ab73f6e4dc6a4e348853183046db564e748360b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Cómo: Adjuntar un menú contextual a un objeto TreeNode mediante el Diseñador
Los formularios Windows Forms <xref:System.Windows.Forms.TreeView> control muestra una jerarquía de nodos, similares a los archivos y las carpetas que aparecen en el panel izquierdo de la característica Explorador de Windows en sistemas operativos Windows. Estableciendo la <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propiedad, puede proporcionar operaciones contextuales al usuario cuando haga clic en el <xref:System.Windows.Forms.TreeView> control. Asociando un <xref:System.Windows.Forms.ContextMenuStrip> componente de individual <xref:System.Windows.Forms.TreeNode> elementos, puede agregar un nivel personalizado de funcionalidad del menú contextual para su <xref:System.Windows.Forms.TreeView> controles.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Para asociar un menú contextual a un objeto TreeNode en tiempo de diseño  
  
1.  Agregar un <xref:System.Windows.Forms.TreeView> control al formulario y, a continuación, agregar nodos a la <xref:System.Windows.Forms.TreeView> según sea necesario. Para obtener más información, consulte [Cómo: agregar y quitar nodos con el TreeView Control de formularios Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Agregar un <xref:System.Windows.Forms.ContextMenuStrip> componente al formulario y, a continuación, agregar elementos de menú al menú contextual que representan las operaciones de nivel de nodo que desea que estén disponibles en tiempo de ejecución. Para obtener más información, consulte [Cómo: agregar elementos de menú a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Vuelva a abrir la **TreeNodeEditor** cuadro de diálogo para la <xref:System.Windows.Forms.TreeView> de control, seleccione el nodo para editar y establecer su <xref:System.Windows.Forms.ContextMenuStrip> propiedad en el menú contextual que agregó.  
  
4.  Cuando se establece esta propiedad, se mostrará el menú contextual cuando haga clic en el nodo.  
  
     Además, desea escribir código para controlar la <xref:System.Windows.Forms.ToolStripItem.Click> eventos para estos elementos de menú.  
  
## <a name="see-also"></a>Vea también  
 [TreeView (control)](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Información general del control TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [ContextMenuStrip (Control)](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
