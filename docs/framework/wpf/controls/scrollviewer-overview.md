---
title: "Información general sobre ScrollViewer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7317bade85641d7d055facabcf7103b945609583
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="scrollviewer-overview"></a>Información general sobre ScrollViewer
El contenido en una interfaz de usuario suele ser mayor que el área de presentación de la pantalla del equipo. El <xref:System.Windows.Controls.ScrollViewer> control proporciona una manera cómoda de habilitar el desplazamiento de contenido en [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicaciones. Este tema se presentan los <xref:System.Windows.Controls.ScrollViewer> elemento y se proporcionan varios ejemplos de uso.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Control ScrollViewer  
 Hay dos elementos predefinidos que habilitan el desplazamiento en [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicaciones: <xref:System.Windows.Controls.Primitives.ScrollBar> y <xref:System.Windows.Controls.ScrollViewer>. El <xref:System.Windows.Controls.ScrollViewer> control encapsula horizontal y vertical <xref:System.Windows.Controls.Primitives.ScrollBar> elementos y un contenedor de contenido (como un <xref:System.Windows.Controls.Panel> elemento) para mostrar otros elementos visibles en un área desplazable. Debe crear un objeto personalizado para poder usar el <xref:System.Windows.Controls.Primitives.ScrollBar> , elemento de contenido que se desplaza. Sin embargo, puede usar el <xref:System.Windows.Controls.ScrollViewer> elemento por sí solo, porque es una composición de control que encapsula <xref:System.Windows.Controls.Primitives.ScrollBar> funcionalidad.  
  
 El <xref:System.Windows.Controls.ScrollViewer> control responde a los comandos del mouse y teclado y define numerosos métodos con los que se va a desplazarse por el contenido en incrementos predeterminados. Puede usar el <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> eventos para detectar un cambio en un <xref:System.Windows.Controls.ScrollViewer> estado.  
  
 A <xref:System.Windows.Controls.ScrollViewer> sólo puede tener un elemento secundario, normalmente un <xref:System.Windows.Controls.Panel> elemento que puede hospedar una <xref:System.Windows.Controls.Panel.Children%2A> colección de elementos. El <xref:System.Windows.Controls.ContentPresenter.Content%2A> propiedad define el único elemento secundario de la <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Desplazamiento físico y lógico  
 El desplazamiento físico se utiliza para desplazar el contenido mediante incrementos físicos predeterminados, normalmente por un valor que se declara en píxeles. El desplazamiento lógico se utiliza para desplazarse al elemento siguiente del árbol lógico. El desplazamiento físico es el comportamiento de desplazamiento predeterminado para la mayor parte <xref:System.Windows.Controls.Panel> elementos. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] admite ambos tipos de desplazamiento.  
  
#### <a name="the-iscrollinfo-interface"></a>Interfaz IScrollInfo  
 El <xref:System.Windows.Controls.Primitives.IScrollInfo> interfaz representa la región desplazable principal dentro de un <xref:System.Windows.Controls.ScrollViewer> o control derivado. La interfaz define el desplazamiento de propiedades y métodos que pueden ser implementadas por <xref:System.Windows.Controls.Panel> elementos que requieren desplazamiento por unidad lógica, en lugar de en un incremento físico. Convertir una instancia de <xref:System.Windows.Controls.Primitives.IScrollInfo> hasta un derivada <xref:System.Windows.Controls.Panel> y, a continuación, usando sus métodos de desplazamiento proporciona una manera útil para desplazarse a la siguiente unidad lógica en una colección secundaria, en lugar de por incrementos en píxeles. De forma predeterminada, el <xref:System.Windows.Controls.ScrollViewer> control admite el desplazamiento por unidades físicas.  
  
 <xref:System.Windows.Controls.StackPanel>y <xref:System.Windows.Controls.VirtualizingStackPanel> ambos implementan <xref:System.Windows.Controls.Primitives.IScrollInfo> y admiten de forma nativa el desplazamiento lógico. Para controles de diseño de esa forma nativa compatibilidad con el desplazamiento lógico, se puede mantener un desplazamiento físico ajustando el host <xref:System.Windows.Controls.Panel> elemento en un <xref:System.Windows.Controls.ScrollViewer> y estableciendo el <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> propiedad `false`.  
  
 En el ejemplo de código siguiente se muestra cómo convertir una instancia de <xref:System.Windows.Controls.Primitives.IScrollInfo> a una <xref:System.Windows.Controls.StackPanel> y usar los métodos de desplazamiento de contenido (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> y <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) definidos por la interfaz.  
  
 [!code-csharp[IScrollInfoMethods#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Definir y utilizar un elemento ScrollViewer  
 En el ejemplo siguiente se crea un <xref:System.Windows.Controls.ScrollViewer> en una ventana que contiene texto y un rectángulo. <xref:System.Windows.Controls.Primitives.ScrollBar>los elementos aparecen solo cuando son necesarios. Cuando cambia el tamaño de la ventana, el <xref:System.Windows.Controls.Primitives.ScrollBar> elementos aparecen y desaparecen, debido a los valores actualizados de la <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> y <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> propiedades.  
  
 [!code-cpp[ScrollViewer#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Aplicar estilos a ScrollViewer  
 Al igual que todos los controles en Windows Presentation Foundation, el <xref:System.Windows.Controls.ScrollViewer> puede ser un estilo con el fin de cambiar el comportamiento de representación predeterminado del control. Para obtener información adicional sobre los estilos de control, consulte [Aplicar estilos y plantillas](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Paginar documentos  
 Para el contenido del documento, una alternativa al desplazamiento es elegir un contenedor de documentos que admita la paginación. <xref:System.Windows.Documents.FlowDocument>es para los documentos que están diseñados para ser hospedados dentro de un control de visualización, como <xref:System.Windows.Controls.FlowDocumentPageViewer>, que permite paginar el contenido en varias páginas, evitando la necesidad de desplazamiento. <xref:System.Windows.Controls.DocumentViewer>Proporciona una solución para su visualización <xref:System.Windows.Documents.FixedDocument> contenido, que usa el desplazamiento tradicional para mostrar el contenido fuera del dominio Kerberos del área de presentación.  
  
 Para más información sobre los formatos de documentos y opciones de presentación, consulte [Documents in WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md) (Documentos en WPF).  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.Primitives.ScrollBar>  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>  
 [Crear un visor de desplazamiento](http://msdn.microsoft.com/library/c8e46af7-b417-441b-aa30-791cbdbd43ef)  
 [Documentos en WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [ScrollBar Styles and Templates](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md) (Estilos y plantillas de ScrollBar)  
 [Controles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
