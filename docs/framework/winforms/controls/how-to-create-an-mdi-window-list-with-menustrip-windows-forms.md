---
title: "Cómo: Crear una lista de ventanas MDI con MenuStrip (formularios Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MDI [Windows Forms], creating window lists
- MenuStrip control [Windows Forms], creating window lists
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8bf09170b4def3f041e34942a968fdf41fcdf66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-mdi-window-list-with-menustrip-windows-forms"></a>Cómo: Crear una lista de ventanas MDI con MenuStrip (formularios Windows Forms)
Usar la interfaz de múltiples documentos (MDI) para crear aplicaciones que pueden abrir varios documentos al mismo tiempo y copie y pegue el contenido de un documento a otro.  
  
 Este procedimiento muestra cómo crear una lista de todos los formularios secundarios activos en el menú de la ventana del elemento primario.  
  
### <a name="to-create-an-mdi-window-list-on-a-menustrip"></a>Para crear una lista de ventanas MDI en un control MenuStrip  
  
1.  Cree un formulario y establezca su propiedad <xref:System.Windows.Forms.Form.IsMdiContainer%2A> en `true`.  
  
2.  Agregue un control <xref:System.Windows.Forms.MenuStrip> al formulario.  
  
3.  Agregar dos elementos de menú de nivel superior a la <xref:System.Windows.Forms.MenuStrip> y establezca sus <xref:System.Windows.Forms.Control.Text%2A> propiedades `&File` y `&Window`.  
  
4.  Agregue un elemento de submenú al elemento de menú `&File` y establezca su propiedad <xref:System.Windows.Forms.ToolStripItem.Text%2A> en `&Open`.  
  
5.  Establecer el <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propiedad de la <xref:System.Windows.Forms.MenuStrip> a la `&Window` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Agregue un formulario al proyecto y agregue el control que desee, por ejemplo, otro <xref:System.Windows.Forms.MenuStrip>.  
  
7.  Cree un controlador para el evento <xref:System.Windows.Forms.Control.Click> del <xref:System.Windows.Forms.ToolStripMenuItem>`&New`.  
  
8.  En el controlador de eventos, inserte código similar al siguiente para crear y mostrar nuevas instancias de `Form2` como elementos secundarios MDI de `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
9. Incluya código similar al siguiente en el `&New` <xref:System.Windows.Forms.ToolStripMenuItem> para registrar el controlador de eventos.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Dos controles <xref:System.Windows.Forms.Form> llamados `Form1` y `Form2`.  
  
-   Un control <xref:System.Windows.Forms.MenuStrip> en `Form1` llamado `menuStrip1` y un control <xref:System.Windows.Forms.MenuStrip> en `Form2` llamado `menuStrip2`.  
  
-   Referencias a los ensamblados <xref:System?displayProperty=nameWithType> y <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Vea también  
 [Crear formularios principales MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Crear formularios MDI secundarios](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Control MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
